---
title: "Problems when using gdb in Ubuntu"
date: 2007-06-22
forum: Programming Talk
---

### Post by Hiankun on 2007-06-22
Hi, Dear All,

I am a newbie of Ubuntu (also the Linux). These days I have installed Ubuntu on my PC and got very good experience with it.

However, these 2 days I encountered a problem when I started to write C programs in Ubuntu. I have a C program which runs well in WinXP. I complied this program and run it with BCB. Yesterday I tried to copy the C code to Ubuntu to compile it using gcc, then run it... it crashed... Segmentation fault.

Then, I found I have to learn the gdb for debugging (yes... this is my first time to hear about gdb). After following some examples found on websites, however, I found my gdb have some problem.

First, it started with the following message:

GNU gdb 6.6-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "[COLOR="Blue"]i486[/COLOR]-linux-gnu"...
Using host libthread_db library "/lib/tls/[COLOR="Blue"]i686[/COLOR]/cmov/libthread_db.so.1".

Is this normal? I mean, the gdb was configured as i486, but the library is contained in i686 folder??

The gdb in my Ubuntu cannot show the name of the function which bug may occur. For example, the message of one example is

[INDENT]Program received signal SIGSEGV, Segmentation fault.
0x4004ca01in [COLOR="Blue"] __strtod_internal ()[/COLOR] from /lib/libc.so.6[/INDENT]

but my gdb showed

[INDENT]Program received signal SIGSEGV, Segmentation fault.
0xb7e7a08d in[COLOR="Blue"] ?? ()[/COLOR] from /lib/tls/i686/cmov/libc.so.6[/INDENT]

Furthermore, I cannot use `l' to list the code in gdb.

Finally, I decided to test the same code on a laptop with Fedora (FC5), then everything in gdb is okay!

Is there some problem with my Ubuntu? I have used apt-get to install the gcc and also gdb, the response said my packages are the newest version.

Please give me some suggestions to solve this condition. I really want to use Ubuntu to do my works. Thank you all in advance~ :)

---

### Post by dbbolton on 2007-06-22
> **Hiankun said:**
> Hi, Dear All,

I am a newbie of Ubuntu (also the Linux). These days I have installed Ubuntu on my PC and got very good experience with it.

However, these 2 days I encountered a problem when I started to write C programs in Ubuntu. I have a C program which runs well in WinXP. I complied this program and run it with BCB. Yesterday I tried to copy the C code to Ubuntu to compile it using gcc, then run it... it crashed... Segmentation fault.

Then, I found I have to learn the gdb for debugging (yes... this is my first time to hear about gdb). After following some examples found on websites, however, I found my gdb have some problem.

First, it started with the following message:

GNU gdb 6.6-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "[COLOR="Blue"]i486[/COLOR]-linux-gnu"...
Using host libthread_db library "/lib/tls/[COLOR="Blue"]i686[/COLOR]/cmov/libthread_db.so.1".

Is this normal? I mean, the gdb was configured as i486, but the library is contained in i686 folder??

The gdb in my Ubuntu cannot show the name of the function which bug may occur. For example, the message of one example is

[INDENT]Program received signal SIGSEGV, Segmentation fault.
0x4004ca01in [COLOR="Blue"] __strtod_internal ()[/COLOR] from /lib/libc.so.6[/INDENT]

but my gdb showed

[INDENT]Program received signal SIGSEGV, Segmentation fault.
0xb7e7a08d in[COLOR="Blue"] ?? ()[/COLOR] from /lib/tls/i686/cmov/libc.so.6[/INDENT]

Furthermore, I cannot use `l' to list the code in gdb.

Finally, I decided to test the same code on a laptop with Fedora (FC5), then everything in gdb is okay!

Is there some problem with my Ubuntu? I have used apt-get to install the gcc and also gdb, the response said my packages are the newest version.

Please give me some suggestions to solve this condition. I really want to use Ubuntu to do my works. Thank you all in advance~ :)
there is a section of the forum devoted to programming talk. you're more likely to find a solution there: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

best of luck

---

### Post by hod139 on 2007-06-23
When compiling your code make sure you enable the debugging symbols.  This is accomplished by passing the -g flag to g++.

For example, if I had a cpp file called foo.cpp I would type
```

g++ -Wall -g -o foo foo.cpp

```
the -Wall flag enables all warnings, the -g flag enables debugging symbols, and the -o flag allows you name the resulting binary (a.out is default). 

To debug, you would then type
```

gdb foo

```
which starts the gdb prompt.
```

gdb ./a.out 
GNU gdb 6.6-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(gdb)

```
Here, i486 is fine.

To run the code type run (r for short), and after the crash type bt to get a backtrace and find the offending line.

---

### Post by Hiankun on 2007-06-23
Thank you dbbolton and hod139,

I have did what hod139 said before I come here for help
> Finally, I decided to test the same code on a laptop with Fedora (FC5), then everything in gdb is okay!

Therefore, I doubt there is something wrong with my Ubuntu 7.04. What I can do is to upgrade my gcc and also the gdb packages, but they are the latest already. :confused:

---

### Post by Hiankun on 2007-06-23
Wow, strange! Just minutes ago, I did the same tests as yesterday, and everything is okay?! O_O

Now my gdb can list the name and code of the bug function. Just yesterday, it only reply as the following messages that I do not understand

> #0  0xb7e7a08d in[COLOR="Blue"] ?? () [/COLOR]from /lib/tls/i686/cmov/libc.so.6
#1  0xb7f6c27e in[COLOR="Blue"] ?? () [/COLOR]from /lib/tls/i686/cmov/libc.so.6
#2  0x0000000d in[COLOR="Blue"] ?? ()[/COLOR]
#3  0x00000000 in[COLOR="Blue"] ?? ()[/COLOR]

> (gdb) l
1      [COLOR="Blue"] in init.c[/COLOR]

I cannot remember what's the difference between my doing yesterday and today... Maybe just because I didn't get enough sleep yesterday?:oops:

Anyway, I will keep trying and getting more experience with gdb. Thank you all for your kind help. :)

---

