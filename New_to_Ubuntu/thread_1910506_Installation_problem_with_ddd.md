---
title: "Installation problem with ddd"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by newbye on 2012-01-17
HI i am completely new to linux. I want to install ddd package in my computer. But when i use
sudo apt-get install ddd  i get the following error message :
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ddd

What does this mean ? What should I do in order to install ddd ?

---

### Post by yetiman64 on 2012-01-17
What is the program ddd to be used for? 
I ask as there is a command already in your system called "dd", **if**  dd is what you are after it will be already installed (it is a command  line tool in the core-utils package which is part of the default  install).

Edit: after seeing in post 3 there is a ddd app, I checked a bit more and it is specifically in the "Universe" repository. Enabling the Universe repository in "Software Sources" should fix your problem. Typing "soft" in Dash and clicking on Software Sources is a bit more direct way of getting to it than the Synaptic menus (particularly if you are in 11.10 Synaptic is not installed by default anymore).

---

### Post by WasMeHere on 2012-01-17
Hi newbye,

Welcome to the Ubuntu Forums :-)

```
sudo apt-get install ddd
``` works for me with Ubuntu 10.04 LTS. Maybe you need to activate all program sources (in a menu entry of the GUI program Synaptics).

Have fun finding out about Ubuntu
Olle

---

### Post by satanselbow on 2012-01-17
It is in the "Universe" (archive.ubuntu.com) repo ;)

ddd = Data Display Debugger :D

---

