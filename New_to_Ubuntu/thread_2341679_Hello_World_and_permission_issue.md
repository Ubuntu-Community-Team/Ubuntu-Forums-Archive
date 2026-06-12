---
title: "Hello World and permission issue"
date: 2016-10-30
forum: New to Ubuntu
---

### Post by 4l3x2 on 2016-10-30
Good evening.
Maybe it is overused, but I like it anyway: Hello world :popcorn:

I'm a new user of Ubuntu (L Ubuntu, to be precise), I obviously like IT and, despite of my 39 years, I enrolled at university.
Subject? Information Science, of course.

Now, I have 2 issues to solve:
1. this is not pressing, Lubuntu doesn't recognize my bluetooth, I installed it on an Asus EeePc 1005PE
2. this is more important: after compiling a .cpp file with g++, the output file doesn't have the executable attribute on; i get the same behaviour even if i do #chmod 744 a.out, with my user or using sudo, so when I try to execute it I get the error "Not authorized"

How can I solve these issues?

Thank you very much ;)

---

### Post by kevdog on 2016-10-30
./a.out perhaps.

---

### Post by oldfred on 2016-10-30
I am not an expert on file permissions.
But is not execute an odd number?
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

       sudo chmod +x <path>
sudo chmod 755 <filename>

---

### Post by steeldriver on 2016-10-30
> **4l3x2 said:**
> 
2. this is more important: **after compiling a .cpp file with g++**, the output file doesn't have the executable attribute on; i get the same behaviour even if i do #chmod 744 a.out, with my user or using sudo, so when I try to execute it I get the error "Not authorized"


Please post the exact g++ command you used (including any flags / switches)

If you used an appropriate g++ command AND the output file is written to a filesystem that supports Unix-style permission bits**, then there should be no need to manually chmod anything

** not, for example, a FAT or NTFS formatted USB drive

---

### Post by 4l3x2 on 2016-11-03
Hi everybody.

First of all thank you for your answers and sorry for being absent.

The problem with the executable was that it was stored on a usb key vfat formatted (or fat32, I do prefer the first), after copying it in my home directory chmod worked fine, so I was able to run the executable.
The commands were simply #g++ file.cpp -Wall, with no errors, and #chmod 744 a.out.
As far as I know it should give all access to the owner and only read permission to the owner's group and everyone else.

Now I have to address the bluetooth, as soon as possible (are the contraction allowed? I mean, can I write asap instead of as soon as possible? Or afaik for as far as I know....) I'll post the result of dmesg and/or the content of /var/log/messages (but Ubuntu stores the kernel messages in /var/log/kern.log, if I remember right, please tell me which one fits better) and I'll try to add the bluetooth module to the kernel.

Thank you again :smile:

---

### Post by vasa1 on 2016-11-03
> **4l3x2 said:**
> ..., as soon as possible (are the contraction allowed? I mean, can I write asap instead of as soon as possible? Or afaik for as far as I know....) ...
Contractions aren't disallowed although, with the more exotic ones, we run the risk of not being understood by some readers.

A couple of points ... asking one question per thread with an appropriately descriptive title is preferable. It will help others who may have similar issues. 

Thanks!

---

### Post by 4l3x2 on 2016-11-04
> [COLOR=#000000]Contractions aren't disallowed although, with the more exotic ones, we run the risk of not being understood by some readers.[/COLOR]

Thank you. I'm italian and I only know the most used contractions :-)

> [COLOR=#000000]A couple of points ... asking one question per thread with an appropriately descriptive title is preferable. It will help others who may have similar issues. [/COLOR]

Sorry.
I wasn't able to change the title, however, I'll try again and I'll open a new one containing only the bluetooth issue.

---

