---
title: "[SOLVED] DISK BOOT FAILURE Error or GRUB Error 21 upon boot."
date: 2008-09-01
forum: New to Ubuntu
---

### Post by Iwneferi on 2008-09-01
I decided that I wanted to use Linux and so, undaunted by my complete lack of knowledge, I decided upon ubuntu and immediately installed it on my computer. Because of my lack of knowledge I immediately screwed up everything. 

 With dual-monitors, three IDE hard drives, and a wireless network connection to work out, I likely have a long road ahead of me. A daunting task to be sure but, to be honest, I am a little bit surprised by my unconcerned attitude about the whole thing. For some unknown reason, I have faith that the community will help me out.

Lets start at the beginning shall we? I installed ubuntu on the smallest of my three IDE hard drives (80Gig). The installation seemed to go just fine, but after it was done, my computer wouldn't work--that is--ubuntu won't load. It gives me one of two errors depending on it's mood. 
Either: 
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

Or:
GRUB Loading, please wait...


Error 21

I'm not sure if it's a problem with BIOS, or a hardware problem, or an ubuntu problem. Lol, I guess I really don't know much of anything. Will someone please set me in the right direction? I am not desperate, but the sooner I could get my computer up and running the better. Thanks in advance for the help!

---

### Post by jemate18 on 2008-09-01
> **Iwneferi said:**
> I decided that I wanted to use Linux and so, undaunted by my complete lack of knowledge, I decided upon ubuntu and immediately installed it on my computer. Because of my lack of knowledge I immediately screwed up everything. 

 With dual-monitors, three IDE hard drives, and a wireless network connection to work out, I likely have a long road ahead of me. A daunting task to be sure but, to be honest, I am a little bit surprised by my unconcerned attitude about the whole thing. For some unknown reason, I have faith that the community will help me out.

Lets start at the beginning shall we? I installed ubuntu on the smallest of my three IDE hard drives (80Gig). The installation seemed to go just fine, but after it was done, my computer wouldn't work--that is--ubuntu won't load. It gives me one of two errors depending on it's mood. 
Either: 
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

Or:
GRUB Loading, please wait...


Error 21

I'm not sure if it's a problem with BIOS, or a hardware problem, or an ubuntu problem. Lol, I guess I really don't know much of anything. Will someone please set me in the right direction? I am not desperate, but the sooner I could get my computer up and running the better. Thanks in advance for the help!

Didn't you encounter any error message on the installation process?

Did you verify your installation CD for errors? before installing check if your installer has no errors before proceeding in the installation process

---

### Post by jemate18 on 2008-09-01
You can also check this out
> [http://ubuntuforums.org/showthread.php?t=59719](http://ubuntuforums.org/showthread.php?t=59719)

---

### Post by egalvan on 2008-09-01
As long as the drive is bootable, grub does not care which drive it is on. Master, slave, it's all the same to grub.

"All you ever wanted to know about grub"

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)


One of your drives may be going dead.

Your BIOS may be set incorrectly.

Your drives may be set incorrectly. Check the jumpers.
Not all cables will work with all drives,
 "cable select" does not always work well.

---

### Post by egalvan on 2008-09-01
Further from Herman's zone

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

A lot to read, but very informative.

---

### Post by xeth_delta on 2008-09-01
> **Iwneferi said:**
> DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER


To me that looks like the BIOS can't locate the boot sector of the HDD which has GRUB. If you know precisely on which one of the three drives you installed it, set it in the BIOS as the immediate second option to boot, after the CDROM.

Error 21, by the other hand might have something to do with the fact that grub cannot find the selected OS partition. But this later. You should first make sure that your computer is consistenly booting into GRUB.

---

### Post by egalvan on 2008-09-01
> **Iwneferi said:**
> . It gives me one of two errors depending on it's mood.
Either:
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

Or:
GRUB Loading, please wait...

Error 21



The fact that the error changes points to a hardware problem.
Still sounds like a bad drive (to me)
[B]
DISK BOOT FAILURE[/B] means the **BIOS CANNOT BOOT** from the boot drive.

