---
title: "Xserver?"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by rm2011 on 2008-11-01
Hello,
I am trying to install xubuntu on my laptop.  I checked all of the specs and it looks as if everything should be working.  However, when I try to install all i get is a command line, after the "xubuntu" logo.  It says: ```
ubuntu@ubuntu~$
```    But before the command line the screen kinda flashes three or four times.  I have tried earlier suggestions of trying ```
startx
``` but i get the error ```
FATAL ERROR; NO SCREENS FOUND
```  So I have no idea if this is correct but im thinking that the flashing is the graphics system trying to start up?  I have no idea what is wrong, and its getting very frustrating. :mad:   any ideas? :confused:

---

### Post by Mazza558 on 2008-11-01
What does 

> glxinfo 

show, if you run it at the command line?

---

### Post by rm2011 on 2008-11-01
i get:  The program "glxinfo" is not installed.  You may install it by typing sudo apt-get.....

I tried that and it did not work.  I am pretty sure it is because i dont have a network connection
? :confused:

---

### Post by Mazza558 on 2008-11-01
> **rm2011 said:**
> i get:  The program "glxinfo" is not installed.  You may install it by typing sudo apt-get.....

I tried that and it did not work.  I am pretty sure it is because i dont have a network connection
? :confused:

That sounds pretty bad. It sounds like large parts of your install are missing. Do you have the original CD? What happens when you check it for integrity?

---

### Post by rm2011 on 2008-11-01
it says no errors were found.  Do you think maybe i should try to download again, and then make a new CD?  Just an idea...  But i have no idea if that would help or not

---

### Post by Crafty Kisses on 2008-11-01
Not sure what version of Xubuntu you're using, but it could be a driver issue, I'm not sure what kind of video card you have, but if it's NVIDIA try the following:
```
sudo dpkg-reconfigure xserver-xorg
```
You then need to select the **vesa** driver. You can also try to do the following:
```
sudo nano /etc/default/linux-restricted-modules-common
```
Once you've done that add the **nv** module, assuming you have a NVIDIA card:
```
DISABLED_MODULES="nv"
```
If you get something like "This program is not installed" then I'd say you are missing some chunks of your installation and need to reinstall with a alternate CD.

---

### Post by rm2011 on 2008-11-01
it is version 8.10 if that makes a diffrence

---

