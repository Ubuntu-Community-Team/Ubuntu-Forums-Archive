---
title: "[SOLVED] Simple Encryption/Decryption Algorithm (Python)"
date: 2008-11-30
forum: Programming Talk
---

### Post by sofiankrt on 2008-11-30
Hi!

I've just finished (not exactly finished, but I've got a working version) writing a little algorithm in Python that encrypts text (a => 1, b => 2, etc.) and then adds a key that the user specifies to the numbers. So for example:

If the key is 4, and the message: abcd efg

The encrypted output would be:

```
4 5 6 7  8 9 10
```

Code for the encryption part (once I finish the decryption part, I'll bundle them together in one file):
```
#!/usr/bin/env python

# importing the string module
import string

# welcome message
print "Welcome to Sofian's Cesaer Encryption Algorithm!"

# asking for the encryption key
key = input("Please enter the encryption key (a whole number): ")

# asking for the message to encrypt
raw_message = raw_input("Input the message that you want to encrypt (DO NOT ENTER NUMBERS!!!): ")

# converting it to lower case
message = string.lower(raw_message)

# intializing the variable "code"
code = ""

# encrypt each letter...
for letter in message:
	if letter in string.lowercase:						# if it's a character...
		index = string.find(string.lowercase, letter)	# find it's index in the list of characters
		number = str(index + key)							# since we start counting from zero (but normal people don't), add 1
		code += "%s " % number							# concatenate the letter into the final message
	else:
		if letter == " ":
                        code += " "
		else:
			code += "%s " % letter						# if it's not a character (ie. .,!?, etc...), concatenate it directly
		
print code												# print the message

```

But I'm stuck on the decryption part! I haven't figured out how to use a for loop (or anything) to go number by number and decrypt the message, and when encountering two spaces, to put a space between the words. Any ideas?

---

### Post by ghostdog74 on 2008-11-30
what you are doing doesn't look like caesar's algorithm.

---

### Post by sofiankrt on 2008-11-30
lol, I kinda figured that out as I was reading about cryptography after I finished writing the program. Too lazy to change it, bleh.

But, other than that, is the encryption algorithm OK?

---

### Post by ghostdog74 on 2008-11-30
> **sofiankrt said:**
> lol, I kinda figured that out as I was reading about cryptography after I finished writing the program. Too lazy to change it, bleh.

But, other than that, is the encryption algorithm OK?

if its just for fun, that's ok. Also, there are Python modules that specifically does encryption, such as pycrypt

---

### Post by sofiankrt on 2008-11-30
No, it's just for fun! And for being able to tell my friends at school, "I, Sofian the Cryptographer, have written an encryption algorithm!". Yes, fun. A lot of it...

But I'm kinda stuck on the decryption part, any ideas?

---

### Post by bigdidz on 2008-11-30
actully I find your code really good.

But, you should calculate in 'modulo 26'.  Let's me explaine.  There is 26 letters in the English alphabet. If you just add a number to each element of the array that represent your string, you will just translate your array.  It's going to be very easy to crack.

Eg let's take 'abcxyz' for the string and 10 for the key.The string is represented by [1,2,3,24,25,26] and the code by [11,12,13,3,25,26].  As you see, you cannot even comeback to letters from your cypher.

So if your coding algorithm is f(a) = (a+n) mod26 than, your decoding formula will be g(a) = (a-n)mod26.  where a represent the number associated to a character and n your key.

Look on wikipedia, there is plenty on algorithm well explain.

---

### Post by sofiankrt on 2008-11-30
Thanks!

Ok, I've tried doing this, (I'm using mod 27 instead of 26 so that z will be 26, not 0):
[PHP]#!/usr/bin/env python

# importing the string module
import string

# welcome message
print "Welcome to Sofian's Wonderful Encryption Algorithm!"

# asking for the encryption key
key = input("Please enter the encryption key (a whole number): ")

# asking for the message to encrypt
raw_message = raw_input("Input the message that you want to encrypt (DO NOT ENTER NUMBERS!!!): ")