**Error 21** means that the **BIOS BOOTED** from the boot drive, but grub  can't find the second part of itself.

---

### Post by Iwneferi on 2008-09-02
> **egalvan said:**
> The fact that the error changes points to a hardware problem.
Still sounds like a bad drive (to me)
[B]
DISK BOOT FAILURE[/B] means the **BIOS CANNOT BOOT** from the boot drive.

**Error 21** means that the **BIOS BOOTED** from the boot drive, but grub  can't find the second part of itself.

Yea, it could be a bad drive. In one of the links you posted, Inferno3000 said: > 2) A problem with the wiring of the harddisks might give an error like this (usually when you have more than 2 harddisks)
2a) GRUB only works if you install it on a master/slave of the same sort... Meaning that if you have a harddisk HD0 (Windows installation harddisk, or c:\ to speak in windows terms), a HD1 (let's call it d:\) and a HD"2" (e:\), and HD0 + HD1 being the respectively primary master and primary slave, it isn't possible to install Ubuntu on a secondary master or slave (HD"2").
My solution was to rewire the harddrives, making HD3 the slave of HD1 and HD2 the secondary slave of the CDrom drive (might change that in the future... But for the time being this is my solution).
Make sure you set the jumpers correctly.

I'd like to make sure that my hardware is put in correctly and that my jumpers are set correctly. Currently the physical layout is as such: I have one IDE cable going to the 80gig hard drive (which should have ubuntu installed on it) set as Master, which then goes to my DVD ROM, which is set as cable select. (didn't notice that before) And the other IDE cable goes to a 400gig hard drive and then to a 150gig hard drive. I'm a little bit confused about the pinouts for master and slave for these. They are the same brand and the pinouts are the same, but have tons of options not quite as simple. I think they are both set to device1 slave.

How incorrect is this layout? Should I change anything, and if so, what??

---

### Post by wolfen69 on 2008-09-02
did you check the drive boot order in the BIOS?

---

### Post by aimpau on 2008-09-02
1. Check your jumpers. Just to be sure, your boot drive should be the PRIMARY master.
2. The second one obviously is the primary slave.
3. Since you have a 3rd IDE, make that as the SECONDARY master.
4. The CD/DVDROM should be either separate or as a SECONDARY slave.
5. Again, all of them have jumpers, check.

---

### Post by Gone fishing on 2008-09-02
It could also be that Ubuntu is confused about which HD is the primary HD and grub has been installed on the wrong HD. This can easily happen if you have both IDE and SATA drives.

I'd disconnect the other 2 HDs and reinstall on the primary HD then when its all working ad the other HDs. 

Possibly first check the Ubuntu is on the first boot device it could be on the second in which case you'll get a no OS error or if BIOs does find grub by finding the next bootable device you'll get a grub error as grub expects Ubuntu to be on a partition of the first boot device.

---

### Post by egalvan on 2008-09-02
> **Iwneferi said:**
> Yea, it could be a bad drive. In one of the links you posted, Inferno3000 said: 

I'd like to make sure that my hardware is put in correctly and that my jumpers are set correctly. Currently the physical layout is as such: I have one IDE cable going to the 80gig hard drive (which should have ubuntu installed on it) set as Master, which then goes to my DVD ROM, which is set as cable select. (didn't notice that before) And the other IDE cable goes to a 400gig hard drive and then to a 150gig hard drive. I'm a little bit confused about the pinouts for master and slave for these. They are the same brand and the pinouts are the same, but have tons of options not quite as simple. I think they are both set to device1 slave.

How incorrect is this layout? Should I change anything, and if so, what??

Again,
***as long as the drive is bootable, grub does not care which drive it is on. Master, slave, it's all the same to grub.***

next,
cable and jumper layout are a little funky...
your DVD-ROM should be set as 'slave'

