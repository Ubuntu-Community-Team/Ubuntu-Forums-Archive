---
title: "Having Problem With Ndiswrapper"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Brainal on 2008-04-27
Here's the problem: I'm having trouble installing Ndiswrapper. Previously, I had everything running, wireless and all, and then I decided to do a fresh install because Hardy Heron came out. I'm not a complete beginner, but I'm borderline. Anyways, I go into the package manager and look for it...nothing. Oh, and the package is extracted on my desktop. I have the CD in and do ndiswrapper -l in the terminal and says for me to type sudo something or other. I type it in and it says it can't find the file. So right now...no internet on my Ubuntu partition. What shall I do?

---

### Post by coolbrook on 2008-04-27
As long as your CD is one of the software sources then Synaptic/Aptitude should be looking in the CD's repository.

Synaptic > Settings> Repositories > Third Party Software.

Ensure that the CD is checked off and you follow instruction to update.

---

### Post by Brainal on 2008-04-27
Keep in mind that this is a completely new install. By default, it should be on. I'm guessing for some reason I need to reinstall the .iso on the CD

---

### Post by anewguy on 2008-04-27
> **Brainal said:**
> Here's the problem: I'm having trouble installing Ndiswrapper. Previously, I had everything running, wireless and all, and then I decided to do a fresh install because Hardy Heron came out. I'm not a complete beginner, but I'm borderline. Anyways, I go into the package manager and look for it...nothing. Oh, and the package is extracted on my desktop.

What package do you have on your desktop?


>  I have the CD in and do ndiswrapper -l in the terminal and says for me to type sudo something or other. I type it in and it says it can't find the file. So right now...no internet on my Ubuntu partition. What shall I do?

By "the CD", which CD do you mean - the Ubuntu CD or the driver CD, or what?

Please do the following, and post back the results along with the answers to my 2 questions above, and we'll go from there......

sudo ndiswrapper -l  <- cut and paste the command and output back here

lspci  <- cut and paste the command and output back here


:)

---

### Post by Brainal on 2008-04-27
The Ubuntu CD. I tried on another computer and had the same problem. Oh, and it's the 64bit Ubuntu home package.

Now, I'm on my Vista partition right now so give me a some time to get back to you.

Oh, and I think it was you, but I have your tutorial for this stuff and the "finding ndiswrapper" is a road block

---

### Post by Brainal on 2008-04-27
sudo ndiswrapper -l

sudo: ndiswrapper: command not found


lspci

00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
02:00.0 Mass storage controller: Silicon Image, Inc. Sil 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
04:07.0 Network controller: Broadcom Corporation BCM43XG (rev 01)
04:08.0 Multimedia audio controller: Creative Labs SB Audigy LS
04:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

I had internet before. Somehow, I got it to recognize the CD or something and it found ndiswrapper...I think that's what I did but now that I did a fresh install, nothing

---

### Post by anewguy on 2008-04-27
Were you running 32-bit or 64-bit Linux before your new install?  I'm probably going to end up wrong here, but I thought I remembered something about ndiswrapper not working with 64-bit (maybe it was 32-bit ndiswrapper).  I'll do some more checking and see what I can find.  

BTW - I'm flattered, but I don't remember writing a how-to for getting ndiswrapper (I wrote a how-to for a laptop that included ndiswrapper). :)

---

### Post by Brainal on 2008-04-27
My last install was 64 and my new one is too. Same exact CD. The first install worked and I was online so I guess you're wrong with that

---

### Post by anewguy on 2008-04-27
I found some information for you - beyond just having ndiswrapper compiled for 64 bit, you must also have the 64-bit drivers for your card.

If you google or yahoo search "ndiswrapper", you'll find the sourceforge site where you can download the source for ndiswrapper.  Copy that (share a disk or some other media) to your Ubuntu and follow the instructions to compile.  It's possible you don't have the build-essentials, etc., needed to compile, and I'm not sure how to go about getting those from a non-Ubuntu box.  Is there any way you can hardwire you PC to the router to at least download stuff until your wireless works?

