---
title: "ubuntu did not work, xubuntu 12.04 will not instal, no disk message"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by yellowmans on 2013-03-17
hello all
i lost ubuntu when trying to update upgrade to newest version. i was adviced to instal xubuntu 12.04 i did, burned the iso for original 12.04 did not work, alternative 12.04 installs, then when done ejects disk, but will not load from hdd??!! 
message: no disk. error
no operating system and no real help from forums, check live disk for errors: ok; checked ram with memtest86+: ok.
is a fujitsu lifebook P2110. help anyone, pretty please.
im thinking of formating hdd

---

### Post by sully101 on 2013-03-17
Is the bios set to boot from the hard disk or cd?

---

### Post by yellowmans on 2013-03-18
the bios is set up to boot from hdd, this has happened the 3 or 4 times i tried to install it. im just reading about debian. im guessing i will have to install that first, and follow instructions from there to install it again. thanks

---

### Post by pqwoerituytrueiwoq on 2013-03-18
i would suggest xubuntu 13.04 beta over xubuntu 12.04 any day
that said i would suggest lubuntu, that is one really weak system

probably should burn a cd and boot, you may be able to usb boot if you are lucky
use the boot menu to select a drive to boot

---

### Post by fantab on 2013-03-18
> **yellowmans said:**
> hello all
i lost ubuntu when trying to update upgrade to newest version. i was adviced to instal xubuntu 12.04 i did, burned the iso for original 12.04 did not work, alternative 12.04 installs, then when done ejects disk, but will not load from hdd??!! 
message: no disk. error
no operating system and no real help from forums, check live disk for errors: ok; checked ram with memtest86+: ok.
is a fujitsu lifebook P2110. help anyone, pretty please.
im thinking of formating hdd

Give us more specs about your "lifebook", especailly RAM and Graphics, cpu etc...
Was your HDD ever part of any RAID?
Do you dual boot with Windows or anything else?
Can you boot from Xubuntu LiveCD/USB (regular not Alternate) and "Try Xubuntu", does it take you to a live working desktop?


If you can successfully boot to a Live desktop then you can find a utility called "DISKS", you can use it and run SMART check on your HDD... see what it shows and report back.

---

### Post by mastablasta on 2013-03-18
> **yellowmans said:**
> no operating system and no real help from forums, check live disk for errors: ok; checked ram with memtest86+: ok.



check downloaded file for errors ? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

check hard disk for errors ?

Note: even if hard disk has errors you should be able to boot into live OS (aka select try it and boot to it ) to do further diagnostics (as suggested). as long as the burned image is good.

---

### Post by yellowmans on 2013-03-18
hey [**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("http://ubuntuforums.org/member.php?u=865458")
[COLOR=#000000][/COLOR]well it is an old notebook, therefore i was advise to install something lite like 12.04 but ubuntu game the same problem, it will run from the disk but not from the hdd. i tried xubuntu original same problem, finaly the xubuntu 12.04 alternate appears as installed but like i said after installation ejects disk, and says error no disk. i will post specs of my oldie thanks

---

### Post by yellowmans on 2013-03-18
hello these are the specs from the ubuntu resources

[LIST]
[*]Processor: 867MHz Crusoe TM5800 processor
[*]RAM: 256Mb, upgradable to 384 (reports of 512Mb RAM upgrade possible)
[*]10.6" wide-format SXGA TFT display, 1280x768
[*]Video Card: ATI Rage Mobility-M1 8MB video RAM
[*]Storage: 20Gb hard drive
[*]Optical Drive: DVD/CD-RW combo drive (8x DVD/16X CD-R/24X CD)
[*]Floppy: External USB Floppy disk drive
[*]Audio: Sigma Tel AC 9757T 16bit
[*]Built-in ports: 56K Modem, 10/100 RealTek RTL8139, headphones, mic, line out, IEEE 1394, 2 USB ports, Mini-VGA, S-Video, Type I or Type II CardBus slot, optional internal 802.11b
[*]Dimensions: 10.6"(w) x 7"(d) x 1.59"(h)
[*]Weight: 3.5lbs
[/LIST]
1) it has 512 of ram now. 2) i dont know about RAID, im pretty new in ubuntu. 3)it had windows xp, then also ubuntu 10.11? when i tried to update to recomended ubuntu updates (im guessing 12.something) it crashed. cannot load anything now. 4) im gonna look for the ubuntu 12.04 disk, im pretty sure it loaded from disk. thank you. do you think i should format all hdd?

---

