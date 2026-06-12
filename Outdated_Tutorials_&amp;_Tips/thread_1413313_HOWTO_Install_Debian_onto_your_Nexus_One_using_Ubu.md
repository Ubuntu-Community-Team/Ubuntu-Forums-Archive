---
title: "HOWTO: Install Debian onto your Nexus One using Ubuntu"
date: 2010-02-22
forum: Outdated Tutorials &amp; Tips
---

### Post by hobo14 on 2010-02-22
**_[SIZE="3"]1) Introduction[/SIZE]_**

Here's a longish guide to unlock, root and run Debian on your Nexus One.
 
It's based on various guides and forum posts around (see embedded links), but with more details, with some missing pieces and corrected mistakes, all compiled into a (hopefully) newb-friendly step by step guide.

Note **[COLOR="Red"]THIS WILL WIPE THE SETTINGS AND APPS FROM YOUR PHONE[/COLOR]**, so backup first (I suggest Astro for your apps).  
This will not affect Android at all; it will be as it was the first time you turned the phone on.

You will need between 1.5 and 2 GB of free space on your SD card.

I did this after I had applied the first Android patch (Feb 2010), and the patch seemed unaffected (ie. I still had multitouch afterwards)


**_[SIZE="3"]2) Connect the phone to computer[/SIZE]_**

 - Install the [Android SDK]("http://developer.android.com/sdk/download.html?v=android-sdk_r04-linux_86.tgz") on your computer.

$ **sudo gedit /etc/udev/rules.d/51-android.rules**

 - Save these two lines into the file:
```
SUBSYSTEM=="usb", SYSFS{idVendor}=="18d1", MODE="0666"
SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666"
```

$ **sudo chmod a+rx /etc/udev/rules.d/51-android.rules**

$ **sudo service udev restart**

Now, for example, if you plug in the phone and run 
$ sh android-sdk-linux_86/tools/ddms
you will see the phone listed. (Note: this is not a step in the howto) 


**_[SIZE="3"]3) Unlock the bootloader[/SIZE]_**

- Turn the phone off.

- Hold the trackball down, and turn it back on. The phone will boot into the white bootloader screen with Androids on skateboards.

- Plug the phone into the computer

 - The title of the menu on the phone will be FASTBOOT USB. 

 - Download [fastboot.zip from the link in the OP here]("http://android.modaco.com/content/google-nexus-one-nexusone-modaco-com/299078/how-to-unlock-the-bootloader-on-your-nexus-one/") and open a terminal window wherever you extract it's contents to
 
 $ **sh ./fastboot-linux oem unlock**

- If you see "< Waiting for device >" you may need to use the power button to select BOOTLOADER and FASTBOOT to switch back and forth between the two menus a couple of times, until the phone connects to the computer.

- The phone will now ask if you want to unlock the bootloader, select yes.

The bootloader is now unlocked, the bootloader screen will have a pink UNLOCKED at the top, and an open lock is displayed in the phone startup graphics.


**_[SIZE="3"]4) Root the phone[/SIZE]_**

 - Check Build Number in Settings > About Phone.  Mine was ERE27

 - Go [here]("http://android.modaco.com/content/google-nexus-one-nexusone-modaco-com/298782/12-feb-erd79-ere27-ere36b-superboot-rooting-the-nexus-one/") to get the appropriate Superboot image.  I used the himem version of ERE27, to make full use of my RAM.

 - Turn the phone off, and back on with the trackball held down to get into the bootloader screen

 - Plug the phone into the computer

 - Unzip the Superboot archive file, and open a terminal window there

 $ **sh ./install-superboot-linux.sh**

 - Go to Settings > Applications > Development > allow USB debugging on the phone. 

