---
title: "giving python a shot a few question"
date: 2009-01-31
forum: Programming Talk
---

### Post by aszxcv on 2009-01-31
i am going to start with 2.5 since thats whats i have installed on my ubuntu 8.04 box.

how long does it take to be able to create worthwhile apps ?

is it better to start with just an ide or just plain gedit?

after learning 2.5 will the jumped to 3.0 be huge?


are most web host still hosting python 2.5?

---

### Post by slavik on 2009-01-31
1. depends on how long it takes you to learn the needed parts and come up with an idea for a "worthwhile" app.

2. gedit

3. from what I've seen, no.

4. most web hosts will host 2.5 for a while, IMO

---

### Post by maximinus_uk on 2009-01-31
> **aszxcv said:**
> how long does it take to be able to create worthwhile apps ?

is it better to start with just an ide or just plain gedit?


Depends on how you define 'worthwhile'. What is your goal? I'm a perfectionist and in 30 years of programming it's a rare moment that I'm fully happy. But sometimes you can knock out useful code in a few minutes.

If you use GEdit in combination with an terminal it is almost an IDE :D

---

### Post by .Maleficus. on 2009-01-31
1.  Worthwhile is a very broad term.  I have backup scripts that I wrote while learning Python that I think are worthwhile and that I wrote in the first few days.

2.  Doesn't really matter.  I find Vim a very nice "IDE" - write the script, do a ":chmod +x %" and then a simple "!%" to execute and it works very well.  Gedit is nice for a text editor but Netbeans or Wing101 are my favorite Python IDEs.

3.  No.  Some notable changes - "print 'text'" became "print('text')" and integer division was removed (it all returns a floating point).  *These are from memory, correct me if I'm wrong.

4.  Yes.  Some may have jumped to 2.6.1 but the 2.6 release was just to make the 3.0 release easier for devs.  If not, I'm sure you can request that they install 2.5 for you (or do it yourself).

---

### Post by imdano on 2009-01-31
> **.Maleficus. said:**
> integer division was removed (it all returns a floating point).  *These are from memory, correct me if I'm wrong.You can still do integer division using '//'
```
dan@ubuntop:~$ python3.0
Python 3.0 (r30:67503, Dec  7 2008, 18:45:11) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 4/2
2.0
>>> 4//2
2
>>> 
```

---

### Post by Martin Witte on 2009-01-31
For editor: I like gedit with the gedit-plugins package.
How long it will take to create a usefull program: that really depends on your experience with other languages.

---

### Post by aszxcv on 2009-01-31
thanks for answering my questions :KS

---

