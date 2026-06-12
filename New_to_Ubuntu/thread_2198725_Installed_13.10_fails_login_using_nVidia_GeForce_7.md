---
title: "Installed 13.10 fails login using nVidia GeForce 7300 LE"
date: 2014-01-10
forum: New to Ubuntu
---

### Post by cwmoser on 2014-01-10
I installed Ubuntu 13.10 and it fails login.
My old system was 12.04 and ran just fine.
Tried both the 32-bit and the 64-bit install DVDs.
I am using the nVidia GeForce 7300LE video card.

The 13.10 install seems to work just fine.
On initial login, I get a scrambled screen and then kicked back to the login screen.

Is there a work around?

Thanks

Carl

---

### Post by marianoa on 2014-01-10
You can switch to a terminal session (Ctrl+Alt+F1), install a package called jockey-gtk, it should install a program called jockey-text. You can use this to determine from the command line the drivers that are installed, which one you are using and also select a different one. You can obtain the help page of jockey-text using "jockey-text -h".
I think this is a good starting point to solve your problem.
To go back to the graphical session in order to try to login again use (Ctrl+Alt+F7)

---

### Post by cwmoser on 2014-01-10
Tried jockey-text.  Had to also sudo apt-get jockey-common too.
But, nothing about drivers was outputted when I ran jockey-text.

I did try installing 13.10 in a partition with its own new /home all in the same partition 
and was able to get it to work.  Must have been something in my existing /home
that was causing problems.

Carl

---

### Post by cincibluer6 on 2014-01-10
I find that with graphics problems like that (for future reference) it's good to jump to a terminal like posted above and run the Xreset script in /etc/X11
It has alleviated problems for me in the past when something just won't work right with a graphics card.

Also, with an Nvidia card, using sudo apt-get install nvidia-current usually works too.

---

### Post by cwmoser on 2014-01-11
Tried the Xreset command and tried sudo apt-get install nvidia-current, 
but that screwed the pooch.  Now I get a blank screen when 13.10 boots.

Oh well, not a biggie.  I put it in a partition all by itself for testing.
Funny that neither the 386 version, nor the 64 bit version, nor the Ubuntu-Gnome version 
of 13.10 will work properly on my PC.  I have gone through several versions of
Ubuntu on this PC.  12.04 runs just fine.

I was reading where 13.10 focused on "quality" -- somethings not quite right for PCs like mine.

Carl

---

### Post by cwmoser on 2014-01-11
Are many other folks having problems getting 13.10 to install?

---

### Post by kooldino on 2014-04-11
I'm having the same problem.  I can get it to boot with a different driver (nvidia 331 driver), but the resolution is very low and I can't figure out how to change it.

---

### Post by kooldino on 2014-04-11
Here's how you can install the 331 driver:

[http://news.softpedia.com/news/How-to-Install-the-Latest-NVIDIA-331-20-Drivers-in-Ubuntu-13-10-399182.shtml](http://news.softpedia.com/news/How-to-Install-the-Latest-NVIDIA-331-20-Drivers-in-Ubuntu-13-10-399182.shtml)

---

### Post by kooldino on 2014-04-11
Ok, so now I'm running the 304 driver, but it will load up in just a terminal screen.

However, it will load the desktop in full res if I do the following...

$ sudo modprobe nvidia_304
$ startx

---

