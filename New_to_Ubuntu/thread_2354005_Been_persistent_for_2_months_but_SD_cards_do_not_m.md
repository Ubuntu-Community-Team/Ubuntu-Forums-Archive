---
title: "Been persistent for 2 months but SD cards do not mount. About to give up with Ubuntu"
date: 2017-02-27
forum: New to Ubuntu
---

### Post by westone2 on 2017-02-27
Philips Freevent X59 Laptop - Intel (R) Core (TM) 2 CPU T5500 at 1.66Ghz, 32bit, 1Gb Ram. As recommended following my 1st Post I tried Lubuntu. Nothing works without a lot of researching to see what dependencies need to be downloaded after the initial install. Eg LSE and Cups for printer. Something (forget now) from Restricted Repository for Audio players as they did not play from library imports. Got all the normal office stuff working then find there is no way to eject USB sticks without finding its mount point from "df command" in terminal then running umount command. Surely this should all be basic stuff and work straight away after the initial download? Anyway my main interest is producing up to A3 photo prints up to camera club Advanced Class standard so I want to trial GIMP and Darktable ( on opening this warns is does not work in 32 bit mode). At this point I find I cannot load images from a SD card as it does not mount. So I install Ubuntu Studio from a disc which came with a GIMP hand book magazine. SD Card does not mount here either and this is also the case with Ubuntu 16.04LTS 32bit which I am now trying. By the way this card mounts OK in Windows and MAC computers. Surely this is basic stuff which should work? Another SD card also does not mount in Ubuntu.
"df" command does not find the SD Card. Neither does "Sudo fdisk -1" or "lsusb". Within the script "lspci" returns there are two lines which may be relevant:

03.06.2 SD Host controller: 02 Micro, Inc. Integrated MMC/SD Controller (rev/01)
03.06.2 Mass storage controller:  02 Micro, Inc. Integrated MS/xD Controller (rev/01)

I have researched this problem and tried many of the suggested solutions but nothing seems to solve this problem. So in order to fix this is there anybody out there who can tell me what dependencies I should look for, where in the file system I can find them and how to install them if they are not there? 

I really think it is a poor show if a photographer cannot load his images from an SD card!

If this problem can be solved and I am able to find a way of calibrating my monitor with a device such as a Datacolor Spyder or similar (Not unreasonable since all photographers can easily do this on Windows or Mac systems) then I will continue to investigate Ubuntu otherwise NO.

Perhaps the moderaters can point his out to the relevant developers.

Thanks

iwone2

---

### Post by Impavidus on 2017-02-27
> **westone2 said:**
> Philips Freevent X59 Laptop - Intel (R) Core (TM) 2 CPU T5500 at 1.66Ghz, 32bit, 1Gb Ram. As recommended following my 1st Post I tried Lubuntu. Nothing works without a lot of researching to see what dependencies need to be downloaded after the initial install. Eg LSE and Cups for printer. Something (forget now) from Restricted Repository for Audio players as they did not play from library imports. Got all the normal office stuff working then find there is no way to eject USB sticks without finding its mount point from "df command" in terminal then running umount command. Surely this should all be basic stuff and work straight away after the initial download?It shouldn't be that hard, but of course stuff that is only released under restrictive licenses cannot be included automatically on Ubuntu. As for ejecting usb sticks, I just right click->eject. Has worked flawlessly for over ten years. Something strange must be going on at your side. Maybe start a seprate thread about that.

> At this point I find I cannot load images from a SD card as it does not mount. So I install Ubuntu Studio from a disc which came with a GIMP hand book magazine. SD Card does not mount here either and this is also the case with Ubuntu 16.04LTS 32bit which I am now trying. By the way this card mounts OK in Windows and MAC computers. Surely this is basic stuff which should work? Another SD card also does not mount in Ubuntu.
How big are those SD cards? [SD card over 32GiB]("https://en.wikipedia.org/wiki/Secure_Digital#SDXC") are formatted with the exFAT system, which is a Microsoft format which has some legal problems for use on Linux. There are some workarounds, not all of them entirely reliable. Using SD cards of no more than 32GiB should work too.

---

### Post by Bucky Ball on 2017-02-27
Try installing 'exfat-fuse' and 'exfat-utils'. In the repositories. Install from terminal or using a package manager.

This is probably all you're missing. Just a note: if you want to get issues fixed as quickly as possible, post an issue per thread in the appropriate forum area and give the threads descriptive titles. Just gets confusing otherwise. You'll find there are plenty of people here ready, willing and, usually, able to help. ;) 

