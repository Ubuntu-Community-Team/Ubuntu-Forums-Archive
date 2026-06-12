---
title: "Rikomagic"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by evertonmint on 2012-11-24
Hi, I have just purchased a rikomagic mini pc, it has 8g memory with an expansion slot to take sd card up to 32g. It has built in goggle o/s with wifi. In the write up it mentions installing a version of ubuntu on it, the version mentioned is 8,10, What would be the best version to install via the sd card.

regards
evertonmint.

---

### Post by newb85 on 2012-11-24
Please clarify, is that 8GB your RAM, or a built-in SSD?  If it's SSD, then it's possible to install Ubuntu on that without even needing the SD card for your OS.  (Ubuntu takes ~5GB, if memory serves, so that won't leave a lot of room for your documents, music, etc.  That's where the expansion card comes in.)

The fact that 8.10 was recommended concerns me a little.  8.10 was released October 2008, and was only supported until April 2010.  Older releases require fewer resources, but running unsupported releases poses security risks and can cause usability issues as well.

I'm afraid I know nothing about your specific PC.  I would assume there's no optical drive (CD or DVD).  Do you have any USB ports?  If you do, you'll want to create a Live USB and test out a newer release of Ubuntu.  (Instructions [here]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows"), assuming you have access to a Windows machine.)  10.04 is the oldest release still supported, and it expires April 2013.  If you're planning to use your machine longer than that, I suggest you go with the next long-term support release, 12.04, supported until April 2017.

You will probably have to use a much lighter variant like Lubuntu or the unofficial PeppermintOS.  Tests using a Live USB will tell a lot.

---

### Post by raja.genupula on 2012-11-24
look at here 
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by evertonmint on 2012-11-25
[http://www.laptopmag.com/review/minipc/android-4.0-mini-pc-mk802-ii.aspx](http://www.laptopmag.com/review/minipc/android-4.0-mini-pc-mk802-ii.aspx)

Thanks newb85,above is the website for info on the said pc, halfway down the page there is an editors review. I have the next model up the MK802 III. Could I just overwrite the o/s with lubuntu 12? or would I need to put it on a card first? I am familiar with the ubuntu 12 I have it at the office, and was really just looking for a familiar o/s to use, rather than the one that is pre-installed.

Thanks for the links raja.genupula

regards
evertonmint

---

### Post by newb85 on 2012-11-25
I believe your specs fall towards the low end of the official system requirements for regular Ubuntu.  So my guess is, you can install Ubuntu, but it will feel slow.

Again, I would use Live media to give Lubuntu a test-drive.  Running from Live media isn't really a good speed indicator (it will be slower than once you install), but it will give you an idea of whether you would be satisfied with the LXDE interface (as opposed to the Unity interface in Ubuntu).  If you find LXDE easy to work with, Lubuntu will be a better experience on that machine.

If you want to overwrite your Android system, you should be able to install (L)Ubuntu on the internal SSD.  (I have several releases of Ubuntu running on Virtual Machines with their HDDs limited to 8GB.)  The system will fit, and you should be able to add the applications you want (provided you don't go hog-wild), but if you're going to be saving many media files, you'll probably need an SD card in that expansion slot for those files.

---

### Post by evertonmint on 2012-11-26
Thanks newb85,  Yes the spec is 1gb of ram and 8gb of ddr3 memory, does the (L)ubuntu have the wifi installed or would I have to access that also?

Regards

evertonmint

---

### Post by newb85 on 2012-11-26
All the under-the-hood stuff for handling wireless networking will be the same for Lubuntu as for Ubuntu.  The little applet you use to control it will look a little different, but I think you'll find that if you can use one, using the other is a breeze.  (My memory is a little fuzzy right now as to how different they really are.)

---

### Post by squakie on 2012-11-26
I would be more concerned about the make of processor - allwinner a10.  I doubt there's an ubuntu/lubuntu/xubuntu image for that processor.

As an example, a search of the net found several links, but they refer to either building your own OS or using 3rd party OS pre-builts.  I would be a little concerned on the knowledge level that might be needed.

One such thread:  [http://www.cnx-software.com/2012/06/13/hardware-packs-for-allwinner-a10-devices-and-easier-method-to-create-a-bootable-ubuntu-12-04-sd-card/](http://www.cnx-software.com/2012/06/13/hardware-packs-for-allwinner-a10-devices-and-easier-method-to-create-a-bootable-ubuntu-12-04-sd-card/)

---

### Post by evertonmint on 2012-11-27
@squakie
Here are the complete specs;
Model	MK 802 III

CPU	RK 3066 Duel Core

RAM	1G DDR3

Memory	8GB

GPU	Quad-core 2D/3D 
	Open GL ES2.0 (AMD Z430)/  Open VG 1.1

OS	Android 4.1

Main Freq	Cortex-A9 Up to 1.6Ghz

Expand Micro SD	T-Flash (Max 32GB)

WiFi	802.11 b/g/n

Flash	supports 11.1
Ports	HDMI(male) Micro SD slot, 
	USB host, USB power port;Led (Blue)

Accessory	HDMI cable, USB power cable, manual,
	USB power adapter (optional)
Unit Size	90mm(L) 40mm (W) 13mm (T)


All I really want to know is if I put Lubuntu 12.04 on will I lose the wifi? Also, how easy would it be to install Lubuntu?

Thanks
evertonmint

---

### Post by newb85 on 2012-11-27
Not to sound like a broken record, but a Live USB will tell you whether the wifi will work out-of-the-box.  Select the "Try Ubuntu" option, and then see if the wireless works.  If it doesn't run the following from the terminal and post the output.

```
sudo lshw -**C** network
```

Edit: I had a capitalization issue in that last command.  Sorry.

---

### Post by audiomick on 2012-11-27
> **newb85 said:**
> 
Edit: I had a capitalization issue in that last command.  Sorry.

if you mean the modifier, that command works with a -c the same as with -C or -class.
The man page doesn't mention a lower case c, and I don't know how I found out that it works, but it seems to work consistently.
```
       -class class
              Only show the given class of hardware. class can be found using lshw -short or lshw -businfo.

       -C class
              Alias for -class class.

```

---

