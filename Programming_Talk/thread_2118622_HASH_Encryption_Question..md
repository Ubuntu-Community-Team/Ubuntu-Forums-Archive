---
title: "HASH Encryption Question."
date: 2013-02-21
forum: Programming Talk
---

### Post by fdrake on 2013-02-21
I have a project for college, in C++ regarding the Cryptography subject. I wanted to know how to create rainbow-tables . What I mean, is this:

I am trying to build [rainbow tables]("http://en.wikipedia.org/wiki/Rainbow_table") for  GNU/Linux (kernel ~ 3.7) Hash code password[ (SHA)]("http://www.backtrack-linux.org/forums/showthread.php?t=39771") found in /etc/shadow and( or) windows 7 hash password([LM hash function]("http://en.wikipedia.org/wiki/LM_hash")) found in the SAM files. 

I need to get access to the source code of these encryption method. Anyone knows exactly here where can I get them. I did try to google around but without success (probably because of my ignorance, since it is quite a huge topic).

Any help would be appreciated.


edit:
in Linux (kernel 3.5.0 ) my hash code uses "$6$" SALT =  SHA-512

---

### Post by haqking on 2013-02-21
> **fdrake said:**
> I have a project for college, in C++ regarding the Cryptography subject. I wanted to know how to create rainbow-tables . What I mean, is this:

I am trying to build [rainbow tables]("http://en.wikipedia.org/wiki/Rainbow_table") for  GNU/Linux (kernel ~ 3.7) Hash code password (SHA) found in /etc/shadow and( or) windows 7 hash password(LM hash function) found in the SAM files. 

I need to get access to the source code of these encryption method. Anyone knows exactly here where can I get them. I did try to google around but without success (probably because of my ignorance, since it is quite a huge topic).

Any help would be appreciated.