next,
your second and third drive (on the second cable) should also be set as 'master' and 'slave'. 'Cable select' is not always reliable, as not all cables support this (and some mobo's are also non-compliant)

Next, are your cables 40-wire or 80-wire?
Notice I ask about "wire" not "pin".
all ide cables are 40-pin, 
not all are 80-wire.

80-wire is NEEDED for proper functioning of ATA-3 (ATA-2?)or above.
your 80g may or may not need 80-wire, but all the rest definitley do, 
so it's best to have both cables be 80-wire.

Next,
Unless you have an older BIOS which has a size-limitation,
 the second and third drives should use the simplest settings for master/slave.
 The more complex ones are usually used to size-limit the drive.
This is not needed for Linux, except for the boot drive.

ErnestG

---

### Post by egalvan on 2008-09-02
But I still lean towards hard drive failure :)

I'll be back Wednesday afternoon,

gotta go do my shift at the firehouse.

lotsa luck with this.

But at least you have an excellent attitude about it all! :lolflag:

ErnestG

---

### Post by egalvan on 2008-09-02
> **Gone fishing said:**
> It could also be that Ubuntu is confused about which HD is the primary HD and grub has been installed on the wrong HD. This can easily happen if you have both IDE and SATA drives.

I'd disconnect the other 2 HDs and reinstall on the primary HD then when its all working ad the other HDs. 

Possibly first check the Ubuntu is on the first boot device it could be on the second in which case you'll get a no OS error or if BIOs does find grub by finding the next bootable device you'll get a grub error as grub expects Ubuntu to be on a partition of the first boot device.

I missed this the first time around...

The OP didn't state that he had SATA, only three IDE.
And grub doesn't get confused., only us mere mortals :)


