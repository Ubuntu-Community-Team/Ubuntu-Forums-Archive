---
title: "HOWTO: Avoid random lockups (with Nvidia Driver)"
date: 2005-04-12
forum: Outdated Tutorials &amp; Tips
---

### Post by vnbuddy2002 on 2005-04-12
I am writing this to help Nvidia users who are struggling with random lockups. To begin with, make sure that you are using Nvidia Driver. Secondarily, make sure your system has the following symtom:

(*) Random lockups while the "mouse" is still moving.


STEP 1: ENABLE DPMS AND NvAGP
- Add the following settings to /etc/X11/xorg.conf (under "BusID")

```
Option "DPMS" "true"
Option "NvAGP" "1"
```

Save the changes

STEP 2: TURN OFF THE APCI 
- Edit "/boot/grub/menu.lst" and add the following option to the kernel

```
pci=noapci
```

Example:
```
kernel          /vmlinuz-2.6.10-5-386 root=/dev/hdf2 ro quiet splash pci=noacpi
```

STEP 3: HARD DRIVE CHECK
- Try to copy a big file from one place another ( 200MB +)
- If your copy gets freezed after 2 minutes or so, then it is probably caused by hdparm.
- Issue the following command:
```
sudo /etc/init.d/hdparm stop
```
- and try to copy again, if it finishes copying without any problem, then remove hdparm by 
```
sudo /apt-get remove hdparm
```

Reboot your computer and post your result(s) here. Good luck!

---

### Post by Technoviking on 2005-04-12
If you remove hdparm, you can not turn on DMA on CD/DVD drives. Some cd-burner software needs DMA to work, plus you can get slow playback on music cds and movie dvds.

Mike

---

### Post by bman08 on 2005-04-12
Removing hdparm is not a good solution.  It will also devastate the performance of ATA hard drives.  This solution is like cutting off your nose to make your glasses fit better.

---

### Post by vnbuddy2002 on 2005-04-12
You gain something by loosing something. It is only a matter of which one is more important to you.

Unless there are changes in hdparm, otherwise, you can not have both.

hdparm gives "time out waiting for device .. bla bla bla..". 

Or another option is to write a simple daemon to detect CD/DVD drive. If the device is mounted, then "/etc/init.d/hdparm start", else "/etc/init.d/hdparm stop".


:) I only brought up options for you to decide. It is your call to pick whichever solution would work for you.

---

### Post by dabang on 2005-04-13
Hi there,
I encountered the same problem, but solved it by switching from AGP 4x to 2x. Like discribed in the NIVIDIA [readme](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7174/README.txt) appendix F "AGP Rate", you have to extract the files and then edit the file "os-registry.c":
search and change

static int NVreg_ReqAGPRate = 7;
to
static int NVreg_ReqAGPRate = 2;

and

{ NULL, "ReqAGPRate",     &NVreg_ReqAGPRate,      0 },
to
{ NULL, "ReqAGPRate",     &NVreg_ReqAGPRate,      1 },

and then recompile the kernel module an reboot.

At least it worked for me...

---

### Post by Gianni Exile on 2005-04-13
I had the same lockups, they were fixed by having the following 
in the /etc/X11/xorg.conf file:
```

Section "Device"
        Identifier      "NVIDIA Corporation NV17 [GeForce4 MX 440]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"

        Option "NvAGP"          "2"
        Option "NoLogo"         "true"
        #Option "RenderAccel"   "true" # EXPERIMENTAL # RANDOM LOCKUPS? noapic
        #Option "UseEdidFreqs"  "true" # EXPERIMENTAL -- appears useless
EndSection

```

Prior to this I tried all suggested above, neither apic nor acpi nor hdparm had anything to do with it... removing "RenderAccel" fixed it though.

---

### Post by vnbuddy2002 on 2005-04-13
Try "RenderAccel", but lower the value for NvAGP?

Option "NvAGP"          "1"

Let me know if it helps.

---

### Post by astoltz on 2005-04-13
Removing the RenderAccel option also worked for me - as for many people judging by the discussions in other threads.  However, I really want RenderAccel to work so I'm looking for other solutions.

[QUOTE=vnbuddy2002]
STEP 1: ENABLE DPMS AND NvAGP
- Add the following settings to /etc/X11/xorg.conf (under "BusID")
[/QUOTE]
DPMS is already enabled in the "monitor" section.  Should it also get turned on in the "devices" section?  Also, enabling NvAGP results in an error having to do with AGPGART already loaded - see [this thread](http://ubuntuforums.org/showthread.php?t=25080).  I'll try to sort out this problem later but for now, i've got to leave NvAGP out.

I don't want to do anything with hdparm right now so all I'm left with is the apci kernel option.  I'll give that a try and see if it helps.  Stay tuned.

---

### Post by Gianni Exile on 2005-04-27
[QUOTE=astoltz]Removing the RenderAccel option also worked for me - as for many people judging by the discussions in other threads.  However, I really want RenderAccel to work so I'm looking for other solutions.
[/QUOTE]
Add this instead:
```
Option "backingstore"    "true"
```

Not as fast as RenderAccel, but helps significantly for certain 2D operations.
I've had no lockups with this one.

---

### Post by crazybill on 2005-04-28
Just a quick emphasis that I also recommend that you modify  /etc/X11/xorg.conf  rather than destroy hdparm. ... better results without the negative of not having hdparm

---

### Post by nocturn on 2005-04-28
I'm  curious if this is related to my problems...

What kind of problems where you experiencing?

I had Xorg use up 99% CPU while hanging.
dmesg shows this error:
NVRM: Xid: 13, 0000 02006100 0000008a 00000300 00c4099b 00000002

I will try the noacpi option in any case.

---

### Post by fordp on 2005-06-15
Hi everyone !

I have simalar problems to above excpet when it hits my pc it swithes off, just like if you press the power button for 4 seconds.

The PC will not then restart from the power button on the front and I have to remove the power for a few seconds to regain power.

My machine is a MSI MEGA 180 which is an Nvidia Nforce 2 IGP based machine.

I am running Hoary, Nvidia binary  gfx driver,  Self built  nvaudio (to get  hardware mixing and  spdif out) and Back Ports  1.04 Firefox.

I have just tried the first post above so we will see !

Has anybody else had there machine switch off ?

---

### Post by fordp on 2005-07-16
I have found the problem with my pc and it was not  Nvidia Driver releated.

It was not even releated to any software, apart from the deafult keyboard handling i guess.

I have a MSI Mega 180 Athlon XP 2500 PC and the problem was as follows :- 

I have finally fixed my shutdown problem :D

I noticed just before one of the shutdowns keys streaming accross the screen, and i was not even touching the keyboard.

I have swapped out my keyboard and I m now using a "Microsoft Internet Keyboard Pro" and the problem has gone !!!!

My latest theory as to the root cause is that it is power supply related and that the rail supplying the keyboard was overloaded or noisy.

This was causing the other keyboard to go nutty and issue random codes. When some special key press is issued the machine shutdown, standby or whatever.

I guess it is standby as it is notorious for not restarting properly.

I hope this helps others !

Cheers.

---

