---
title: "Samsung Galaxy S3 USB error: Unable to mount SAMSUNG_Android_SGH-T999"
date: 2013-12-21
forum: New to Ubuntu
---

### Post by Jim_Granite on 2013-12-21
When I unlock and then plug in my Samsung Galaxy S3, Android 4.3, phone  by USB cable (MTP mode) into my 64-bit Ubuntu 13.10 laptop USB port, I get a  zillion error boxes of the form:[IMG]http://oi43.tinypic.com/2mm8ggm.jpg[/IMG]
> 
Unable to mount SAMSUNG_Android_SGH-T999
Unable to open MTP device '[usb:003,001]' (where 001 increments forever)
 ... a hundred of those ... and then ... 
Unable to mount 04e8 68
Couldn't find matching udev device.


What is going on? Why can't the most common phone on the planet connect to the most common Linux system on the planet?
(It has no problems connecting to Windows 7.)
```

$dmesg
... ... ... ... reports ... ... ... ... ... 
[59996.395475] usb 3-1: Manufacturer: SAMSUNG
[59996.446549] usb 3-1: USB disconnect, device number 69
[59998.492841] usb 3-1: new high-speed USB device number 76 using xhci_hcd
[59998.492975] usb 3-1: Device not responding to set address.
[59998.697238] usb 3-1: Device not responding to set address.
[59998.901195] usb 3-1: device not accepting address 76, error -71
[59999.197377] usb 3-1: new high-speed USB device number 78 using xhci_hcd
[59999.219128] usb 3-1: New USB device found, idVendor=04e8, idProduct=6860
[59999.219136] usb 3-1: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[59999.219141] usb 3-1: Product: SAMSUNG_Android_SGH-T999
[59999.219146] usb 3-1: Manufacturer: SAMSUNG
[59999.325673] usb 3-1: USB disconnect, device number 78
[60001.342539] usb 3-1: new high-speed USB device number 85 using xhci_hcd
[60001.342752] usb 3-1: Device not responding to set address.
[60001.546846] usb 3-1: Device not responding to set address.
[60001.750749] usb 3-1: device not accepting address 85, error -71
[60003.111507] usb 3-1: new high-speed USB device number 90 using xhci_hcd
[60003.111723] usb 3-1: Device not responding to set address.
[60003.315762] usb 3-1: Device not responding to set address.
[60003.519694] usb 3-1: device not accepting address 90, error -71
[60010.363461] usb 3-1: new high-speed USB device number 114 using xhci_hcd
[60010.363694] usb 3-1: Device not responding to set address.
[60010.567774] usb 3-1: Device not responding to set address.
[60010.771593] usb 3-1: device not accepting address 114, error -71
[60013.945323] usb 3-1: new high-speed USB device number 125 using xhci_hcd
[60013.945556] usb 3-1: Device not responding to set address.
[60014.149754] usb 3-1: Device not responding to set address.
[60014.353569] usb 3-1: device not accepting address 125, error -71

```

```

$ lsusb | grep Samsung
Bus 002 Device 039: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II], GT-I9300 Phone [Galaxy S III], GT-P7500 [Galaxy Tab 10.1]

```

```

$ sudo apt-get install mtp-tools
$ mtp-detect
Unable to open ~/.mtpz-data for reading, MTPZ disabled.libmtp version: 1.1.6
Listing raw device(s)
Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
   Found 1 device(s):
   Samsung: Galaxy models (MTP) (04e8:6860) @ bus 2, dev 40
Attempting to connect device(s)
ignoring libusb_claim_interface() = -6PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device

```

---

### Post by Keith_Beef on 2013-12-21
I have a [long(ish) thread]("http://ubuntuforums.org/showthread.php?t=2191520") about getting this same error when I plug in a Thrustmaster HOTAS X, and replied to other threads [here]("http://ubuntuforums.org/showthread.php?t=2158365") and [here]("http://ubuntuforums.org/showthread.php?t=2191417") about the same problem..

The errors are supposedly because the device is drawing too much current, though I really doubt that this is truly the case.

---

### Post by Jim_Granite on 2013-12-21
> **Keith_Beef said:**
> The errors are supposedly because the device is drawing too much current, though I really doubt that this is truly the case.

Hmmm... anything is possible - but excessive current draw would be an unexpected cause, especially since it happens even when the battery is at 99%.
The original phone charger puts out something like 800ma, I think, so, I will try to dig up a 1A or 2A powered USB hub, to see if that makes any difference.
In addition, I'll read your referenced threads ... and report back. Thanks.

---

### Post by Jim_Granite on 2013-12-24
I haven't been able to do anything about this, but, I also hadn't been able to connect for days.
Then, all of a sudden, I try it today, and guess what?
it connects.
Don't ask me how or why ... 'cuz I don't know ... 
[ATTACH=CONFIG]248867[/ATTACH]
I'll see if this lasts more than a couple of days, and then mark the thing resolved, if it stays working.

---

