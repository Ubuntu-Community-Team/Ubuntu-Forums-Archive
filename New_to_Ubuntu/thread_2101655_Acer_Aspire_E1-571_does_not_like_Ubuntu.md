---
title: "Acer Aspire E1-571 does not like Ubuntu?"
date: 2013-01-05
forum: New to Ubuntu
---

### Post by Oubountourette on 2013-01-05
I have a Acer Aspire E1-571 and try to install Ubuntu as dual boot. [LIST]
[*]It is not booting from the DVD. The BIOS has a boot from ATAPI CD-ROM choice, but bringing that choice to the top of the boot order menu does not allow booting from the DVD. I have turned off security boot for UEFI (option in BIOS), but still does not boot from DVD. In other words, swapping the Win8 hard drive for an empty 320Gb hard drive and inserting a LiveCD for Ubuntu into the the DVD will not boot from the DVD. 
[*]I also tryed to boot off a USB stick. It fails as well.
[*]I tried also to install Ubuntu on an other (empty) partition. It works well until I have to restart: start with windows 8 or with ubuntu ("windows cannnot be startet.... is missing") 
[*]Leaving the Win8 hard drive in the Acer and trying to install Ubuntu from wubi.exe off a DVD will result in a failed dual boot installation.
[*]Start with a mini CD ROM (for network installation) failed[/LIST]
Is there no way to install Ubuntu on a Aspire E1-571 with i3-2328M?

---

### Post by ActionpackedPIVII on 2013-01-05
hmm.. Is it even trying to boot from the DVD/USB drive? or does it just go straight to the harddrive?

---

### Post by arpanaut on 2013-01-05
This should get you started:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Oubountourette on 2013-01-06
I created different (nine) entries to start with Easy BCD to start with DVD, USB or another (not Windows) Partition, I tried also to install with Wubi.
[LIST]
[*]If I will start with the LiveUSB, Screen is blinking black/Acer-Logo until I retire the stick (I waited for more then 30 min) The USB stick was made with LinuxLive USB Creator
[*]In all other cases (with GRUB2, CD, pre-installed or iso file), an error page appears that tells me, that *Windows* could not be startet (I wanted Ubuntu, not Windows), while a file is missing. See below.
[/LIST]File: \NST\AutoNeoGrub1.mbr (the number is 1-8)
Status: 0xc000000f
 
File:\ubuntu\winboot\wubildr.mbr
Status: 0xc000007b
 
Is there someone that installed Ubuntu successfull on a Acer Apsire E1?

---

### Post by Calinou on 2013-01-06
EasyBCD doesn't work with UEFI.

---

### Post by Oubountourette on 2013-01-06
> **Calinou said:**
> EasyBCD doesn't work with UEFI.
 
