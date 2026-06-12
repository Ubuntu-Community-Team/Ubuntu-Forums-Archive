---
title: "Install Ubuntu on Eee PC 1015PX (*over* Win7 Starter)"
date: 2012-01-13
forum: New to Ubuntu
---

### Post by NagiMani on 2012-01-13
System / Situation: 
Just bought a new Asus EEE PC 1015PX Notebook w/ Win7 Starter OS factory pre-installed.

Objective:  
- Install U10.04.3 LTS i386 Desktop 
- Completely eliminate the Win7 Starter OS in the process

Tools in my inventory:
- CD burned with U10.04.3 LTS Desktop i386  (presumably bootable as-is)
- USB created with Pendrive / U10.04.3 LTS Desktop i386  (presumably bootable as-is)
- The CD and USB above were both created using a Win7 / IBM Desktop system

Why I assume that 10.04.3 is a good choice:
- It's the most recent LTS version - probably the best for my techno-putz skill-level (?)

Problems:
- My User-IQ rating:  Clumsy Beginner - *basic* experience with Ubuntu 8 and 9 on Eee PC including *basic* terminal / command line
- Tons of conflicting info available about which Ubuntu version to use on the 1015PX
- Tons of conflicting and piecemeal info available about the installation process/choices, and post-installation tweaks for the 1015PX

Questions:
- Is U10.04.3 Desktop i386 (natively / out of the box) the best version of Ubuntu for the 1015PX?
- Are there certain specific option-choices in the install / set-up process which are optima, unique or even mandatory for the 1015PX?
- Are there specific post-installation tweaks that best suit the 1015PX?
- Is there anything specific I need to know or do during the install given that Win7 Starter is already pre-intalled on the 1015PX?
- Are clear keystroke-specific answers to these types of questions *always* archived at a specific website/URL that I should be using?


I'd like to get the install and tweaks right the first time around, so I would appreciate keystroke-specific instructions wherever possible (or referrals to them elsewhere).  

Thank you very much for any help you can offer.  I'll answer any follow-up questions as best I can.  

FWIW:  I'll post a keystroke-specific, start-to-finish guide (install and tweak U v.? on the 1015PX) once I get through this, subject to editing by your board-masters as they see fit - if there's any value in that.

I'm including a dump of the 1015PX system-specs below in case they need to be taken into account.  


Nagi


----


System Specs Dump:
(generated with Belarc System Advisor freeware)


