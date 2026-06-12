---
title: "HP Deskjet 3520 No Print"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by muddpup64 on 2013-01-26
I have recently bought a HP Deskjet 3520 gone through and installed the proper driver but when I try to print it says it's proccessing but nothing happens.

Any suggestions?
I am running Ubuntu 11.04.

---

### Post by coffeecat on 2013-01-26
I have a HP Deskjet 3520 all-in-one. First thing:

> **muddpup64 said:**
> 
I am running Ubuntu 11.04.

11.04 has been end-of-life (=unsupported) since last October. You'd be better trying to get your printer working in a supported version of Ubuntu.

As far as the latest LTS - 12.04 - is concerned I get the same as you are getting in 11.04, but I haven't investigated this thoroughly yet, mainly because I am using 12.10 routinely, and this HP printer works fine right out of the box in 12.10 and you don't have to install anything - just set up the printer from the Printers utility. The scanner works just fine in 12.10 too.

---

### Post by mapes12 on 2013-01-27
> 11.04 has been end-of-life (=unsupported) since last October. You'd be better trying to get your printer working in a supported version of Ubuntu.Yep. Newer versions of Ubu have the updated hplip package installed by default which means your printer should work out of the box. If you want the printer to work with 11.04 then you will need to visit the hplip website and follow the instructions for downloading and installing the latest version of hplip.

---

### Post by coffeecat on 2013-01-27
> **mapes12 said:**
> If you want the printer to work with 11.04 then you will need to visit the hplip website and follow the instructions for downloading and installing the latest version of hplip.

@muddpup64, I've now had a chance to test this in 12.04. The hplip website recommends the same hplip-3.12.11.run package for both 11.04 and 12.04 and both the printer and scanner now work in 12.04 after installing the 3.12.11 drivers. Hplip website:

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

You will need to remove your 3520 printer from where you installed it in the GUI printing utility and then re-install it after installing the 3.12.11 drivers.

However, I strongly urge you to upgrade your Ubuntu to either 12.04 or 12.10. Just to be clear, with 12.04 you will need to install the hplip 3.12.11 drivers from the hplip website, but the instructions are straightforward. 12.10 comes with the earlier 3.12.6 drivers but both printing and scanning with the 3520 work just fine without you having to install the later drivers.

---

### Post by oldfred on 2013-01-27
Yesterday I just installed my new HP 3520 in 12.04. 
I also down loaded hplip-3.12.11.run as the default install was .3 and quite a bit older.

But there were a bunch of missing dependencies which the script automatically downloaded. If you try to install in a version that is not supported, I do not think you will get the dependencies. Some said required & others seemed optional.

So I also encourage you to upgrade.

---

### Post by lalawawa on 2013-02-16
I went to the ubuntu software center and installed hplip.  I got version hplip 3.12.2-1ubuntu3.1, which is much earlier than the version recommended by others in this thread.

When I try to print, according to 'lpq' the print job runs successfully, but nothing comes out of the printer.

I'm running ubuntu 12.04 LTS.

How do I specify exactly which version of hplip I am to get from the Ubuntu software center?

---

### Post by coffeecat on 2013-02-16
> **lalawawa said:**
> 
I'm running ubuntu 12.04 LTS.

How do I specify exactly which version of hplip I am to get from the Ubuntu software center?

Since you are running 12.04, you need to manually install the later version of hplip downloaded from the website linked earlier in this thread.

---

### Post by oldfred on 2013-02-16
Last day or two I had pop-up from HP saying newer version was available. I run this from command line and it updated.
hp-upgrade


But that was after I had downloaded & installed the version from HP which was a lot newer than the one in the repository so it supported the upgrade. Not sure if old version in repository will work that way or not?

---

### Post by lalawawa on 2013-02-16
OK, I went to install the newer version of hplip:

$ sh hplip-3.13.2.run 

then it says a lot of stuff, and eventually it says

A package manager '18:26 0:07' appears to be running. Please quit the package manager and press enter to continue (i=ignore, r=retry*, f=force, q=quit) :

I go

$ ps auxww | grep package

and it finds nothing.  What is this 'package manager' and how do I turn it off.  I tried rebooting, but it seems that a package manager is always there.

-- Bill

---

### Post by coffeecat on 2013-02-16
A package manager is either update manager, Synaptic or Software Centre. Close whichever of these is open and the installer should be able to run. It could be update manager doing its periodic routine check for updates without you realising it has opened.

---

### Post by lalawawa on 2013-02-16
It will print now, thanks a lot!

But it won't scan.  When I tell the unit to scan (via buttons on the printer/scanner) it says "No computer found.  Make sure the printer software is installed on your computer, and that "Scan to computer" is enabled via the printer software".

So how do I enable scanning?

-- Bill

---

### Post by coffeecat on 2013-02-17
> **lalawawa said:**
> When I tell the unit to scan (via buttons on the printer/scanner) it says "No computer found.  Make sure the printer software is installed on your computer, and that "Scan to computer" is enabled via the printer software".

So how do I enable scanning?

Scan from the computer. I'm fairly sure the default simple scan application works with it, but I always install the more featured app xsane for all my scanning.

---

### Post by lalawawa on 2013-02-17
I used '/usr/bin/simple-scan' and it worked.  Thank you very much! -- Bill

---

