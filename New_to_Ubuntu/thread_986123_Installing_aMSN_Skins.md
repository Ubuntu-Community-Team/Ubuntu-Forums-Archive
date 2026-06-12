---
title: "Installing aMSN Skins"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Liam1964 on 2008-11-18
I have spent hours trying to figure this one out, to the point that I am now not even sure I want to do it, but because I can't do it ... well now I just have to "get err done" - please help before I go any more insane!!

I am simply trying to copy a decompressed set of files (a skin for aMSN) from one directory to another directory, and I just can't do it for one reason or another ...

liam@liam-ubuntu:~$ sudo su
[sudo] password for liam: 
root@liam-ubuntu:/home/liam# cp /home/liam/Test/ /usr/share/amsn/skins
cp: omitting directory `/home/liam/Test/'
root@liam-ubuntu:/home/liam# 

I have tried as many variations of that as I can think of ... what stupid & silly thing am I getting wrong?

In the directory home/liam/Test is another directory named amsn, I want to move or copy that directory to usr/share/amsn/skins

---

### Post by Liam1964 on 2008-11-18
Am I in the right forum for this question?
Have I not given enough information?
Have I not asked the question clearly enough?
Or do I just smell?

---

### Post by mjwhitfield on 2008-11-18
```
sudo -i
[put in password]
cd /usr/share/amsn/skins/
cp -r /home/liam/Test/* .
```

Which translates to:
Become root
Change to amsn skins directory
Recursively copy everything inside test folder to current location.

---

