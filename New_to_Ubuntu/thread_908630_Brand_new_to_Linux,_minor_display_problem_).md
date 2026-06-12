---
title: "Brand new to Linux, minor display problem :)"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by victorcrane on 2008-09-02
Hey folks, after a long time intending to install and use my ubuntu disc, I finally got the kick up my **** I needed this morning when I turned on my laptop to find it crippled by a virus. Bye bye windows...

So here I am a few hours later up and running with Hardy Heron, and I'm stunned at how nice it is to use. I have managed to install drivers for my wireless card and I figured out how to download and install flash and firefox 3 and thunderbird.. I'm probably doing it the long way round but hey it's all part of the fun...

Anyway, my only issue is that my laptop (a dell inspiron 1300) has a widescreen, and the display is stretched a bit as it seems the resolution isn't quite right, but in the display settings there's only one resolution available to me. I've dug around for drivers but can find none. 

Anyone want to give me a clue? I look hilariously fat in my myspace picture on the current setting! :guitar:

---

### Post by t0p on 2008-09-02
The driver you need may be available under **System > Administration > Hardware Drivers**

---

### Post by brentoboy on 2008-09-02
to fix this, (if a proprietary driver doesnt work) you will have to hand edit your /etc/X11/xorg.conf file, which is potentially dangerous.  The problem is that it didnt detect your monitor's specifications correctly.

you need to find out the exact settings for your monitor as far as maximum horizontal and vertical refresh rates, and native resolutions, all that stuff.

once you have it all together, then you use it to modify the entry in there for your monitor (or create a new entry).  use the xorg.conf man page (found here: [http://linux.die.net/man/5/xorg.conf](http://linux.die.net/man/5/xorg.conf)) to get the settings in there just right, save the file, and then restart X (either reboot, or hit ctrl+alt+backspace to kill your current gui session).

If all goes well, great.  if not, restore from backup.
to make the backup (before you edit the file) try this:
sudo cp /etc/X11/xorg.conf /etc/X11/old-xorg.conf

to edit the file:
sudo gedit /etc/X11/xorg.conf

and to restore from backup:
sudo cp /etc/X11/old-xorg.conf /etc/X11/xorg.conf

---

### Post by Starecase on 2008-09-02
ignore this post please.

---

### Post by victorcrane on 2008-09-02
Cripes, that hand editing business looks pretty heavy for a novice but I may have to give it a shot, I checked the hardware drivers section and found nothing there. This looks like it could well be tricky!

---

### Post by ugm6hr on 2008-09-02
Give us the output from:
```
lspci
lshw -class display
sudo xrandr -q
```

And what should your resolution be?  Standard laptop widescreens tend to be 1280x800.

---

### Post by doas777 on 2008-09-02
editing Xorg can be tough, no doubt. on the upside you only really need to do it once, and then just back it up somewhere.

do you have the restricted drivers enabled for your vid card? you can find out at:
System -> Administration -> Hardware Drivers

sometimes it takes a few reboots to get it to detect the hardware.

---

### Post by victorcrane on 2008-09-02
victorcrane@victorcrane-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
victorcrane@victorcrane-laptop:~$ lshw -class display
WARNING: you should run this program as super-user.
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
victorcrane@victorcrane-laptop:~$ sudo xrandr -q


That's what I got from that bit of code... I hope that's what you wre after anyway. :confused:

---

### Post by victorcrane on 2008-09-02
I should perhaps add my current resolution is coming up as 1024 x 768. I think it does usually run at 1280 x 800 in windows. It doesn't look quite as sharp as usual.

---

### Post by doas777 on 2008-09-02
you will most likey have to edit your xorg.conf. brentoboy gave some good instructions on that above.

can you please post your xorg?

theres a great post that may be of use to you, by LondonSteve posted here:
[http://ubuntuforums.org/showthread.php?t=808812&page=2](http://ubuntuforums.org/showthread.php?t=808812&page=2)

it really reminded me of my first experience with xorg.

---

### Post by ugm6hr on 2008-09-02
> victorcrane@victorcrane-laptop:~$ sudo xrandr -q
where's the result from this?  there must be some output.

---

### Post by victorcrane on 2008-09-03
victorcrane@victorcrane-laptop:~$ sudo xrandr -q
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 (normal left inverted right) 0mm x 0mm
   1024x768       60.0* 

Sorry about that Ugm6hr... must have missed that bit.

---

### Post by ugm6hr on 2008-09-03
I suspect this is an Intel video driver issue.

Read this: [http://packages.ubuntu.com/hardy/915resolution](http://packages.ubuntu.com/hardy/915resolution)

I think you need to install this to enable resolutions.

Not 100% certain - but can't hurt.

Otherwise, ensure you have updated xserver-xorg-video-intel.

---

### Post by victorcrane on 2008-09-03
Ugm6hr, you sir are a scholar and a gentleman. All is looking fantastic now thank you so much. It seems I have much to learn with this system. 

To all others who have offered advice please accept my thanks. All the best. :)

---

### Post by ugm6hr on 2008-09-03
> **victorcrane said:**
> Ugm6hr, you sir are a scholar and a gentleman. All is looking fantastic now thank you so much. It seems I have much to learn with this system. 

Just so you understand those commands:
lspci lists your hardware (identified the Intel chipset)
lshw identifies further hardware details (display class = display), with drivers - yours was "UNCLAIMED" with no driver listed
xrandr lists (and potentially controls) your available resolutions

So a google for your chipset revealed that there is an issue with the default driver - looks like it will be sorted (with a default install) in the near future (possibly with Ibex).

You should now find that lshw and xrandr have different results now.

Glad to help.

---

### Post by victorcrane on 2008-09-03
That's very helpful thanks, I'm hoping I can find some kind of guide to help me understand more of these commands so I can get to grips with it all. 

It's definitely a great OS and I'm enjoying working my way through it and finding everything. Sure it'll take me a while but I'll get there. :)

---

