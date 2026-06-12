---
title: "How to start terminal with full screen display"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by sohaikia1 on 2008-06-12
Hi, I am new to ubuntu and currently I am using ubuntu 8.04 and I think its great beyond my expectations. It is easy to use with extremely good package installer. I am now playing with the terminal and I was wondering how to start the terminal with full screen by default. Hope you guys can help.

---

### Post by Kronie on 2008-06-12
ctrl+alt+f1
ctrl+alt+f7 to quit

---

### Post by iaculallad on 2008-06-12
I don't know if that could be done: starting terminal in full screen mode. You can press F11 to make it full screen once terminal is opened.

---

### Post by ad_267 on 2008-06-12
You can start gnome terminal with the command "gnome-terminal --geometry=100x100" Where 100x100 is replaced with the dimensions you want. If you pick something bigger than your  monitor then it will run fullscreen.

Edit: The dimensions are in characters, not pixels.

Second Edit: You can use gnome-terminal --full-screen
This wasn't in the man page but it was in gnome-terminal --help

If you start the terminal from the menu you will need to right click on the menu and select edit menus then right click on the terminal launcher and select properties and change the command used by adding --full-screen to the end.

---

### Post by buniti on 2009-10-29
> **ad_267 said:**
> 
Second Edit: You can use gnome-terminal --full-screen
ad_267 it must be said: "sweet as". #1 hit on google and spot on. Thanks a lot!

buniti

---

