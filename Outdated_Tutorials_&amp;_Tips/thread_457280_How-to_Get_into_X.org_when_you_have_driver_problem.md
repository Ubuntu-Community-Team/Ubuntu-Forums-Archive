---
title: "How-to Get into X.org when you have driver problems"
date: 2007-05-28
forum: Outdated Tutorials &amp; Tips
---

### Post by fjr0122 on 2007-05-28
I was having problems with my nvidia drivers a while back (I think I had changed cards on it), and I knew if I could get into Envy or Automatix they could install the drivers properly, but for the life of me I couldnt make it work....

Eventually I realized something from way back when (around the time of RedHat 4) where my drivers werent working and so I went in and enabled the Vesa driver, and this gives you a slow unoptimized desktop, but at least it isnt the command line and you can run graphical setup utilities. 

So that is the solution, here's how....

```
ubuntu@ubuntu:~$sudo dpkg-reconfigure xserver-xorg
```

The first question is what driver you want it to use, just choose the Vesa driver towards the bottom and hit enter till the program finishes rolling through all the options....

Then just type 

```
ubuntu@ubuntu:~$startx
```

And you should be able to use your graphical desktop. 

You can also ....

```
ubuntu@ubuntu:~$sudo nano /etc/X11/xorg.conf
```

Then find the Device section...

> Section "Device"
Identifier "Videocard0"
Driver "nv" ....

Then change the driver to vesa, and save the file then run startx. 
 
Your welcome :D

(I also posted this on my blog [www.fjr122.blogspot.com](www.fjr122.blogspot.com) )

---

### Post by Ace2016 on 2007-05-31
My advice is to make a copy of the original xorg.conf after you first install (or just any file like your /boot/grub/menu.lst) that way you can use that as a guide if you end up in a livecd trying to repair the system by hand where the dpkg command won't help (unless you chroot to it, but that takes more work, and a working net connection unless you can remember the commands)

---

