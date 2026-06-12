---
title: "Will Ubuntu run on a PC with no hdd?"
date: 2012-12-14
forum: New to Ubuntu
---

### Post by rayshif on 2012-12-14
I have a Dell Inspiron 5100 notebook with 1.25GB RAM.  It worked for years, then got a "Drive 0 not found" error.  Replacing the HD did not fix it.  Finding that Ubuntu would run from a USB stick, I created one using 12.10 as instructed on Windows and changed my bios order to boot from USB.  I used a new 16GB Micro Center jump drive formated FAT32.  The notebook now boots to the Ubuntu welcome screen OK, and
everything but the HD works.  But when I click on Try Ubuntu, all I get is the desktop picture and a mouse pointer.  Will Ubuntu run from USB on a PC with no hdd?

---

### Post by TOMBSTONEV2 on 2012-12-14
I used to have an ubuntu on an 8 gb flash drive. My laptop supports booting from usb. I see no reason as to why it wouldn't run from a usb stick/drive.

---

### Post by pqwoerituytrueiwoq on 2012-12-14
sounds like compiz is not working for you, try a differnet DE like xubuntu/kubuntu/lubuntu, you may prefer linux mint

---

### Post by deadflowr on 2012-12-14
> Will Ubuntu run from USB on a PC with no hdd?

Simple answer: Yes.

Here's a way how:

