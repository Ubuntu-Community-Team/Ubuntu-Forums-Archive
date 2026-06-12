---
title: "dkpg of death?"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Servet on 2008-09-13
Hi Ubuntu guys, 1st of let me just say that Ubuntu has been nothing but a positive experience, thank you so much :')

Everytime I try to install a package in add/remove applications.

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So I run it in terminal, and then ...

> dpkg: den ønskede handling kræver superbrugerrettigheder
"dpkg: the following action requires super user rights" or something.

Now I installed a font package, > sudo apt-get install _msttcorefonts_
After install, there was something about deb. something, not sure. 

However this is the result of going fastforward, and now I can't even manage packages and stuff. Please help Ubuntu Forums.

Once again, it has not been anything less than an amazing experience to discover the so many aspects of Ubuntu.

Btw I'm running [SIZE="5"]Ubuntu Hardy Heron 8.04[/SIZE]

---

### Post by northern lights on 2008-09-13
Open a terminal and run ```
sudo dpkg --configure -a
```
What's the scene now?

---

### Post by nothingspecial on 2008-09-13
You need to ```
sudo dpkg --configure -a
```

---

### Post by Sef on 2008-09-13
> northern lights 	 		**Re: dkpg of death?**
 		Open a terminal and run  	Code:
 	sudo dpkg --configure -a 


To open the terminal: Applications > Accessories > Terminal 

then type in that code.

---

### Post by billgoldberg on 2008-09-13
If you need to run a command with "super user" rights, root, just put sudo in front of it.

---

### Post by Servet on 2008-09-13
wow thanks, 4 responses so fast, thank you so much Ubuntu community.

And thanks to you _billgoldberg_, didn't know that :o

---

### Post by northern lights on 2008-09-13
> **billgoldberg said:**
> If you need to run a command with "super user" rights, root, just put sudo in front of it.

> **Servet said:**
> wow thanks, 4 responses so fast, thank you so much Ubuntu community.

And thanks to you _billgoldberg_, didn't know that :o

[This]("https://help.ubuntu.com/community/RootSudo") might be an interesting read.

---

### Post by SunnyRabbiera on 2008-09-13
this error is common, but easy enough to fix.
its nowhere near as bad as a BSOD

---

### Post by Servet on 2008-09-13
thank you :o !
edit:  BSOD? :O

---

### Post by krede21 on 2008-09-25
I had the same problem - i tried 

```
dpkg --configure -a 
```

and got this response:

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
mv: cannot stat `/boot/initrd.img-2.6.24-19-generic.new': No such file or directory
dpkg: underproces post-installation script returnerede afslutningsstatus 1
root@John:/home/christian# 

underproces post-installation script returnerede afslutningsstatus 1 =

something like: "subprocess post-installation script returned finishing-status 1".

What's my problem? And most important, how do I solve it?

---

### Post by lisati on 2008-09-25
> **Servet said:**
> thank you :o !
edit:  BSOD? :O

BSOD = "Blue screen of death". In other words, when the OS grinds to a halt, putting up an error message in white text on a blue background, and forcing you to hit the "big red (power) switch" or it's equivalent on your computer to restart it.

---

### Post by krede21 on 2008-09-25
Reposting on page two:

I had the same problem - i tried

Code:

dpkg --configure -a

and got this response:

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
mv: cannot stat `/boot/initrd.img-2.6.24-19-generic.new': No such file or directory
dpkg: underproces post-installation script returnerede afslutningsstatus 1
root@John:/home/christian#

underproces post-installation script returnerede afslutningsstatus 1 =

something like: "subprocess post-installation script returned finishing-status 1".

What's my problem? And most important, how do I solve it?

---

