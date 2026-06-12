---
title: "Acer aspire 4930 wireless not working"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by thejames on 2008-09-03
Hi I just bought an Acer Aspire 4930G Laptop. I installed Ubuntu (dual booting with vista) and everything is working fine **except wireless**. It has a button to on and off wireless but the button is not working and the LED is also not lighting up. However I can connect to the network if wired, wireless is not working. Latest updates are installed.

It has a bluetooth button which works fine.

Everything is working fine in vista as this came pre-installed with vista home premium.

---

### Post by gggggdxn on 2008-09-04
I'm suffering the same problem with same laptop. My sound card does not work either.

---

### Post by Kevbert on 2008-09-04
Welcome to Ubuntu.
Please gpo to Applications - Accessories -Terminal and enter
```
lspci
```
Highlight the output with the mouse, copy with Ctrl-Shift-C and post here with Ctrl-V.
You probably need some firmware drivers.
Regarding sound enter the command
```
lshw -C multimedia
```
and again post here.  
Please note that commands are case sensitive.

---

### Post by thejames on 2008-09-04
lspci


```
00:00.0 Host bridge: Intel Corporation Cantiga Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Cantiga PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 06e9 (rev a1)
04:00.0 Network controller: Intel Corporation Unknown device 4232
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
07:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
07:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
07:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
07:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384

```

lshw -C multimedia

```

WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```


Yeah i forgot to add, my audio also doesn't work. Thanks for taking the time to help.

---

### Post by bobnutfield on 2008-09-04
For sound, look in /etc/modprobe.d and look for a file named "sound". If it exists, look for an entry called "options."  It should have an entry like this:

> options snd-hda-intel model=acer

Before doing anything else, type:

> sudo lsmod

and check to see if you see the snd-hda-intel module loaded.  
The snd-hda-intel module should work out of the box.  On some laptops, it is necessary to create the above entries in /etc/modprobe.d to get sound working.  If you create it, then you must reboot to try your sound again.

For the wireless, it is shown as an unkown device.  Open a terminal and type:

> dmesg | grep wlan0

If you get no output, then your hardware is not being picked up at boot.  This further evidenced by the fact that the light is not coming on.  Your ethernet port IS being detected.

---

### Post by gggggdxn on 2008-09-04
> **Kevbert said:**
> Welcome to Ubuntu.
Please gpo to Applications - Accessories -Terminal and enter
```
lspci
```
Highlight the output with the mouse, copy with Ctrl-Shift-C and post here with Ctrl-V.
You probably need some firmware drivers.
Regarding sound enter the command
```
lshw -C multimedia
```
and again post here.  
Please note that commands are case sensitive.

Here is my results:
```
sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 06e9 (rev a1)
04:00.0 Network controller: Intel Corporation Unknown device 4235
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
07:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
07:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
07:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
07:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384

```

```
sudo lshw -C multimedia
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```

Thanks!

---

### Post by gggggdxn on 2008-09-04
> **bobnutfield said:**
> For sound, look in /etc/modprobe.d and look for a file named "sound". If it exists, look for an entry called "options."  It should have an entry like this:



Before doing anything else, type:



and check to see if you see the snd-hda-intel module loaded.  
The snd-hda-intel module should work out of the box.  On some laptops, it is necessary to create the above entries in /etc/modprobe.d to get sound working.  If you create it, then you must reboot to try your sound again.

For the wireless, it is shown as an unkown device.  Open a terminal and type:



If you get no output, then your hardware is not being picked up at boot.  This further evidenced by the fact that the light is not coming on.  Your ethernet port IS being detected.

