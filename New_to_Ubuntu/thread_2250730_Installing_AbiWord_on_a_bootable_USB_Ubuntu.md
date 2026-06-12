---
title: "Installing AbiWord on a bootable USB Ubuntu"
date: 2014-10-30
forum: New to Ubuntu
---

### Post by shaz2 on 2014-10-30
HI there

I am having issues installing AbiWord on the command terminal. 

New to this, basically I want to install Abiword from the Command terminal however I am getting the following error message. 

Where am I going wrong on this. 

```
ubuntu@ubuntu:~$ sudo apt-get install abiword-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package abiword-gnome
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 
```

---

### Post by shaz2 on 2014-10-30
Got ot sorted :) gnome removed at it worked

---

### Post by Rob Sayer on 2014-10-31
Little hint: if installing via terminal do sudo apt-get update first.

Second little hint: install synaptic.  It's a great package manager.  I always use it or terminal to install.  It's been so long since I used the Software Center I'm starting to forget how it works. In synaptic hit the reload button to update your package list before installing.  Best of all, it searches so you could just type 'abiword' or whatever.  You can end up with a long list though ...

Now you should mark this thread [SOLVED].

---

### Post by shaz2 on 2014-11-02
Solved Thank you :)

---