Now if you enter "su" into a terminal app on the phone such as Android Terminal Emulator (don't use Terminal Emulator - no virtual keybd) you will be root. You also have the Superuser Permission icon available in the phone applications


**_[SIZE="3"]4) Install Busybox [/SIZE]_**

 - Get busybox from [their website]("http://busybox.net/downloads/") (build from the src if you like, but I just downloaded the 1.16.0 binary for ARMv6l) 

 - Plug in phone (turned on and running, not in fastboot)

 - Rename the busybox-armv6l file to "busybox" and put it in android-sdk-linux_86/tools. Open a terminal window there

 $ **sh ./adb shell**

 # **su**

 # **mount -o rw,remount -t yaffs2 /dev/block/mtdblock3 /system**

 # **exit** (repeat if necessary, until out of adb shell)

 $ **sh ./adb push busybox /data/local**

 $ **sh ./adb shell**
 
 # **su**
 
 # **chmod 755 /data/local/busybox**
 
 # **/data/local/busybox mkdir /system/xbin**

 #** cd /data/local**

 # **./busybox cp /data/local/busybox /system/xbin**

 # **cd /system/xbin**

 #** chmod 755 busybox**

 # **./busybox --install -s /system/xbin**

 # **rm /data/local/busybox**

 # **reboot**

The phone will reboot, busybox is installed.


**_[SIZE="3"]5) Install Debian[/SIZE]_** [SIZE="1"]
(Based on [this guide]("http://forum.xda-developers.com/showthread.php?t=529233"), and using the image from it.)[/SIZE]

 - Download [the Debian installer files]("http://www.darkmystics.com/g1/Debian%20Installer/debian.tar.bz2")
