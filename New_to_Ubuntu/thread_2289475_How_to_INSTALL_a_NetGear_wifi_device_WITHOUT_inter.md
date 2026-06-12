---
title: "How to INSTALL a NetGear wifi device WITHOUT internet access via Thumbdrive?"
date: 2015-08-04
forum: New to Ubuntu
---

### Post by lukes2 on 2015-08-04
So it was supposively solved here: [http://ubuntuforums.org/showthread.php?t=2221251&page=4](http://ubuntuforums.org/showthread.php?t=2221251&page=4)
but it wasn't thorough enough because it required internet on the actual PC. I don't have that luxery. Instead, I have to manually install everything (I got ubuntu on via YUMI on a flashdrive), which can be a pain, and sometimes overwhelming.

On the forum, the said to use their Broadcom driver ([http://media.cdn.ubuntu-de.org/forum...4bit_v2.tar.gz]("http://media.cdn.ubuntu-de.org/forum/attachments/06/41/2612284-Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz")). But in order to do that, you need the WLAN tool, and in order to access the WLAN tool, you need ndiswrapper installed. I then checked to see how to install the ndiswrapper from a thumb drive ([http://ubuntuforums.org/showthread.php?t=1727542](http://ubuntuforums.org/showthread.php?t=1727542)), and then I found out that their their thread to install a WINDOWS DRIVER was no longer available (I went through all the "Installation/Downloading" instructions from the program [and they said to go on [http://ndiswrapper.sourceforge.net/wiki/List](http://ndiswrapper.sourceforge.net/wiki/List), which is no longer available). 

So now, I have no ndiswrapper, and no WLAN tool to unpackage the wacom driver. 

Long story short, I'm frusterated and about the ditch the stupid computer if this continues. I have no internet connection, which why in the first place would someone want an internet stick if they don't have internet?! (that was rhetorical). In any case, please help me. 

Specs:
the lsusb command recognizes my Netgear USB.

the ndiswrapper -l command says that "ndisrappwer" is currently not installed. If I do the command to get it, it leads to the internet.

Basically, I need help running through how to find a "windows driver" for my computer to finish the installation of ndiswrapper (according to [http://ubuntuforums.org/showthread.php?t=1727542](http://ubuntuforums.org/showthread.php?t=1727542))




Yea, it's a long loop, but I just poured out my story. PLEASE SAVE ME!!!

Thanks
-I_M_3rd
LukeS

---

### Post by Geoffrey_Arndt on 2015-08-04
Provided you do have access to a wifi network, and, if you really want a simple solution . . . just get the right internet device (plug & play).    See below (the dongle costs about $10 on Amazon).

Available on Amazon or similar sites - about $20 usd for the adapter w/high gain antenna - - or can get _Panda 150 Ultra Wireless adapter _(dongle) for 1/2 the price.

_Panda  300Mbps Wireless-N USB Adapter w/ WPS button - 802.11 n, 2.4GHz -  w/  High Gain Antenna_ -Compatible with Windows   XP/Vista/7/8/8.1/10/2008r2/2012r2, Mint 14/15/16/17/17.1, Ubuntu   12.10/13.04/13.10/14.04/14.10, Fedora 18/19/20/21, openSUSE   12.2/12.3/13.1,CentOS 6.4/6.5/7, Lubuntu 12.10/13.04/13.10/14.04/14.10,   Zorin 8.1/9.1, Kali Linux and Raspbian Wheezy

No drivers, No Wrapper, No-Problem!  ):P

---

### Post by lukes2 on 2015-08-04
> **Geoffrey_Arndt said:**
> Provided you do have access to a wifi network, and, if you really want a simple solution . . . just get the right internet device (plug & play).    See below (the dongle costs about $10 on Amazon).

Available on Amazon or similar sites - about $20 usd for the adapter w/high gain antenna - - or can get _Panda 150 Ultra Wireless adapter _(dongle) for 1/2 the price.

_Panda  300Mbps Wireless-N USB Adapter w/ WPS button - 802.11 n, 2.4GHz -  w/  High Gain Antenna_ -Compatible with Windows   XP/Vista/7/8/8.1/10/2008r2/2012r2, Mint 14/15/16/17/17.1, Ubuntu   12.10/13.04/13.10/14.04/14.10, Fedora 18/19/20/21, openSUSE   12.2/12.3/13.1,CentOS 6.4/6.5/7, Lubuntu 12.10/13.04/13.10/14.04/14.10,   Zorin 8.1/9.1, Kali Linux and Raspbian Wheezy

No drivers, No Wrapper, No-Problem!  ):P

If I'm in total dispair, I'll think about it. Thanks you, though. I already have to spend $30 to upgrade my RAM and CPU, so $50 is kind of out of my price range.

---

### Post by haplorrhine on 2015-08-04
You can probably fit hundreds of .deb files onto any old flashdrive.  Find out which driver you need -- I'm tempted to suggest [bcmwl-kernel]("http://packages.ubuntu.com/trusty/bcmwl-kernel-source").  Once you know, search for it in packages.ubuntu.com.  Look at its dependencies and get those too.  For each .deb file, be sure to get the right version for your processor architecture and Ubuntu release.

---

### Post by lukes2 on 2015-08-04
> **haplorrhine said:**
> You can probably fit hundreds of .deb files onto any old flashdrive.  Find out which driver you need -- I'm tempted to suggest [bcmwl-kernel]("http://packages.ubuntu.com/trusty/bcmwl-kernel-source").  Once you know, search for it in packages.ubuntu.com.  Look at its dependencies and get those too.  For each .deb file, be sure to get the right version for your processor architecture and Ubuntu release.
I'm confused at what you mean, can you restate that in a simpler format for me please? What am I looking for exactly? The desktop HAD windows 7, but it's no longer there. The ubuntu version is 14.04 LTS, and the nswrapper is 1.59. What do I look for?

---

### Post by sandyd on 2015-08-04
You basically need another computer to download the packages in the meantime.

For example, with ndiswrapper, what you will need is ndiswrapper-utils.

So, we go on [http://packages.ubuntu.com](http://packages.ubuntu.com) (we can normally do this via apt-cache, but you don't have internet), and search for ndisrapper-utils. That brings us to [http://packages.ubuntu.com/trusty/ndiswrapper-utils-1.9](http://packages.ubuntu.com/trusty/ndiswrapper-utils-1.9) after a few clicks.

From the page, we can download either the amd64 deb or the i386 deb onto a USB drive. The package also depends on ndiswrapper-common and reccomends ndiswrapper-dkms, so we go to the page for those two packages and download them as well. 

Place them into a empty folder in your USB drive, and then plug it into your internet-less Ubuntu installation.

Using the terminal, browse to the folder on the USB, and run the following
```
sudo dpkg -i *deb

```

That should get ndiswrapper installed

Regards,

---

### Post by Vladlenin5000 on 2015-08-05
> **sandyd said:**
> That should get ndiswrapper installed

Then, you'll need the exact Windows XP drivers for your device and, again, you'll need another PC to download it and save to the thumbdrive.
Then you'll have to open the wrapper and select those 5 years old drivers.

Then, most certainly you'll find out it doesn't work and all of this was a huge waste of time. At this point you'll finally understand post #2, hopefully.

---

### Post by lukes2 on 2015-08-08
> **Vladlenin5000 said:**
> Then, you'll need the exact Windows XP drivers for your device and, again, you'll need another PC to download it and save to the thumbdrive.
Then you'll have to open the wrapper and select those 5 years old drivers.

Then, most certainly you'll find out it doesn't work and all of this was a huge waste of time. At this point you'll finally understand post #2, hopefully.
Do you have a link to the windows xP drivers? I can't find one... And I don't understand anything.

This has been a really bad week. -_-

WAIT: So you're saying the drivers won't work, and I'll have to invents $20... 0_o Get ubuntu cause it's compatable they said... -_-

---

### Post by lukes2 on 2015-08-08
> **sandyd said:**
> You basically need another computer to download the packages in the meantime.

For example, with ndiswrapper, what you will need is ndiswrapper-utils.

So, we go on [http://packages.ubuntu.com](http://packages.ubuntu.com) (we can normally do this via apt-cache, but you don't have internet), and search for ndisrapper-utils. That brings us to [http://packages.ubuntu.com/trusty/ndiswrapper-utils-1.9](http://packages.ubuntu.com/trusty/ndiswrapper-utils-1.9) after a few clicks.

From the page, we can download either the amd64 deb or the i386 deb onto a USB drive. The package also depends on ndiswrapper-common and reccomends ndiswrapper-dkms, so we go to the page for those two packages and download them as well. 

Place them into a empty folder in your USB drive, and then plug it into your internet-less Ubuntu installation.

Using the terminal, browse to the folder on the USB, and run the following
```
sudo dpkg -i *deb

```


That should get ndiswrapper installed

Regards,

It says "dpkg: dependency problems preven configuration of ndiswrapper-utils-1.9: ndiswrapper-utils-1.9 depends on ndiswrapper-common; however: Package ndiswrapper-common is not installed

The i386 was the correct version (it didn't recognize the amd64 one), but for some reason it won't download.

---

