---
title: "HOWTO: Setting up Hauppauge WinTV-PVR-USB2 on Ubuntu 6.10 (Edgy Eft)"
date: 2007-01-07
forum: Outdated Tutorials &amp; Tips
---

### Post by thing on 2007-01-07
*EDIT: With Ubuntu 7.04 it works out-of-the-box !!*

Here is a simple guide for those of you who wants to use your Hauppauge WinTV-PVR-USB2 (an external MPEG2 tuner) on Ubuntu 6.10 (Edgy Eft). This will allow you to use e.g. MythTV.

Hauppauge WinTV-PVR-USB2 needs a driver and the driver needs a copy of the firmware to communicate correctly with the device. Mike Isely is the masterful maintainer of the driver. Read more about PVRUSB2 at [http://www.isely.net/pvrusb2/pvrusb2.html](http://www.isely.net/pvrusb2/pvrusb2.html) . You can get the necessary firmware from [http://ivtvdriver.org](http://ivtvdriver.org) .

This guide involves three steps:
1) Config and build upgraded kernel in Ubuntu to enable the PVRUSB2 driver
2) Downloading and extracting firmware 
3) Verify the setup

**Config and build upgraded kernel in Ubuntu to enable the PVRUSB2 driver**
The PVRUSB2 driver for Hauppauge WinTV-PVR-USB2 is available directly in the kernel since 2.6.18. To build an upgraded kernel you should use this guide [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) . However, when you reach step 6 (config the kernel) you must enable the PVRUSB2 driver by answering M or Y to the following options:
CONFIG_VIDEO_PVRUSB2=m
CONFIG_VIDEO_PVRUSB2_24XXX=y
CONFIG_VIDEO_PVRUSB2_SYSFS=y
CONFIG_VIDEO_PVRUSB2_DEBUGIFC=y

Finish the guide.

**Downloading and extracting firmware**
After building and rebooting with the upgraded kernel you must download and extract firmware. Use the following steps:
```
sudo -s -H
mkdir /lib/firmware/`uname -r`
cd /lib/firmware/`uname -r`/
wget http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz
tar zxvf firmware.tar.gz

```

**Verify the setup**
Before installing MythTV you should verify that PVRUSB2 and the firmware communicates with your hardware. 
You can use mplayer. If you do not have mplayer installed use:
```
sudo apt-get install mplayer
```

Then you should get input (snow or picture) with this command:
```
mplayer /dev/video0
```

Your hardware should now work so you can proceed with installing e.g. MythTV.

Good luck. The hyperlinks include further information if you need to debug.

---

### Post by erflol on 2007-01-13
I've managed to get the WinTV-PVR-USB2 working with ubuntu and mplayer however after an install of mythtv, I can't get any audio when I try to watch live TV. Audio still works through mplayer, but won't work through Mythtv.

Did you have to do anything special to get your tuner to work with myth?

Cheers
eRflol

---

### Post by Helmi on 2007-01-16
i got the usb2 running with a hand baken 2.6.19.2 kernel (drivers are included). unfortunately there's no VBI support with this driver and so noch channel scan is possible.

any ideas about that?

---

### Post by dvarsam on 2007-01-20
Hello!

[QUOTE=thing]Here is a simple guide for those of you who wants to use your Hauppauge WinTV-PVR-USB2 (an external MPEG2 tuner) on Ubuntu 6.10 (Edgy Eft). This will allow you to use e.g. MythTV.[/quote]

Can you please add a snapshot of your product "**Hauppauge WinTV-PVR-USB2**" on your original "HowTo" post?

It is always better to add a picture of the product you are talking about...

Thanks.

P.S.1> If you don't know how to do this:

1. visit the site: [www.photobucket.com](www.photobucket.com)

2. Create an account inside that site.

3. Upload your product's picture in that site.
Note: If you don't have a picture of your product, you can search for one in the internet.

4. Under the list of all your uploaded pictures:

   a. Click on the right of the box named "IMG Code" & the text named "[I M G]http://i69.photobucket.com/albums/i58/**your_account_name**/**your_picture's_name**.png[/I M G]" will be selected.

   b. Perform a copy (on the selected text) & paste it inside your original post.

P.S.2> I also added your product on the Ubuntu wiki Hardware Page:

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaHauppauge#preview](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaHauppauge#preview)

IF you happen to know the details missing (on some of those cells) please edit that Page & add the necessary info.
In the future, if you happen to own other Hardware & have added a post inside the "Faqs, Howto, Tips & Tricks" section of Ubuntu Forums, on how to make it work, please don't forget to add it also in the wiki.

---

### Post by cborga1985 on 2007-06-07
Has anybody had any luck getting this to work with the 29xxx series? I built the kernel answering "Y" to the options stated above. Afterwards, I extracted the firmware using your instructions but even after a restart. It doesn't work for me. I built kernel version 2.6.18-8.



Edit: I got it working by building kernel version 2.6.19.7 chosing all the options you said above except one. You have to say "N" to 24xxx and say "m" to 29xxx option instead. After that I extracted the firmware using instructions from [here]("http://www.isely.net/pvrusb2/setup.html#Firmware").

---

### Post by thing on 2007-07-11
Guide now updated for Ubuntu 7.04

---

### Post by ep3w on 2007-10-11
What steps do I exactly need to do to get this to work in feisty?  Just extract the firmware?  I did this and with tvtime it says there is no signal.  Am I missing something?

---

### Post by cborga1985 on 2007-10-24
> **ep3w said:**
> What steps do I exactly need to do to get this to work in feisty?  Just extract the firmware?  I did this and with tvtime it says there is no signal.  Am I missing something?

TVtime does not support mpeg2. To test it do mplayer /dev/video0 in terminal. Also, Iextracted the firmware from the drivers because the firmware at ivtv did not work for me.

---

