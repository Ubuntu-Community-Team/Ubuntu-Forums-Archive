---
title: "Eclipse: &quot;Launch failed. Binary not found&quot;"
date: 2008-11-15
forum: Programming Talk
---

### Post by qwertyuiop23 on 2008-11-15
I am using Eclipse Ganymede.  I am at the moment using it for development in C++ applications using Opengl. (Using this as apposed to other compilers because eclipse is very easy and small to transport on a pen drive).  And i was half way through developing a program when I went to test it and go this error:

"Launch failed. Binary not found."

Now please do not say "Change the path of the MinGW compiler it doesn't like '/'s," because it was working until a random point in the development.  I can get a new C++ project to work so I am a bit perplexed as how come it was working then suddenly stopped.  Does anyone know what could be the cause of this problem? 

Cheers
~Qwertyuiop

---

### Post by fuabrandon on 2009-01-03
I just had the same problem after installing Eclipse in Ubuntu. In fact, I installed Ubuntu and Eclipse together today (first time in my life) on my machine- Intel Xeon EMT64.

I was disappointed after I saw the error message.
"Launch failed Binary not found"

However, I found a solution by installing g++ "compiler" which was not installed originally.

Some website gave me a hint to install g++ by below command

sudo apt-get install g++

I hope this also solves your problem !

-Brandon

---

### Post by memoks on 2009-09-19
omg !! It really works. thx

---

### Post by poker on 2010-06-03
I just tried it, and it helped me also! thanks a lot! ))

---

### Post by ubu@ on 2010-08-07
> **fuabrandon said:**
> 
sudo apt-get install g++

-Brandon

one line, fixed all of my problems. THANK YOU!!!

---

### Post by Smartflight on 2010-11-18
> **fuabrandon said:**
> Some website gave me a hint to install g++ by below command

sudo apt-get install g++

I hope this also solves your problem!

And until now, I thought it was installed by the IDE itself (which now seems very unlikely on any IDE- stupid me!!)

You're a savior! It works now.

---

### Post by Nwe Nwe on 2012-12-25
> **fuabrandon said:**
> I just had the same problem after installing Eclipse in Ubuntu. In fact, I installed Ubuntu and Eclipse together today (first time in my life) on my machine- Intel Xeon EMT64.

I was disappointed after I saw the error message.
"Launch failed Binary not found"

However, I found a solution by installing g++ "compiler" which was not installed originally.

Some website gave me a hint to install g++ by below command

sudo apt-get install g++

I hope this also solves your problem !

-Brandon


I also found error in "Launch failed Binary not found". So, as your experience, I type  sudo apt-get install g++, it saids it has already installed. But, the error still occur. How to solve it. I use Ubuntu 12.10 with Eclipse Juno. Please kindly share some advice. Thanks in advance.

---

### Post by howefield on 2012-12-25
Old thread closed.

---

