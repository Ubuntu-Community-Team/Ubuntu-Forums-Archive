---
title: "[C] Alternative to toascii()"
date: 2008-04-13
forum: Programming Talk
---

### Post by nvteighen on 2008-04-13
I'm trying to write a little RSA-Algorithm implementation in C (as my second serious program!). It works reading the plaintext from a text file and storing it into a string array. But, now I need to convert the characters into plain numbers so I can pad them afterwards. I found toascii() could be useful... but it makes you pass from 8 to 7-bit and that means e.g. accented letters and other characters will cause data corruption and faulty encryption.

Is itoa() what I need (but it needs and int as argument, and I have char)? Or wouldn't be better to read the file with fscanf the "%d" format directly to an int array and avoid a conversion?

Surely OpenSSL libraries have an implemented RSA function, but where would be the fun then? :p

---

### Post by Zugzwang on 2008-04-13
Erm, correct me if I'm wrong, but can't you just use a "char" that you read from file as a number? You don't need any conversion function, afaik.

---

### Post by mike_g on 2008-04-13
To convert a character to a number:
```
if(character >= '0' && character <= '9' ) character -= '0';
```
To convert a digit to a character:
```
if(num >= 0 && num <= 9) num += '0';
```

---

### Post by nvteighen on 2008-04-13
Yes, I can read a char as a number, but I must group them into a single integer... In JavaScript I'd concatenate characters into a variable M and then just put the result into the RSA function "f(M, e, p, q) = exp(M, e) (mod pq)".

Say I have the string "abc" stored at char *A. That's A[0] = 97, A[1] = 98, A[2] = 99 (using ASCII values). OK, if I'm told to pad each e.g. 3 digits, I should first concatenate all values into the number 979899 and then pad it into an array of 3-digit integers B[0] = 979, B[1] = 899. This is done to avoid certain security leaks such as character-wise encryption (which would just be as crackable as a Caesar cipher!!).

Have I been clearer now?

---

### Post by Zugzwang on 2008-04-13
Ah, ok, but you won't really solve the problems that way. Note that you're just appending the  decimal digits in your example which isn't the correct way to do this (since there are ASCII values > 100!) Also you would still have the vulnerability but only accounting three digits instead of one.

Assume that you have three chars c1,c2,c3 then you can put them together into an int by:
```
int i = (unsigned char)c1 + ((unsigned char)c2 << 8) + ((unsigned char)c3 << 16)
```

Note that "int" is only 16 bit large on 16-bit machines. 

If you really want secure encryption, you should look into some Bigint library and just put all of your message into one huge number -or- as it is done more often, just compute a random password, encrypt it and store the encrypted version together with the message encrypted using a classical symmetric method and the generated password together.

---

### Post by nvteighen on 2008-04-13
> **Zugzwang said:**
> Ah, ok, but you won't really solve the problems that way. Note that you're just appending the  decimal digits in your example which isn't the correct way to do this (since there are ASCII values > 100!) Also you would still have the vulnerability but only accounting three digits instead of one.

Assume that you have three chars c1,c2,c3 then you can put them together into an int by:
```
int i = (unsigned char)c1 + ((unsigned char)c2 << 8) + ((unsigned char)c3 << 16)
```

Note that "int" is only 16 bit large on 16-bit machines. 

If you really want secure encryption, you should look into some Bigint library and just put all of your message into one huge number -or- as it is done more often, just compute a random password, encrypt it and store the encrypted version together with the message encrypted using a classical symmetric method and the generated password together.

Thanks, you're right: a Known-plaintext attack would also be possible with what I wanted to do. I'm think I'm going to try a Bigint approach: I've installed the GNU Multi-Precision Library headers... Let's see what it has.

I'm not going to work on Key Generation for now. First, I want a program that encrypts properly... I'll have to generate a RSA key manually for testing, but well...

---

