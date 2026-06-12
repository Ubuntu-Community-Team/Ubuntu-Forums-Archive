---
title: "[SOLVED] configure script missing"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by no_idea on 2008-08-14
Hello, I'm having a problem with installing a package in ubuntu 8.04. I've just downloaded it in tar.gz format, untarred it, and i'm trying to run ./configure in the specific folder but i can't because the file is missing. Can this be? And if it can what can I do to go on with the package installation?

---

### Post by no_idea on 2008-08-14
I forgot to say that the package is ubuntu-restricted-extras and I can't find it it synaptic so that's why i had to install it manually

---

### Post by Troll_the_Great on 2008-08-14
Hi!
Tar.gz file are difficult to install, especially for a beginner.Look inside the folder and see if you find a "read me" file with install instructions.
Can I ask what package are you trying to install?Couldn't you find it in synaptic, or a .deb file?

---

### Post by Troll_the_Great on 2008-08-14
> **no_idea said:**
> I forgot to say that the package is ubuntu-restricted-extras and I can't find it it synaptic so that's why i had to install it manually

Lol, I was too slow in my first post.And I don't know why you can't find it in synaptic because is there....I just searched and found it...Are you sure you didn't mistype?

---

### Post by no_idea on 2008-08-14
There's no readme, only another folder named debian and lots of files. I could only find this tar.gz format and dsc format but I don't know what to do with it

---

### Post by Troll_the_Great on 2008-08-14
Or you can try this:go to Applications-Add/Remove and under "Show" choose "All available applications"
In the search bar type "ubuntu" and is the first thing that appears.
Cheers!

---

### Post by no_idea on 2008-08-14
I really can't find it in synaptic. i just looked for it again and it isn't there :(

---

### Post by Troll_the_Great on 2008-08-14
> **no_idea said:**
> I really can't find it in synaptic. i just looked for it again and it isn't there :(

Try in Add/Remove how I said in my last post.

---

### Post by no_idea on 2008-08-14
what do you know, it's in that add/remove thing thanks a lot, but still.. how come i can't find it in synaptic? anyway.. doesn't matter
Thanks!

---

### Post by Troll_the_Great on 2008-08-14
> **no_idea said:**
> what do you know, it's in that add/remove thing thanks a lot, but still.. how come i can't find it in synaptic? anyway.. doesn't matter
Thanks!

I am surprised myself...but all is well when ends well.Glad I could help, please mark you thread as solved using the thread tools.
Cheers!

---

### Post by t0p on 2008-08-14
> **no_idea said:**
> I really can't find it in synaptic. i just looked for it again and it isn't there :(

The only reason I can think of for your inability to find ubuntu-restricted-extras in Synaptic is because you don't have the correct repos enabled.  That package will be in "multiverse" I think (please correct me if I'm wrong).

If you really, really want to install from the tarball you downloaded and don't know how, the best thing to do is to list here the contents of the folder.

---

### Post by no_idea on 2008-08-14
well.. i guess it's always useful to learn something new.. especally when we're talink about the command line :D So here's the contents of the folder:

ubuntu@ubuntu:~/temp/ubuntu-restricted-extras-15$ ls -la
total 84
drwxr-xr-x 3 ubuntu ubuntu 500 2008-04-17 13:54 .
drwxr-xr-x 3 ubuntu ubuntu 120 2008-08-14 22:22 ..
drwxr-xr-x 2 ubuntu ubuntu 160 2008-04-17 13:58 debian
-rw-r--r-- 1 ubuntu ubuntu 121 2008-03-23 03:09 kubuntu-restricted-extras-amd64
-rw-r--r-- 1 ubuntu ubuntu 101 2008-04-17 13:58 kubuntu-restricted-extras-hppa
-rw-r--r-- 1 ubuntu ubuntu 121 2008-04-17 13:54 kubuntu-restricted-extras-i386
-rw-r--r-- 1 ubuntu ubuntu 101 2008-03-23 03:09 kubuntu-restricted-extras-ia64
-rw-r--r-- 1 ubuntu ubuntu 101 2008-04-17 13:57 kubuntu-restricted-extras-lpia
-rw-r--r-- 1 ubuntu ubuntu 107 2008-04-17 13:55 kubuntu-restricted-extras-powerpc
-rw-r--r-- 1 ubuntu ubuntu 101 2008-03-23 03:09 kubuntu-restricted-extras-sparc
-rw-r--r-- 1 ubuntu ubuntu 231 2008-03-23 03:09 ubuntu-restricted-extras-amd64
-rw-r--r-- 1 ubuntu ubuntu 211 2008-04-17 13:58 ubuntu-restricted-extras-hppa
-rw-r--r-- 1 ubuntu ubuntu 253 2008-04-17 13:54 ubuntu-restricted-extras-i386
-rw-r--r-- 1 ubuntu ubuntu 211 2008-03-23 03:09 ubuntu-restricted-extras-ia64
-rw-r--r-- 1 ubuntu ubuntu 211 2008-04-17 13:57 ubuntu-restricted-extras-lpia
-rw-r--r-- 1 ubuntu ubuntu 217 2008-04-17 13:55 ubuntu-restricted-extras-powerpc
-rw-r--r-- 1 ubuntu ubuntu 211 2008-03-23 03:09 ubuntu-restricted-extras-sparc
-rw-r--r-- 1 ubuntu ubuntu  98 2008-03-23 03:09 xubuntu-restricted-extras-amd64
-rw-r--r-- 1 ubuntu ubuntu  78 2008-04-17 13:58 xubuntu-restricted-extras-hppa
-rw-r--r-- 1 ubuntu ubuntu  98 2008-04-17 13:54 xubuntu-restricted-extras-i386
-rw-r--r-- 1 ubuntu ubuntu  78 2008-03-23 03:09 xubuntu-restricted-extras-ia64
-rw-r--r-- 1 ubuntu ubuntu  78 2008-04-17 13:57 xubuntu-restricted-extras-lpia
-rw-r--r-- 1 ubuntu ubuntu  84 2008-04-17 13:55 xubuntu-restricted-extras-powerpc
-rw-r--r-- 1 ubuntu ubuntu  78 2008-03-23 03:09 xubuntu-restricted-extras-sparc

---

