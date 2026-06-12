---
title: "ultranoob needs help updating firefox in xubuntu 12.04"
date: 2014-03-20
forum: New to Ubuntu
---

### Post by woogie2 on 2014-03-20
Hello all

So far I can use my Xubuntu 12.04 disc to look around in xubuntu live, but can't figure out how to update the firefox to the lastest version so I can get the HTML5 add-on so I can watch youtube. :confused:

I *think* I downloaded the update, but from there I'm lost, it makes no logical sense to me.

---

### Post by kc1di on 2014-03-20
not sure I understand what your doing there. 
if your using the live Dvd you can't upgrade it until you install it on your computer.  then you should be able to update the the latest version.

---

### Post by woogie2 on 2014-03-21
So I can't update Firefox (I think the Firefox that comes with my Xubuntu 12.04 32 bit CD is a low rev like 2.xx or 4.xx or something, and now it's up to 28.xx) until I actually *install* the Xubuntu?

---

### Post by codingman on 2014-03-21
Why don't you install Xubuntu? Once you do, you can run:

```
sudo apt-get update && sudo apt-get upgrade firefox
```

It will then ask for password, and you can enter it, but remember it will not show your password as you are typing, only a blinking cursor.

If you do want the latest version of Firefox in a live CD, Xubuntu 13.10 might have it, but I'm not sure why you wouldn't want to install Xubuntu before watching YouTube.

---

### Post by woogie2 on 2014-03-21
Okay thanks people that I will do, install the Xubuntu and see how I do.


So I have to insert that bit of code somewhere? Where? Or will it be easy enough to find?:popcorn:

---

### Post by codingman on 2014-03-21
Just let us know when you have it installed, and I'll walk you through it :) .

---

### Post by kc1di on 2014-03-22
In fact while you are installing , if you have a fairly good internet connection , you can upgrade all the programs by selecting the option to update while installing.
or your can wait until it's installed and type the following in a terminal to update your system to the latest stable programs
```
sudo apt-get update
sudo apt-get upgrade
```

Good Luck and enjoy :)

---

### Post by Rob Sayer on 2014-03-22
Lots of people prefer to do the upgrades while installing.  Use a wired connection if you do this.  This could be made clearer in the installer IMO.

I prefer to install and then update.  But if you do that the above commands in terminal aren't what you want to do.  apt-get upgrade won't actually remove packages/programs and replace them, and if you do a 12.04 update you'll replace the kernel.  The right commands are:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

... or you could just use the GUI tool in Menu->Settings Manager->Software Updater ... if I remember that right (I'm an ex xubuntu user).

---

### Post by codingman on 2014-03-22
Oh yeah, forgot that you can install updates during installation! When you're done, just to check, run:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get clean
sudo apt-get autoclean

```
(Did I get the commands right?, currently in the Windows side of dual-boot.)

---

### Post by kc1di on 2014-03-22
> **codingman said:**
> Oh yeah, forgot that you can install updates during installation! When you're done, just to check, run:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get clean
sudo apt-get autoclean

```
(Did I get the commands right?, currently in the Windows side of dual-boot.)
as pointed out above you should use:

```
sudo apt-get dist-upgrade 
```
instead of upgrade..

---