Good luck.

---

### Post by westone2 on 2017-02-27
Hi Impavidus
Thanks. Right Click brings up the drop down Menu but there was no Eject option there. That was in Lubuntu. SD Card is only 8gb.
Hi Bucky Ball
Thanks. that's one of the things I tried with no success. That was with Ubuntu Studio I'll try again in Ubuntu 16.04 32bit.

---

### Post by Geoffrey_Arndt on 2017-02-27
Your PC is not going to handle Ubuntu Studio or standard Ubuntu 32 bit well (Unity desktop environment really needs 2 gig of ram to be usable).

Might want to take a quick look at MX16 32 bit with XFCE as default DE.   MX16 based on Debian and has lots of tweaks to aid the new user.    Great forum for Linux neophytes also.   

Even lighter and much faster would be AntiX.    See Distrowatch.com for more info.

There are MANY photographers that use Linux and Ubuntu . . . maybe going through their websites/blogs and checking workflow can help . . . [https://scribblesandsnaps.com/linux-tools-for-serious-photographers/](https://scribblesandsnaps.com/linux-tools-for-serious-photographers/)

For other tips including color optimization . . . check this out:   [https://www.rileybrandt.com/2015/10/15/foss-photo-flow-2015/](https://www.rileybrandt.com/2015/10/15/foss-photo-flow-2015/)

---

### Post by Keith_Helms on 2017-02-27
> **westone2 said:**
> 
If this problem can be solved and I am able to find a way of calibrating my monitor with a device such as a Datacolor Spyder or similar (Not unreasonable since all photographers can easily do this on Windows or Mac systems) then I will continue to investigate Ubuntu otherwise NO.


I used DisplayCAL and an old Spyder (3, I think) to calibrate my monitor under Xubuntu.  The color profile loads a second or two after I log in and I can see the colors on my wallpaper change when it does.

---

### Post by Bucky Ball on 2017-02-27
I missed this.

Intel (R) Core (TM) 2 CPU T5500 at 1.66Ghz, 32bit, 1Gb Ram

Well, most photographers (particularly professional ones) use a much beefier and more up-to-date system than that. You'd be lucky to get Lubuntu going on that machine. You may be able to move photos around and do a bit of editing, but not sure how far you'll get if you want to do some serious post-processing with layers, transparencies, effects and whatever else you want to use or experiment with.

A few more gig of RAM might help, but good luck with it. :)

---

### Post by westone2 on 2017-02-28
Thanks Everyone
Geoffrey_Arndt. 
I have taken a note of these photographer's websites. I realise my old laptop is very limited but I was trying to get an overview of Ubuntu and using it for photo editing (I realise this would be limited on the Philips). I was not impressed with Lubuntu desktop  which is why I tried  the other versions.
Keith_Helms 
I have a Spyder 3 so I can  give this a try.
Bucky Ball
I tried installing the exfat stuff from terminal but it was already installed. Please also see my comments above re the limitations of my laptop.
Overall
I am between a rock and a hard place. My old Windows desktop used for photo processing is about to fail so I need to invest in something like Intel i7 (preferably 4 core), with  graphics card, 16gb Ram, small SSD + 1tb 7200rpm drives. Before putting Ubuntu on an expensive machine like this I need to be certain the  FOSS photo software will meet my needs. I'm not sure of this at present, but I would really like to kick Windows out.

---

### Post by Bucky Ball on 2017-02-28
Well, Gimp is the primary replacement for Photoshop. That has a Windows version. Download, install, fire away and see if you like it. 

[https://www.gimp.org/downloads/](https://www.gimp.org/downloads/)

Many open-source programs are multi-platform, not just for Linux. ;)

---

### Post by Geoffrey_Arndt on 2017-03-01
Westone2 . . . perhaps keep your windows machine as long as you can, but get a current technology Linux friendly PC "pre-installed" . . . I just had a friend demo the System76 "Meerkat" at a PC Club meeting.    Was impressed such a small PC could have so much capability.   He had an I5, 8 gig ram, a 7200 rpm 1 TB hdd, and a 256 Gig SSD.   Current Intel Iris Pro graphics are pretty decent for all his uses, but you may need a bit  more.   See the link in my signature for more info.

Note if you want to do a Win/Ubuntu dual boot, there are some vendors that will set that up, or if you buy a unit, Dell is quite Linux friendly compared to some others.

---

### Post by westone2 on 2017-03-01
Thanks for your help Geoffrey & Bucky Ball

---

