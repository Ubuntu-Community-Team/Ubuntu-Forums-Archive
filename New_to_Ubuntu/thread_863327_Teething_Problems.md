---
title: "Teething Problems"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by Crackity Jones on 2008-07-18
Hi there.
So I created a live-CD and booted up into it, finding Ubuntu to be great.
I am one small step away from fully-installing Ubuntu into being my main OS - but unfortunately there are a few problems:
The biggest brute of a problem is the networking issues I am having. Ubuntu can not detect my network or drivers or anything. It also needs to download some drivers but can't because it can't connect to the internet.

I was also wondering if anyone could help me before I remove XP: what's the best way of moving over all my music, photos and other media files?
I thought Ubuntu would just change the C drive but in the live-CD I can't access my D-drive (containing my documents) plus I couldn't play a DVD - is this another driver issue?

Sory if what I have written is a bit cryptic, I'm letting a lot out of my mind at once.

---

### Post by NE Key on 2008-07-18
What I suggest you do is partition your hard drive and install Ubuntu on the new partition.

Then, when you start up your computer you will be able to choose which system to run (dual boot).
You will be able to access the files in your windows side from Ubuntu.

Later, when you are happy with everything you can dump windows.

---

### Post by overdrank on 2008-07-18
> **Crackity Jones said:**
> Hi there.
So I created a live-CD and booted up into it, finding Ubuntu to be great.
I am one small step away from fully-installing Ubuntu into being my main OS - but unfortunately there are a few problems:
The biggest brute of a problem is the networking issues I am having. Ubuntu can not detect my network or drivers or anything. It also needs to download some drivers but can't because it can't connect to the internet.

I was also wondering if anyone could help me before I remove XP: what's the best way of moving over all my music, photos and other media files?
I thought Ubuntu would just change the C drive but in the live-CD I can't access my D-drive (containing my documents) plus I couldn't play a DVD - is this another driver issue?

Sory if what I have written is a bit cryptic, I'm letting a lot out of my mind at once.

HI and welcome, you can use the command ```
lspci
``` in the terminal located under applications, accessories. This will identify your hardware and you can search the forums for a solution.
Once you have installed Ubuntu you should have access to your data (music).
If you want to play dvd's and such you will need the restricted formats once you have install ubuntu.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

                                                                           Edit   and    look   below   for  the future titles of threads  VVVVV

---

### Post by Crackity Jones on 2008-07-18
So Ubuntu will just install itself to the C drive, leaving all the documents in my D drive intact?

---

### Post by overdrank on 2008-07-18
> **Crackity Jones said:**
> So Ubuntu will just install itself to the C drive, leaving all the documents in my D drive intact?

If you installed it to the partition you create for it. Here is a link that may help.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by philinux on 2008-07-18
> **Crackity Jones said:**
> So Ubuntu will just install itself to the C drive, leaving all the documents in my D drive intact?

Make sure you backup everything important and verify it's backed up.

---

### Post by overdrank on 2008-07-18
> **philinux said:**
> Make sure you backup everything important and verify it's backed up.

Agreed :)
From the first link I posted 
```
Back up your existing PC

While the Ubuntu installer is very safe and can reliably partition your hard disk to allow you to dual boot, it may be a good idea to be ensure that you are able to restore your Windows installation before you try to install Ubuntu.

Backing up your data

Although this may seem obvious, do backup your important data files to another media before attempting a dual-boot install. Many backup solutions exist for Windows users, but the easiest one may be to just create as many CDs or DVDs with copies of your data as required. Another way is by plugging in a USB key or external storage with enough space.

Backing up your operating system - using recovery tools

Have your recovery CD or DVD handy - Most systems which are delivered with Windows already installed also come with some sort of recovery or re-installation disk. There is a recent tendency for companies to try to save money and not ship such a disk. Instead, they provide you a hidden partition on which there is a recovery tool and an image of the pre-installed system. 
```

---

### Post by Crackity Jones on 2008-07-18
In the whole excitement of a new fast OS I threw caution into the wind and decided to do a full install. I am now slightly regretting this decision.
I'm sure as soon as I can get an internet connection I will be fine.

I did the hardware search from the tip before - heres the result:
[COLOR="Gray"][I][SIZE="1"]00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0b.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:0d.0 Communication controller: Intel Corporation 536EP Data Fax Modem
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)[/SIZE][/I][/COLOR]
I know I have a built in Belkin wireless reciever and a belin wireless router, plus my network has a WEP key. Can you suggest what I do to get my internet connection?

I saw a note-taking application, is there anyway that I can synch my evernote notes with this?

iTunes has been life-support for me for the last few years. I tried the built-in Jukebox, but when I imported a CD, the music was imported as Oggvorbis, plus the software didn't pick-up the song ID tags. Is there better music collection software?

I have made a mistake, well at least at this stage I think I have. Please help me, I really need it.

---

### Post by NE Key on 2008-07-28
00:0b.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Do a search of this forum and you will find the "How to" for this wireless card. This is one a number of guides;
[http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306](http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306)

Probably easiest to plug your laptop into your router with a cable to set up the wireless.

---

