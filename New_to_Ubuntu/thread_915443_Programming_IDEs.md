---
title: "Programming IDEs"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by beetlejuice_masterson on 2008-09-09
OK--I'm very new to xubuntu.  First off, my wireless card doesnt seem to be working with xubuntu, so until I fix that I'm going to be transferring any software to my xubuntu comp with a usb drive.

That being said, I want to download and install both monodevelop and a good PHP/HTML/JavaScript/HTML IDE.

I don't know how, though.  I guess files can be compressed sometimes and sometimes you ahve to compile them yourself.  Does xubuntu have all the stuff I need to install these types of archives?  How does one go about it?  Any help is appreciated!!!

---

### Post by Sorivenul on 2008-09-10
First lets try to solve that wireless problem.  What card are you using?  If you don't know, in Xubuntu go to Applications > Accessories > Terminal and type:
```
lspci
```

Copy your results to a text file, put it on a flash drive, pop that into a computer you can post from, and post the results here.  Fixing the card may be easier than trying to get all the needed files for any of the major IDEs to work.  

If you have a networked Windows machine, a Wubi install and [APTonCD]("http://aptoncd.sourceforge.net/") may be your best bets if you can't get wireless working.

---

### Post by ad_267 on 2008-09-10
You can download packages from packages.ubuntu.com but you have to make sure you get all the dependencies you need too.

For what IDE to use, geany is pretty basic but it should fit the bill. I just use gedit with a few plugins myself like the symbol browser, embedded terminal, file browser, regex search and replace and LaTeX plugins.

---

### Post by Faolan84 on 2008-09-10
For monodevelop just use synaptic package manager and search for monodevelop. Or if you prefer the terminal:
sudo apt-get install monodevelop

also for a good HTML/PHP IDE try Bluefish or Kompozer.

---