(Should download fine, but if not then check this thread for links: [http://forum.xda-developers.com/showthread.php?t=529233](http://forum.xda-developers.com/showthread.php?t=529233))

 - Extract all the files

 - Copy bootdeb, debian.img, debian.sh, mountonly, fsrw, uninonfs to /sdcard/debian/ on the phone (make the directory if needed)

 - Copy vnc.apk and swapper.apk to android-sdk-linux_86/tools/

 - Plug the phone in

 - Open a terminal window in android-sdk-linux_86/tools/

 $ **adb remount**

 $ **adb install vnc.apk**

 $ **adb install swapper.apk**

 $ **adb shell**

 # **cd /sdcard/debian**

 # **su**

 # **sh ./debian.sh**

 # **exit** (repeat until out of adb)

 - Fix a line in bootdeb. Replace this line:
```
mount -o loop,noatime $kit/debian.img $mnt
```
with this:
```
mount -o loop,noatime -t ext2 $kit/debian.img $mnt
```

 - On the phone Run swapper. Set swap to 96 MB. Set swappiness to 60. Press "Swap ON"

 - Install "Android Terminal Emulator" (not "Terminal Emulator") on the phone through the market

 - Open terminal emulator on the phone

 [COLOR="Navy"]# **su**[/COLOR]
 
 [COLOR="Navy"]# **sh /sdcard/debian/bootdeb**[/COLOR]

 - Press the home button

 - open androidVNC
 [I]Nickname = anything
 Password = android
 Address = LocalHost
 Port = 5901
 Colors = up to you[/I]

 - Press connect

That's it, you now have Debian running on your N1.
To exit cleanly press and hold the home button, go to the terminal, enter "exit".
Every time you want to start Debian, do swapper, terminal, androidVNC, as above.
AndroidVNC isn't necessary if you don't want a GUI.


**_[SIZE="3"]4) Conclusion[/SIZE]_**

 If you discover any ways, or any packages to install, that make Debian easier or better to use on the N1, please put them in this thread.

Note Debian here is just an image chrooted in Android.  It is not running directly on the hardware, but this [is possible]("http://forum.xda-developers.com/showthread.php?t=631389").  However, switching between Android and Debian then becomes painful, and requires a reboot, so I prefer this way.

---

### Post by djvishnu on 2010-02-25
Great howto!

The fastboot.zip link is down.

What part of this procedure is it that wipes the settings/apps?

---

### Post by hobo14 on 2010-02-25
Thanks, fixed that link.

Unlocking the bootloader wipes the phone.

---

### Post by www.rzr.online.fr on 2010-03-01
is this what you're looking for ?
[http://www.romraid.com/paul/fastboot.zip](http://www.romraid.com/paul/fastboot.zip)

Btw I will insert the procedure to backup the flash using nandroid ...

---

### Post by hobo14 on 2010-03-02
> **www.rzr.online.fr said:**
> is this what you're looking for ?
[http://www.romraid.com/paul/fastboot.zip](http://www.romraid.com/paul/fastboot.zip)

Btw I will insert the procedure to backup the flash using nandroid ...

Rzr that is the link I originally posted. It doesn't work (test it).
I have already fixed the link in the OP.

---

### Post by www.rzr.online.fr on 2010-03-05
that link used to work when i tested .. weird

that one has the same checksum :
[http://www.bernie.net.my/files/fastboot.zip](http://www.bernie.net.my/files/fastboot.zip)

btw for the backup i wonder if it requieres to be rooted 1st

that page said not :
[http://www.ehow.com/how_5853749_tether-nexus-one-wirelessly.html](http://www.ehow.com/how_5853749_tether-nexus-one-wirelessly.html)

but how to on n1 ?
[http://forum.xda-developers.com/showthread.php?p=5799946#post5799946](http://forum.xda-developers.com/showthread.php?p=5799946#post5799946)

regards

---

### Post by charansingh on 2010-03-05
Please give credit where it is due, thanks

---

### Post by Murphy2712 on 2010-03-06
> **www.rzr.online.fr said:**
> 
btw for the backup i wonder if it requieres to be rooted 1st

that page said not :
[http://www.ehow.com/how_5853749_tether-nexus-one-wirelessly.html](http://www.ehow.com/how_5853749_tether-nexus-one-wirelessly.html)


Ehow's howto is definitely wrong.
Nandroid is only provided with custom recoverys.
And custom recovery is only installable if you are root.

---

### Post by hobo14 on 2010-03-07
> **charansingh said:**
> Please give credit where it is due, thanks

I did write that this howto is based on guides by others, and I do already  provide a link directly to your guide Charansingh, but I will edit the post to be more explicit.

---

### Post by cyberjar09 on 2010-03-24
Hi, im a complete noob so please help me out.

I am getting the following error in terminal when i want to install the amon_ra recovery image

user@user-desktop:~/Desktop/android-sdk-linux_86/tools$ fastboot flash recovery recovery-RA-nexus-v1.7.0-cyan.img 
fastboot: command not found

My computer no longer recognizes fastboot as a command. It says fastboot: not found. What now? I'm trying to flash Amon_RA's recovery image.

My computer only recognizes the N1 as a device if it's fully booted up and the sd card is mounted. Otherwise, my computer doesn't see it.

What can i do?

OS: Ubuntu 9.10

---

### Post by diet sprite on 2010-04-09
I have been trying to get this to work for atleast 6 hours now and i still cannot figure it out, i have installed the sdk (i think) and when i try to get ubuntu to reconize my phone it says it cannot open android-sdk-linux_86/tools/ddms. Any help would be great. Thanks

---

### Post by diet sprite on 2010-04-09
Anyone?

---

### Post by austin8868 on 2010-04-11
Hello, i am trying to boot this on my n1 as you all probably but im having one small problem, when i put cd /sdcard/debian into the terminal it tells me 
cd: can't cd to /sdcard/debian anyone know how to fix this? Thanks

---

### Post by nicandris on 2010-06-22
emmmm ok... try ./fastboot

---

### Post by plusnplus on 2010-07-13
Hi..,

is this tutorial also can be use in other android phone?
my phone is samsung i5700, with android 2.1(samdroid.net)

thanks for any info/ reply

---

### Post by andyzammy on 2011-01-14
trying this out but N1 keeps rebooting on me after i run bootdeb.

i'm actually using Swapper2 because swapper is meant for android 1.5 and below.. i think this is the problem though because looking at the feedback Swapper2 is giving me the swapon function isn't implemented..

---

### Post by gk007 on 2011-05-17
Whenever I run bootdeb it starts up then says /bin/bash cannot be found, shuts down and rebooted the phone.  I too am using swapper2, which doesn't work properly, but neither does swapper.

---