### Post by Jim_Granite on 2014-01-05
The weird thing is that my Lenovo W510 laptop has 4 USB ports, and, at the moment, if I put the phone into three of them, I get that problem (even though they have all worked in the past); but the 4th port consistently works.
It's as if they're "clogged" up with something (some kind of persistent memory or setting).
Anyway, since one port consistently works lately, I'll close this and reopen as needed.

But, is there some way to "clear" a USB port?

---

### Post by Mark Phelps on 2014-01-05
> Why can't the most common phone on the planet connect to the most common Linux system on the planet?
(It has no problems connecting to Windows 7.)

Simple -- drivers!  Or, more correctly, the lack of the same.

I have a Samsung Galaxy S3 and was not able to connect it either to Linux or Win7 until I installied Kies in Win7 -- which also installed new USB drivers from Samsung.  Now, it connects just fine in Win7.  Unfortunately, Samsung does NOT provide drivers for Linux (what else is new?).

---

### Post by philinux on 2014-01-05
Well, as I had my s3 handy I thought I'd give it a go. On the phone it said connected as a media device. I got one pop up error about not connecting then the nautilus window appeared with the card and phone mounted.
I then unmounted, unplugged and tried again. This time not pop up error message.
My phone is still on android 4.1.2

I can browse the external sd card and the phone no problems. I had to change mode on phone from media (mpt) to camera (ptp) to access the photos.

I wonder if it's anything to do with android version?

---

### Post by Jim_Granite on 2014-01-12
> **philinux said:**
> I wonder if it's anything to do with android version?

I have gotten inconsistent results.
I always unlock the Samsung Galaxy S3, running Android OS 4.3, first, and then connect to only of 4 USB ports on the PC.
Sometimes, all four ports work, and even with the error, I can browse the microSD card and the phone memory; other times none of the ports work; other times only one of the ports work.
It seems something gets stuck with the ports.

Is there a way to "clear" the USB ports?

---

### Post by squakie on 2014-01-13
Should be released any time you reboot.

I would consider three things - 2 of which have already been mentioned:

- too much current draw
- as Mark Phelps said - drivers
- it's also possible the usb ports may not at the correct "level".  Are they  USB 1, 1.1, 2, 3?

USB communications is done via "endpoints".  It's possible there's an inconsistency in the S3 itself.

EDIT:  Additionally, it's possible a udev rule may be getting in the way and needs updating or creating.  I would first try a google search with the following as the search string:

linux unable to mount samsung_android_sgh-t999

and see if something turns up/

---

### Post by squakie on 2014-01-13
I just did that search myself and there is a lot of reading to be done.  Some are what I would think are too old - 2011 on back.  I did find some from 2013, most dealing with wanting to move multiple pictures from the S3 to a linux box (in their case, a Centos laptop). 

I noticed you said using MTP.  One of those threads suggests that PTP is the way you have to go, not MTP.  Here's  part of that thread:


> Re: [RESOLVED] How does one transfer files from Android Samsung Galaxy S3 to Centos 6?

Postby Rocksockdoc » 2013/05/31 17:02:24
Success at last!

