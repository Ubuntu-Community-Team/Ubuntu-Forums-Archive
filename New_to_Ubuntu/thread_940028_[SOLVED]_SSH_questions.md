---
title: "[SOLVED] SSH questions"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by Headfirst on 2008-10-06
First off let me start with I am new to Linux just last week i did my first dual-boot with xp great success! Now my problem is in xp i used Putty to connect to the unix server at my college when writing programs..what is the best way to login to that unix server from Linux i assume it should be easy to do i'm just not quite knowledgeable enough to figure it out.

Thanks in advanced.

---

### Post by cek on 2008-10-06
You need an ssh client, such as open-ssh.  This will give you an ssh client that can be run in the terminal via the command "ssh".

---

### Post by AndyCooll on 2008-10-06
PuTTY is in the repositories and you could install that if that's what you are comfortable working with.

However as cek points out installing openssh-client would be sufficient. You can install it either from Synaptic (System > Administration > Synaptic Package Manger) or from the command line (Accessories > Terminal):
```
sudo apt-get install openssh-client
```
Then you'd connect to the server using:
```
ssh you@server
```
Or using more arguments depending on you circumstances.

:cool:

---