The module snd_hda_intel was loaded by default but not working correctly. There is no file called /etc/modprobe.d/*sound*, so I created one, which wrote: "options snd-hda-intel model=acer". But there is still no sound after reboot.

The command dmesg | grep wlan0 gives no output. So how to let linux kernel pick up it at boot?

---

### Post by gggggdxn on 2008-09-04
I found this in /var/log/kern.log:
```
kernel: [   17.150244] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

```

What does this mean and where can I place "pci=routeirq"? Thanks!

---

### Post by thejames on 2008-09-04
> **gggggdxn said:**
> The module snd_hda_intel was loaded by default but not working correctly. There is no file called /etc/modprobe.d/*sound*, so I created one, which wrote: "options snd-hda-intel model=acer". But there is still no sound after reboot.

The command dmesg | grep wlan0 gives no output. So how to let linux kernel pick up it at boot?

Got the same results, but haven't created a sound file. I'm currently on vista because i can't get a wired connection now. I'll post my results in a couple of hours. But I expect results will be same as this is the same hardware.

---

### Post by bobnutfield on 2008-09-04
If creating the file in /etc/modprobe.d did not work, then delete it.  It does not always work with every distro.  Are you both sure that alsa is selected in Preferences>sound?  This sound module is very mature and as mentioned before should work out of the box.

---

### Post by thejames on 2008-09-04
yes i'm very sure. I even changed to see if it would work, but it didn't so I have changed back to alsa.

---

### Post by bobnutfield on 2008-09-04
If you have not already tried it, open a terminal and type:

> alsamixer

and make sure the master volume is not muted.  Do you have a speaker icon in your panel?

---

### Post by thejames on 2008-09-04
Its not muted and I have a speaker icon in the panel. thanks for everything, but can you help me more with the wireless, because internet is very important, I can't have a wired connection everytime. Sound is secondary.

---

### Post by bobnutfield on 2008-09-04
I will be glad to try and help with the wireless, but I have not been able to find out what wireless chip your laptop is using.  The best I could find is that many Acer Aspires use the Intel Pro Wireless chip which uses the ipw2200 module.  Since you are dual booting, find out what chip you have by going to the Device Manager in Windows.  It will be more likely we can help by knowing the exact chipset.

---

### Post by thejames on 2008-09-04
Intel wireless wifi link 5100. thats the one.

---

### Post by bobnutfield on 2008-09-04
Here is a thread in the Ubuntu about your chipset:

> [http://ubuntuforums.org/showthread.php?t=879134&highlight=Intel+Wifi+Link](http://ubuntuforums.org/showthread.php?t=879134&highlight=Intel+Wifi+Link)

However, in checking with the NDISwrapper site, I found a post that indicated that this chipset has recent support in the kernel, but requires a firmware update.  This post gives instructions for Fedora 9, but it can be translated to Ubuntu.  This is the instructions from that post:

> 1. update your kernel
-close all unneeded applications
-press ALT+F2
-enter gnome-terminal
-press enter key
-enter "su -" without quotes
-press enter key
-enter root password (it is the password you've had to enter at the end of installation process of your operating system)
-press enter key
-enter "yum update -y kernel" without quotes
-press enter key and wait
-reboot your computer and check if your wireless card works, if not do the steps below
2.get the firmware for wireless card
-enter "cd /lib/firmware" without quotes
-press enter key
-enter "wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-5.4.A.11.tar.gz" without quotes
-press enter key and wait
-enter "tar -xf iwlwifi-5000-ucode-5.4.A.11.tar.gz" without quotes
-press enter key
-enter "cp ./iwlwifi-5000-ucode-5.4.A.11/iwlwifi-5000-1.ucode ./" without quotes
-press enter key
-enter "rm -rf iwlwifi-5000-ucode-5.4.A.11*" without quotes
-press enter key
-reboot your computer and check if your wireless card works

Obviously, where it calls for "su", that is not used in Ubuntu and you would simply substitute sudo.  This explains how to get the firmware update, but it is for the Fedora kernel 2.6.25.14-108 and I cannot confirm that it would work with Ubuntu's kernel.

Since support is apparently very new, you might try the ndiswrapper route first as describe in the post linked above.

---

### Post by thejames on 2008-09-04
alright thanks, booting to ubuntu and checking now. Will post results when I finish.

---

### Post by Kevbert on 2008-09-04
The sound file you are looking for is /etc/modprobe.d/alsa-base
You can edit this file with 
```
sudo gedit /etc/modprobe.d/alsa-base 
```
Add the following to the end of the file.
```
options  snd-hda-intel model=acer
```
Save the file, exit and reboot.

---

### Post by bobnutfield on 2008-09-04
Thanks, Kevbert.  I have used that to get sound working a hundred times in other distros, but never had to in Ubuntu.  Now I know what file to put this in.

---

### Post by Kevbert on 2008-09-04
With regard to wireless. I believe you have a dual band Intel 5100/5300 adapter which supports 802.11a/b/g/Draft N wireless.  the best link I could find was [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=879134").  If that fails you could try searching on the Intel.com website for linux 5100/5300 drivers (you may need to use ndiswrapper).

---

### Post by gggggdxn on 2008-09-04
> **bobnutfield said:**
> If creating the file in /etc/modprobe.d did not work, then delete it.  It does not always work with every distro.  Are you both sure that alsa is selected in Preferences>sound?  This sound module is very mature and as mentioned before should work out of the box.

By default it looks like the attached screen shot (that is, "Auto detect"); no improvement after change every drop-down menus into "ALSA".

---

### Post by thejames on 2008-09-05
> **Kevbert said:**
> The sound file you are looking for is /etc/modprobe.d/alsa-base
You can edit this file with 
```
sudo gedit /etc/modprobe.d/alsa-base 
```
Add the following to the end of the file.
```
options  snd-hda-intel model=acer
```
Save the file, exit and reboot.
Didn't work, I added the line to the end of the file and restarted.

About the wireless, everything in that thread went over my head as I'm fairly new to this and I don't have the time now to learn through trial and error. 

However, by reading through it I have come to the conclusion that wireless is working fine in another version of the kernel 2.6.27 rc something. I have 2.6.24 and there is no kernel update in the update utility. 

How can I get a new kernel without having to compile it myself? Do I have to wait until it is officially available in the update manager? 

Thanks for all the help guys.

---

### Post by gggggdxn on 2008-09-05
I managed to make wlan0 to show up finally. Although still doesn't work, it's a step towards success.

This what I did:
1. Although I'm using 8.04.1, I install the newest kernel from 8.10, whose version is 2.6.27-2-generic.
2. Download the firmware from "http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-5.4.A.11.tar.gz" and decompress it.
3. Copy iwlwifi-5000-1.ucode to /lib/firmware/ and reboot.
4. Though "dmesg | grep wlan" gives nothing, the results from "iwconfig" show that the kernel have recognized the wireless card as wlan0.

Here are some ideas:
1. Official support of Intel Wifi Link 5300 & 5100 was announced in Linux Kernel Mail-list on Aug 15, 2008 ([http://groups.google.com/group/linux.kernel/browse_thread/thread/29aaff8982c9da6e/e25bfdad4175927c](http://groups.google.com/group/linux.kernel/browse_thread/thread/29aaff8982c9da6e/e25bfdad4175927c)), in which the 2.6.27 kernel was mentioned. The module would named iwlagn.

2. The newest kernel in 8.04.1 is 2.6.24-21, while in 8.10 is 2.6.27-2. So I decide to install the kernel from 8.10.

3. "grep IWLWIFI /boot/config*" shows that 8.04.1's kernel doesn't have the modules for my wireless card compiled, while 8.10's kernel have.

4. After boot with a 2.6.27 kernel, "dmesg | grep iwl" shows that the firmware iwlwifi-5000-1.ucode was required. According to the letter in kernel's mail-list, I downloaded that from "http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-5.4.A.11.tar.gz".

Now the kernel keep complaining:
```
$ dmesg | grep iwl
[   14.881428] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   14.881430] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   14.881588] iwlagn 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.881617] iwlagn 0000:04:00.0: setting latency timer to 64
[   14.881665] iwlagn: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[   14.910319] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[   14.931480] iwlagn 0000:04:00.0: PCI INT A disabled
[   14.933237] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   23.954610] iwlagn 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   23.954691] iwlagn 0000:04:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   23.954852] firmware: requesting iwlwifi-5000-1.ucode
[   28.060066] iwlagn: START_ALIVE timeout after 4000ms.
[   28.060115] iwlagn 0000:04:00.0: PCI INT A disabled
[   30.700269] iwlagn 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   30.700348] iwlagn 0000:04:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   34.704071] iwlagn: START_ALIVE timeout after 4000ms.
[   34.704128] iwlagn 0000:04:00.0: PCI INT A disabled
[   51.764284] iwlagn 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   51.764364] iwlagn 0000:04:00.0: restoring config space at offset 0x1 (was 0x180002, writing 0x100006)
[   55.772072] iwlagn: START_ALIVE timeout after 4000ms.
[   55.772125] iwlagn 0000:04:00.0: PCI INT A disabled

```
Any further ideas? Thanks!

---

### Post by Slug71 on 2008-09-05
On my Acer i had to enable the Restricted Driver wl in Admin-Hardware Drivers.

---

### Post by Kevbert on 2008-09-07
> **thejames said:**
> 
About the wireless, everything in that thread went over my head as I'm fairly new to this and I don't have the time now to learn through trial and error. 

However, by reading through it I have come to the conclusion that wireless is working fine in another version of the kernel 2.6.27 rc something. I have 2.6.24 and there is no kernel update in the update utility. 



I wouldn't upgrade to Intrepid (kernel 2.6.27.2) yet as it's still in Alpha release and still has the odd bug with regards to sound.  With wireless I've had to use my fix as detailed in that post even for Intrepid.  The drivers (B43) look as if they're installed but as soon as I pull the ethernet cable out the PC complains (so installed as per post).

---

### Post by thejames on 2008-09-07
I see, so what do you suggest? Is there no easy way to get wireless working, or any step-by-step instructions?

---

### Post by Kevbert on 2008-09-08
What you could do is put the Hardy install CD in the drive, using Nautilus file manager browse to pool, main, n, ndiswrapper and double click on each of the .deb files in turn in this directory to install ndiswrapper and utils. Next you want to go up one directory and go into the ndisgtk directory and double click on the .deb file there. The file that you've just installed in the graphical front end for ndiswrapper. This file can be found under System-Admin-Windows Wireless Drivers. You can now use your Intel windows drivers (CD) by browsing to them using this program (click on the folder icon to the right of the text box).  The file that you need is an .inf file.

---

### Post by gggggdxn on 2008-09-20
Finally my wireless card and sound card works.
After installed the firmware I mentioned before, I download & compiled the latest kernel (2.6.27-rc6), and everything works.

---

### Post by inash on 2008-10-11
I have an Acer Aspire 4930 and had the same problem with WIFI and audio on Hardy. How ever, installing the Intrepid beta, cured the problem. The new WIFI support was updated in kernel version 2.6.27 along with the sound driver as well.

There was one other problem even then. The ALSA sound driver didn't work. I had to change everything to OSS. And today, there were some beta package updates. I did the update and by default the ALSA driver was working. I change the sound settings to auto detect and everything seemed to be working just perfectly.

I suppose the final version of Intrepid will be quite complete and would have support for the rest of the hardware series in line.

Cheers.

---

### Post by thejames on 2008-10-18
now the only problem is I can't here the sound thru headphones, only with the speaker. Even with a headset plugged in sound comes from the speakers.

---

### Post by inash on 2008-10-18
Change the audio output device from your audio or video application to /dev/dsp1. That'd do the trick. And probably you will be able to control the levels from the ALSA mixer.

---

### Post by thejames on 2008-10-22
err.. how do i do that??

---

### Post by inash on 2008-10-22
Ok. Here's a temporary solution for that. Seems that the kernel isn't still up to date with the hardware probably or there might be some other problem.

If the ALSA driver is working, select the volume control by double clicking the sound icon in the tray. Goto preferences and tick on Surround. Click close to come back to the volume control. Now if the Surround volume bar is muted, unmute it and set the level high to an optimal level.

If your headphones are plugged in, you should be getting the audio from the headphones now; the volume is adjusted through the Surround volume bar. The laptop speak can be controlled through the Front volume bar. You can lower it or mute it to cancel the sound from the laptop speakers.

For now, you should be able to enjoy sound from the headphones now. Cheers.

---

### Post by thejames on 2008-10-23
thanks very much, works great.

---

### Post by 1902 on 2008-10-27
I bought the acer aspire 9430g few days back and make it dual boot also with vista and ubuntu 8.10 beta, everything works out of the box (wireless, webcam,etc...) exept the built in microphone i couldn't get it working, but i guess it's some kind of bug not yet fixed in the beta version (the microphone is allways disabled even if you enable it manualy), but i could manage to use my external mic for the time being.

---

### Post by snigapoe on 2008-11-05
> **bobnutfield said:**
> For sound, look in /etc/modprobe.d and look for a file named "sound". If it exists, look for an entry called "options."  It should have an entry like this:



Before doing anything else, type:



and check to see if you see the snd-hda-intel module loaded.  
The snd-hda-intel module should work out of the box.  On some laptops, it is necessary to create the above entries in /etc/modprobe.d to get sound working.  If you create it, then you must reboot to try your sound again.


i'm using ubuntu8.1 currently on acer aspire 4930
my sound seems to be not working on the ALSA mixer (previously work but not sure wat did i done now the speaker always gv buzzing sound) 
i found the solution buy download realtek hd audio codec
but now seems to be my audio jack not functioning any idea??

---

### Post by noblepa on 2009-01-01
> **gggggdxn said:**
> Finally my wireless card and sound card works.
After installed the firmware I mentioned before, I download & compiled the latest kernel (2.6.27-rc6), and everything works.

i am also having the same problem. 
How do you compile kernel?

 Please give step-by-step instructions.

---

### Post by noblepa on 2009-01-20
:KS
 I have installed Ubuntu Intrepid Ibex (which Include kernel 2.6.27.xx). Now wireless, sound, display everything works fine for me on Aspire 4930G

Thank you All

---