grub doesn't care which drive it's on, or which partition,
it happily plays anywhere.
And grub doesn't care where Ubuntu is, as long as it's told the location (or can find it itself) [-X

and yes, i've done moved grub around alot. and booted from first, second, third, fourth, and higher (SCSI, you know ;))

And as for leaving the first drive alone, if the drive is bad, this won't solve the problem, but will help to isolate the drive to prove it's bad. And being only 80g in size, I would guess it's getting on in years. :-s
and if the drive is not bad, re-connecting the second and third drive without solving the jumper problem will not help.
A slight variation on his advice...
Make sure of the jumpers by connecting each drive by itself, one at a time, seeing what the BIOS says about it. This may take a while as you have to shut down AND DISCONNECT the power supply each time, but it will remove any uncertainty about what the BIOS sees.

Possibly posting the make and model of the equipment involved may help us to better help you.

---

### Post by Gone fishing on 2008-09-02
Agree grub doesn't care where it goes, my grub is on the second partition of my second disk. I use a bootloader program.

However, I have had the situation where the Ubuntu install CD assumed my IDE drive was the first boot device when in fact my SATA drive was the boot device so obviously it didn't boot. Also it then writes into grub wrong entries as to where root is say hd1,0 rather than hd0,0.

Obviously its not grub getting confused but the install routine thats writing grub

---

### Post by Iwneferi on 2008-09-03
Okay, I changed all of the jumpers and now bios sees all of my IDE devices. (it didn't before) Yay!! But now I am getting GRUB Error 17.

The two newer harddrives are both Hitachi Deskstar brand and they are on an 80 wire cable. The old 80gig and DVD ROM are on a 40 wire cable. I might be able to dig up another 80 wire cable if you think it's worth my while. 

I have another 80gig HD someone gave me, but I have no idea what condition it's in. The only reason that I don't use one of the other harddrives is that they both have data that is very valuable to me and I don't want to lose it.

:-\ So what do you suggest I do next??

Your humble servant,
~William~

---

### Post by Iwneferi on 2008-09-04
Okay, so I decided to put in the newer 80gig HD. When I was installing Ubuntu (again) I noticed that ubuntu seems to think that all of my harddrives are SCSI--they are just IDE--which made me think that that may have been the problem all along.

Then I reread Inferno3000's "GRUB MADNESS!" Which I think says to put the DVD ROM as master to one of the larger drives, and the 80gig as master of the other large drive. With the OS on the 80gig. But now we're talking about rearranging everything again and this concerns me.

Will someone please give me another opinion before I do something truly stupid?!

---

### Post by Gone fishing on 2008-09-04
I install grub on the root partition not on the mbr and use GAG boot loader gag.sourceforge.net this is very easy to configure (all graphical) and has features such a allowing you to exchange boot drives. I'd give it a try.

I'm sure the problem was the install getting mixed up with which drives were which. If you fix grub or reinstall putting grub on the root partition and using GAG things will go well.

---

### Post by caljohnsmith on 2008-09-04
> **Iwneferi said:**
> Okay, so I decided to put in the newer 80gig HD. When I was installing Ubuntu (again) I noticed that ubuntu seems to think that all of my harddrives are SCSI--they are just IDE--which made me think that that may have been the problem all along.

Then I reread Inferno3000's "GRUB MADNESS!" Which I think says to put the DVD ROM as master to one of the larger drives, and the 80gig as master of the other large drive. With the OS on the 80gig. But now we're talking about rearranging everything again and this concerns me.

Will someone please give me another opinion before I do something truly stupid?!
I don't know which HDD corresponds to master/slave or is external, but the bottom line is:
[LIST]
[*]If you are always going to have all the HDDs connected to your computer and in the boot order they are currently set up for in BIOS, just install Ubuntu wherever you want (any HDD), and Grub will automatically install itself to the master boot record (MBR) of your boot HDD (hd0). Everything should work great, unless you change something in the future with the set up of all your HDDs.
[*]If you want to have the option to disconnect a HDD and not have problems booting, then you'll need to give us more information on all your HDDs and what OSes are on each of them, and also which HDD you want to boot from. Then we can help you come up with a viable plan.
[/LIST]
Also, in all likelihood, Grub can easily handle all your booting needs; you don't need to use GAG or another boot loader unless you want to. Let me know if you need more info/details.

---

### Post by Iwneferi on 2008-09-04
> **caljohnsmith said:**
> I don't know which HDD corresponds to master/slave or is external, but the bottom line is:
[LIST]
[*]If you are always going to have all the HDDs connected to your computer and in the boot order they are currently set up for in BIOS, just install Ubuntu wherever you want (any HDD), and Grub will automatically install itself to the master boot record (MBR) of your boot HDD (hd0). Everything should work great, unless you change something in the future with the set up of all your HDDs.
[*]If you want to have the option to disconnect a HDD and not have problems booting, then you'll need to give us more information on all your HDDs and what OSes are on each of them, and also which HDD you want to boot from. Then we can help you come up with a viable plan.
[/LIST]
Also, in all likelihood, Grub can easily handle all your booting needs; you don't need to use GAG or another boot loader unless you want to. Let me know if you need more info/details.

I already tried that and got Error 21 and then, after changing the pinouts, got Error 17. I am going to put my computer back together like so, if that doesn't work than I'll try the GAG thing or super GRUB. 

This is what I am hoping to accomplish:

IDE 1= 80gig (HD0) Master w/OS
       DVD (CD1 maybe?) Slave

IDE 2= 400gig (HD1) Master
       250gig (HD2) Slave

And if that doesn't work than I will probably resort to explosives. :)Surely that'll fix it.

I will be working on this for the next little while and will be looking for new posts. Thanks everyone.

---

### Post by Iwneferi on 2008-09-04
I have defeated the dastardly grub errors. Yay!! Only there seems to be several new problems to contend with. I expected this, but it grows tiresome all the same. 

**Ubuntu isn't detecting my USB wireless network device.

**Although it can see them, Ubuntu cannot mount my larger two harddrives.

Any ideas??

---

### Post by Gone fishing on 2008-09-05
Just curious to know how you solved the grub problem?

As for the wireless I always buy Gigabyte realtek wireless cards both USB and PCI just work out of the box (and there cheap and easy to get in South Africa).

I'm supprised that Ubuntu can't mount the partitions on the other drives - what are they? On my system it automatically mounts extra NTFS and ext3 partitions.

---

### Post by Iwneferi on 2008-09-05
> **Gone fishing said:**
> Just curious to know how you solved the grub problem?

As for the wireless I always buy Gigabyte realtek wireless cards both USB and PCI just work out of the box (and there cheap and easy to get in South Africa).

I'm supprised that Ubuntu can't mount the partitions on the other drives - what are they? On my system it automatically mounts extra NTFS and ext3 partitions.

I just rewired all of my drives. I switched IDE1 and IDE2 and replaced the 40wire IDE with an 80wire cable. I also used an unused harddrive to install Ubuntu on just in case the previous one was bad. Voila!

I'm having a devil of a time getting anything to work without the Internet. I just bought a USB drive to move files from my laptop to my PC but apparently Ubuntu can't mount that either. Grrr. WTF am I supposed to do now??

---

### Post by Gone fishing on 2008-09-05
I suppose the easiest way would be a crossover cable between the PC and the laptop you could also get internet via the laptop that way.

But again I'm surprised I've never had a usb memory stick not work with ubuntu

---

### Post by Iwneferi on 2008-09-05
> **Gone fishing said:**
> I suppose the easiest way would be a crossover cable between the PC and the laptop you could also get internet via the laptop that way.

But again I'm surprised I've never had a usb memory stick not work with ubuntu

LoL, :)Unfortunately I get that a lot. My friends tell me I am an electromechanical vampire, that I suck the life out of machinery and electronics. 

I think I have a crossover cable... I'll try to find and use it in a little bit. Wish me luck.

---

### Post by egalvan on 2008-09-06
> **Gone fishing said:**
> But again I'm surprised I've never had a usb memory stick not work with ubuntu


:) Agreed, I've never had Ubuntu (old or new) not see a USB memory stick..