Model:
ASUSTeK Computer INC. 1015PX 
(I haven't yet found any model "suffix", e.g. "-MU17-WT", "-MU17-BK", etc.)

Board: 
ASUSTeK Computer INC. 1015PE
Bus Clock: 167 megahertz
BIOS: American Megatrends Inc. 1401 08/30/2011

Processor:
CPU:  1.67 gigahertz Intel Atom N570
56 kilobyte primary memory cache
512 kilobyte secondary memory cache
64-bit ready
Multi-core (2 total)
Hyper-threaded (4 total)

Hard Drive:
Hitachi 250GB
233.93 Gigabytes Usable Hard Drive Capacity
221.71 Gigabytes Hard Drive Free Space

Memory Modules:
1016 Megabytes Usable Installed Memory
Slot 'DIMM0' has 1024 MB (serial number SerNum00)
Slot 'DIMM1' is Empty
(DDR3, 1 x SO-DIMM, 1GB / Maximum 2GB)

Local Drive Volumes:
c: (NTFS on drive 0) * 107.37GB / 95.25 GB free
d: (NTFS on drive 0) 126.56 GB / 126.46 GB free
Operating System is installed on c:

Contoller:
Intel(R) NM10 Express Chipset

Display:
Intel(R) Graphics Media Accelerator 3150 [Display adapter] (2x)
(10.1" LED Backlight WSVGA (1024x600) Screen)

Bus Adapters:
Intel(R) N10/ICH7 Family USB Universal Host Controller - 27C8
Intel(R) N10/ICH7 Family USB Universal Host Controller - 27C9
Intel(R) N10/ICH7 Family USB Universal Host Controller - 27CA
Intel(R) N10/ICH7 Family USB Universal Host Controller - 27CB
Intel(R) N10/ICH7 Family USB2 Enhanced Host Controller - 27CC

Interface:
1 x VGA Connector
3 x USB 2.0
1 x LAN RJ-45
1 x Audio Jack (Headphone/Mic-In)
1 x Card Reader : SD/ SDHC/ MMC

Comm:
Atheros AR8152/8158 PCI-E Fast Ethernet Controller (NDIS 6.20)
Microsoft Virtual WiFi Miniport Adapter (2 of them)
Intel(R) Centrino(R) Wireless-N 6150
Intel(R) Centrino(R) WiMAX 6150 (<- I'm tempted to ask whether I should disable this thing since I opted not to subscribe)

Wireless Data Network:
WLAN 802.11 b/g/n@2.4GHz
Bluetooth V3.0

Also has numerous Asus Live Update & related built-in apps (standard for Asus machines)

- End of System Specs Dump -

---

### Post by C.S.Cameron on 2012-01-13
My wife and kid's use 10.04 LTS on there computers, at least until 04/12.
I am using 10.04 Live on a SD card on my EEE but it is just a 4GB machine.

---

### Post by NagiMani on 2012-01-14
> **C.S.Cameron said:**
> My wife and kid's use 10.04 LTS on there computers, at least until 04/12.  I am using 10.04 Live on a SD card on my EEE but it is just a 4GB machine.

Thanks.  

At least in the case of the newer Eee PC's, I get the impression that the more current versions of Ubuntu present a lot of issues.  For example:

Until yesterday, according to [http://www.ubuntu.com/certification/hardware/201103-7432:201103-7458](http://www.ubuntu.com/certification/hardware/201103-7432:201103-7458) (in Item #1 of the certification notes), the 1015PX is certified _only_ for 11.04 and 11.1 with notes, and _only_ if factory installed.  That page also specifically warned (in Item #2) that both those versions might either not work correctly, or might not work at all _unless_ factory installed.

Then:

Today, that URL-page is gone (first it was "unexpected system error - contact admin" / then ten minutes later "page not found").  The apparent replacement URL-page is now [http://www.ubuntu.com/certification/hardware/201103-7458](http://www.ubuntu.com/certification/hardware/201103-7458).  The Item #2 warning doesn't appear on the new page.

That's one example of many light-speed info-changes which have me a little nervous about just shot-gunning an Ubuntu installation (any version) without some serious guidance from experienced users.

Nagi

---

### Post by 2F4U on 2012-01-14
I would suggest that you either burn the versions of interest to a cd or place them on a flash drive and then try the first in live mode. Don't install until you at least see that it boots correctly to the desktop. If you have the patience, use the live system for a while and see how it goes.

---

### Post by C.S.Cameron on 2012-01-14
> **2F4U said:**
> I would suggest that you either burn the versions of interest to a cd or place them on a flash drive and then try the first in live mode. Don't install until you at least see that it boots correctly to the desktop. If you have the patience, use the live system for a while and see how it goes.

Good advice, a 4GB SD card works well for a Live install, use a 8GB SD card for a Full install

---

### Post by NagiMani on 2012-01-14
> **2F4U said:**
> I would suggest that you either burn the versions of interest to a cd or place them on a flash drive and then try the first in live mode. Don't install until you at least see that it boots correctly to the desktop. If you have the patience, use the live system for a while and see how it goes.

Got it.  I'll do that using the two items from the original post:  

> - CD burned with U10.04.3 LTS Desktop i386  (presumably bootable as-is)
- USB created with Pendrive / U10.04.3 LTS Desktop i386  (presumably bootable as-is)
- The CD and USB above were both created using a Win7 / IBM Desktop systemI guess I'll be the first one to know if I burned them correctly from the iso files.  :rolleyes:

Thanks very much.

Nagi

---

### Post by BlinkinCat on 2012-01-14
Any ISO burnt to a CD you should check with the MD5Sum - See here -

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by mastablasta on 2012-01-14
latest versions have newer drivers preinstalled. so i would firts try the latest version and then if it all works install it then when 12.04 comes out, and if everything works ok on it, upgrade to it and stick with it for the next 5 years. newer/updated drivers are only important if you have a newer maschine or newer model of computer. they can be also installed on 10.04 manually (PPA, tar.gz etc.).

to sue less processor power and ram you could choose Xubuntu instead of Ubuntu which can be quite heavy. thoguh you can tweak it's resource usage down a bit (e.g. by using Unity 2D).

---

### Post by NagiMani on 2012-01-14
Thanks very much all around for the feedback.

_By the numbers_:

@C.S.Cameron
I plan on using my 16GB USB thumb drive since I've occasionally seen Ubuntu's memory-footprint hit 10GB.

@BlinkinCat
Thanks.  Got the checksum from the Ubuntu web and ran MD5Sum - it checks out.

@mastablasta
Got it:  use 10.04.3 LTS i386 Desktop for the 1015PX as long as it works, then upgrade to a stable 12.04 LTS when available.  And thanks very much for the useful tips on Unity2D tweaks + Xubuntu's reduced resource usage.

_USB Issue + Question_:

I'd like to use an Ubuntu USB for no other reason than ease of use and handling (versus a CD + external CD drive for the new 1015PX).  I vaguely recall from a couple years ago that making a bootable Ubuntu USB was pretty simple.  That seems to have changed.

The only functioning system here is a Win7 Desktop.  In a perfect world, I'd point Win7's burner-app from the iso file to the USB and be done with it - or something along those lines.   But now there are tons of "intermediary" USB-maker apps out there (like pendrivelinux, cd2usb, etc) and they're _apparently_ mandatory for creating a bootable Ubuntu USB.   

My question:  As things stand right now, what's the best way to put Ubuntu (10.04 LTS) on a USB so that I can both (1) test-drive it from the USB, and (2) install it to the 1015PX from the USB if it works?


Nagi

---

### Post by C.S.Cameron on 2012-01-15
> My question: As things stand right now, what's the best way to put Ubuntu (10.04 LTS) on a USB so that I can both (1) test-drive it from the USB, and (2) install it to the 1015PX from the USB if it works?


Download 10.04.3 LTS
Extract usb-creator.exe from the iso.
Run usb-creator.exe in Win 7.
Select Max Reserved Extra Space, (Persistence).


You can continue to use the remaining 11GB of the USB for storage and transfer.
If you need to access this data while booted fron the thumbdrive, or save data windows can read, go to filesystem/cdrom.

EDIT:
To install from the USB click on "install" on the opening screen or click the install icon on the desktop when booted from it.

---

### Post by NagiMani on 2012-01-15
@CSCameron

> [I]Download 10.04.3 LTS
Extract usb-creator.exe from the iso.
Run usb-creator.exe in Win 7.
Select Max Reserved Extra Space, (Persistence).[/I]

usb-creator.exe did not allow any options other than start and cancel - no reserved space option.  It ran on auto-pilot and self-created 600MB of reserved space (if I'm reading the list of post-install files correctly).

I tried pendrive's universal usb installer, which gave me the reserve option - so I maxed it out at 4GB.  I plan to use this _pendrive-generated USB_ to test drive and eventually install 10.04 on the new EeePC 1015PX.  

Note:  
These two different usb makers created only _slightly_ different files on the usb drive - no radical difference that I can tell.  But I can post or email a list of both for comparison if someone with more experience (than me) thinks that's worthwhile before I take the 10.04 pendrive USB for test drive on the new 1015PX.

Thanks again for the guidance.

Nagi

---

### Post by NagiMani on 2012-02-16
I've installed and used 10.04 on the new EeePC 1015PX with only one major flaw.  All native apps are working except that I have _**no ****network connection (wired or wireless)**_.  

My only frame of reference for Ubuntu web access is based on using U8 and U9, both on an older EeePC.   In both cases (U8 and U9), both wired and wireless network connections were working immediately after installing / upgrading.  So I was accustomed to simply plugging in the wired cable and hopping onto the web (with Firefox).  And for the wireless connection, all I had to do was select my wireless-net name and enter the wireless net password to use it.  

I've looked at just about every ambiguous document, forum and web reference to be found on _**10.04 network config**_ and am now completely lost on where to start in getting my network connections config'd / set-up.  

I'm using ADSL, an ISP-supplied modem, and a wireless router.  I have my Win7 connection information, my modem settings, and my router settings, but I don't know what to do with any of that information in a network config.

That's a very short list of what I don't know.   Any suggestions on a _**step by step 10.04 network config instruction / troubleshooting resource for dummies**_?


NagiMani

---

### Post by roger_1960 on 2012-02-16
Hi

On an off chance, I think FN+F2 toggles the wifi & bluetooth hardware on and off on that laptop.  Could that be part of the problem?

---

### Post by NagiMani on 2012-02-16
Fn+F2:  
That was probably the smartest place to start, but it didn't connect.  FWIW:  It *tried* to connect, as I could see the customary pulsing vertical line next to the network icon when I switched it off, then on again - but I got no connection.  Thanks for the idea.

---

### Post by NagiMani on 2012-03-01
Update:   From what I can tell, this problem dates back 18 months or more.
 

 Apparent culprit issue:
 Original/native U10.04 kernel* (&#8804;2.6.34) doesn't include driver for Atheros AR8151 LAN  
  [Atheros AR8152/8158 PCI-E Fast Ethernet Controller (NDIS 6.20)]
  

  * the driver/code is included in kernels  &#8805;2.6.35  (2.6.35-xx and later)
  

 Now that I vaguely know the basic nature of the problem:   this thread probably belongs in the Networking & Wireless threads-section @  [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)
 

 Solution(s) #1  
 (a)  Brute-install AR8151 driver in 10.04  -OR-  (b)  Upgrade the 10.04 kernel  
 

 [http://ubuntuforums.org/showthread.php?t=1624052](http://ubuntuforums.org/showthread.php?t=1624052)
 [http://ubuntuforums.org/showthread.php?t=1555540&highlight=build-essential](http://ubuntuforums.org/showthread.php?t=1555540&highlight=build-essential)
  - [http://ubuntuforums.org/showpost.php?p=9738022&postcount=7](http://ubuntuforums.org/showpost.php?p=9738022&postcount=7)
 [http://ubuntuforums.org/showthread.php?t=1553834](http://ubuntuforums.org/showthread.php?t=1553834)
 [http://ubuntuforums.org/showthread.php?t=1476231](http://ubuntuforums.org/showthread.php?t=1476231)
 [http://ubuntuforums.org/showthread.php?t=1677122](http://ubuntuforums.org/showthread.php?t=1677122)
 and a muddled explanation at
 [http://www.ubuntugeek.com/kernel-2-6-35-officially-available-for-ubuntu-10-04.html](http://www.ubuntugeek.com/kernel-2-6-35-officially-available-for-ubuntu-10-04.html)  
 

 Potential recurring issue with 10.04 and the driver-only solution(s):
 May require re-executing the same solution with each 10.04 update/upgrade
 

 Solution #2  (alternate)
 Install U10.10 Maverick (which apparently contains the 2.6.35-xx kernal w/ AR8151 driver)
 

 Note to self - - obstacle to overcome whether adding driver or upgrading kernel:   
 No internet connection, either wired or wireless.
 

 Question:   
 Will upgrading the 10.04 kernel to 2.6.35-xx prevent the recurring update issue?
 (i.e., will I have to re-upgrade the kernel every time I allow 10.04 updates?)
 

 

 Nagi

---

### Post by NagiMani on 2012-03-25
[U][B]
Post Mortem:  Unresolved + Functional Workaround [/B][/U]

Bought a USD $30 Buffalo Giga USB-2-LAN adapter (with its own built-in LAN chip).  See pic at  [http://www.gadgetfolder.com/wp-content/uploads/2009/02/buffalo-lua2_u2_kgt.jpg](http://www.gadgetfolder.com/wp-content/uploads/2009/02/buffalo-lua2_u2_kgt.jpg)

Connected to the web immediately.

This at least allows me to web-connect via hard cable so that I can resolve problems without bouncing back and forth between the 1015PX and other machines / media.

A minor victory, but for people like me, you take them wherever you can find them.  :p

Nagi

---

### Post by GuitarRocker2562 on 2012-03-25
Honestly. I think you should really install the latest version of Ubuntu 11.10 on your machine. The wireless will work and it is much more optimized for netbooks than 10.04. Plus I think you'll have more support on the forums that way.

---

### Post by gordintoronto on 2012-03-25
> **GuitarRocker2562 said:**
> Honestly. I think you should really install the latest version of Ubuntu 11.10 on your machine. The wireless will work and it is much more optimized for netbooks than 10.04. Plus I think you'll have more support on the forums that way.

+1! New computer, old OS, many problems.

---

### Post by Mark Phelps on 2012-03-25
I would also advise AVOIDING 11.x versions at the current time. Given the increase in resource demands due to the Unity desktop, I can not recommend them over 10.x.

The recommendation you were given to stay with 10.x and then try out 12.04 to see if it works better is the way I would go.

---

### Post by NagiMani on 2012-03-26
> **GuitarRocker2562 said:**
> Honestly. I think you should really install the latest version of Ubuntu 11.10 on your machine. The wireless will work and it is much more optimized for netbooks than 10.04. Plus I think you'll have more support on the forums that way.

I was tempted to do that.   In fact, U11 is _presumably_ the factory burn-in version of Ubuntu for the Eee PC 1015PX.  But I noticed Asus took their 1015PX/U11 page down so fast that smoke rolled off the servers.  That was for the factory installed scenario, so that doesn't encourage me to do it myself.

Lesson learned:  check forums for persistent hardware-related problems before buying a computer.

Beyond that - and no offense intended to anyone - but it strikes me as... very odd that I could expect _less_ forum support for an LTS. *

*  LTS _should =_ JFW  (Just Freekin' Works)


Nagi

---

### Post by NagiMani on 2012-03-26
> **gordintoronto said:**
> +1! New computer, old OS, many problems.


The computer isn't "new", and the OS isn't "old":   

The 1015PX was six months old when I bought it retail.  Asus no doubt had it longer than that, since they offered U11 factory pre-loaded on the 1015PX until last month at least.   And eight month old U10 has another year before EOL (end of life).  

I'm tempted to think we've entered the age of 30 day digital obsolescence (which probably isn't far off), but the reality seems to be more a matter of hardware mfrs and code writers just plain getting too sloppy-rushed out of the new-model / new-release gates.  _*That*_ causes many problems - although it sure does keep a lot of idiots in work.

Nagi

---

### Post by Mark Phelps on 2012-03-26
> **NagiMani said:**
> *  LTS _should =_ JFW  (Just Freekin' Works) Nagi

Well ... it SHOULD be true, which is why I still recommend trying out 12.04 in LiveUSB mode to see if it brings anything better to the table than the 10.x that you have now.

The 11.x series introduced MAJOR changes with the move to Unity and away from Gnome.  The 12.x series is supposed to have made those changes more stable and be a better platform.

Which is why, given a choice, I would recommend avoiding 11.x and going with 12.x.

---

### Post by NagiMani on 2012-03-26
> **Mark Phelps said:**
> I would also advise AVOIDING 11.x versions at the current time. Given the increase in resource demands due to the Unity desktop, I can not recommend them over 10.x.   The recommendation you were given to stay with 10.x and then try out 12.04 to see if it works better is the way I would go.

> **NagiMani said:**
>  <snip> ***LTS _should =_  JFW  (Just Freekin' Works)*** 

> **Mark Phelps said:**
> Well ... it SHOULD be true, which is why I  still recommend trying out 12.04 in LiveUSB mode to see if it brings  anything better to the table than the 10.x that you have now.   The 11.x series introduced MAJOR changes with the move to Unity and away  from Gnome.  The 12.x series is supposed to have made those changes  more stable and be a better platform.   Which is why, given a choice, I would recommend avoiding 11.x and going with 12.x.


Thanks - I hear you.   If Asus couldn't get U11 to work on the 1015PX, I'm not inclined to climb over their corpses to try it - not with my digital-dunce IQ.  I'll wait on 12.04 and do the Live USB trial run, as suggested.

On the lighter side, the workaround was pretty funny (the USB-2-LAN-cable adapter):  I'm sitting here banging my head on the screen trying to figure this out for two months;  then a neighborhood whiz kid walks in, I tell him the story, he plugs his adapter in, and I'm web connected.

That's worth passing on to anyone having related LAN connection problems with U10 (1015PX; AR8151 chip; etc).

Next up on my Ubuntu train wreck agenda:
Installing Xubuntu 10 on a five year old netbook (Panasonic Toughbook CF-R4)


Nagi

---

### Post by NagiMani on 2012-03-27
FYI Only - Not a request for any further support

Final Post Mortem:  U10.04 on EeePC 1015PX  (Persistent Issues)

1 - LAN doesn't work (neither cable nor wireless / workaround with USB-2-LAN adapter)
2 - openvpn doesn't work (persistent time-out)
3 - no sound (systemic - including all apps)
4 - keyboard characters are hybrids with antny/scim (instead of consistently one language or the other)
5 - intermittent: duplicate icons in top panel
- - battery icon
- - time and date
- - antny/scim


Nagi

---

### Post by NagiMani on 2012-04-04
Epilogue:  
U10LTS rendered the 1015PX useless - Resorted to U 11.10

Upside:
Everything works without exception.

Downside:
- Unity is almost as impressive as Windows 3.1  (but requires more time to optimize)
- @Mark Phelps:  You're dead-on - - Unity UI resource usage is off the charts.

Suggestion (very, very short version):
Use U-resources to keep tweaking Gnome and make sure the LTS really work before final release.

My status:
Waiting anxiously for U12 LTS - and hoping it has the right stuff for my 1015PX.



Nagi

---

### Post by NagiMani on 2012-04-22
Preparing for probable move from 11.10 to 12 LTS, and would like to get a sense of direction from experienced users:

Should I try upgrading 11->12 (assuming that's even an option), or do a fresh install?

Nagi

---

### Post by 3rdalbum on 2012-04-22
Unity in Ubuntu 11.10 isn't bad, it's just different. Quite good once you've spent some time with it and taken advantage of some of its good features.

You can certainly update to 12.04. If this is a very fresh install of 11.10 the update should go perfectly well. Press Control-Alt-T to bring up a terminal and run this command:

```
sudo update-manager -d
```

At the top of the window you'll be told that Ubuntu 12.04 is now available, and you can click the Upgrade button to upgrade.

---

