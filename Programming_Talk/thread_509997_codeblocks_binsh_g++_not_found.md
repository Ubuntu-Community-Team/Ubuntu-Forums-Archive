---
title: "codeblocks /bin/sh: g++: not found"
date: 2007-07-26
forum: Programming Talk
---

### Post by G_force on 2007-07-26
I have installed codeblocks successfully

but when i try and compile the file i get

Compiling: main.cpp
/bin/sh: g++: not found
Process terminated with status 127 (0 minutes, 0 seconds)
0 errors, 0 warnings

I need some help, i am used to using codeblocks in windows!!!

Thanks in advance

---

### Post by smartbei on 2007-07-26
Try:
> 
sudo aptitude install build-essential


That installs g++, gcc, make, etc.

---

### Post by PaulFr on 2007-07-26
```
aptitude show g++ | grep State:
```If this shows **not installed**, then ```
sudo apt-get install g++
``` Otherwise, perhaps your PATH variable is not set right.

---

### Post by G_force on 2007-07-26
Thanks Fellas :)

---

### Post by Mark.G. on 2008-09-22
Thanks, it works now wuhu :D

---

### Post by changokun on 2008-11-23
thanks! this worked for me

---

### Post by Harry_Iyer on 2009-01-02
Thanks. Was facing the exact same problem - forcing me to use Code::Blocks in windows.

---

### Post by spartan1011 on 2009-04-27
thanks for the help... keep up the good work.

---

### Post by mdifabio on 2009-08-10
Thanks due from me too.  Google is my friend!

---

### Post by fsw90628 on 2009-12-16
:popcorn:thanks! this worked for me

---

### Post by damnated on 2010-02-24
Thanx a bunch :D

---

### Post by emongev on 2010-03-21
thanks this worked for me as well =)

---

### Post by AnaCaroline on 2010-03-27
thanks!!
:P

---

### Post by rahul_bhise on 2010-06-14
thanks it worked

---

### Post by Johnkozz on 2010-08-09
lol here's he my thanks to be added on to the thank you thread

---

### Post by Zacinfinite on 2010-08-14
THANKS AAAAALLLLLLLOOOOOOOTTTTTTTT. 
I cant believe i rubbed my backside on iron fence soo long for this tiny solution.

---

### Post by elyawm on 2010-09-30
Thanks it works : it better to do as said first : ```
 sudo aptitude install build-essential 
```

---

### Post by continue on 2010-12-15
Thank you, it works for me.
Thank you a lot !

---

### Post by kimora16 on 2011-04-11
hey guys i need help i am new to ubuntu and i have no clue what you guys are talking about but i have the same problem can you walk me through how to fix this

---

### Post by stchman on 2011-04-11
> **smartbei said:**
> Try:


That installs g++, gcc, make, etc.


The build-essential actually install the libraries for gcc and g++.

---

### Post by stchman on 2011-04-11
> **Harry_Iyer said:**
> Thanks. Was facing the exact same problem - forcing me to use Code::Blocks in windows.

Since Code::Blocks does not have an included compiler, what C/C++ compiler were you usging in Windows?

---

### Post by Phenax on 2011-04-11
> **stchman said:**
> Since Code::Blocks does not have an included compiler, what C/C++ compiler were you usging in Windows?

Code::Blocks has two downloads for Windows, and one includes MingW.

---

### Post by bruce282 on 2011-10-17
> **PaulFr said:**
> ```
aptitude show g++ | grep State:
```If this shows **not installed**, then ```
sudo apt-get install g++
``` Otherwise, perhaps your PATH variable is not set right.

When I tried to run the first example in a term window it told me APTITUDE NOT FOUND.

The apt-get worked fine and I can now compile, but being new to ubuntu I'm wondering if I'm missing something in my install.

Bruce

Oh yea 11.10 install.

---

### Post by dewsworld on 2011-12-12
Thanks! Good post!

---

### Post by javiermorale on 2012-01-03
Thanks it work for me either but can somebody tell me what I have done by installing g++ package! Because I know I had the GNU GCC compiler installed and I had code::block installed too. So what was this g++ package..?

---

### Post by fysicalplant on 2012-01-14
> **smartbei said:**
> Try:


That installs g++, gcc, make, etc.

I used apt-get instead of aptitude in ubuntu.  Also, sometimes you must log out and back in or restart after installing this package.

---

### Post by automagp68 on 2012-02-02
Thanks worked for me also

---

### Post by neo1691 on 2012-03-05
Moved to linux>installed code::blocks>gave the error>this solved it!

:popcorn:

---

