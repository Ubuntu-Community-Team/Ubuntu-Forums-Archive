---
title: "use a different ld-linux.so.2?"
date: 2012-05-28
forum: Programming Talk
---

### Post by danielsender on 2012-05-28
I saw this topic in  other forums but I could not find the solution.  I have this big package for  which I have no access to the sources, therefore I cannot re-compile  the executables. This program used to run on a CentOS 4x just fine, so I installed 4.8 on a  VirtualBox and it runs but is very slow, so I would like to run it on  the base machine. I copied the key library files in a  folder and exported the LD_LIBRARY_PATH. But the problem is that the  system ALWAYS calls /lib/ld-linux.so.2 to run the programs. I  experimented with a command like:

<my library folder>/ld-linux.so.2 --library-path $LD_LIBRARY_PATH <the ELF executable>

and  it ran well. But the problem is that the main program calls many, but  many children executables for which it would be very cumbersome to  modify the scripts according to the command above. I tried with  LD_PRELOAD but it didn't work (segmentation fault). I wonder if there is  a way to do this.

Thanks in advance

Daniel

---

### Post by danielsender on 2012-05-29
any guru willing to help?

---

### Post by roelforg on 2012-05-30
*sigh* Fine...
The problem is this:
Ubuntu and Cent-OS are 2 totally different distros (yes, i've used centos and i like ubuntu a lot better).
The ld-linux on them isn't compatible.
For one, Centos is from the rpm (redhat) family and ubuntu the deb (debian) family.
They're like black and white, not very compatible.
Statically compiled binaries will sometimes work (given the kernel versions/arch/(some other stuff) match), but if it were statically compiled you wouldn't need ld-linux.
It's not gonna work w/o wrecking either setup to the point most stuff won't work (i've tried).

EDIT: Lol - 1024'th post (i'm a geek and a programmer, it's just a special number... 1-2-4-8-16-32-64-128-256-512-**1024**-2046-4096-etc)

---

### Post by danielsender on 2012-05-30
Sorry, perhaps I didn't make myself clear on my setup. I have this machine with 2 partitions. One has Precise 12.04 and the other CentOS 6.2 (the latest). So in reality, Ubuntu has nothing to do here (I also like Ubuntu MUCH better). I have a program that runs OK on CentOS 4x, but barfs on 6.2. I copied some library files from 4x into a dedicated folder on 6.2 and try running one of the executables of the program by using:

<my_folder>/ld-linux.so.2 --library-path $LD_LIBRARY_PATH <the executable>

and did OK. The problem is that I don't know how to make my own ld-linux.so.2 be de default program loader, it seems that always goes into /lib/ld-linux.so.2, ignoring LD_LIBRARY_PATH. If there would be a single executable, there wouldn't be an issue, but this program opens a bunch of children processes with the same library issues. I thought that perhaps something like fakechroot could do the job, but its documentation is very cryptic to say the least.

---

### Post by roelforg on 2012-05-31
> **danielsender said:**
> Sorry, perhaps I didn't make myself clear on my setup. I have this machine with 2 partitions. One has Precise 12.04 and the other CentOS 6.2 (the latest). So in reality, Ubuntu has nothing to do here (I also like Ubuntu MUCH better). I have a program that runs OK on CentOS 4x, but barfs on 6.2. I copied some library files from 4x into a dedicated folder on 6.2 and try running one of the executables of the program by using:

<my_folder>/ld-linux.so.2 --library-path $LD_LIBRARY_PATH <the executable>

and did OK. The problem is that I don't know how to make my own ld-linux.so.2 be de default program loader, it seems that always goes into /lib/ld-linux.so.2, ignoring LD_LIBRARY_PATH. If there would be a single executable, there wouldn't be an issue, but this program opens a bunch of children processes with the same library issues. I thought that perhaps something like fakechroot could do the job, but its documentation is very cryptic to say the least.

In that case, post in other os/distro because this forum is for programming and this is clearly a centos issue.
Ps. binaries tend to break when the kernel versions differ so much.
Read up on dynamic linking on linux and you'll understand why it's very complex to do what you want..

---

### Post by danielsender on 2012-06-01
This is the scope of this particular forum:
[B]
Programming Talk[/B] This forum is for all programming questions.
The questions do not have to be directly related to Ubuntu and any programming language is allowed.

Or am I missing something?

---

### Post by roelforg on 2012-06-01
> **danielsender said:**
> This is the scope of this particular forum:
 
**Programming Talk** This forum is for all programming questions.
The questions do not have to be directly related to Ubuntu and any programming language is allowed.
 
Or am I missing something?
 
Ubuntu AND any programming language.
This question involves neither (you admitted that yourself).

---

### Post by danielsender on 2012-06-01
Perhaps the scope is in a different language than English or this is a Monty Pithon type of dialog

---

