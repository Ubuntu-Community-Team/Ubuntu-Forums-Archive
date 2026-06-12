---
title: "HowTo: Get Ubuntu 9.10 working great on Toshiba Sateliite T110 and similar"
date: 2010-01-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Vignesh S on 2010-01-12
I recently got the Toshiba Satellite T110, but SHOCK HORROR, Ubuntu doesn't quite like it :-O ([this thread]("http://ubuntuforums.org/showthread.php?t=1354666") outlines the problems I faced)

The issues I came across were (in order of severity)
1. Wifi, ethernet and bluetooth refusing to work
2. Screen brightness refusing to change
3. Webcam not working
4. Microphone not working

Of these, I got the first 3 working, the microphone is still a mystery, though to me it isn't all that terribly important, seeing that it isn't the best in the world, but still....

Alright, first off, wifi/ethernet/bluetooth.
[COLOR=Lime]
**HOWTO: Get wifi/ethernet/bluetooth working on Toshiba Satellite T110**[/COLOR]

Getting the RTL8192SE wifi card to work proved to be much trickier than I thought. The fix was a lot simpler than what I first thought it to be though :-P. 

My initial frustrations about the wifi was because the driver wouldn't work in the kernels provided by Ubuntu 9.10. So I went to [this site ]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")and downloaded the next kernel version: 2.6.32. This not only works for the following wifi instructions, it also has the ethernet driver working out of the box :-D. To install kernel version 2.6.32, one simply picks it up from from here [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/") and downlaod:

