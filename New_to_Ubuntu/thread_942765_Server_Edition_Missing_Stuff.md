---
title: "Server Edition Missing Stuff"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by johanang on 2008-10-09
Ubuntu 8.04 LTS Server Edition - Supported to 2013

I recently downloaded the above. After installing i am missing the entire /etc/apt directory.. where are all the applications?? I went to install Fluxbox and this is where i noticed the problem..

All the application packages are missing. Does anyone know why, what happend? Why does the install not included what they say it includes?

---

### Post by werries on 2008-10-09
Most programs aren't installed in /etc/apt. they're mostly in their own directories in /etc. and the other half are in /usr/bin and /usr/lib.

/etc/apt is NOT where packages are installed. 

/usr/bin is where most programs are located.
/sbin is where system and admin programs are.

isn't there a fluxbox package in the repositories? or maybe add one?
why would you bother installing it manually?

---

### Post by jerome1232 on 2008-10-09
/etc/apt is where apt's configuration settings are stored.

---

### Post by johanang on 2008-10-09
Man i was just paying attention to the instructions provided and documented by Ubuntu on their document site....

I do not want to install manually however seems like a good idea since their fluxbox is way outdated and slow.

FAQ...The following is their instructions that DO NOT WORK.. 

    * - Can I add a "Graphic User Interface", [GUI] To a Server?
    *

      Newbie Question Stanz 

Yes you can, depending on what window manager you wish to use you can install the xserver and the window manager via apt-get. This will install fluxbox for you. Plus you may want some other programs to add to it as you see fit.

sudo apt-get install fluxbox x-window-system-core xdm

This would install the default GNOME desktop that comes with Ubuntu Desktop version.

sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
sudo dpkg-reconfigure xserver-xorg

---

### Post by jerome1232 on 2008-10-09
Those commands work, maybe you need to do a 
'sudo apt-get update' first, what errors are you getting can you post them here?

---

### Post by SunnyRabbiera on 2008-10-09
Any reason you are using the server edition?
Are you running a server?

---

### Post by egalvan on 2008-10-09
> **johanang said:**
> FAQ...The following is their instructions that [COLOR="Red"]DO NOT WORK[/COLOR].. 

    * - Can I add a "Graphic User Interface", [GUI] To a Server?
    *   Newbie Question Stanz 

Yes you can, depending on what window manager you wish to use you can install the xserver and the window manager via apt-get. This will install fluxbox for you. Plus you may want some other programs to add to it as you see fit.

sudo apt-get install fluxbox x-window-system-core xdm

This would install the default GNOME desktop that comes with Ubuntu Desktop version.

[COLOR="Red"]sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
sudo dpkg-reconfigure xserver-xorg[/COLOR]

They worked on my box, no major problems for this newbie...

---

### Post by johanang on 2008-10-14
W: Failed to fetch.. im assuming this means it connected okay.

Im using the Server to learn about the server and Unix. THis is my first attempt at unix in about 10 years.

So i did a sudo apt-get fluxbox install fluxbox x-window-system-core xdm and it cannot find a package called fluxbox. This was done after a apt-get update.

In fact it cannot find any packages.. I've been very disapointed in the documentation. It spends more time talking about what a ip address is rather then trying to change the address. "Figured it out however documentation is awful."

---

### Post by Nxion on 2008-10-14
You need to do this:

```
sudo apt-get install package-name
```Not:
 
```
sudo apt-get fluxbox install
```That command is not the correct way to type it.


This one is:
```
sudo apt-get install package-name
```

---

### Post by jerome1232 on 2008-10-14
> **johanang said:**
> W: Failed to fetch.. im assuming this means it connected okay.

Im using the Server to learn about the server and Unix. THis is my first attempt at unix in about 10 years.

So i did a sudo apt-get fluxbox install fluxbox x-window-system-core xdm and it cannot find a package called fluxbox. This was done after a apt-get update.

In fact it cannot find any packages.. I've been very disapointed in the documentation. It spends more time talking about what a ip address is rather then trying to change the address. "Figured it out however documentation is awful."

If it says "failed to fetch" when you do an apt-get update then your not getting a connection, hence the reason apt can't find any packages. Is the server getting an ip address? Can you ping out to the internet from it?

---

