---
title: "Installing Openoffice 3"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by rayboston on 2008-10-22
Hi,

How do I install Open Office 3 so that it replaces Open Office 2.4 in my menus and as the program that gets launched when I double click on an open office document?

I can't find a .deb file for it, or a reference in Synaptic.

Thanks!
Ray

PS. I have downloaded it, and run the setup.  But this installed it in /tools/opt and I don't think that I've done it right.

---

### Post by Ctrl+Alt+Del on 2008-10-22
no you did right, it is supposed to go in /opt

---

### Post by rayboston on 2008-10-22
Hi,

OK.  I can reinstall then and tell it to put it into / and it will go into /opt.

But will that get it into the menus and register it with the .odt extension?

Thanks!

Ray

---

### Post by DJ_Peng on 2008-10-22
OpenOffice.org 3 won't replace your current installation of OpenOffice.org 2.4, but [Tombuntu]("http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/") has steps to replace 2.4.

---

### Post by rayboston on 2008-10-22
Hmmm..

I decided to run ./setup with sudo and now I'm getting an error.

It is complaining that openoffice.org3 must be installed to fulfill a dependency for open office.  But I see an openoffice.org3 directory.

Am I doing something wrong?

Ray

PS It is now trying to install in /opt with no problem.  The sudo took care of that.

---

### Post by rayboston on 2008-10-22
Aha!  Thanks.  The Tombunto site showed me the error of my ways.  I had downloaded the RPM version.

---

### Post by jmcgovern on 2008-10-22
If you want 3.0 to completely replace 2.4, you'll have to use the 2.4 uninstall command listed on Tombuntu to completely remove 2.4 before installing 3.0.  Id recommend using Tom's terminal command instead of trying to do it through some other terminal command or through synaptic, since Tom's oommand gets every part of 2.4 off.  If there's any part of 2.4 left on the system when you try to install 3.0, you'll end up with broken packages and updating may break.

---

### Post by DJ_Peng on 2008-10-22
I have to agree with the Terminal uninstall. I went through Synaptic a while back trying to figure out why the heck 3.0's Calc wouldn't run. Tombuntu's a site I make a point of having in my RSS feeds just because he's always got such great info.

---

### Post by NewJack on 2008-10-22
Not trying to hijack here, but....

Is Tombuntu's installation directions the best so far?  I have come across many sites that all slightly differ from each other on the install process.  I honestly just didn't feel like following the first "HowTo" I came across and then have to figure out what went wrong later.

Thanks!

---

### Post by Teamgeist on 2008-10-22
> **NewJack said:**
> Not trying to hijack here, but....

Is Tombuntu's installation directions the best so far? 

From what I've read about installing OO.o 3.0 in **Hardy** YES!

For Intrepid the PPA from calc might be better.

---

### Post by Fass on 2008-10-22
> **Teamgeist said:**
> For Intrepid the PPA from calc might be better.

For those who are running Intrepid, in order to use them, add this to your /etc/apt/sources.list file:

```
#Calc's Open Office PPA
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

Then just run the update manager and upgrade to Open Office 3 (or, you know, do your command line magic with apt-get/aptitude or whathaveyou).

Edit: Though it may seem that the PPA has a Hardy version as well, [if I am browsing correctly.](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/) In which case just replace "intrepid" with "hardy" in the above lines.

---

### Post by jbg7474 on 2008-10-22
> **Fass said:**
> For those who are running Intrepid, in order to use them, add this to your /etc/apt/sources.list file:

```
#Calc's Open Office PPA
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

Then just run the update manager and upgrade to Open Office 3 (or, you know, do your command line magic with apt-get/aptitude or whathaveyou).

Edit: Though it may seem that the PPA has a Hardy version as well, [if I am browsing correctly.](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/) In which case just replace "intrepid" with "hardy" in the above lines.

Doesn't seem to work with hardy--updating doesn't indicate any packages available for upgrade.  Also, the package sizes are much different than the ones in intrepid (too small).  My guess: these are placeholders for a future available upgrade for hardy.

---

### Post by Fass on 2008-10-22
> **jbg7474 said:**
> Doesn't seem to work with hardy--updating doesn't indicate any packages available for upgrade.  Also, the package sizes are much different than the ones in intrepid (too small).  My guess: these are placeholders for a future available upgrade for hardy.

Thanks for trying anyway, I would have checked myself, but I don't have a Hardy install left.

---

### Post by DJ_Peng on 2008-10-22
> **Fass said:**
> For those who are running Intrepid, in order to use them, add this to your /etc/apt/sources.list file:

```
#Calc's Open Office PPA
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```Then just run the update manager and upgrade to Open Office 3 (or, you know, do your command line magic with apt-get/aptitude or whathaveyou).

Edit: Though it may seem that the PPA has a Hardy version as well, [if I am browsing correctly.]("http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/") In which case just replace "intrepid" with "hardy" in the above lines.
Actually if you look at the list of packages on the [PPA page]("https://launchpad.net/%7Eopenoffice-pkgs/+archive") it only says "Intrepid" under Series, which means there's only packages for 8.10. And then there's the info at the very top of the page:
> **PPA for OpenOffice.org Scribblers**
                                          
        **URL: [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu)**

                          OpenOffice.org 3.0.0 - INTREPID ONLYThose last two words should have been a tell: There's no packages for Hardy in that PPA at all. Sorry.

---

### Post by NewJack on 2008-10-22
> **Teamgeist said:**
> From what I've read about installing OO.o 3.0 in **Hardy** YES!

Thanks again!  Just installed using the Tombuntu instructions and all went flawlessly.

---

