---
title: "Running programs written in 'C'"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-05-26
Several years ago I did a little programing in 'Turbo C'. Is there any way to compile, access & run these programs with Ubuntu ? I haven't been able to find any information about this.

---

### Post by Joeb454 on 2008-05-26
From a terminal (Applications > Accessories > Terminal) and run ```
sudo apt-get install build-essential
```

This will install GCC and the headers you need to compile your applications :) I can't say for sure that it works with Turbo C, as I've never tried it :)

---

### Post by Abild on 2008-05-26
The standard C (and C++, D, obj-C, etc...) compiler on Linux is called GCC (GNU C Compiler). In ubuntu you must first install it by installing the build-essentials package

```

sudo apt-get install build-essentials

```

If you have your sourcecode in  a file called helloworld.c you compile it the folowing way:

```

gcc -o helloworld helloworld.c

```

You can then run the program using:
```

./helloworld

```

If your program is large you will probably want write a makefile for it. Search for makefile tutorial for more information

---

### Post by CoCoKnots on 2008-05-26
Thanks, I tried doing this each way. The string load appeared to go OK & asked that I insert cdrom ubuntu 7.10 - After completing, left me a little lost of where to go next. So, I tried to enter a couple of the old programs I had created in the past using Turbo C but couldn't get in. Do I need to load 'Turbo C' into the ubuntu somehow?... Would I need to use 'Wine'?.

---

### Post by nick_h on 2008-05-26
> Do I need to load 'Turbo C' into the ubuntu somehow?... Would I need to use 'Wine'?.
Yes, it looks like it.  The following link suggests using dosemu.

[Mariuz's Blog](http://mapopa.blogspot.com/2007/12/antique-software-turbo-c-version-201-in.html).

---

### Post by CoCoKnots on 2008-05-26
OK... So Far, Everything went well loading dosemu as requested in Mariuz's Blog. It then asked that I click on the 'Turbo C' zip file to download the software... Where can I find the file they are requesting that I am to download? The prompt just returned to a blank set on the terminal page.

---

### Post by CoCoKnots on 2008-05-26
I now have ver 2.01 of Turbo C on my desktop. It still need to be unzipped. I  added '7zip' thru the add/remove feature under 'applications>. 
I then tried to install using the apt-get... 

[COLOR="Blue"]cocoknots@cocoknots-laptop:~$ sudo apt-get install 7zip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 7zip
cocoknots@cocoknots-laptop:~[/COLOR]$ 

I am able to get into the 'DOS Emulator under 'System Tools, which is now installed under the 'Applications' Tab.

How do I unzip the downloaded Turbo C zip files to use with the DOS prompt?

---

### Post by nick_h on 2008-05-26
gzip is installed by default so you could try:
```
gunzip <filename>
```
If you need 7zip then the package name is p7zip.

You can search for packages with aptitude:
```
aptitude search zip
```

---