[https://help.ubuntu.com/community/LiveCD/Persistence]("https://help.ubuntu.com/community/LiveCD/Persistence")


I run LiveCDs on systems where I unplug the hard drives all the time, never didn't work.
Mind you CD and USB are different the basic concept is the same.

---

### Post by rayshif on 2012-12-14
Thanks to all 3 of you who answered my question.  I reinstalled Ubuntu to my USB stick, and this time I chose 12.04 instead of 12.10, and left my internet connected while running the Pendrivelinux Universal USB Installer, and added a 1GB persistent file.  I don't know which of these changes made the difference, but this time Ubuntu booted up without any problems, and everything works!  Problem resolved!

---

### Post by C.S.Cameron on 2012-12-15
> **rayshif said:**
> Thanks to all 3 of you who answered my question.  I reinstalled Ubuntu to my USB stick, and this time I chose 12.04 instead of 12.10, and left my internet connected while running the Pendrivelinux Universal USB Installer, and added a 1GB persistent file.  I don't know which of these changes made the difference, but this time Ubuntu booted up without any problems, and everything works!  Problem resolved!

1GB persistence will likely be used up quite soon.
You can have up to 4GB persistence using a casper-rw file.
If you need more persistence, you can make a ext partition named casper-rw of any size that will fit on your drive.

---

### Post by DuckHook on 2012-12-15
> **deadflowr said:**
> Simple answer: Yes...I run LiveCDs on systems where I unplug the hard drives all the time

+1

@OP

You might also consider installing a fully functioning system to a USB hard drive in the usual way. Don't have to fight with persistence issues, install whatever apps you want, etc. Obviously more fragile than an internal HD, but backups should look after that.

---

### Post by s1baker on 2012-12-15
I just installed Xdbuntu 12.04.01 on a 32 gig SD that will boot off of a card reader.
I followed C.S.Cameron's intructions on this 
link ( post #3 ):

  [http://ubuntuforums.org/showthread.php?t=2092077&highlight=flash]("http://ubuntuforums.org/showthread.php?t=2092077&highlight=flash")

This works whether or not you have a HD with
windows on it.

Works excellent.

---

### Post by rayshif on 2012-12-15
I guess I don't know what persistence is. Is it used for programs and data? I have 14GB free on my USB stick. Should I use it all? How can I increase it? Do I need to reinstall Ubuntu to the stick?

---

### Post by C.S.Cameron on 2012-12-15
Persistence is space used to save installed programs and settings.
You can have two types of persistent files or partitions:

Casper-rw which saves everything, (that doesn't load at boot, such as video drivers).

Home-rw can be used along side casper-rw, it is similar to a separate home folder, or partition. it will save your settings and downloads.

Most people just use casper-rw.

Once a persistence file is filled up the drive will no longer boot, at least until some files are removed.

It is important not to do an update using update manager when using a persistent install.

I have been often accused for making things seem over complex.

---

### Post by asifnaz on 2012-12-15
Yes you can run live CD or install it on a USB

---

### Post by Mark Phelps on 2012-12-15
> **rayshif said:**
> ... I don't know which of these changes made the difference, but this time Ubuntu booted up without any problems, and everything works!  Problem resolved!

Given that you've used this PC for years, it's possible that the video chipset does not work with 12.10 but does work with 12.04.  That's because 12.10 uses a new version of the X-server that is incompatible with many of the older video chipset drivers.

---

### Post by DuckHook on 2012-12-15
> **C.S.Cameron said:**
> I have been often accused for making things seem over complex.

You too?! 

> **rayshif said:**
> I guess I don't know what persistence is.

In the interest of keeping explanations simple, I will try to keep it non-technical.

After Ubuntu implemented their LiveCD, someone came up with the idea to do the same thing to a USB stick. By simply writing the disk image that is used for the LiveCD onto a USB stick, you get the same functionality as a LiveCD. But the LiveCD image is designed for a medium that is read only. So, the programs and OS on the LiveCD image have been modified to never write to the disk. You can still download apps and data while running from a LiveCD, but such data resides only in RAM and are lost at shutdown (ergo: not persistent). However, a USB stick is not only writable, but has way more capacity than a CD. It was only natural for some smart geeky sort to modify the LiveCD install so that the OS image is written to one USB partition (which remains read only), but to create and use another USB partition for programs and data. Consequently, data is now no longer just in RAM, but instead is written to your USB stick (ergo: it is persistent).

Charitably, it's sort of a hybrid between a full install and a LiveCD. The OS portion of the stick isn't permitted to change, but another section has been created that can be changed. Less charitably, this could be considered a kludge. And some of us don't like kludges when a cleaner and more elegant solution can be used.

> Do I need to reinstall Ubuntu to the stick?This depends on what you want to do. If your current setup is working well and not giving you problems, then, in the interest of keeping things simple, I would suggest that you not monkey with it and leave things be. However, if you are curious about how to make a full install (i.e. a fully functioning OS that can be modified) to a USB stick, either because you want more functionality or are just curious, then I would suggest the following:

1. Use a new USB stick. They're so cheap that it makes no sense to risk your current setup.
2. Follow @oldfred's instructions [here]("http://ubuntuforums.org/showthread.php?t=2088113").

---

### Post by C.S.Cameron on 2012-12-15
> **DuckHook said:**
> 
... But the LiveCD image is designed for a medium that is read only. So, the programs and OS on the LiveCD image have been modified to never write to the disk... 

Just a small note:

If you have an ext3 partition named casper-rw on your hard drive,
and while booting the Live CD you press f6, 
then type <space> persistent:

```
 persistent

```

You will end up with a persistent session with stuff saved to the casper-rw partition on the hard drive.

---

### Post by honeybear on 2012-12-15
> **rayshif said:**
> I have a Dell Inspiron 5100 notebook with 1.25GB RAM.  It worked for years, then got a "Drive 0 not found" error.  Replacing the HD did not fix it.  Finding that Ubuntu would run from a USB stick, I created one using 12.10 as instructed on Windows and changed my bios order to boot from USB.  I used a new 16GB Micro Center jump drive formated FAT32.  The notebook now boots to the Ubuntu welcome screen OK, and
everything but the HD works.  But when I click on Try Ubuntu, all I get is the desktop picture and a mouse pointer.  Will Ubuntu run from USB on a PC with no hdd?

sure. it is regularly done on a Sheeva type PC. en.wikipedia.org/wiki/SheevaPlug

If you have a fast CPU, you can handle Ubuntu.
If not, you could rather look into : [http://www.debian.org/CD/live/](http://www.debian.org/CD/live/)

---