:)

Here's some info from a Linux forum:

14-2005, 07:56 PM   	   #8
superbnerb
Member
 
Registered: Jul 2005
Location: about town
Distribution: Kanotix64
Posts: 71
	
linuxant
dear dudes who read this in the future...

if you have a 64 bit OS, like kanotix64 [http://www.kanotix.comyou](http://www.kanotix.comyou) must use a 64 bit driver. I found a site, that found a driver for our card. i am using a Presario V2310CA machine and it has a built in broadcom chipset. the driver files come from ACER at this URL

and i used linuxant's driverloader and signed up for the free 30 day trial. [http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/)

here is the driver

once the free trial ends, then maybe i'll try again. The thing is now I can't make the machine connect with the AP. i use kwifi and i can see my access point. I input my wep and essid and stuff i used to do on the 32 bit system, but it won't connect. It's like Valhala... i'm close and i can see it, but it won't let me in.
superbnerb is offline   	  	Reply With Quote
superbnerb
View Public Profile
View LQ Blog
View Bookmarks
View Review Entries
View HCL Entries
Find More Posts by superbnerb
Old 12-14-2005, 08:36 PM 	  #9
Lenard
Senior Member
 
Registered: Dec 2005
Location: Indiana
Distribution: RHEL/CentOS/SL 5 i386 and x86_64 pata for IDE in use
Posts: 4,790
	
Doing so right now. running a 2.6.14.3 kernel and using ndiswrapper-1.7 on my Acer Aspire 5002 laptop;

00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

With the Windows 64-bit driver (see ndiswrapper wiki list card # 36 for where to get the driver)

$ ndiswrapper -l
Installed ndis drivers:
bcmwl5 driver present, hardware present

$ uname -a
Linux Aspire5000 2.6.14.3 #1 Sun Dec 11 19:02:03 EST 2005 x86_64 x86_64 x86_64 GNU/Linux
Lenard is offline   	  	Reply With Quote

---

### Post by Brainal on 2008-04-27
I found the forum post you made. Exact adapter I have. I got the same drivers you posted too. It's just that the part where you need to search for ndiswrapper in the package thinger, I  get no results.

[http://www.backports.ubuntuforums.org/showthread.php?t=539208](http://www.backports.ubuntuforums.org/showthread.php?t=539208)

---

### Post by adult swim on 2008-04-27
are you sure that your cd is marked as a repository?  my install was fresh and the cd was not checked by default

---

### Post by adult swim on 2008-04-27
EDIT:
also these parts of that tutorial arent going to work 
"sudo ndiswrapper -m

(4) Type:

gksudo gedit /etc/modprobe.d/blacklist

This will open an editor window. Go to the bottom of that list and add the following if they are not already there:

# broadcom default no firmware, using ndiswrapper instead
blacklist bcm43xx"

once you get to there see here [http://www.backports.ubuntuforums.org/showthread.php?t=734003&highlight=ndiswrapper](http://www.backports.ubuntuforums.org/showthread.php?t=734003&highlight=ndiswrapper)

---

### Post by anewguy on 2008-04-27
Gee, that's been a while!  I actually did the upgrade to Hardy, so I don't have the disk.  Let me go out and download it and then perhaps I can tell you how to install ndiswrapper from it (if it's like most of these disks, somewhere on it will be a reference to disk sets, with subdirectories like "A", etc. - this is where the packages usually are).

I'll get that download going, then head off to the store for a minute or two.  I'm on DSL, so it will take me a while to download and get back to you.

:)

---

### Post by anewguy on 2008-04-28
Okay, I have a copy of the 32-bit installation disk - I imagine the 64-bit is laid out the same.  Put the Cd in the drive, wait for it to mount, and it should open the drive in a browse window.  Click on "pool" then on "main" then on "n" then on "ndiswrapper".  There you will find the 2 packages you need to install.  Just double-click each one and they should each open in package manager (do them 1 at a time) and install.  When you're done, I don't know if you have to reboot or not - try the ndiswrapper -l again and see what happens.

:)

---

