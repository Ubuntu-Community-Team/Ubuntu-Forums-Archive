---
title: "GCC abd pthread lib"
date: 2007-11-27
forum: Programming Talk
---

### Post by hexbin on 2007-11-27
Hy, now here is my problem. I am using pthread in my C programs, and any time I use gcc to compile them I need to add "-lpthread", while when I am compiling them on my collages computers, "-lpthread" is not needed.

How can I setup my GCC compiler to not need that extra argument?

---

### Post by seetho on 2007-11-28
Try:

```
sudo ldconfig
```

Should work after that.

You can read this [http://www.linux.com/articles/114007]("http://www.linux.com/articles/114007") if you are interested to know what ldconfig does.

st

---

### Post by hexbin on 2007-11-28
Thanks, but that didn't help :(

I entered **sudo ldconfig**, there was no output. I restarted my machine, and still no effect as to need to enter **-lpthread** while compileing. Still geting the output:

```
/tmp/ccE0UX4S.o: In function `main':
server.c:(.text+0x488): undefined reference to `pthread_join'
server.c:(.text+0x535): undefined reference to `pthread_create'
collect2: ld returned 1 exit status
```

---

### Post by monkeyking on 2007-11-28
I havn't tried with pthread, but other libraries.

You can't just enter ldconfig, you need to setup the file
```

/etc/ld.so.conf

```
And then run ldconfig.

But I wouldn't really worry about typing in -lpthread.
And if it annoys the extra typing, i would suggest using a makefile.

that way all you need to do is type
```

Make

```
(after you have written your Makefile)

---

### Post by hexbin on 2007-11-28
Well, the thing is, I am trying to make a virtual machine for all my fellow students to practice on... Making anything different then it is on our collage computers would confuse a lot of students. So I really need to make GCC work without -lpthread

how do I edit /etc/ld.so.conf, or more accurately... what do I write in it?

---

### Post by iharrold on 2007-11-28
> **hexbin said:**
> Well, the thing is, I am trying to make a virtual machine for all my fellow students to practice on... Making anything different then it is on our collage computers would confuse a lot of students. So I really need to make GCC work without -lpthread

how do I edit /etc/ld.so.conf, or more accurately... what do I write in it?

Applications->Accessories->Text Editor

Then:
File->Open

Navigate to File System/etc

Double click ld.so.conf

Edit:  I should read more closely...  Your asking what to put.  Not sure really.  Mine reads:
```
include /etc/ld.so.conf.d/*.conf
```
But I also include the -l compile command.

---

### Post by dwhitney67 on 2007-11-28
I think you guys are headed down the wrong path.

What type of system do you use at your College vs. what you use at home?

---

### Post by hexbin on 2007-11-28
> **dwhitney67 said:**
> I think you guys are headed down the wrong path.

What type of system do you use at your College vs. what you use at home?

Well, at collage we have several type of systems. One cabinet has one version of Ubuntu, other cabinet has another version... But the main computer that actually holds all of our user accounts, and that we actually connect to via SSH to work on, I don't know what system is there. The version I use at home on my virtual machine is Ubuntu 7.10 Server edition

---

### Post by dwhitney67 on 2007-11-28
Ok, the reason why I ask is because typically on Linux distros, the pthread libraries are located in /usr/lib.  This path is automatically parsed when /sbin/ldconfig is run.

As a user, you should not have to worry one bit about ldconfig.  This is only matters if you add new libraries to the system that are not in the traditional areas (e.g. /usr/lib, /lib, etc.)

As for using the -lpthread when compiling under one system versus another, it could be two different *nix systems.  Linux usually requires that this be specified; maybe the system at your college is some other flavor of Unix (Sun, HP, ??).

Anyhow, create a Makefile to compile your application.  It should be able to determine the type of system, perhaps using the "uname" command.

```
$ uname -s
```

---

### Post by hexbin on 2007-11-29
Ok, using **uname** i got HP-UX (which actually has a lot of sense since at 1st, all our computers used HP-UX). I don't have a clue as how to use makefile, but as I stated before, I am trying to make a replica of our collage main system, but in that much as students actually need for everyday use in practice. I had hard enough time explaining to them that they can use **pico** instead of **VI** and I think that I would have a hell of a time explaining them to use something else instead of GCC...

---