# converting it to lower case
message = string.lower(raw_message)

# intializing the variable "code"
code = ""

# encrypt each letter...
for letter in message:
	if letter in string.lowercase:						# if it's a character...
		index = string.find(string.lowercase, letter)	# find it's index in the list of characters
		number = str((index + 1 + key) % 27
		)							# since we start counting from zero (but normal people don't), add 1
		code += "%s " % number							# concatenate the letter into the final message
	else:
		if letter == " ":
                        code += " "
		else:
			code += "%s " % letter						# if it's not a character (ie. .,!?, etc...), concatenate it directly
		
print code												# print the message
[/PHP]

But the problem is, the key you specify is limited to 0-26 (or multiples thereof), so you can't use arbitrarily large numbers to confuse whoever is trying to crack your code.

Yes, if both a *and* z are used in the message, the cracker can subtract all the numbers by a+1 and get the normal 1 to 26 code. But at least it makes it harder for the cracker, especially if a and z are not used in the same message. (maybe do some further calculations using the key?)

But the big problem I'm facing now is with Python's syntax. How would I make it go number by number (eg. 26, then 9, then 12, and so on) and convert it to its corresponding letter (this part is easy), put all the letters in a variable (message += letter, simple) and (this is the hard part) make it concatenate a space when it encounters two adjacent spaces in the encoded message.

Any ideas?

---

### Post by Modred on 2008-12-01
> But the problem is, the key you specify is limited to 0-26 (or multiples thereof), so you can't use arbitrarily large numbers to confuse whoever is trying to crack your code.

If I know your alphabet, I can take all the integers in your cipher text and compute their equivalent modulo the size of the alphabet.  Adding arbitrarily large numbers does not change the size of your alphabet or the fact that your message must use letters from that alphabet.  There are only N number of unique keys, when N is the size of your alphabet.  Ergo, not performing the modulus does nothing to increase security.

Seeing that you put a space between each integer in the cipher text, detecting multiple spaces should be simple.  For example, you could split that string by a single space, which will give you a list with two types of elements: a string with an integer where there should be a letter, and an empty string where there should be a space.  EG:

```

>>> '2 23 6 31  2'.split(' ')
['2', '23', '6', '31', '', '2']

```

You could then iterate through this list and decrypt the number when the element is not an empty string, and insert a space when there is an empty string.

---

### Post by sofiankrt on 2008-12-01
I'm not sure I quite get your point. Are you saying that removing the modulus will not result in better security?

Thanks! That message.split thing is exactly what I was looking for!

Now, for the encryption part, if I add the key to the number representing the letter, and then multiply it by the key, etc. Assuming the source code isn't available to the cracker, would they be able to crack it without using frequency analysis?

---

### Post by CptPicard on 2008-12-01
Actually, the algorithm essentially *is* the Caesar cipher, is it not, with numbers instead of letters and an arbitrary-size shift constant?

It's actually so trivial to break though that it's not even funny -- it does not matter what key you choose. You just end up with a relabeling of the alphabet...

---

### Post by sofiankrt on 2008-12-01
Come on, I'm not trying to sell this to the NSA!

But at least it's better than not giving it a key, don't you think? And there's this special feeling of having a special key with which to communicate with people. No one's interested in my messages anyway, so coolness is a big factor.

---

### Post by Modred on 2008-12-01
> **sofiankrt said:**
> I'm not sure I quite get your point. Are you saying that removing the modulus will not result in better security?

That's exactly what I'm saying.  Assuming you're encrypting English, you have an alphabet 26 letters long.  If your key is 5, then a will encrypt to 5 (assuming we start at 0).  If your key is 2432554543255, then a will be 2432554543255.  However, 2432554543255 mod 26 is equivalent to 5.  So no matter how large you choose your key, by taking each integer in your encrypted text and finding it's equivalent modulo the size of the alphabet, I can restrict the possible keys to the values 0 <= K <= 25.

