---
title: "g++ (i don't think im compiling right) gives a file that runs... and shows nothing"
date: 2008-08-01
forum: Programming Talk
---

### Post by personjerry on 2008-08-01
this is my syntax:

> g++ foo.cpp fooheader.h fooheadertwo.h -o test

where foo.cpp includes fooheader.h, and fooheader.h includes fooheadertwo.h

It compiles, with some warnings > warning: #pragma once in main file
However, when I run the file in terminal

> ./test

the terminal prints a new line and just stays there.
I've waited a while and it doesn't do anything so I'm getting suspicious.

Where did I go wrong?
They all have > #pragma once
and I even put > #ifndef checks to make sure

I am reluctant to show the code because it's code from when I was younger and so very very messy and bad technique (this is just for archival purposes).

However, the additional outputs that I've added to the constructors of my classes don't show up, which makes me think that the file just isn't running.

---

### Post by ad_267 on 2008-08-01
You don't need to specify the .h files. Use:
```
g++ foo.cpp -o test
```

I don't know if that would cause the problems you're getting though. If that doesn't fix it I'd think it's a problem with the actual code.

---

### Post by dribeas on 2008-08-02
> **personjerry said:**
> 
I am reluctant to show the code because it's code from when I was younger and so very very messy and bad technique (this is just for archival purposes).

However, the additional outputs that I've added to the constructors of my classes don't show up, which makes me think that the file just isn't running.

That seems more like a programming error than compilation. Just print out something in the beginning of main(), and check whether it shows.

   David

---

### Post by samjh on 2008-08-02
First of all: what is your program supposed to do?

Second: as *ad_267* already pointed out, you don't need to compile the *.h files.

Third: have you tried without using "#pragma once"?

---

### Post by DMills on 2008-08-02
test is normally a very bad name for a program as it conflicts with a shell built in of the same name. 

Are you sure you did ./test and not just test? 

Just typing test will invoke the shell built in which does not print anything, ./test should run your program...

BTW: gcc pretty much ignores pragmas as the developers think them bad practise. 

Regards, Dan.

---