This bug report was the key for understanding *how* to transfer photos by USB wire from the Samsung Galaxy S3 to Linux!
[https://bugzilla.gnome.org/show_bug.cgi?id=671906](https://bugzilla.gnome.org/show_bug.cgi?id=671906)

Googling "How to put samsung galaxy s3 in ptp mode", I find:
[http://www.samsunggalaxys3forum.com/for](http://www.samsunggalaxys3forum.com/for) ... -mode.html

Which says:
1. Connect the phone (in that case, to the Mac)
2. Pull down the notification bar (in that case, on the Samsung phone)
3. Tap on the connection (in that case, the same USB connection)
4. Select PTP mode (to transfer photos)

When I tried that on Linux (Centos 6 in my case):
1. Connect the phone by USB cable (you have to ignore this, which pops up 1st):
2. Pull down the notification bar (which says it's "Connected as a media device"):
3. Tap on the "Ongoing" connection:
4. Switch from "MTP mode" to "PTP mode":
5. The Samsung Galaxy S3 is now in "Connected as a camera" mode:

Hmmm... this, again, pops up, on the Desktop (just ignore this warning):

But, wait! This then shows up on the Desktop a few seconds later:

And, for the first time, the folders are no longer zero size:

Pensively, I click on the DCIM folder, holding my breath:

And, transfer my photos at will from the Android phone to the Linux laptop!

Voila! Success at last!
It's so simple, once you already know the answer!

PS: I'm not sure if there is a graceful way to disconnect; and, I'm not sure if I should leave the phone in PTP mode; but, the good news is that single and multiple photo transfer by USB wire now works, in PTP mode, on the Samsung Galaxy S3!

Please note I had to edit out links to screen shots in that quote as the editor was kicking out messages and refusing to save.

---

### Post by josh-9 on 2014-02-05
On my HP Envy one of the USB ports is a USB 3.0 "Charging Port."  I believe that is where I encountered the issue (faint burning smell is why I'm not anxious to verify).  In another USB 3.0 port everything worked fine.  Not sure what drivers or configuration are needed to use the charging port, but the "too much current draw" warning is very possibly legit.

---

### Post by SeijiSensei on 2014-02-05
Support for the MTP protocol was poor in Ubuntu versions prior to 13.04.  This wasn't a problem until Android version 4 dumped the traditional "USB mass-storage" protocol and replaced it with MTP.  If you are using a version of Ubuntu older than 13.04, you either need to upgrade or use a [wireless]("https://play.google.com/store/apps/details?id=com.smarterdroid.wififiletransferpro") [method]("https://play.google.com/store/apps/details?id=com.acrosync.android.plus") for file transfers.

---

### Post by ixtok on 2014-02-05
Out of curiosity I gave my Samsung Galaxy S3 running Android version 4.3 a try. On the phone I enabled USB debugging in Developer options. My computer is a HP Mini with three USB ports. Initially I had no results but after changing the USB cable to a different port I achieved a connection the phone connecting as a media device (MTP). It quickly gave me an error message "unable to mount android divice" but then went into file browser showing device and memory card. Switching phone to camera (ptp) did the same thing, error message then file browser. I only tried all this once and whether it will work the same way in the same in the future is a guess.

---

### Post by Keith_Beef on 2014-02-07
> **Mark Phelps said:**
> Unfortunately, Samsung does NOT provide drivers for Linux (what else is new?).

Crazy… I have a Samsung TV set. Guess what is at the heart of it: Linux and BusyBox.

Samsung has Linux people in-house working on some projects, and yet leaves other products without any kind of Linux support.

Like most big corporations, the left hand doesn't know what the right hand is doing.

---

### Post by Votlon on 2014-02-07
Woot worked on my Android!

---

### Post by SeijiSensei on 2014-02-07
I have to speak up on behalf of Samsung here.

It was Google who decided to remove support for USB mass storage from current and future Android versions.  Now they use the Media Transfer Protocol instead.  There is no need for special drivers or anything like that; you just need to use an operating system that has good support for MTP.  Before 13.04, Ubuntu was not one of those systems.  I see the problem more on the Debian/Ubuntu side.  MTP has been around [since 2008]("http://en.wikipedia.org/wiki/Media_Transfer_Protocol"), but it was not well implemented in Ubuntu Linux until recently.  Whose fault is that?

---

### Post by Vladlenin5000 on 2014-02-07
> **SeijiSensei said:**
> It was Google who decided to remove support for USB mass storage from current and future Android versions.  Now they use the Media Transfer Protocol instead.  There is no need for special drivers or anything like that; you just need to use an operating system that has good support for MTP.  Before 13.04, Ubuntu was not one of those systems.  I see the problem more on the Debian/Ubuntu side.  MTP has been around [since 2008]("http://en.wikipedia.org/wiki/Media_Transfer_Protocol"), but it was not well implemented in Ubuntu Linux until recently.  Whose fault is that?

I have to agree with you in this point.

---

### Post by RedRat on 2014-04-10
[ 						 							 						 					]("http://ubuntuforums.org/member.php?u=698195") 				 				 					 						 	[**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195")
Thanks for the reply and the info. I plan to upgrade to 14.04LTS when it is released. You have answered my question. Of course my Samsung is using a version of Android 4. Odd that I can see the folders but not the files in them, but hey the mysteries of these protocols. As I noted Windows Explorer does see everything but that means I have to use a Windows machine (yuk).

---

### Post by KillEmAllx on 2014-04-27
So anyone found a solution for this? I have the same problem, get a popup saying "unable to mount..." but I can see both the sdcard and internal storage and go through the folders and files without any problems... Sometimes it disconnects all of the sudden though... Anyone?

---

### Post by SeijiSensei on 2014-04-27
Even on Kubuntu 14.04 I've found MTP support is still buggy.  Like you, I'll get a connection for a while, then it will hang, and I'll need to disconnect and reconnect the cable to restart.  KDE implements its own methods for handling mounted media, so it's possible these problems don't extend to other flavors of Ubuntu.

---

### Post by snurfle on 2014-12-29
I've got the same issue with my Galaxy S4, already posted the question, but no answers yet.  Did anyone here ever get it resolved?

---

### Post by phord2 on 2015-03-18
> **Jim_Granite said:**
> Hmmm... anything is possible - but excessive current draw would be an unexpected cause, especially since it happens even when the battery is at 99%.
The original phone charger puts out something like 800ma, I think, so, I will try to dig up a 1A or 2A powered USB hub, to see if that makes any difference.
In addition, I'll read your referenced threads ... and report back. Thanks.

I get this same error on my new Lenovo W540 laptop running Mint 17 (Ubuntu 14.10) when it's on battery, even if the battery is fully charged.  In syslog it looks like the device begins connecting and then is removed, it begins connecting again and is removed, etc.  If I plug the charger into my laptop so I'm on AC power, the problem goes away.

I expect a powered hub would also work, but I haven't tried it.

Phil

---

### Post by sanjayak on 2015-09-20
In my case it was a failing SD card. Hope this will help to at least some of you on this forum. I had the same issue and I decided to take the SD card out and copy the data by plugin it in to the PC. Then I realised the culprit is the SD card. It some times mounts some times does not. Without this SD card the phone is mounted as MTP/PTP. Of course it's working fine with the new SD card now.

---