but the OP was talking about a USB wireless device, which Ubuntu 7.10 and older were notorious for not liking.

Can't state about 8.04, 'cause I got rid of my USB wireliess.


Anybody else with experience in this?

---

### Post by Iwneferi on 2008-09-07
Okay, according to [Ubuntu Documentation]("https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html") I need to install NDISWrapper, which will allow me to use a windows driver (for wireless devices) in Ubuntu. The problem is that when I try to install it, Ubuntu tells me that I need an Internet connection to install. WTF?? So, I downloaded the installation file from sourceforge and put it on a USB drive.

**I Ubuntu could read the USB drive, but couldn't mount it. *Shrug* Apparently I just needed to reboot, because the USB drive worked just fine after restarting my computer the next time.**

I guess I just don't know how to use Ubuntu though, because I have access to the file and don't have any idea what to do with it. 

How do I make Ubuntu install from the USB drive? Does anybody know??

---

### Post by Iwneferi on 2008-09-07
I finally decided to just cut all of the zip-ties holding my computer cables and move the computer to the router. I was able to install everything I needed and got the Internet working. Only again, weird problems. When I got the computer put back together at my desk and started it up again, the Internet wouldn't work. Everything seems to be ok, but I can't get my wireless connection to work. 

I've had enough for tonight. As always, any suggestions are more than welcome.

P.S. It is a crappy USB linksys network adapter, but note that it was working at this desk before I installed ubuntu.

---

### Post by Gone fishing on 2008-09-07
The command ifconfig will give you information about your connection such as if your card has an IP addresss.

I'd try that and see can you ping the router?

---

### Post by Iwneferi on 2008-09-08
I finally bought a new network adapter (belkin USB). I am having more success, but still no Internet. I can ping the router and I have an ip address, but I can't ping [www.ubuntu.com](www.ubuntu.com) and I can't browse the Internet.

I am also still needing to get my extra two harddrives to work. When I click on them Ubuntu says that it can't mount them. It does see them fine though. Ideas anyone??

---

### Post by Iwneferi on 2008-09-09
Well I did fix the grub problem by rewiring and redoing my hard drive pinouts, so I guess I'll tackle all of my other problems in new threads.

Thanks everyone!

---