> Now, for the encryption part, if I add the key to the number representing the letter, and then multiply it by the key, etc. Assuming the source code isn't available to the cracker, would they be able to crack it without using frequency analysis?

With some guess work, yes.  Although, if you start multiplying by your key without applying a modulus, all I have to do to undo this is find the common factor(s) of all the numbers in your cipher text and test each one of them.  Then I'm back to a plain Caesar Cipher.  If you apply the modulus, then you must carefully choose the key or you won't be able to decrypt!  (Hint, 2 has no inverse modulo 26, so if 2 is your key, "dividing" by 2 [which is the same as multiplying by it's inverse] when you decrypt will not give you the expected result!)

---

### Post by sofiankrt on 2008-12-01
Oh, I see. In that case you wouldn't need both a and z in the message, would you?

So, I'll just multiply, add, etc. And hope that the cracker isn't very good at guessing!

---

### Post by Modred on 2008-12-01
> **sofiankrt said:**
> Oh, I see. In that case you wouldn't need both a and z in the message, would you?

So, I'll just multiply, add, etc. And hope that the cracker isn't very good at guessing!

Now you're getting close to an Affine cipher, where K1 = K2. As I mentioned in my edit of the last post, you can't arbitrarily choose your key anymore, or else you might not get the same message back when you decrypt.  For example, let's say I want to multiply by K1 and then add K2 (this is the Affine cipher).  So here's how you encrypt a letter M, to it's cipher text value, C.  Note that K1 and K2 can be different, and n is the size of your alphabet.

C = M * K1 + K2 mod n

To decrypt, you do the following:

M = (C - K2)/K1 mod n

However, 1/K1 might not exist modulo 26!  And even if it does, it isn't the same as 1/K1 over the real numbers.  Let me try encrypting the an A and a N when K1 = K2 = 2.

A = 0, N = 13

0 * 2 + 2 mod 26 = 2
13 * 2 + 2 mod 26 = 28 mod 26 = 2

As you can see, both A and N map to the same cipher text!  What happens when you try to decrypt the value 2?

(2 - 2)/2 = 0

But my original number might have been 13 (for N).  As you can see, 2 is not a valid K1.  This occurs because it has no inverse modulo 26.

Now, if you pick 3, then you can calculate the decryption.  However, the inverse of 3 is not 0.333.

3 * 1/3 = 1, correct?

When we're working modulo 26, we get the following:

3 * x = 1 mod 26

Where x is the inverse of 3.  For example, x can be 9 (3 * 9 = 27 = 1 mod 26).  More technically, x is 9 plus or minus any multiple of 26.  So, in your decryption, you aren't really dividing by 3, you're multiplying by 9!

Say K1 = K2 = 3, M = 2.

15 * 3 + 3 mod 26 = 22

For decrypting:

(22 - 3)/3 = 19/3

As you can see, if 1/3 is .333, then you won't get an integer here!  But if 1/3 is 9 (which it is mod 26), then we actually have:

19 * 9 mod 26 = 15

Tada, the correct answer.

---

### Post by sofiankrt on 2008-12-01
But I'm not using mod at all. I'm just multiplying and adding, eg:

key = 4

b => 2

encrypting b would be

(1 ** key) - key) * key = 240 (I think? I did it mentally)

something like that. No two letters would have the same value, right?

---

### Post by Modred on 2008-12-01
Without the modulus, it's just a straight substitution.  Frequency analysis will take it down quickly.  If the attacker can't do frequency analysis, then you might be fine.  But it's quite easy to see which numbers appear the most often in the cipher text, so I can start making guesses about how the numbers map to letters.  A few good guesses and the system can be broken.  Every wrong guess puts you closer to a correct guess.

---

### Post by sofiankrt on 2008-12-01
Yes, but, other than by using frequency analysis, the code can't be broken?

Ok, now I'm beautifying the code, I'll put it online once I'm finished.

---

### Post by nvteighen on 2008-12-01
A suggestion, why don't you try now the Vigenère cipher (an enhanced Caesar cipher)? Look at Wikipedia.

Anyway, any English  substitution cipher is the most stupid thing to break because of the high std. deviation the frequencies have.

---

### Post by sofiankrt on 2008-12-01
Will do.

I tried cracking some encrypted text using frequency analysis once. Two hours. Two hours. The plaintext turned out to be the most boring thing in the world, and I came out of it with an enormous headache.

It'd be *wonderful* to cause someone so much pain! MUAHAHAHAHAHA!

---

### Post by sofiankrt on 2008-12-01
Phew, finished coding!

This is the final (at least for this kind of encryption) version of my encryption/decryption algorithm.

[PHP]#!/usr/bin/env python
# sipher - encryption/decryption program. Just run the program, give it a key, give it your message, give the key to your friend, let him run the program, give it the key, give it the encoded text and TADA! Your original message appears.
# written by Sofian Rahmani, website: www.nightscribe.tk, email: sofiankrt@gmail.com
# Copyright (C) 2008 Sofian Rahmani. Free to redistribute if this copyright notice is left intact.

# importing the string module
import string

# welcome message
print "Welcome to Sofian's Amazing Encryption Algorithm!"

# encryption function
def encrypt():
	# asking for the encryption key, making sure it's a number
	while True:
		try:
			key = input("Please enter the encryption key (a whole number): ")
			break
		except:
			print "Enter a ******* number, idiot!"

	# asking for the message to encrypt
	raw_message = raw_input("Input the message that you want to encrypt (DO NOT ENTER NUMBERS!!!): ")

	# converting it to lower case
	message = string.lower(raw_message)

	# intializing the variable "code"
	code = ""

	# encrypt each letter...
	for letter in message:
		if letter in string.lowercase:									# if it's a character...
			index = string.find(string.lowercase, letter)				# find its index in the list of characters
			number = str(index + (key ** 2) - (key * 2) + (key + 1))	# do some mathematical operations on it to make encrypted message harder to crack
			code += "%s " % number										# concatenate the letter into the final message
		else:
			if letter == " ":											# putting two spaces between words
					code += " "
			else:
				code += "%s " % letter									# if it's not a character (ie. .,!?, etc...), concatenate it directly

	print code[:-1]														# print the message, deleting the final space in the process

# decryption function
def decrypt():
	# initializing the message variable (the final plaintext output)
	message = ""

	# making sure the key is numeric, if not, asking the user for the key again
	while True:
		try:
			key = input("Please enter the secret key: ")
			break
		except:
			print "Enter a ******* number, idiot!"

	# asking for the encrypted text
	code = raw_input("Enter the encrypted text: ")

	# splitting it into chunks
	numberslist = code.split(" ")

	for number in numberslist:								# going element by element in the list...
		if number == "":
			message += " "									# replacing two spaces with one space
		else:
			try:											# checking if the element is numeric
				index = (int(number) - (key**2) + key - 1)	# elemenating all prior mathematical operations...
				try:
					letter = string.lowercase[index]		# checking if the key is within range for the encrypted text
					message += letter						# concatenating the letter (or punctuation mark) to the final message in the process
				except:
					print "You have got the wrong key."
					break
			except ValueError:
				letter = number
				message += letter
			
	print string.capitalize(message)						# capitalizing the first letter. Might as well make it look good...

# asking whether the user wants to encrypt or decrypt
choice = raw_input("Would you like to encrypt your message or decrypt your code? [encrypt/decrypt]: ")

if choice == "encrypt":		# running the correct function accordingly
	encrypt()
elif choice == "decrypt":
	decrypt()
else:
	print 'Please enter either "encrypt" or "decrypt" only!' # if the user entered something else

# thank you for viewing the source code of my program! INFRINGE MY COPYRIGHT AND I WILL RAPE YOU!

print "Thank you for using Sofian's Amazing Encryption Algorithm!"
[/PHP]

Wow, that was fun!

---

### Post by nguchet on 2008-12-01
cool, i had this program in my Asm class last year :) and i d coded it in C++ too, Python version is so much shorter, impressive :D

---