### Post by yellowmans on 2013-03-18
hello [COLOR=#000000][B]mastablasta
i did check for errors in the xubuntu 12.04. disk was ok, ram was ok and live cd was ok also. xubuntu 12.04 does not give me an option to run it from the live cd only to install it check for errors. thanks[/B][/COLOR]

---

### Post by yellowmans on 2013-03-18
hello FANTAB
xubuntu alternate 12.04 does not give me an option to run from disk, only install, check for errors, run from hdd.
i boot from hdd and get this
booting from local disk
error: oout of disk
grub rescue>

---

### Post by mörgæs on 2013-03-18
Your best option is a [minimal Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") , if you want to use the computer at all.

---

### Post by fantab on 2013-03-18
You have only 256MB of RAM, which means you have to use 'Alternate install method' from CD/DVD/USB.

Both XFCE (xubuntu) and LXDE ([Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")) are light weight, but LXDE is recommended for your machine specs as it is relatively lighter than XFCE.
You say you have only 20GB HDD, in that case you have to partition it, for instance:

19GB - Primary - EXT4 - / (root)
1GB - Linux SWAP

Without SWAP you will have memory issues... 1GB is minimum, if you can, then make it 2GB.
Delete your existing partitons, recreate them accordingly and format as ext4. When you install GRUB install it on /dev/sda and not in a partition like /dev/sda1.

Good Luck...

---

### Post by verymadpip on 2013-03-18
Hi there.

I'd be super tempted to try a minimal install plus bits & pieces eg: file manager, window manager & panel.
That's how I revived a Compaq TC1000 tablet PC, which also uses a Crusoe (1000MHz) CPU & not enough RAM :D

---

### Post by sully101 on 2013-03-18
@fantab +1

---

### Post by yellowmans on 2013-03-19
hello moarges
of course i want to use the computer. it had windows, then ubuntu 11.10, then i tried ubuntu 12.04 and xubuntu 12.04 and finally xubuntu 12.04 alteranate. this seems to install but like at said not really. is lubuntu the "lightest"

---

### Post by yellowmans on 2013-03-19
hey fantab
please bare with me. im a rockie. ok when memtest86+ checked for errors i noticed it said 512MB ram so maybe it was upgraded. i did tried the alternate install disk, once the original xubuntu 12.04 did not work. i will get an lubuntu iso and try it. since i am an absolute beginer i do not know how to partition. if you would be so kind.. please explain. i will research how to partition.
when i tried to install again it aske me about grub and gives me options
/dev/sda1
/dev/sda2...
again i dont know how to delete existing partitions :) but i will continue to reseach, thanks so much, any other info will be greatly appreciated

---

### Post by yellowmans on 2013-03-19
hello verymadpip
hey im willing to do that. but dont know how. how can i go about it?

---

### Post by mörgæs on 2013-03-19
Too much advice is being given in this thread. 

Yellowmans, you need one test: 

Burn the minimal 12.10 ISO from my link to a CD. It should be around 20 MB of size.
Install using wired internet connection. 
Erase everything on the drive in the process.
Accept the default partition suggestion.

The aim is to get a command-line system running where you can do **login** and **shutdown**, nothing more. 
Please report back when you have tried this, then we go to next step.

---

### Post by yellowmans on 2013-03-19
hello moarges
thank you for your reply i will follow your advice. i will burn the cd, and use a wired contection altough the laptop detects and uses the wireles contection previously during instalation. mm i think everything has been erased during instalation previously. i will accept the default sugestions. you are correct i get the grub rescue> comand line but cannot boot or shut down. i press ctr+alt+dlte to restart. i will report later on today, i thank you for your help.

---

### Post by yellowmans on 2013-03-20
hello moarges
i have another problem, i should start another thread. i created a new partition (i think). xubuntu 12.04 was reinstalled and this time when the laptop start i have 8 options 2 memtest86 one of them recovery, 3 ubuntus 12.04 and 3 ubuntu 12.04 recovery mode. i tried the first one and could barely see the screen so restarted. one of them let me load xubuntu 12.04 (i believe) i get the blue screen with bird, the cursor but mouse does not work?

---

### Post by mörgæs on 2013-03-20
I can't add anything besides what's written in #18. I believe you are on the wrong track, loading too heavy a system on very modest hardware. Also I see no point in sticking to 12.04 when this release has never worked well for you.

Leaving the thread for now but maybe others have a suggestion.

---

### Post by fantab on 2013-03-20
Forget everything you have done until now.

Download and burn: [Gparted LiveCD/USB]("http://gparted.sourceforge.net/livecd.php"). 
Boot with it and **delete ALL Partitions** on your Hard Disk. 

Create: 
2GB SWAP Partition 
18GB format as EXT4 (during lubuntu install you will use this as "/").

Download and Burn: [**Lubuntu Minimal CD/USB**]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") and READ CAREFULLY everything that is written at the link.
Follow the instructions CAREFULLY.

Good Luck.

---

