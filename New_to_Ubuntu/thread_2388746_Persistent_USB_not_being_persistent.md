---
title: "Persistent USB not being persistent"
date: 2018-04-06
forum: New to Ubuntu
---

### Post by fsa259 on 2018-04-06
Hello everyone,

I tried using UNetbootin and Linux Live USB Creator to create a persistent Ubuntu 17.10 on my Fat32 flash drive. I am able to boot into it but on every restart it still doesn't save anything. I created a few folders to test it and they all disappear. My main issue is that the laptop I am trying to use it on to try and repair requires the [COLOR=#000000][FONT=&quot]bcmwl-kernel-source[/FONT][/COLOR] to be installed on each restart in order to make use of the wlan adaptor.

Mkusb is mentioned in a few threads here, but as I understand it is a Linux programme and I can't use it on the same USB I am booting from. One solution is to buy another USB and use my current one to boot into Ubuntu and create on the new one. 

Is there any known reason as to why the USB is not being persistent when being created from Windows? Are there any other Windows USB creator programmes which have given more success?

Many thanks

---

### Post by sudodus on 2018-04-06
The solution with two USB pendrives and [mkusb](https://help.ubuntu.com/community/mkusb) is straightforward and will work.

But the other options are also possible.

- **Unetbootin** and **Linux Live** *should* work, at least if you get a current version.

- If your USB pendrive is big enough, you can get a compressed image of a linux system with a persistent live system (with mkusb installed), and you can use Windows tools to extract from the compressed image and then clone from the extracted image to the USB pendrive.

See these links,

[Compressed image file with a persistent live system](https://help.ubuntu.com/community/mkusb/persistent#Compressed_image_file_with_a_persistent_live_system)

[Win32 Disk Imager - compressed image to USB or SD](https://wiki.ubuntu.com/Win32DiskImager/compressed-image_2_USB-or-SD)

- It is even possible to use the same USB as you are booting from (if you use the boot option 'toram'), but it is tricky, and not the first choice.

---

### Post by fsa259 on 2018-04-06
Thanks for your quick reply. Since mkusb is the simplest option, I'll get hold of a new USB and do that.

I used the latest versions of UNetbootin and Linux Live with Ubuntu 17.10. Any idea why that didn't work? Is it only compatible with certain USBs or something like that?

---

### Post by sudodus on 2018-04-06
I don't know why it did not work with UNetbootin and Linux Live to make an Ubuntu 17.10 live drive with persistence. Maybe Ubuntu 17.10 is too new for those tools to work. They are extracting tools and sensitive to the internal structure of the iso file (which files there are, and where they are located (which directory structure).

Cloning tools are more robust.

Edit: mkusb clones, when it makes live-only drives, which is the standard method. It works with most linux iso files.

But when mkusb creates a persistent live drive, it cannot only clone. It is also extracting some critical components. For this reason it can only do it with Ubuntu and Debian iso files (and community flavours and re-spins, other linux distros, that are based on Ubuntu and Debian and have the same or very similar internal structure of the iso file).

---

### Post by fsa259 on 2018-04-06
I understand, thank you very much. I used mkusb to install 16.04 LTS and restarted after creating a folder which remained after restart. Although now, there are is no taskbar or default apps like Firefox. Does this mean I have to manually install it all or did I miss something on mkusb?

---

### Post by sudodus on 2018-04-06
1. How did you install mkusb? In what system, with which method?

2. How did you use mkusb (did you create a live-only or a persistent live Ubuntu system)?

3. Most people want to make a full installation of Ubuntu into an internal drive (maybe alongside another operating system, a dual boot system).

Have you done that yet? Or are you still working on USB drives, trying to make a persistent live drive with Ubuntu?

---

### Post by sudodus on 2018-04-06
It is very important that you let the computer shut down completely, before you unplug the USB pendrive with the persistent live system. Otherwise the file system will be corrupted, and many strange things can happen, but the most common thing is that the system does not start in persistent live mode, only as live-only.

In general, a persistent live system is sensitive, so it is important to take frequent backups. See this link,

[Backup and restore of persistent overlay data](https://help.ubuntu.com/community/mkusb/persistent#Backup_and_restore_of_persistent_overlay_data)

---

### Post by fsa259 on 2018-04-06
> **sudodus said:**
> 1. How did you install mkusb? In what system, with which method?
I installed mkusb on a live USB 17.10. I followed these instructions: [https://askubuntu.com/questions/772744/how-to-make-a-live-usb-persistent](https://askubuntu.com/questions/772744/how-to-make-a-live-usb-persistent)

> **sudodus said:**
> 2. How did you use mkusb (did you create a live-only or a persistent live Ubuntu system)?
As per those instructions, I used [COLOR=#111111][FONT=Consolas]sudo -H mkusb /path/to/iso/filename.iso p
[/FONT][/COLOR]
It was a persistent live Ubuntu system 16.04 LTS

> **sudodus said:**
> 3. Most people want to make a full installation of Ubuntu into an internal drive (maybe alongside another operating system, a dual boot system).
I haven't done a dual boot system as my HDD has bad sectors. What I am trying to do is have a persistent live USB so at the very least I can have the WLAN driver present. I am having to restart a fair bit and my router isn't in a convenient place to maintain a wired connection.

> **sudodus said:**
> Have you done that yet? Or are you still working on USB drives, trying to make a persistent live drive with Ubuntu?
I think I have a persistent live drive as folders I just created remained after restart. The issue now is that there is no taskbar and the pointer isn't displaying on the 16.04. I was going to use 17.10 for the persistent live but mkusb said it didn't have some configuration files for it so I decided to go for the latest LTS version.

---

### Post by fsa259 on 2018-04-06
> **sudodus said:**
> It is very important that you let the computer shut down completely, before you unplug the USB pendrive with the persistent live system. Otherwise the file system will be corrupted, and many strange things can happen, but the most common thing is that the system does not start in persistent live mode, only as live-only.

In general, a persistent live system is sensitive, so it is important to take frequent backups. See this link,

[Backup and restore of persistent overlay data]("https://help.ubuntu.com/community/mkusb/persistent#Backup_and_restore_of_persistent_overlay_data")


Thank you for the link. I will make sure I continue to shut down properly. When booting I have been selecting 'persistent live to RAM'...is this okay or should I be selecting just the 'persistent live'?

---

### Post by sudodus on 2018-04-06
```
sudo -H mkusb /path/to/iso/filename.iso p
```

is an old instruction showing how to use the old mkusb versions 9--11.

I would recommend, that you use the new mkusb version 12 alias mkusb-dus. It is well tested and works with Ubuntu 17.10.1 and also with Ubuntu Bionic Beaver to be released soon as 18.04 LTS.

See the instructions at this link, [ mkUSB quick start manual](http://phillw.net/isos/linux-tools/mkusb/mkUSB-quick-start-manual.pdf)

I tested the [beta-2 iso files](http://iso.qa.ubuntu.com/qatracker/milestones/388/builds) of Ubuntu, Lubuntu and Xubuntu yesterday (and mkusb can create persistent live systems from those **desktop** iso files (but the alternate and server iso files can only be cloned to installer drives (not live or persistent live drives)).

Xubuntu Bionic Beta-2 looks good and has a much lighter desktop environment compared to standard Ubuntu. This is a great advantage in a persistent live drive.

Lubuntu 17.10.1 and Xubuntu 17.10.1 are both good alternatives. Lubuntu is even lighter than Xubuntu. And they all work with mkusb.

---

### Post by sudodus on 2018-04-06
> **fsa259 said:**
> Thank you for the link. I will make sure I continue to shut down properly. When booting I have been selecting 'persistent live to RAM'...is this okay or should I be selecting just the 'persistent live'?

*I usually select just the 'persistent live'.* But if you have more than 4 GB RAM, 'persistent live to RAM' can be a good idea (with standard Ubuntu).

Anyway, something is wrong, when you lost the taskbar and there is no pointer.

I think the pointer problem is a separate problem with the graphics driver. Try to switch to a text screen and then back to the graphical screen with the hotkey combinations

***ctrl + alt + F1*** - to text screen

***ctrl + alt + F7*** - back to graphical screen

In some systems this will bring back the pointer.

---

### Post by fsa259 on 2018-04-06
Thanks very much for your advice. I have successfully created a live xubuntu bionic beta. I've restarted and test files remain.

I'm not sure what caused the pointer etc to disappear, but now I'm using a lighter version, so it should be okay. 

I have 6Gb of RAM, so I'll have a play with both from RAM and not from RAM and see how I fare.

Slight issue with wlan remains as I have a Broadcom. It installed and worked fine, upon restart the Additional Drivers page shows the Broadcom and under connections my wifi is there, however there's no option to connect to it.

I can't attribute this to not being persistent as files came back. I'll purge and reinstall the Broadcom package and see what happens.

---

### Post by sudodus on 2018-04-07
I think there is a problem if you need proprietary kernel drivers in live and persistent live systems. The kernel and these drivers are activated before the overlay structure. And if I understand correctly, the wifi drivers are that kind of drivers.

So if you need but cannot access the network via wifi, I suggest that you **install** Xubuntu (or Lubuntu) into

- a really fast USB 3 pendrive, or an SSD in a USB box, if you have that possibility, or

- the faster and bigger of your current USB pendrives (should work, if it is at least 8 GB, better if at least 16 GB).

**I mean install Xubuntu (or Lubuntu) like into an internal drive, but into a USB drive.** This works best, if you disconnect/unplug your internal drive(s) before starting the installation.

See the following links and links from them,

[Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

---

### Post by fsa259 on 2018-04-07
> **sudodus said:**
> I think there is a problem if you need proprietary kernel drivers in live and persistent live systems. The kernel and these drivers are activated before the overlay structure. And if I understand correctly, the wifi drivers are that kind of drivers.

So if you need but cannot access the network via wifi, I suggest that you **install** Xubuntu (or Lubuntu) into

- a really fast USB 3 pendrive, or an SSD in a USB box, if you have that possibility, or

- the faster and bigger of your current USB pendrives (should work, if it is at least 8 GB, better if at least 16 GB).

**I mean install Xubuntu (or Lubuntu) like into an internal drive, but into a USB drive.** This works best, if you disconnect/unplug your internal drive(s) before starting the installation.

See the following links and links from them,

[Installation/FromUSBStick#Prerequisites]("https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites")

[Boot Ubuntu from external drive]("https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312")

Thank you so much for the advice, I didn't realise it was possible to install into a USB drive With all the information I came across about live and persistent live, I thought they were the only options. If this works it means I can still use my laptop for basic work and wait till next month's to buy a replacement HDD. Many thanks.

---

### Post by sudodus on 2018-04-08
You are welcome :-)

When you have a working system in a USB drive, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by fsa259 on 2018-04-08
It worked like a charm. Thank you for your time!

---