I am sorry, I did not mention that I use the new Version EasyBCD 2.2 that [LEFT][COLOR=#333333]supports Windows 8, the latest GRUB2 distributions and EFI machines. So at least *this* should work.[/COLOR][/LEFT]

---

### Post by Oubountourette on 2013-01-06
> **arpanaut said:**
> This should get you started:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
 That is was I did. And at one Point I have to restart to finish Installation of Ubuntu. Then I can choose Ubuntu or Windows. When I choose Ubuntu, Comes th black error Screen that cannot find a file to start Windows?!
 
(Sorry for hazardous capitalisation; Windows 8 changes this against what I write.)

---

### Post by Oubountourette on 2013-01-06
> **ActionpackedPIVII said:**
> hmm.. Is it even trying to boot from the DVD/USB drive? or does it just go straight to the harddrive?
 As I wrote below, it does not start with CD or USB stick. 
[LIST]
[*]With CD, it Comes to a Screen where I can use Windows or Ubuntu, but when I click Ubuntu, a black Screen tells me, that Windows cannot been startet, because a file is missing.
[*]With USB, Screen is blinking black/Acer-Logo until I retire the Stick (I waited for >30min before doing this).
[/LIST] 
 
(Hazardous capitalisation made by Windows 8)

---

### Post by Oubountourette on 2013-01-06
In this tread (1) in italian language, the same Problem is / was discussed. People there think, that there is no way to install a dual boot when **Windows 8** is the other one. Following the source (2), it could be a Problem with secure boot in UEFI. I do not speak well italian, but it seems, that a new Version of Ubuntu will be released in january that **Secure Boot** should no longer be an insurmountable Problem? 
 
Can someone confirm this Information or are there Laptops with pre installed Windows 8 and dual boot for Ubuntu?
 
 
 
 
(1) [http://www.istitutomajorana.it/forum/Thread-Win-8-Edubuntu-HELP](http://www.istitutomajorana.it/forum/Thread-Win-8-Edubuntu-HELP)
(2) [http://www.ossblog.it/post/16957/canonical-e-tornata-a-proporre-grub2-per-ubuntu-12-10-col-secure-boot](http://www.ossblog.it/post/16957/canonical-e-tornata-a-proporre-grub2-per-ubuntu-12-10-col-secure-boot)

---

### Post by Oubountourette on 2013-01-07
> **Oubountourette said:**
> it seems, that a new Version of Ubuntu will be released in january that **Secure Boot** should no longer be an insurmountable Problem? 
 
Following an article from Christmass (1) and a blog entry from Canonical (2), *new* *Versions* from Ubuntu will have another boot loader, that **dual boot** with **Windows 8** and **Secure boot** will be possible. 
 
New Ubuntu 12.04.2 is expected for january 31, 2013.(3) So I have to wait or to go a complicated way as f.ex. described in (4).
 
(1) [http://www.techspot.com/news/50271-ubuntu-to-continue-using-grub-2-with-windows-8-secure-boot.html](http://www.techspot.com/news/50271-ubuntu-to-continue-using-grub-2-with-windows-8-secure-boot.html)
(2) [http://blog.canonical.com/2012/09/20/quetzal-is-taking-flight-update-on-ubuntu-secure-boot-plans/](http://blog.canonical.com/2012/09/20/quetzal-is-taking-flight-update-on-ubuntu-secure-boot-plans/)
(3) [https://launchpad.net/ubuntu/+milestone/ubuntu-12.04.2](https://launchpad.net/ubuntu/+milestone/ubuntu-12.04.2)
(4) [http://ubuntuforums.org/showthread.php?t=2098914](http://ubuntuforums.org/showthread.php?t=2098914)

---

### Post by mysteriousdarren on 2013-01-10
Disable UEFI? Enabled it will not boot.

---

### Post by amoun on 2013-01-26
I know it says solved but didn't see the solution.

It worked for me by enabling legacy support in bios mode

---

### Post by AcerSpades on 2013-01-27
I've just got an Acer Aspire E1-571...

Bit of a newbie... couldn't get it to boot from USB or DVD.  HELP!

---

### Post by Oubountourette on 2013-01-29
> **amoun said:**
> I know it says solved but didn't see the solution.

It worked for me by enabling legacy support in bios mode
At me it starts not at all, if I change the bios mode :-(
The «until now» solution is in #10 on the first page: a complicated way (see linkt here) or an easyer way with [12.04.2]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule"), expected for February 14th ([instead]("http://www.phoronix.com/scan.php?page=news_item&px=MTI3MjY") of end of January).

---

### Post by Oubountourette on 2013-02-19
Well, new LTS Version 12.04.2 and Version 12.10 are now available. What I did and what happend:
- turn UEFI off and start with USB key with **Ubuntu (12.04.2 and 12.10)**, created with LinuxLiveKey. Aspire E1 starts well, but after choosing language and time Zone, troubel starts and all gets frozen (I tried about two times with each).
- turn UEFI off and start with USB key with **Xubuntu**, created with LinuxLiveKey. Aspire E1 starts well, and I can install it, but Installation never end.
- turn UEFI off and start with USB key with **Lubuntu**, created with LinuxLiveKey. Aspire E1 starts well, and I can install it with no porblem, but then, I cannot restart without the USB stick, because Lubuntu is not UEFI compatible. For this, I have to wait for the Version 13.x in April....

---

### Post by porthuon on 2013-03-18
> **Oubountourette said:**
> Well, new LTS Version 12.04.2 and Version 12.10 are now available. What I did and what happend:
- turn UEFI off and start with USB key with **Ubuntu (12.04.2 and 12.10)**, created with LinuxLiveKey. Aspire E1 starts well, but after choosing language and time Zone, troubel starts and all gets frozen (I tried about two times with each).
- turn UEFI off and start with USB key with **Xubuntu**, created with LinuxLiveKey. Aspire E1 starts well, and I can install it, but Installation never end.
- turn UEFI off and start with USB key with **Lubuntu**, created with LinuxLiveKey. Aspire E1 starts well, and I can install it with no porblem, but then, I cannot restart without the USB stick, because Lubuntu is not UEFI compatible. For this, I have to wait for the Version 13.x in April....

I was looking to get one if these laptops for dual booting or if that isn't possible, then just installing Ubuntu by itself.
I take it from you post  that you still can't install Ubuntu on the E1-571?

Regards
Geoff

---

### Post by Repuran on 2013-03-18
Same for me, I have been searching for laptops and this seems the best value for money but if it can't install Ubuntu then I will have to carry on searching :[

---

### Post by porthuon on 2013-03-18
A re-read of this thread seems to refer to a dual boot issue. Will Ubuntu install standalone on this laptop?
While dual boot might be useful, I've lived Linux only for quite a while so the loss of Windows doesn't worry me too much.

---

### Post by dnewman4952 on 2013-03-18
Im running Linux Mint 14 standalone on mine and everything works well.

---

### Post by porthuon on 2013-03-18
> **dnewman4952 said:**
> Im running Linux Mint 14 standalone on mine and everything works well.

Good to hear. I might just go and order one of these.

---

### Post by Repuran on 2013-03-19
Now I'm torn between the Lenovo B570e and the Acer Aspire E1, I'm just going to be using Ubuntu anyone have a preference?

---

### Post by Mrhihat on 2013-04-29
Hello, first post.

I have the same problem as other owners of the E1-571 regarding installing Ubuntu. As I do not consider the problem solved I would like to inquire if there have been any progress on this issue (as I really, really would like to install Ubuntu on my laptop). changing to Legacy bios does not help as you only get the syslinux error.

So, what are the options here? I am considering trying to format the disk to get rid of the pre-installed windows 8, but something tells me that it is not the easiest thing to do...

---

### Post by Mrhihat on 2013-04-30
No one?

I guess the "solved" tag deflects some of the attention to this thread.

---

### Post by JonPaul on 2013-05-14
Hello 

I successfully installed Ubuntu on this machine. I removed Windows 8 however....

---

### Post by vratnica on 2013-05-17
Well, to install Ubuntu where the Windows is removed, isn't really of help to anyone here. As if you would tell: I installed Win 8 on my machine....who cares?

The Problem is to install both Systems side by side...and since yesterday, I have the same problem

---

### Post by vratnica on 2013-05-17
so, this is how it worked for me today, although I don't really know which parts of the process are really needed and which not

I used 12.04 .iso. I couldn't start the Live CD, so I tried to install it directly via wubi.exe, that is to bi found on the .iso image. After I was finished, on the boot I could choose between Windows 8 and Ubuntu, but if I choose Ubuntu, I get a black error Screen, where it says that wubi is blocking Windows. If I press Enter, I could still load Windows 8.

But than I noticed that if I eject and againg load the .iso image CD, and than press the Enter (at the Moment described above), the Live CD starts.

So I booted then again Windows, defragmented the Partition, made three more partitions (root, home and swap), and repeted the whole procidure and installed Ubuntu

The only Problem after the process was, that I couldn't boot Ubuntu :P

So I went to BIOS, and under the boot menu found also now "ubuntu" row, and put it on the top. I can now boot either to Windows or Ubuntu, but I always have to first change the first item in the booting list.

emmmm, an another Problem was that after the succesful Installation of Ubuntu, although in the process WLAN functioned, doesn't function anymore....:confused:

---

### Post by JonPaul on 2013-06-08
> **vratnica said:**
> Well, to install Ubuntu where the Windows is removed, isn't really of help to anyone here. As if you would tell: I installed Win 8 on my machine....who cares?

The Problem is to install both Systems side by side...and since yesterday, I have the same problem

No Vratnica - the title of the thread is "Acer Aspire E1-571 does not like Ubuntu?" not dual boot with windows 8.

---

### Post by Iowan on 2013-06-08
Perhaps a new thread is in order.
The [SOLVED] tag may have disappeared recently.

---

