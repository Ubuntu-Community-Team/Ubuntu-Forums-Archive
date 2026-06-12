---
title: "first boot cant login- ubuntu 8.04 gen."
date: 2008-07-25
forum: New to Ubuntu
---

### Post by linux noobyy on 2008-07-25
hello all,
 okay I'm completely new to Linux and having trouble logging into desktop. I have installed ubuntu 8.04 general as a dual boot with windows xp. 
 
 I boot from the grub to ubuntu 8.04 general and everything goes well, until i get to the login page. 
 
 I type in my user name and password, which it accepts, it starts to login to my desktop but then the screen goes black and it goes right back to the log in screen again. Ive tried logging in several times but this happens every time. I have even tried reinstalling ubuntu a few times and still get the same results.

 The default session is, Xclientscript, which im not able to log into. I am only able to login in gnome fail-safe mode. I am not able to login to a regular session. 

PLEASE HELP!
-thanks, the noooob

---

### Post by gerbalblaste on 2008-07-25
Try this:
At boot up, you should have (at least) 3 options (if you don't see them, pres ESC several times when the computer boots):
Ubuntu 8.04.1 kernel 2.6.24-19 generic
**Ubuntu 8.04.1 kernel 2.6.24-19 generic-recovery mode**
Memtest86
Choose **recovery mode** and in the menu that you see choose **repair X server** and then normal boot.
See if this works and post the results.

---

### Post by linux noobyy on 2008-07-25
no luck. same thing still happening. i log in and hear the music but just a blank desktop then it redirects me right back to the login page.

I have an AMD 64 athlon so i downloaded the 64 bit version. maybe I should try the x86 version?

---