Why not just download them already made [http://project-rainbowcrack.com/table.htm](http://project-rainbowcrack.com/table.htm)

[https://www.cryptohaze.com/gpurainbowtables.php](https://www.cryptohaze.com/gpurainbowtables.php)

for source look in any of the open source tools which already do it 

[https://sites.google.com/site/reusablesec/Home/rainbow-tables](https://sites.google.com/site/reusablesec/Home/rainbow-tables)

The majority of tools that work with CUDA will be open source so look at them.

And others such as

winrtgen
rtgen
genpmk

Hope you have a good GPU or more than one ;-)

Perhaps i misread

---

### Post by fdrake on 2013-02-21
thanks for the links: they are very helpfull.  I did not know about rainbowcrack (only about ophcrack). 

My project will build tables  with a pasword of a certain size : up to 3-4 (max) characters ; But it will support numbers- alphabetic characters (Upper/Low case) and SYMBOLS. Most of the tables on the net support only few symbols (since it is huge the amount of memory required).

My project/code is suppost to build these tables, I cannot use pre-buildones.  :(

I will check the documentation/source code of the program and see what method they used. This might do it too.

---

### Post by surfer on 2013-02-21
just to be sure: the salt is not "SHA-512"; that's just the hashing algorithm used. the salt is what follows after that dollar sign (from [https://en.wikipedia.org/wiki/Passwd):](https://en.wikipedia.org/wiki/Passwd):)

[INDENT]"$id$salt$hashed", where "$id" is the algorithm used (On GNU/Linux, "$1$" 
stands for MD5, "$2$" is Blowfish, "$5$" is SHA-256 and "$6$" is SHA-512, [/INDENT]

---

### Post by surfer on 2013-02-21
and from [https://en.wikipedia.org/wiki/Rainbow_table](https://en.wikipedia.org/wiki/Rainbow_table) :

[INDENT]A rainbow table is ineffective against one-way hashes that include salts. For example, consider a password hash that is generated using the following function (where "+" is the concatenation operator):

[FONT="Courier New"]saltedhash(password) = hash(password+salt)[/FONT]

Or

[FONT="Courier New"]saltedhash(password) = hash(hash(password)+salt)[/FONT][/INDENT]

or do you consider the salt to be the same for all passwords?

---

### Post by haqking on 2013-02-21
> **fdrake said:**
> thanks for the links: they are very helpfull.  I did not know about rainbowcrack (only about ophcrack). 

My project will build tables  with a pasword of a certain size : up to 3-4 (max) characters ; But it will support numbers- alphabetic characters (Upper/Low case) and SYMBOLS. Most of the tables on the net support only few symbols (since it is huge the amount of memory required).

My project/code is suppost to build these tables, I cannot use pre-buildones.  :(

oh ok, well the most commonly used one is GenPMK which is open source so look at the code. here is the source [https://code.google.com/p/distributed-wpa-cracking/source/browse/trunk/src/cowpatty-CU5673/genpmk.c?r=242](https://code.google.com/p/distributed-wpa-cracking/source/browse/trunk/src/cowpatty-CU5673/genpmk.c?r=242)

./genpmk.py in BT

You can see it in action (comes preinstalled in backtrack though you need to setup CUDA)
[https://www.youtube.com/watch?v=yVlX8lh967M](https://www.youtube.com/watch?v=yVlX8lh967M)

---

### Post by haqking on 2013-02-21
ahh i just saw above posts, yes they wont work with salting.

oh and here is the math if you want it [http://lasecwww.epfl.ch/~oechslin/publications/crypto03.pdf](http://lasecwww.epfl.ch/~oechslin/publications/crypto03.pdf)

---

### Post by fdrake on 2013-02-21
> **surfer said:**
> just to be sure: the salt is not "SHA-512"; that's just the hashing algorithm used. the salt is what follows after that dollar sign (from [https://en.wikipedia.org/wiki/Passwd):](https://en.wikipedia.org/wiki/Passwd):)

[INDENT]"$id$salt$hashed", where "$id" is the algorithm used (On GNU/Linux, "$1$" 
stands for MD5, "$2$" is Blowfish, "$5$" is SHA-256 and "$6$" is SHA-512, [/INDENT]

yes , sorry if I wasn't clear on my statement. What I meant is that the salt presend in my shadow file is "6" between the 2 dollar sign. And yes , hash code follows after the 2nd dollar sign. I was aware of it.

---

### Post by fdrake on 2013-02-21
> **surfer said:**
> and from [https://en.wikipedia.org/wiki/Rainbow_table](https://en.wikipedia.org/wiki/Rainbow_table) :

[INDENT]A rainbow table is ineffective against one-way hashes that include salts. For example, consider a password hash that is generated using the following function (where "+" is the concatenation operator):

[FONT="Courier New"]saltedhash(password) = hash(password+salt)[/FONT]

Or

[FONT="Courier New"]saltedhash(password) = hash(hash(password)+salt)[/FONT][/INDENT]

or do you consider the salt to be the same for all passwords?

I do consider the salt to be the same in all the password, in this case.

---

### Post by fdrake on 2013-02-21
> **haqking said:**
> ahh i just saw above posts, yes they wont work with salting.

oh and here is the math if you want it [http://lasecwww.epfl.ch/~oechslin/publications/crypto03.pdf](http://lasecwww.epfl.ch/~oechslin/publications/crypto03.pdf)

funny I just started to read that last night. It put me to sleep in 30 sec. :D 
I'll go further with the reading and check the different source you have provided. I'll keep posted the progress.

---

### Post by papibe on 2013-02-21
Hi fdrake.

Unless I misunderstood, you don't need to get the source code of the cryptographic functions, but to use them. That is, to use the already existing and available libraries to write a program with them.

The relevant function is called crypt:
```
char *crypt(const char *key, const char *salt);
```
Here's more details how it works:
```
man crypt
```
Then, take a look at this sample code: [GNU libc - Encrypting Passwords]("http://www.gnu.org/software/libc/manual/html_node/crypt.html").

Does that help? Let us know how it goes.
Regards.

---

### Post by surfer on 2013-02-22
> **fdrake said:**
> yes , sorry if I wasn't clear on my statement. What I meant is that the salt presend in my shadow file is "6" between the 2 dollar sign. And yes , hash code follows after the 2nd dollar sign. I was aware of it.

sorry to be picky again, but no: in every line with a password in your shadow file there should be exactly 3 dollar signs. something like
```
$6$????????$...
```
6 is the id (after the 1st "$"); the following eight characters the salt (after the 2nd "$") and the rest the salted hash (after the 3rd "$").

the salt is not just one character!

---

### Post by fdrake on 2013-02-22
> **surfer said:**
> sorry to be picky again, but no: in every line with a password in your shadow file there should be exactly 3 dollar signs. something like
```
$6$????????$...
```
6 is the id (after the 1st "$"); the following eight characters the salt (after the 2nd "$") and the rest the salted hash (after the 3rd "$").

the salt is not just one character!
oh i see now ... ](*,)  Thanks for insisting and making this clear to me. Now I understand what you ment in the first post, before by asking me if the salt was the same. I apreciate that! :D

---

### Post by fdrake on 2013-02-22
hold on. so it won't work !  WTF!!!!!!

------------------------------------

> 
The intent of the salt itself is primarily to defeat pre-computed rainbow table attacks that could otherwise be used to greatly improve the efficiency of cracking the hashed password database.

wait a sec this means that the building of a table is harder (since you have longer string to consider), but not that it does not work. I still know the SALT after all from the hash code.

so this means that a password long 3 characheters requires huge size tables already due to the salt! Correct me if I am wrong here.

---

### Post by fdrake on 2013-02-22
> **papibe said:**
> Hi fdrake.

Unless I misunderstood, you don't need to get the source code of the cryptographic functions, but to use them. That is, to use the already existing and available libraries to write a program with them.

The relevant function is called crypt:
```
char *crypt(const char *key, const char *salt);
```
Here's more details how it works:
```
man crypt
```
Then, take a look at this sample code: [GNU libc - Encrypting Passwords]("http://www.gnu.org/software/libc/manual/html_node/crypt.html").

Does that help? Let us know how it goes.
Regards.
thanks a lot. this is exactly what I was looking for my project.

---

### Post by surfer on 2013-02-22
> **fdrake said:**
> 
so this means that a password long 3 characheters requires huge size tables already due to the salt! Correct me if I am wrong here.

yes, that is correct. the salt is meant to defeat that kind of attack.

---

