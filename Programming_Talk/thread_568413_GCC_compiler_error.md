---
title: "GCC compiler error"
date: 2007-10-05
forum: Programming Talk
---

### Post by user0182 on 2007-10-05
Hi All,

I have just install Ubuntu, and when I try to compile a simple C program using gcc, I get the following error.

gcc <sourcefile.c> -o <outputfile.exe>

hello.c:1:19: error: stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

I am assuming that I do not have the C libraries, installed. I have tried the following commands:

sudo apt-get install build-essential
sudo aptitude install build-essential

Although, in both cases the shell asks that I insert the installation CD. Which I have tried, but it doesn't seem to recognise the CD.

Could someone please tell me, what is the best way, in their opinion, to install the C libraries. Also, I want to be able to compile C++ programs, using g++, therefore could one tell me if I will need to do anything further to install g++.


Thanks in Advance

---

### Post by Wybiral on 2007-10-05
Do you have internet connection when you're trying to install build-essential? You can look for the build-essential package in the graphical synaptic manager too.

That is most likely the problem, you need build-essential.

---

### Post by dwhitney67 on 2007-10-06
```
gcc <sourcefile.c> -o <outputfile.exe>
```

Dispense with the <> brackets.

Perhaps you were showing them for "clarity", but if not, then they are not needed.

Also, before assuming you have gcc installed, consider running this command:
```

$ gcc --version
```

When I installed build-essential(s?) on my system, it prompted me for the install CD as well, and in my case, the installation proceeded normally.  What CD are you inserting?

---

### Post by Compyx on 2007-10-06
First off, GCC is installed because those error messages are definitely GCC's output.

If you have an internet connection, you should try commenting out the line in /etc/apt/sources.list that looks like this:
```

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Alpha i386 (20070823)]/ gutsy main restricted

```

On your install the line might look slightly different (I'm running Gutsy).

Just stick a '#' in front and try running
```

sudo apt-get install build-essential

```
again.

As far as g++ is concerned, the above command should be enough to get going with C++ as well.

You might also consider running:
```

sudo apt-get install manpages-dev manpages-posix-dev

```
to get some useful references for C-coding.

Also, get rid of the .exe suffix, Linux and Unix are a bit smarter than DOS/Windows so they don't need a suffix to determine the file type.

---

### Post by xyzt on 2007-10-14
Thanks. That's quite it. Not only GCC/C but also Pascal were unable to find some **crt1.o** and also GCC/C couldn't find its headers as stated here. They're doing alright now and I have a reference manual too.

---

