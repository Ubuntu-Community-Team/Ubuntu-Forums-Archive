---
title: "[python] My Encrypt &amp; Decrypt Functions"
date: 2009-10-16
forum: Programming Talk
---

### Post by Pyro.699 on 2009-10-16
Hello everyone,

I was looking on the net for an easy way to store passwords in plain text files by encrypting them, then later decrypting them for use. I did find a few examples but nothing that could really help me.

So i built this script, its not perfect but it gets the job done. I was wondering if you could provide some feedback on it for ways i might be able to improve it. Currently you MUST have an even number of encryption values inorder for the script to work properly; I'm not sure why that it but it is something that i would like to fix.

[php]
import re

def encrypt(string, encrypt_values):
    #Turn the string into a list
    split = list(string)
    #Declare the variable
    password = ""
    
    #This will be used to calculate the added length of the initial string (int values)
    x = 0
    
    for char in split:
        #Turn the character into ascii integer
        ascii = ord(char)
        #Add to the total lengeh
        x += ascii
        
        '''
        This is hard to explain, but i will try my best...
        
        It creates a loop that runs from 0 to the length of encrypt_values.
        If the modulo of ascii and the length of encrypt_values is equal to the loop number add it to the password
        '''
        
        for i in range(0,len(encrypt_values)):
            if ascii%(len(encrypt_values)) == i:
                password += "("+str( ((ascii + i) * int(encrypt_values[i]) /2) )+","+str(i)+")."
                break
    
    #Complete the password
    password = "{"+str(x)+"}"+password.rstrip(".")
    return password
    
def decrypt(string, encrypt_values):
    #Get the total length
    total = int(re.search("\{[0-9]*\}", string).group(0).lstrip("{").rstrip("}"))
    #Remove the total length from the main password
    string = re.sub("\{[0-9]*\}", "", string)
    
    #Initiiate the character list
    char_list = ['']
    
    #Seperate by the periods
    list = string.split(".")
    for set in list:
        #Get the inside portion
        ##0 represents the index number within the list
        ##1 represents the value given at that number
        list2 = set.split(",")
        
        #Cheep way to asign each value
        ascii = ""
        even = ""
        for char in list2:
            if ascii == "":
                ascii = char.lstrip("(")
            else:
                even = char.rstrip(")")
        
        #Preform the backwards algorythm to get the first value
        for i in range(0,len(encrypt_values)):
            if even == str(i):
                ascii = ((int(ascii) * 2) / encrypt_values[i]) - i
                break
        
        char_list.insert(-1, ascii)
    
    #Rebuild the password
    password = ""
    x = 0
    for val in char_list:
        if val != "":
            x += int(val)
            password += chr(int(val))+""
    
    #Only return the work if the totals match up
    if (x == total):
        return password
    else:
        return -1
        

values = [43,32,5,34,32,1]
encrypts = ['test', 't3st with numb3rs', '(001 $$$']
for e in encrypts:
    enc = encrypt(e, values)
    dec = decrypt(enc, values)
    print "Original:  %s\nEncrypted: %s\nDecrypted: %s\n" % (e, enc, dec)
[/php]
```

Original:  test
Encrypted: {448}(295,2).(53,5).(1856,1).(295,2)
Decrypted: test

Original:  t3st with numb3rs
Encrypted: {1620}(295,2).(918,3).(1856,1).(295,2).(85,2).(62,5).(1836,3).(295,2).(265,2).(85,2).(280,2).(2040,3).(1760,1).(250,2).(918,3).(2451,0).(1856,1)
Decrypted: t3st with numb3rs

Original:  (001 $$$
Encrypted: {325}(704,4).(1032,0).(1032,0).(800,1).(85,2).(774,0).(774,0).(774,0)
Decrypted: (001 $$$

```

Thank you and i look forward to your responses.
~Cody Woolaver

---

### Post by diesch on 2009-10-16
It's a simple [substitution cipher](http://en.wikipedia.org/wiki/Substitution_cipher) so it can be attacked by [frequency analysis]("http://en.wikipedia.org/wiki/Frequency_analysis").

For production code I recommend to use an existing module like [M2Crypto]("http://pypi.python.org/pypi/M2Crypto/"). See [PyPI]("http://pypi.python.org/pypi?%3Aaction=search&term=crypt&submit=search") for some more modules.

---

### Post by kripkenstein on 2009-10-16
Python comes with hash functions, that are generally used for this sort of thing (the hashlib module). Here is for example the code in Django for this:

