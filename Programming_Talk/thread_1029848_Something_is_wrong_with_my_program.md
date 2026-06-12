---
title: "Something is wrong with my program"
date: 2009-01-03
forum: Programming Talk
---

### Post by Bob John on 2009-01-03
I wrote a program to judge a number is prime or not. 
"prime" here means a number that can only be divided by itself or one.
When I compiled it by gcc , the error message came up.And I do not very understand the message , so the compiling progress always can't complete.I checked and checked , modified and modified ,but I can't accomplished all the time.
Could you please help me to correct it?
Thank you .
Here is the source code , written in C :

[ATTACH]98624[/ATTACH]
Here is the error message provided by gcc :

[ATTACH]98625[/ATTACH]

---

### Post by bruce89 on 2009-01-03
You're not linking to libm. Use -lm in the gcc command line.

In future, post your source and errors as text, not a screenshot.

---

### Post by jpmelos on 2009-01-03
> **bruce89 said:**
> In future, post your source and errors as text, not a screenshot.

Seconded. Makes it easier for us who want to help to just copy and try to compile the code (if the error is in the code). :)

---

### Post by monkeyking on 2009-01-03
It also makes it easier for catching errors if you compile with -Wall .
You wouldn't have caught this one though...

---

### Post by Bob John on 2009-01-07
Thanks , everyone .

Later I will put all the code in text type.

These two days, I was too busy to log in our ubuntu forum.

Source code text format will come soon ...

---

### Post by Bob John on 2009-01-07
Thanks Everyone&#65281;My problem is solved now.

It is right to link to libm.a or type -lm in the gcc command line.

Thank you everyone ! These useful reply were thanked just before. ^_^

---

