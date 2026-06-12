---
title: "Start an application"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by gc7 on 2008-06-19
I am new to Linux OS, (Ubuntu 8.04 LTS) and having a lot of problems.
1. I can receive e-mail but never get a picture, only text??
2. I have downloaded Google Earth but don't know how to start the     application?? It is on my desktop as a /bin extension??
I would appreciate some advice.

---

### Post by ajgreeny on 2008-06-19
> **gc7 said:**
> I am new to Linux OS, (Ubuntu 8.04 LTS) and having a lot of problems.
1. I can receive e-mail but never get a picture, only text??
2. I have downloaded Google Earth but don't know how to start the     application?? It is on my desktop as a /bin extension??
I would appreciate some advice.
What exactly do you mean by Q1?  Do you get pictures as attachments which do not show or you can not save to your disk?  And what email program are you using, evolution, thunderbird or something else?  It may be possible if using thunderbird to see the pictures in the message by enabling "Display attachments in line" in the view menu.  In evolution, I can't help as I've never used it.

Where did you get Google Earth from, as there is a .deb of it in the medibuntu repos which means you can use synaptic to download and install.  To enable the medibuntu repos use the terminal to add them to your sources.list file with ```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```and then ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```You should now find it listed when you search with synaptic and can install it the easy way.

---