[http://code.djangoproject.com/browser/django/trunk/django/contrib/auth/models.py]("http://code.djangoproject.com/browser/django/trunk/django/contrib/auth/models.py")

get_hexdigest gets the hash, and is called by check_password.

Although it seems you want to also decrypt passwords, while the hashing approach never decrypts them. Instead it hashes the passwords people enter and checks if they match the hash values of the true passwords. That's generally considered more secure, but maybe you have a special reason for wanting decryption as well.

---

### Post by Pyro.699 on 2009-10-16
I do need the decrypt method because the passwords are sent via HTTP to a remote server for authentication.

---

### Post by A_Fiachra on 2009-10-16
In general, it is not a good idea to store raw passwords.

What one typically does in this situation is hash the password, save the hashed string, when the password is input again, compare hashes, not the passwords themselves.

For example:


Input : password
hash = sha1(password)
if hash exists, passwords match

Input : new password
hash = sha1(new password)
store hash

Code example :

```

#!  /usr/bin/python
import sys
import hashlib

password = sys.argv[1]

hex_hash = hashlib.sha1(password).hexdigest()

## store hex_hash

```

Typically, you would store {username, hashed_password } in a database or in disk in file.  THe next time the user inputs a password, it is hashed and the hash values are compared.

---

### Post by A_Fiachra on 2009-10-16
> **Pyro.699 said:**
> I do need the decrypt method because the passwords are sent via HTTP to a remote server for authentication.


Again, that's not how to do it.

HTTP isn't a secure protocol.

You should never have to decrypt anything ... compare hashes to hashes.

If you need to securely send messages, look at SSL -- the public key/private key system used for HTTPS.

---

### Post by Pyro.699 on 2010-09-29
So, i know its almost been a year since i made this post but i do have a relevant update. I once again had the need for a encrypting and decrypting function that worked along the lines of a key and lock... Remembering this post i came back to look at the feedback and completely redid the script.

Using the advice that Diesch gave me i looked more into those types of cryptology. I then stumbled across an intersting article on something called "[One-Time Pad]("http://en.wikipedia.org/wiki/One-time_pad")" which was used in world war 2 to send information ... etc (you don't need a war lesson) ...

Anyways here is what i have come-up with now:
[php]
c=""
for x in range(32,127):    c+=chr(x)

def encrypt(s, k):
    s2=[c.find(v) for v in s]
    
    k2=[]
    i=0
    while len(k2) != len(s):
        if i >= len(k):
            i = 0
        k2.append(c.find(k[i]))
        i+=1
        
    r=[c[(j+k)%len(c)] for j,k in zip(s2,k2)]
    return "".join(r)

def decrypt(r, k):
    r2=[c.find(v) for v in r]
    
    k2=[]
    i=0
    while len(k2) != len(r):
        if i >= len(k):
            i = 0
        k2.append(c.find(k[i]))
        i+=1
        
    s=[c[(j-k)%len(c)] for j,k in zip(r2,k2)]
    return "".join(s)

key = "thisKey"
value = "thisPassword"
enc = encrypt(value, key)
dec = decrypt(enc, key)
print "Original String: %s\nKey: %s\nHash: %s\nDecrypted String: %s\nEqual?: %s"%(value, key, enc, dec, value==dec)
[/php]
```

Original String: thisPassword
Key: thisKey
Hash: iQSg{Gmh`Yf0
Decrypted String: thisPassword
Equal?: True

```It works for ascii values from 32 [Space] to 126 [~]

---

### Post by Bachstelze on 2010-09-29
Your code is too complicated IMHO. When dealing with security, your code must be strictly KISS-compliant.

Also, for your OTP to be effective, it needs to be 1) the same length as the plaintest, and 2) perfectly random. If your OTP is shorter than the plaintext, you have a Vigenère cipher. If your OTP is not random, you are vulnerable to statistical and dictionary attacks.

And of course, in "One-Time Pad", there is "One-Time". A single mask may only be used once. Otherwise, you are once again vulnerable to statistical attacks, and a single known-plaintext attack will totally destroy it.

---

### Post by Pyro.699 on 2010-09-29
Thanks for the reply :)

Im not sure what you mean by complicated? I thought i kept it relatively simple.

I added the different length compatibility so that it would not restrict the passwords or keys. Is there any way i could have such a method without compromising the integrity of the OTP?

Thanks
~Cody

---

### Post by Bachstelze on 2010-09-29
> **Pyro.699 said:**
> 
Im not sure what you mean by complicated? I thought i kept it relatively simple.

The goal is to be able to prove (in the mathematical sense) that the algorithm does what it's supposed to do.  That would really not be trivial with your code.

> I added the different length compatibility so that it would not restrict the passwords or keys. Is there any way i could have such a method without compromising the integrity of the OTP?


No. But as I said, the length is not really your main concern here. The fact that your key is not random and that you're probably using the same one several times is much more serious.

---

