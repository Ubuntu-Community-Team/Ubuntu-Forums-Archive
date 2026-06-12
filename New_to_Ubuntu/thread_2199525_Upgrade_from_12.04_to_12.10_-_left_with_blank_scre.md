---
title: "Upgrade from 12.04 to 12.10 - left with blank screen"
date: 2014-01-14
forum: New to Ubuntu
---

### Post by ghostylad on 2014-01-14
I managed to get lubuntu 12.04 installed and was hoping to work my way up from the inside with updates, so i sudo updated to 12.10 only for it to finish its install, reboot, load screen, then blank, it went no further, seemed to be no processor activity, just a black screen....really starting to get fustrated, can not make sense of it and can not find many people willing to help and give any comprehensive answers.

The hardware though old now should be able to handle a linux based os easily, so can not see a problem there, unless i am missing something completely, possible as i am a newbie but how can i start learning without anything to learn with?

---

### Post by mörgæs on 2014-01-14
Please wait for a response in Askubuntu and stop multiposting.
Thread closed.

---

### Post by Elfy on 2014-01-14
re-opened

---

### Post by ghostylad on 2014-01-15
Bump...Due to being closed then re-opened...

---

### Post by Topsiho on 2014-01-15
I have had the same sort of problem with newer Ubuntu's on one computer: the newer Ubuntu's are very hard on older graphics cards. You could try and boot with the nomodeset option and see whether this helps, as it did for me. Or you install Lubuntu (valid until only a few months from now) or Xubuntu instead.

Topsiho

---

### Post by Bashing-om on 2014-01-15
ghostylad; Hello ;

Is the problem at the system level, or just with the graphics ?
If you can boot to a terminal login, we can assume the system is functional.
To see your graphics card and info:
Terminal codes:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
Which will relate what card(s) is installed, and if/what driver for the graphics card is in use.
These known, we can take corrective actions to get ya "look'n good" .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Rex Bouwense on 2014-01-15
It sounds like the upgrade went wrong somehow.  I have tried to upgrade three times with various versions of Ubuntu and Lubuntu and each time the upgrade failed.  I was forced to re-install.  Fortunately, I had backed up my data so nothing was lost.  Others upgrade without a problem.  Did you back up your data?  If yes I would opt for a fresh install.  However, 12.10 doesn't have a whole lot of life left (EOL in April) and 13.04 is only supported for nine months, it might be better to install Lubuntu 13.10 while you await the long anticipated release of Lubuntu 14.04 which will finally be a LTS version.

---

### Post by ghostylad on 2014-01-15
Thank you for taking time to reply and for suggestions...I have downloaded 13.10 and its on standby.
As 12.04 is the only one i've been able to full install and have it operate i am wary to let it go just yet ;0)

---

### Post by ghostylad on 2014-01-15
> **Bashing-om said:**
> ghostylad; Hello ;

Is the problem at the system level, or just with the graphics ?
If you can boot to a terminal login, we can assume the system is functional.
To see your graphics card and info:
Terminal codes:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
Which will relate what card(s) is installed, and if/what driver for the graphics card is in use.
These known, we can take corrective actions to get ya "look'n good" .
[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]



Apologies for copy/paste but this is what was revealed as per you instructions.
Again thanks for any and all help.

lubuntu@lubuntu:~$ sudo lshw -c display
  
*-display UNCLAIMED     
       
description: VGA compatible controller
       
product: CN896/VN896/P4M900 [Chrome 9 HC]
       
vendor: VIA Technologies, Inc.
       
physical id: 0
       
bus info: pci@0000:01:00.0
       
version: 01
       
width: 32 bits
       
clock: 66MHz
       
capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       
configuration: latency=16 mingnt=2
       
resources: memory:a0000000-bfffffff memory:c8000000-c8ffffff


lubuntu@lubuntu:~$ lspci -nnk | grep -iA3 vga


01:00.0 VGA compatible controller [0300]: 
VIA Technologies, Inc. 
CN896/VN896/P4M900 [Chrome 9 HC] [1106:3371] (rev 01)
	
Subsystem: Fujitsu Technology Solutions Device [1734:10cb]
	
Kernel modules: viafb
04:01.0 Audio device [0403]: 
VIA Technologies, Inc. VT8237A/VT8251 HDA Controller [1106:3288] (rev 10)

---

### Post by Bashing-om on 2014-01-15
ghostylad; Well,

I know nothing about your graphics controller, however, the out put of "sudo lshw -C display: indicates there is no driver loaded.

What results from the "Additional Driver" utility ? Maybe it will find and load a driver (?).

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by ghostylad on 2014-01-15
> **Bashing-om said:**
> ghostylad; Well,

I know nothing about your graphics controller, however, the out put of "sudo lshw -C display: indicates there is no driver loaded.

What results from the "Additional Driver" utility ? Maybe it will find and load a driver (?).
[INDENT][INDENT]just my thought
[/INDENT]
[/INDENT]


I am just fresh installing 12.04 again, will let you know.

As far i as i can glean from any info about VIA/Chrome9 is that its not very
hospitable and certainly no Nvidia, ATI, etc.

---

### Post by Rex Bouwense on 2014-01-15
If you have already downloaded Lubuntu 13.10, run the md5sum, burn the ISO to a CD or flash drive, and see if you can boot from it.  If you can then you can take it for a test drive.  If everything works to your satisfaction then you are probably safe to install.  I was concerned about your data.  Did you back it up?  
You are aware that Lubuntu 12.04 has already reached EOL.  It is not a LTS version as Ubuntu 12.04 is.

---

### Post by ghostylad on 2014-01-15
> **Rex Bouwense said:**
> If you have already downloaded Lubuntu 13.10, run the md5sum, burn the ISO to a CD or flash drive, and see if you can boot from it.  If you can then you can take it for a test drive.  If everything works to your satisfaction then you are probably safe to install.  I was concerned about your data.  Did you back it up?  
You are aware that Lubuntu 12.04 has already reached EOL.  It is not a LTS version as Ubuntu 12.04 is.

Hi Rex,

I had no data to back up, it was basically a blank canvas that i wanted to 
use as a learning tool, to learn all the wizardry that is linux, then rassberry pi and so on
Also i play about with android a little but as i say in original post i am a newbie
to all of it.
Thanks for your suggestions.
Regards

---

### Post by ghostylad on 2014-01-16
Right, well i got 12.04 reinstalled...fine...Completely working, updated fine, no other updated versions found.
Installed muon installer app, detected software up to date but gave option for 12.10 update, hit the button
went through the whole update (1 and half hrs) and installed fine...low and behold same problem?!?!?
Its got to be a hardware thing....in other words a useless laptop.
Trying lubuntu 13.10 now....Don't hold out much hope.

---

### Post by Bashing-om on 2014-01-16
ghostylad; Hey ;

It is regretful that the graphics controller is giving us such a head ache !
Version 13.10 has much greater support for the open source drivers at large, maybe with 13.10 installed it will pick up that ATI controller with no problem.
Else; We will keep pounding away and try and get a driver loaded.

[INDENT][INDENT]not everything in life
[INDENT][INDENT][INDENT]is easy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

