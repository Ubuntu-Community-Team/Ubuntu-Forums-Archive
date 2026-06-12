---
title: "Install any driver the Hardy way."
date: 2012-04-18
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-18
I asked how to install my 8187 USB wifi adapter on a non computer forum.

This was the reply.

I've been on Ubuntu since Warty. 

a bit of googling found this comment:

The key to making this device work, it turns out, is not to install ANY driver. The native driver in Hardy works just fine. Following the various posts for installing the 8187b driver will only lead you down the same frustrating road I walked down. Likewise, the driver offered for linux by the realtek website does not work.

I have been toiling for 3 days until I read this post.

The answer and the steps are here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

In 10 minutes my Adapter was alive and well.

Sticky?

---

### Post by Zill on 2012-04-18
> **Boyntonstu said:**
> ...The key to making this device work, it turns out, is not to install ANY driver. The native driver in Hardy works just fine...
You will recall that in your thread entitled [The Install Paradox]("http://ubuntuforums.org/showthread.php?t=1959978") I pointed you to a weblink entitled [Linux is Not Windows]("http://linux.oneandoneis2.org/LNW.htm")

This document was intended to show that things are done differently with Linux.  One example being that drivers are often already installed, as you have now discovered. ;-)

> As a simple example, consider driver upgrades: one typically upgrades a hardware driver on Windows by going to the manufacturer's website and downloading the new driver; whereas in Linux you upgrade the kernel.

This means that a single Linux download & upgrade will give you the newest drivers available for your machine, whereas in Windows you would have to surf to multiple sites and download all the upgrades individually. It's a very different process, but it's certainly not a bad one. But many people complain because it's not what they're used to.

Hopefully, once you figure out how Linux works, you should find things easier than using Windows.  Just don't expect to do things the same way!

---

### Post by Boyntonstu on 2012-04-18
> **Zill said:**
> You will recall that in your thread entitled [The Install Paradox]("http://ubuntuforums.org/showthread.php?t=1959978") I pointed you to a weblink entitled [Linux is Not Windows]("http://linux.oneandoneis2.org/LNW.htm")

This document was intended to show that things are done differently with Linux.  One example being that drivers are often already installed, as you have now discovered. ;-)



Hopefully, once you figure out how Linux works, you should find things easier than using Windows.  Just don't expect to do things the same way!


You know that, but many here and in other places, advised me to download the driver, tar.gz, etc.

What is needed IMHO is a list of devices and how they were successfully installed.

---

### Post by Zill on 2012-04-18
> **Boyntonstu said:**
> You know that, but many here and in other places, advised me to download the driver, tar.gz, etc.
The best approach with Linux is to start by trying the device out first, on the basis that a driver may well be already installed.  If you cannot get the device running then post here with any relevant information, particularly error messages.  Hopefully, you should then receive sufficient advice to resolve the problem.  Note that compilation and the use of tar.gz files etc is deprecated in Ubuntu and such files should only be used as a last resort.
> **Boyntonstu said:**
> What is needed IMHO is a list of devices and how they were successfully installed.
Such lists may already exist but you may have to search for them. ;-)

Again, you need to understand that Linux is not produced by a mega-corporation with armies of staff to produce tons of documentation.  Instead, Linux/FOSS is the product of many thousands of, often unpaid, volunteers who willingly help with this great OS.  If you too wish to help out by producing (or updating!) such a list of devices then you will be made very welcome if you join the [Documentation Team]("https://wiki.ubuntu.com/DocumentationTeam").

---

### Post by Mark Phelps on 2012-04-18
> **Boyntonstu said:**
> What is needed IMHO is a list of devices and how they were successfully installed.

Not realistic.  There are THOUSANDS of devices, and in the case of networking cards, it's not uncommon for the same card to come in several different versions.  Furthermore, since the drivers depend on the chips being used, not actually the cards, the drivers vary by individual chipset and version of chipset.

As folks have tried to point out, in Linux, you dont' start by searching around for drivers or for driver updates.  The Ubuntu installer does the hardware detection and initial driver installation.  If no drivers are installed for a device, you are left with going to the device manufacturer to see if they supply Linux drivers.  If they do not, there might be a ppa you could install and get drivers from there.

If there is no ppa, then you have to live with the device not working -- the major weakness of using Linux distros since very few manufacturers actually supply Linux drivers.

So, really, each and every device is a different case.  It's not feasible to expect anyone to compile instructions for every single device.

---

### Post by ajgreeny on 2012-04-18
All of which shows why it is very important to search out information in the forum on compatible hardware before rushing out to buy a new $(insert hardware item).

Hardware is getting better and better at working with Linux, much more so than windows, where just about everything needs a driver installation (or used to in my windows use), whereas in Linux most, but not all hardware is supported out of the box, particularly if it is not a brand new model version of something.

---

### Post by Curtis6767 on 2012-04-18
> **Mark Phelps said:**
> .

As folks have tried to point out, in Linux, you dont' start by searching around for drivers or for driver updates.  The Ubuntu installer does the hardware detection and initial driver installation. 

This is nice to know, but if Boyntonstu hadn't gone through the process of searching out how to install drivers and then posting results here, then I would have not known this to be the case. And neither would other Noobs.

---

### Post by Zill on 2012-04-18
> **Curtis6767 said:**
> This is nice to know, but if Boyntonstu hadn't gone through the process of searching out how to install drivers and then posting results here, then I would have not known this to be the case. And neither would other Noobs.
I respectfully suggest that "Noobs", as well as experienced users, might take a look at the [Ubuntu Community Documentation]("https://help.ubuntu.com/community").

Ubuntu forums has "stickies" at the start of each section, which often have links to such information.  For example, the sticky entitled "[Supported wireless cards list and procedure to get help]("http://ubuntuforums.org/showthread.php?t=370108")" at the start of the "[Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336")" sub-forum has a link to "[WifiDocsWirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")".  This document advises that the [Realtek RTL8187B]("https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b") (such as listed by the OP) works out of the box.

There is a wealth of information out there - all you have to do is look. ;-)

---

