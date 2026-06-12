---
title: "Athlon XP, no Flash"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by Larry_Klein on 2014-04-19
After a couple weeks of trying, I guess I should give up. Distros install and run beautifully for a couple hours before the total lockups start. 

I have run xp on this old unit for 5-6 years and never have a problem - never seen the "blue screen of death -(what ever that is)"

I love everything about linux - any ideas and I will give it another shot.

[COLOR=#000000]Full system info from lshw - short[/COLOR]

[COLOR=#000000]H/W path Device Class Description[/COLOR]
[COLOR=#000000]================================================== ====[/COLOR]
[COLOR=#000000]system DK394A-ABA a264w[/COLOR]
[COLOR=#000000]/0 bus A7N8X-LA[/COLOR]
[COLOR=#000000]/0/0 memory 64KiB BIOS[/COLOR]
[COLOR=#000000]/0/4 processor AMD Athlon(tm) XP 2800+[/COLOR]
[COLOR=#000000]/0/4/5 memory 128KiB L1 cache[/COLOR]
[COLOR=#000000]/0/4/6 memory 512KiB L2 cache[/COLOR]
[COLOR=#000000]/0/27 memory 512MiB System Memory[/COLOR]
[COLOR=#000000]/0/27/0 memory 256MiB DIMM 100 MHz (10.0 ns)[/COLOR]
[COLOR=#000000]/0/27/1 memory 256MiB DIMM 100 MHz (10.0 ns)[/COLOR]
[COLOR=#000000]/0/100 bridge nForce2 IGP2[/COLOR]
[COLOR=#000000]/0/100/0.1 memory RAM memory[/COLOR]
[COLOR=#000000]/0/100/0.2 memory RAM memory[/COLOR]
[COLOR=#000000]/0/100/0.3 memory RAM memory[/COLOR]
[COLOR=#000000]/0/100/0.4 memory RAM memory[/COLOR]
[COLOR=#000000]/0/100/0.5 memory RAM memory[/COLOR]
[COLOR=#000000]/0/100/1 bridge nForce2 ISA Bridge[/COLOR]
[COLOR=#000000]/0/100/1.1 bus nForce2 SMBus (MCP)[/COLOR]
[COLOR=#000000]/0/100/2 bus nForce2 USB Controller[/COLOR]
[COLOR=#000000]/0/100/2.1 bus nForce2 USB Controller[/COLOR]
[COLOR=#000000]/0/100/2.2 bus nForce2 USB Controller[/COLOR]
[COLOR=#000000]/0/100/4 eth0 network nForce2 Ethernet Controller[/COLOR]
[COLOR=#000000]/0/100/6 multimedia nForce2 AC97 Audio Controler (MCP)[/COLOR]
[COLOR=#000000]/0/100/8 bridge nForce2 External PCI Bridge[/COLOR]
[COLOR=#000000]/0/100/8/7 communication LT WinModem[/COLOR]
[COLOR=#000000]/0/100/9 storage nForce2 IDE[/COLOR]
[COLOR=#000000]/0/100/d bus nForce2 FireWire (IEEE 1394) Controll[/COLOR]
[COLOR=#000000]/0/100/1e bridge nForce2 AGP[/COLOR]
[COLOR=#000000]/0/100/1e/0 display R200 [Radeon 8500/8500 LE][/COLOR]
[COLOR=#000000]/0/1 scsi0 storage [/COLOR]
[COLOR=#000000]/0/1/0.0.0 /dev/sda disk 80GB ST380022A[/COLOR]
[COLOR=#000000]/0/1/0.0.0/1 /dev/sda1 volume 74GiB Windows NTFS volume[/COLOR]
[COLOR=#000000]/0/1/0.0.0/2 /dev/sda2 volume 510MiB Extended partition[/COLOR]
[COLOR=#000000]/0/1/0.0.0/2/5 /dev/sda5 volume 510MiB Linux swap / Solaris partition[/COLOR]
[COLOR=#000000]/0/2 scsi1 storage [/COLOR]
[COLOR=#000000]/0/2/0.0.0 /dev/cdrom disk DVD Writer 300n[/COLOR]
[COLOR=#000000]/0/2/0.1.0 /dev/sr1 disk CW038D CD-R/RW[/COLOR]
[COLOR=#000000]/0/2/0.1.0/0 /dev/sr1 disk [/COLOR]
[COLOR=#000000]/0/2/0.1.0/0/1 volume 695MiB Hidden HPFS/NTFS partition[/COLOR]
[COLOR=#000000]/0/3 scsi2 storage [/COLOR]
[COLOR=#000000]/0/3/0.0.0 /dev/sdb disk SCSI Disk[/COLOR]
[COLOR=#000000]/0/3/0.0.1 /dev/sdc disk SCSI Disk[/COLOR]
[COLOR=#000000]/0/3/0.0.2 /dev/sdd disk SCSI Disk[/COLOR]
[COLOR=#000000]/0/3/0.0.3 /dev/sde disk SCSI Disk[/COLOR]
[COLOR=#000000]/0/5 scsi5 storage[/COLOR]

---

### Post by pfeiffep on 2014-04-19
Welcome to the forum @Larry_Klein!   
When I first tried Linux on my old Dell laptop only 512Mb main memory was installed. I had similar problems as you described. 
> [COLOR=#000000]/0/27 memory 512MiB System Memory[/COLOR]
I upgraded the sysem's memory to the maximum that the hardware would support (2GB) for ~ $30. Now I'm running the latest OS that Ubuntu offers without problems!

---

### Post by mastablasta on 2014-04-19
run the mem test. linux and windwos xp use memory differently. 

furthermore the issue could also be [COLOR=#000000]/0/100/1e/0 display R200 [Radeon 8500/8500 LE] the GPU although the chip is supposed to be fully supported: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

sometimes the drivers do not load correctly. check the logs and troubleshoot in that area if memorry (RAM) is good. and i do hope you are using one for the lighter distros such as Lubuntu, Xubuntu with that ammount of ram. 
[/COLOR]

---

### Post by Larry_Klein on 2014-04-19
> **pfeiffep said:**
> Welcome to the forum @Larry_Klein!   
When I first tried Linux on my old Dell laptop only 512Mb main memory was installed. I had similar problems as you described. 

I upgraded the sysem's memory to the maximum that the hardware would support (2GB) for ~ $30. Now I'm running the latest OS that Ubuntu offers without problems!

Thanks for the info, but as this is just my shop computer, I am not interested in spending any $$ on it. 

Maybe the next PC I drag out of a dumpster will run linux.

---

### Post by Larry_Klein on 2014-04-19
> **mastablasta said:**
> run the mem test. linux and windwos xp use memory differently. 

furthermore the issue could also be [COLOR=#000000]/0/100/1e/0 display R200 [Radeon 8500/8500 LE] the GPU although the chip is supposed to be fully supported: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

sometimes the drivers do not load correctly. check the logs and troubleshoot in that area if memorry (RAM) is good. and i do hope you are using one for the lighter distros such as Lubuntu, Xubuntu with that ammount of ram. 
[/COLOR]

Lubuntu all the way. I have read about many problems with ati cards.

---

### Post by pfeiffep on 2014-04-19
@[COLOR=#000000]Larry_Klein  I completely understand not wanting to spend money .... try what @[/COLOR][COLOR=#000000]mastablasta suggested[/COLOR]
> [COLOR=#000000]*i do hope you are using one for the lighter distros such as Lubuntu, Xubuntu with that ammount of ram. *[/COLOR]
Good Luck

---

### Post by jdeca57 on 2014-04-19
> **Larry_Klein said:**
> Distros install and run beautifully for a couple hours before the total lockups start. 

That must be a hardware issue, since if it were software and compatibility those distributions wouldn't run 'beautifully' for some hours...

---

### Post by Larry_Klein on 2014-04-19
> **jdeca57 said:**
> That must be a hardware issue, since if it were software and compatibility those distributions wouldn't run 'beautifully' for some hours...

Would the size of the swap file cause these problems?

---

### Post by grahammechanical on 2014-04-19
> **Larry_Klein said:**
> Would the size of the swap file cause these problems?

I would think so. Are you installing Linux onto an NTFS formatted partition? Should we do that?

> [COLOR=#000000][COLOR=#000000]/0/1/0.0.0 /dev/sda disk 80GB ST380022A[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]/0/1/0.0.0/1 /dev/sda1 volume 74GiB Windows NTFS volume[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]/0/1/0.0.0/2 /dev/sda2 volume 510MiB Extended partition[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]/0/1/0.0.0/2/5 /dev/sda5 volume 510MiB Linux swap / Solaris partition[/COLOR][/COLOR]

Where is the Linux partition?

Regards.

---

### Post by jdeca57 on 2014-04-19
> **Larry_Klein said:**
> Would the size of the swap file cause these problems?
If I understand it correctly, you have an 510 MB swap. Of course swapping on 1024 or even 2048 won't hurt and you might try that.

---

### Post by Larry_Klein on 2014-04-19
> **grahammechanical said:**
> I would think so. Are you installing Linux onto an NTFS formatted partition? Should we do that?



Where is the Linux partition?

Regards.

I got the hardware info after i put xp back. I used the live lubuntu cd to get the info.

---

### Post by jdeca57 on 2014-04-19
> **Larry_Klein said:**
> I got the hardware info after i put xp back. I used the live lubuntu cd to get the info.
And do you have the same problem after a few hours with the live CD? Lubuntu should work just as well after installation on a hard disk unless after installation another video driver was selected. But that can be corrected. It's perfect that you can put the older OS back. That means you can experiment untill you find a solution. Unless the problem is hardware related, of course.

---

### Post by Larry_Klein on 2014-04-19
> **jdeca57 said:**
> And do you have the same problem after a few hours with the live CD? Lubuntu should work just as well after installation on a hard disk unless after installation another video driver was selected. But that can be corrected. It's perfect that you can put the older OS back. That means you can experiment untill you find a solution. Unless the problem is hardware related, of course.
 
Yes, the live cd - actually, I ran it a usb stick - froze eventually. 

I do run the update either when installing, or shortly there after. Is there some update file I should avoid? Or the best to use with my card?

I appreciate the help!

---

### Post by jdeca57 on 2014-04-19
> **Larry_Klein said:**
> Yes, the live cd - actually, I ran it a usb stick - froze eventually. 

I do run the update either when installing, or shortly there after. Is there some update file I should avoid? Or the best to use with my card?

I appreciate the help!

OK. Google is your friend and starting with
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)
I found the open source drivers:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

The R200 is fully supported, so that can be ruled out. Since you have the problem with an USB stick, it's not a problem with your hard disk. So it might still be memory related. Did you try increasing swap?

---

### Post by Larry_Klein on 2014-04-19
> **jdeca57 said:**
> OK. Google is your friend and starting with
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)
I found the open source drivers:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

The R200 is fully supported, so that can be ruled out. Since you have the problem with an USB stick, it's not a problem with your hard disk. So it might still be memory related. Did you try increasing swap?

I am running memtest now. I heard I should let it for many hours.

---

### Post by mayagrafix on 2014-04-19
I recommend you go into system set-up and first: set to factory  specs, and second, turn off additional features, (onboard LAN, onboard Audio, etc.) and leave as bare bones as possible. If PC stops freezing, you can now trouble shoot and add extra features one by one.

The older the laptop, the better Linux runs on it. I have one that came with Xp with 512 megs RAM that is great with LXDE. Granted, it ain&#8217;t no fireball, but it does what I want it to instead of serving as paper weight.

Good luck.

---

### Post by Navneet_Kumar on 2014-04-19
i suggest you to run requirement tests on RAM for lighter distros especially lubuntu...........:D

---

### Post by Larry_Klein on 2014-04-20
> **jdeca57 said:**
> OK. Google is your friend and starting with
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)
I found the open source drivers:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

The R200 is fully supported, so that can be ruled out. Since you have the problem with an USB stick, it's not a problem with your hard disk. So it might still be memory related. Did you try increasing swap?

[B]Could I have possibly fixed it !!??
[/B]
Memtest showed no errors. I reinstalled lubuntu 13.10 and was ok for about an hour before it froze. I had the preferred software window open and was moving it when it froze.

I am running the xfree video drivers.

When I restarted, I went in the bios and disabled the firewire - ( I don't use it ) and disabled plug and play.

I have been running firefox under wine playing a streaming full screen video for about a half hour - a sure freeze inducer, and have put it into suspend and woke up - another freezing problem.  

 Time will tell, and thanks for the help.

---

### Post by Larry_Klein on 2014-04-20
> **mayagrafix said:**
> I recommend you go into system set-up and first: set to factory  specs, and second, turn off additional features, (onboard LAN, onboard Audio, etc.) and leave as bare bones as possible. If PC stops freezing, you can now trouble shoot and add extra features one by one.

The older the laptop, the better Linux runs on it. I have one that came with Xp with 512 megs RAM that is great with LXDE. Granted, it ain’t no fireball, but it does what I want it to instead of serving as paper weight.

Good luck.

[B]Could I have possibly fixed it !!??
[/B]
Memtest showed no errors. I reinstalled lubuntu 13.10 and was ok for about an hour before it froze. I had the preferred software window open and was moving it when it froze.

I am running the xfree video drivers.

When I restarted, I went in the bios and disabled the firewire - ( I don't use it ) and disabled plug and play.

I have been running firefox under wine playing a streaming full screen video for about a half hour - a sure freeze inducer, and have put it into suspend and woke up - another freezing problem.  

 Time will tell, and thanks for the help.

---

### Post by verymadpip on 2014-04-20
Hi there Larry.

```
I have been running firefox under wine
```

Why are you doing this?
Is it a "stress test" kind of thing?
Firefox works natively in Lubuntu.

---

### Post by Larry_Klein on 2014-04-20
> **verymadpip said:**
> Hi there Larry.

```
I have been running firefox under wine
```

Why are you doing this?
Is it a "stress test" kind of thing?
Firefox works natively in Lubuntu.

Non sse2 processor - no flash in linux. Wine or old flashplayer versions are the only solution.

---

### Post by verymadpip on 2014-04-20
> **Larry_Klein said:**
> Non sse2 processor - no flash in linux. Wine or old flashplayer versions are the only solution.

Aha, okay.
My bad.
That's what I get for not reading up :D

---

### Post by Larry_Klein on 2014-04-20
I was wrong. Nothing's fixed and the freezing is back. Thanks for everyone's help, but I must give up on linux. I will keep the installation on the partition to visit, but I need something more reliable.

---

### Post by Larry_Klein on 2014-05-16
> **Larry_Klein said:**
> I was wrong. Nothing's fixed and the freezing is back. Thanks for everyone's help, but I must give up on linux. I will keep the installation on the partition to visit, but I need something more reliable.

Well, I tried again and all seems to be working.

I'll admit many of the problems were probably of my own making -  installing things that were not in the software center (themes,  utilities), doing stuff in the terminal that I got of the net, mostly to  try to get flash to work.

Now I have LXLE (ubuntu 12.04) installed and have gone over 24 hours  with no problems or reboots. It has everything I need, looks nice, and  with the qshutdown app I have suspended about 20 times with no problems -  a sure freeze previously.

Newbie advice-
If it is not in the software center - forget it.
For flash on old machines - search for flashplayer archives, download  (save) old version (11.102.62?). Use software center to uninstall  flashplayer, extract the old version, and copy and paste it into the  mozilla plugin folder. If you are as new as I was, post a request for  detailed instructions.

---