[linux-headers-2.6.32-020632_2.6.32-020632_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/linux-headers-2.6.32-020632_2.6.32-020632_all.deb")
_This is the linux headers, that has to be installed with the below kernel versions_

and also either this [(32-bit headers)]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/linux-headers-2.6.32-020632-generic_2.6.32-020632_i386.deb") or this (64-bit headers) depending on whether you have installed 32-bit or 64-bit Karmic Koala.

Now depending on whether you have installed 32-bit or 64-bit Ubuntu

[linux-image-2.6.32-020632-generic_2.6.32-020632_amd64.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/linux-image-2.6.32-020632-generic_2.6.32-020632_amd64.deb") for 64-bit
[linux-image-2.6.32-020632-generic_2.6.32-020632_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/linux-image-2.6.32-020632-generic_2.6.32-020632_i386.deb") for 32-bit

The above are linux kernel (version 2.6.32), and hopefully one day, this driver will also be included in it. They are architecture dependant, so if one doesn't work, just install the other one.

**EDIT: The wifi driver works for me in the 2.6.31-17 kernel (the latest kernel version via Ubuntu's updates). Ethernet also works out-of-the-box in that kernel version**

**EDIT: A new kernel version 2.6.31-19 has been released. When I get my laptop back from service tomorrow, I'll give it a crack **

So instead of doing the below in the 2.6.32 kernel, all you have to do is update the system via an ethernet cable, reboot and boot into the 2.6.31-17 kernel on the bootloader menu (if the only operating system installed is Ubuntu, hold down the shift key and it should come up). 

If ethernet internet access is not available, simply perform the following in the 2.6.32 kernel, and once internet is up and running and after having updated the system..

**Not sure if updating the system will also install the 2.6.31-17 kernel seeing that a newer kernel version 2.6.32 is already installed. I'll come back to you on that one.**

**Here's what you do:**

1. Download [this file]("http://launchpadlibrarian.net/35607918/rtl8192se_linux_2.6.0010.1113.2009.tar.gz"). It is a tar.gz for the wifi driver and you need to extract it to . To do this, you just open with "Archive Manager" and there will be an extract option in that dialog box in the extracting utility. This is the driver for the above wifi card.

2. Go to Applications ----> Accessories ----> Terminal and type in ```
cd ~/Downloads/rtl8192se_linux_2.6.0010.1113.2009
```This will take you into the directory of the file.

3. Type in ```
sudo su
```and type in your password. This will give you root permissions to the computer. 

4. Type in ```
make
```This will compile the source code for the driver

Then:
```
make install 
```This installs the source code onto your computer. 

Restart and it should work :-D. This will also get Bluetooth up and running too, though I can't say for sure as to whether that's an out-of-the-box compatibility (it was actually visible while I used this laptop in Moblin)

By the way, [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126") is the bug report for this issue. Hopefully, the driver will automatically be integrated into the kernel one day, seeing that the priority is quite high :-) 
--------------------------------------------

Now I had my networking working, but I couldn't use them for as long as I could in Windows because the screen brightness refused to go any lower and remained on highest brightness. This not only sucked the juice out of my batteries, it also burned my eyes out whenever I had to use it in dark places. This wasn't acceptable to me, and I went hunting for a fix. At first, I got [this fix (see comment #10)]("https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/392948?comments=all"). It worked to some extent [(see this thread)]("http://ubuntuforums.org/showthread.php?t=1361556"), but then, I came across [this thread]("http://ubuntuforums.org/showthread.php?t=1321403") and that actually fixed it up FOR GOOD :-D. So here's how you do it:

**[COLOR=Lime]HOWTO: Get screen brightness changing when you press the hotkeys[/COLOR]**
Very simple, and this MUST be running GRUB2 in order for this to work (when I find out how to do this in legacy GRUB, I'll add that here)

1. Go to Applications ----> Accessories ----> Terminal and type in 
```
gksudo gedit /etc/default/grub
```This will take you to a file where we can add a parameter to the boot-up

There, you will see a line that looks like this: 
```
GRUB_CMDLINE_LINUX=""
```All we have to do here is put this in between the two quotation marks:
```
nomodeset acpi_backlight=vendor
```so that it looks like this
```
GRUB_CMDLINE_LINUX="nomodeset acpi_backlight=vendor"
```The required text has to be inside the quotation marks, or it won't work. 

Restart, and wait until the desktop is fully loaded. I only did this myself a few hours ago, but there are a few "catches" here and there. If you try to change the screen brightness while the Ubuntu GDM is loading to the desktop, the desktop doesn't exactly load up. And also, on the first reboot into it, I had some panel applets not exactly wanting to load up, and the malfunctioning applets just showed up with a grey space, though they work without any problems after the second reboot. 
-------------------------------------------------------

The webcam works out of the box in chesse after installing it :-D. It just started to work after I installed the program, and when I loaded it up, the LED lighted up, and I saw myself in the picture of the webcam ;-). If you come into any problems, let me know, because I have a feeling that it wasn't working before. Having an updated system probably helps.

**EDIT: **Someone at the launchpad group for the Toshiba Satellite T100 series managed to get the microphone working. They installed the package "gnome-alsamixer" It didn't work for me unfortunately, and turns out I already had installed that package. For now, the microphone recording application doesn't want to work with my microphone :(.

As time goes along, this post will be updated as I make further inroads into making Ubuntu work with the Toshiba Satellite T110 and similar models

---

### Post by Vignesh S on 2010-01-26
A new [launchpad.net]("https://launchpad.net/%7Etoshiba-t100-series") team has been set up for those using the Toshiba Satellite T100 series laptops

---

### Post by Speshio on 2010-02-17
Vignesh S
Thanks very much for your efforts here. I'm plodding along in your wake, several beans back, but making progress, and keeping a close eye on this thread. Toshiba T135-S1309
Good job, mate.

---

### Post by Vignesh S on 2010-03-16
As I am currently in my last 2 years of school (known here as VCE), things are really intense for me, and I don't have too much time to update this thread. I'll try whenever I have the time...

---

### Post by jsampaio57 on 2010-03-18
I have just bought a Toshiba Satellite Pro T110. To have wifi working I followed the installation of the rtl8192se driver as explained above and I got it working. However the bluetooth only started working after installing the omnibook as in [here]("http://ubuntuforums.org/showthread.php?t=316358"), and using:

sudo modprobe omnibook ectype=14

the "14" was pure guess! 

My box runs Ubuntu 9.10. I tried the current 10.04-ALpha3 and is does not solve the difficulty as for now.

It seems that all the difficulty after installing the driver (rtl...) is because ubuntu boots with bluetooth off, and the FN F8 key does not work in the traditional way (on <--> off). In Windows it circles through WIFI on/off --> BT on/off --> All ON --> All OFF. It seems that Ubunto does not recognize this sequence. 

Cheers...

Jorge

---

### Post by Vignesh S on 2010-03-24
> **jsampaio57 said:**
> I have just bought a Toshiba Satellite Pro T110. To have wifi working I followed the installation of the rtl8192se driver as explained above and I got it working. However the bluetooth only started working after installing the omnibook as in [here]("http://ubuntuforums.org/showthread.php?t=316358"), and using:

sudo modprobe omnibook ectype=14

the "14" was pure guess! 

My box runs Ubuntu 9.10. I tried the current 10.04-ALpha3 and is does not solve the difficulty as for now.

It seems that all the difficulty after installing the driver (rtl...) is because ubuntu boots with bluetooth off, and the FN F8 key does not work in the traditional way (on <--> off). In Windows it circles through WIFI on/off --> BT on/off --> All ON --> All OFF. It seems that Ubunto does not recognize this sequence. 

Cheers...

Jorge

Yeah, this particular model doesn't exactly want to recognise the sequence. If it did, it would make my life a lot easier in regards to turning the bluetooth and wifi off in Ubuntu :(. Strange how Toshiba prefers to use the software to turn something on/off rather than physically link it up to that particular piece of hardware. This refers to bluetooth, wifi and the screen brightness.

---

### Post by jsampaio57 on 2010-04-13
With 10.04 beta2  and kernel 2.6.32-20, the bluetooth is working much better. However, to have wireless working, after compiling and installing RTL8192SE, I need to load r8192se_pci using the wlan0up script everytime I boot. How to have it loaded automatically? (I already sudoed modprobe r8192se

About backlight: I can't make it working with beta2 (was ok with beta1). I added the Power Manager Brightness Applet in the upper pane, and the icons has a (NO) symbol on it and says: "Cannot get laptop Brightness". I opened Systems>Preferences>Monitors and checked "Show monitors in panel" and it showed. When I clicked the little monitor icon in the upper panel, it shows "Laptop" disabled. It seems that the OS in not seeing the NB as a notebook/laptop but as as desktop. Maybe because of this the brightness control is disabled. Then I removed the applet and there is no way I can have it back.

Cheers...

---

### Post by Vignesh S on 2010-04-16
Hmm..... I'm not too sure about 10.04 beta, since I haven't tried it yet on my laptop. 

Somewhat strange that the driver doesn't load up at start up though. Hopefully it sorts it out by itself. 

Apparently Ralink made a page that had the updated version of the driver on it, but I'll have to search for it. I'll add it here when I find it.

---

### Post by Dynelight on 2010-08-17
The microphone still doesn't work on Ubuntu 10.04... and I have no idea how to get it to work either...
Alsamixer didn't do anything...

---

### Post by errietta on 2010-08-23
I followed this whole thread on ubuntu 10.04... Wireless still makes the kernel panic :(

---

### Post by jsampaio57 on 2010-09-07
> **errietta said:**
> I followed this whole thread on ubuntu 10.04... Wireless still makes the kernel panic :(

Look,I have a T110 (PST1BA-009007). I had some difficulties with 9.10, but both Wi-fi and bluetooth works in 10.04. I checked my notes about it (I keep all those crazy solutions in my files) and I found the following:


Basic installation instructions
==================================
1- Install GNU make and C compiler (gcc), as well as the configured
source of the running kernels (ie. either the kernel headers or the
sources from which you have compiled your own kernel)

2- get the up-to-date sources:
$ git clone git://omnibook.git.sourceforge.net/gitroot/omnibook/omnibook

3- compile, install and load the module against your kernel sources:
$ cd omnibook/
$ sudo su            (put the password)
# make load
# exit
$

4- (Optional) Add necessary module options to your /etc/modprobe.conf or in a file in /etc/modprobe.d/. e.g.: "options omnibook apmemu=1 dock=1
user=1"

5- (Optional) Edit your startup scripts (eg. /etc/rc.local, /etc/rc.modules or /etc/modules) to load this module at boot time.


I am using the following options:

in /etc/modpbobe.d/omnibook.conf
$ sudo gedit /etc/modpbobe.d/omnibook.conf  (I added the following lines)

## options omnibook ectype=14 userset=1 bluetooth=1
options omnibook ectype=14

(save the file)

in /etc/modules
$ sudo cp /etc/modules /etc/modules.bak
$ sudo gedit /etc/modules   (add at the end of the file)
	....
	lp
	omnibook

(save the file)

Then reboot.
Notice that wifi and bluetooth may conflict because they use the same frequency range and the same chip. I always keep my wifi off then I turn  bluetooh on (if needed - I use a Bt mouse), then I turn wifi on.

Cheers... Jorge

---

### Post by jsampaio57 on 2010-09-07
Hey, does anybody there know what is the 3D accelerometer chip in the Toshiba T110? I am trying access it using Ubuntu. I have tried ECTool but it seems that the accelerometer values are not dump from the EC RAM.

Cheers...
Jorge

---

