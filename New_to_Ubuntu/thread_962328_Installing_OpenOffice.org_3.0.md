---
title: "Installing OpenOffice.org 3.0"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Stalker72 on 2008-10-29
I downloaded OpenOffice.org 3.0 for Linux. The file name is **OOO300_m9_native_packed-1_en-US.9358**. How do I install it?

Stalker72

---

### Post by btermeli on 2008-10-29
First open synaptic and search for openoffice and uninstall all.

Extract the downloaded file on your desktop.
open terminal and be super user, then:
```
cd Desktop
cd NAME_of_the_OO3.0_FOLDER
```
```
cd DEBS
```
```
dpkg -i *.deb
```

to add oo3 to menus;

```
cd desktop-integration
```
```
dpkg -i *.deb
```

---

### Post by Stalker72 on 2008-10-29
??? :confused:

Stalker72

---

### Post by L Campbell on 2008-10-29
> **Stalker72 said:**
> ??? :confused:

Stalker72

In the 6th line of the information in your screenshot, it indicates that you didn't become super user (sudo) as btermeli had recommended.

Hope this helps you.

---

### Post by 73ckn797 on 2008-10-29
> **Stalker72 said:**
> I downloaded OpenOffice.org 3.0 for Linux. The file name is **OOO300_m9_native_packed-1_en-US.9358**. How do I install it?

Stalker72


Here is how I installed Oo 3.0:
[I]  [http://ubuntuforums.org/showthread.php?p=5966220#post5966220](http://ubuntuforums.org/showthread.php?p=5966220#post5966220)

Try it. Very little command line needed.
[/I]

---

### Post by btermeli on 2008-10-29
> **Stalker72 said:**
> ??? :confused:

Stalker72

first , I guess u didn't extract the dowloaded file. you have to right click and choose "extract here".
second,LCampbell mentioned, u have to be super user by 
```
sudo -s
``` u will be asked for your password, enter your pass and press enter.

---

### Post by Stalker72 on 2008-10-29
I don't understand anything of this, seriously. I've tried to follow several guides, including 73ckn797's, with no luck. I only get lots of errors. I'll stick with OpenOffice.org 2.4 for now. Why isn't OpenOffice.org 3.0 already added to Synaptic?

Stalker72

---

### Post by 73ckn797 on 2008-10-29
> **Stalker72 said:**
> I don't understand anything of this, seriously. I've tried to follow several guides, including 73ckn797's, with no luck. I only get lots of errors. I'll stick with OpenOffice.org 2.4 for now. Why isn't OpenOffice.org 3.0 already added to Synaptic?

Stalker72


Did you download the deb that I mentioned? I have installed Oo3.0 on 3 machines without any problem.

---

### Post by OldTimeTech on 2008-10-29
OpenOffice 3 will be in the new 8.10.

---

### Post by Bakon Jarser on 2008-10-29
> **OldTimeTech said:**
> OpenOffice 3 will be in the new 8.10.

I thought it wasn't ready in time for the feature freeze.  I don't think it will be included until 9.04

---

### Post by ad_267 on 2008-10-29
OpenOFfice 3 won't be in 8.10

But if you upgrade to 8.10 then you can add an extra software source to get OpenOffice 3.0. You just add these two lines in System - Administration - Software sources:
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

This WONT work in Hardy.

---

### Post by markharding557 on 2008-10-29
> **Stalker72 said:**
> I don't understand anything of this, seriously. I've tried to follow several guides, including 73ckn797's, with no luck. I only get lots of errors. I'll stick with OpenOffice.org 2.4 for now. Why isn't OpenOffice.org 3.0 already added to Synaptic?

Stalker72

if you download the deb package from open office.org you can install this with gdebi in the right click menu in nautilus or in a console using "sudo dpkg -i package name.deb

---

### Post by ad_267 on 2008-10-29
Yeah you don't need to use the terminal at all to install these packages. You can just double click on them all to install what you want. It's just a hell of a lot quicker to do a "deb -i *.deb" in the terminal.

---

### Post by Stalker72 on 2008-10-29
> **73ckn797 said:**
> Did you download the deb that I mentioned? I have installed Oo3.0 on 3 machines without any problem.
I'm extremely confused with all the file types in Linux. Can you please provide a link?

@ad_267: What is "deb -i *.deb"? Do I substitute the * with something?

(OT: How do I play this movie? See attached thumbnail!)

---

### Post by ugm6hr on 2008-10-29
> **Stalker72 said:**
> I don't understand anything of this, seriously. I've tried to follow several guides, including 73ckn797's, with no luck. I only get lots of errors. I'll stick with OpenOffice.org 2.4 for now. Why isn't OpenOffice.org 3.0 already added to Synaptic?

Do you have the 64-bit Ubuntu? If so - that is slightly trickier.

Otherwise - this should be easy: [http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

I used a very similar tutorial for the OO.org 3.0 Beta, which I haven't bothered upgrading, since I will be installing Intrepid pretty soon anyway.

---

### Post by Stalker72 on 2008-10-29
> **ugm6hr said:**
> Do you have the 64-bit Ubuntu? If so - that is slightly trickier.

Otherwise - this should be easy: [http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

I used a very similar tutorial for the OO.org 3.0 Beta, which I haven't bothered upgrading, since I will be installing Intrepid pretty soon anyway.
I use Linux Mint 5 Elyssa (Main Edition). I think it's 32-bit.

Stalker72

---

### Post by ad_267 on 2008-10-29
This guide seems to explain everything pretty simply: [http://openofficedocs.wordpress.com/2008/10/14/install-openoffice-30-on-ubuntu/](http://openofficedocs.wordpress.com/2008/10/14/install-openoffice-30-on-ubuntu/)

Although it is missing the first step. That is you need to open a terminal and change into the directory where you downloaded the file, for example if it is on the desktop then "cd ~/Desktop"

Looking at your previous attempt, I think you didn't change directory into the DEBS directory.

If you have any questions just ask, it shouldn't be that difficult to get OpenOffice 3 working.

---

### Post by ugm6hr on 2008-10-29
> **Stalker72 said:**
> I use Linux Mint 5 Elyssa (Main Edition). I think it's 32-bit.

Maybe try asking on the Mint forum?  The deb files are for Debian, but work with Ubuntu.  Maybe the modifications in Mint mean that is no longer true?

---

