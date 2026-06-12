---
title: "New assembled PC- Blank HDD- Wubi install only one listed at Ubuntu.com?"
date: 2013-07-03
forum: New to Ubuntu
---

### Post by Mawnkey on 2013-07-03
The parts are all new, we did not buy an OS because we were planning to use Ubuntu 12.04 or 13.04 (open to suggestions there)
All desktop install paths at Ubuntu.com seem to lead to disk images that are autorun>wubi and so are clearly intended to add ubuntu to windows machines.
Every keyword search I can think of doesn't find an answer...

Is there someplace to get a bootable disk image for formatting/installing to an HDD that is right out of the box?

---

### Post by dannyboy79 on 2013-07-03
have you looked here? [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by Zill on 2013-07-03
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

### Post by Mawnkey on 2013-07-03
Yes.  That is what I was saying.
The disk images currently linked there are Wubi.

They are not bootable disks.

The four files in the root directory are autorun.inf, wubi.exe, Md5sum.txt and README.diskdefines.
The autorun reads:

[SIZE=1][autorun]
open=wubi.exe
icon=wubi.exe,0
label=Install Ubuntu

[Content]
MusicFiles=false
PictureFiles=false
VideoFiles=false[/SIZE]


This is set up to run in a Windows environment and install from there.
The disk will not even boot to a command prompt so you could type in wubi assuming your bios could recognize an autorun.inf

The PC does recognize other bootable disks (board drivers etc), so I am pretty sure what I need is a bootable ubuntu disk.

Thank you for your help and your patience.

---

### Post by Mark Phelps on 2013-07-03
> **Mawnkey said:**
> Yes.  That is what I was saying.
The disk images currently linked there are Wubi.

IF you use the link in dannyboy79, you will see a screen with two buttons -- one for 12.04 and one for 13.04. When you click one of those buttons, when you scroll down, you will get another screen with "Not now, take me to the download". If you click that, a window will popup containing the name of the ISO file -- and that is not a Wubi download.

---

### Post by Mawnkey on 2013-07-03
I have done this repeatedly, both before and since my initial post.  I did it again before I wrote this.

I have selected both the 12.04 and the 13.04 64-bit versions and followed through the donation screen to the downloads.
They both lead to downloading .iso disc images. (ubuntu-13.04-desktop-amd64.iso and ubuntu-12.04.2-desktop-amd64.iso respectively)
Both images are wubi install discs set up as I described above.

I agree they should not be...or at least there should be some point where you are given the option to download a straight install disc instead of the secondary OS installer. 
 I seem to remember that there used to be that option but I do not find it currently. If you want 64 bit your choices are those 2 wubi installers.

It makes me think of that Einstein quote: "Everything should be as simple as possible but no simpler"
I do not even see an "other installation choices" on the ubuntu.com site.

I am looking for other links, torrent, FTP locations, usenet posts or even keywords that I could use to locate a disc image that can be used to initially format a hard drive and install a current version of Ubuntu.

---

### Post by Zill on 2013-07-03
> **Mawnkey said:**
> ...I have selected both the 12.04 and the 13.04 64-bit versions and followed through the donation screen to the downloads.
They both lead to downloading .iso disc images. (**[COLOR="#FF0000"]ubuntu-13.04-desktop-amd64.iso[/COLOR]** and **[COLOR="#FF0000"]ubuntu-12.04.2-desktop-amd64.iso[/COLOR]** respectively)
Both images are wubi install discs set up as I described above...
I don't understand this!!!  Are you saying that the two downloads clearly identified as .iso files actually contain wubi files, rather than ubuntu image files?

Maybe your local mirror has corrupted data on it.  I suggest you try an alternative mirror and download again.  See [Official CD Mirrors for Ubuntu]("https://launchpad.net/ubuntu/+cdmirrors")

---

### Post by grahammechanical on 2013-07-03
Every ISO image has a Wubi.exe on it. There are different versions of Ubuntu (12.04, 13.04 + several flaours) but one installation disk. It does not matter if you want to install on to an empty hard disk or to install inside Windows (use wubi.exe for that) or install as a dual boot with Windows, the same image does it all. May I suggest that you put the DVD in the drive of the machine that you want to put Ubuntu on and set the boot system (BIOS/EFI) to give boot priority to the DVD drive or USB stick, whatever you are using and let the thing load the Ubuntu live session from the DVD.

[http://www.ubuntu.com/download/desktop/install-desktop-latest](http://www.ubuntu.com/download/desktop/install-desktop-latest)

You are only having this problem because you are examining the Install disk in another computer. I installed Ubuntu on to a newly self built machine with a blank unformatted hard disk five years ago. I followed the instructions. The installer will format the partition for you. The default file system is Ext4.

Oh, by the way, on Monday I installed Ubuntu 13.10 and on Tuedsay I installed 13.10 for Kubuntu, Xubuntu, Ubuntu Studio, Ubuntu Gnome and Lubuntu. I did not have any problems because the disk has wubi.exe on it. That program will only run if it is accessed through Windows.

Regards.

---

### Post by coldraven on 2013-07-03
You can get all versions and different download options here. I usually download using the torrent method, it seems to be faster.
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by Mawnkey on 2013-07-03
> **Zill said:**
> I don't understand this!!!  Are you saying that the two downloads clearly identified as .iso files actually contain wubi files, rather than ubuntu image files?

Maybe your local mirror has corrupted data on it.  I suggest you try an alternative mirror and download again.  See [Official CD Mirrors for Ubuntu]("https://launchpad.net/ubuntu/+cdmirrors")

That is pretty close to what I am saying...   ISO files are disc images.  The .iso files I am referring to, downloaded from the links we have all described, are non bootable disc images that contain a wubi.exe files as the only identifiable executable file.  
When mounted or burned to a disc these .isos do not produce a boot disc, they make a disc for installing Ubuntu as a secondary operating system.



The thumbnail should take you to a picture of what is in the .iso image.

[[IMG]http://thumbnails102.imagebam.com/26370/728341263692751.jpg[/IMG]]("http://www.imagebam.com/image/728341263692751")
In a windows computer this opens WUBI and offers to install Ubuntu. The autorun.inf directs only to wubi.exe (as posted above)
The .iso file is not an image of a boot disc and so it will not do anything on a PC with no OS.
If there is a bootstrap on the disc.. WUBI.exe does not seem to steer a non windows PC to it.
The new pc recognized three different boot discs, but sees these as non system disks.

I have downloaded the .isos directly from the ubuntu.com  site as well as from releases.ubuntu.com and the ftp interface at archive.ubuntu.com and on to two different PCs.  I have not used mirror sites.

---

### Post by crjackson on 2013-07-03
Okay, here is the deal.  Just burn the .iso image file and it will be bootable.  Boot from it and install.  The wubi files are there yes... They are included on all the downloads.  That way you have the option to run wubi from within windows for a wubi install.  The disc is a bootable install disc however and will install Ubuntu without using wubi.  Understand?

---

### Post by Zill on 2013-07-03
> **grahammechanical said:**
> Every ISO image has a Wubi.exe on it. There are different versions of Ubuntu (12.04, 13.04 + several flaours) but one installation disk. It does not matter if you want to install on to an empty hard disk or to install inside Windows (use wubi.exe for that) or install as a dual boot with Windows, the same image does it all...
Thanks for the clarification.  Haven't used Windows here for around seven years and so I just ignore everything to do with Wubi. ;-)

---

### Post by jockyburns on 2013-07-03
Much easier to download the ISO file to a usb stick, using Unetbootin.  [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)  Alter the startup order (in bios) on the computer you want to install on and Robert's your proverbial uncle. 
My computer's HDD packed in about 2 yrs ago, so I bought a new HDD, with no OS installed, downloaded 11.04 to usb stick and booted from that. After trying it for about 30 minutes I installed Ubuntu to the HDD, and have not looked back since.

---

### Post by Zill on 2013-07-05
> **Mawnkey said:**
> ...When mounted or burned to a disc these .isos do not produce a boot disc, they make a disc for installing Ubuntu as a secondary operating system...
This *may* be because you are simply copying the files to a DVD, rather than burning the iso image.

I suggest you follow the instructions contained in the [BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto") which explain exactly how to burn the iso image.

---

### Post by Mawnkey on 2013-07-05
Just to follow up for anyone who is seeing something similar...
I had somewhat better luck when I changing the settings in Nero to DVD (boot disc)and burning at the slowest speed instead of just burning the image with either the default or Nero.
My guess is somehow the MBT data was not burning onto the disc correctly so the bios was not seeing the copy as a system disc.

Finally got a clean install using the USB drive method.

Thanks to all who tried to help me through this puzzle.

---

### Post by Zill on 2013-07-05
Mawnkey:  I am pleased that you finally got Ubuntu installed. :-)

Enjoy the freedoms you now have with Linux as you explore the wonderful world of Free and Open Source Software (FOSS).  There is lots of support available and a quick websearch will often help resolve any problems you may experience.  Alongside that, there are many experienced users on Ubuntu Forums that are pleased to help so just post a new thread if a search of the forums does not find what you are looking for.

Just remember that [Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm") and things are done *very* differently here. ;-)

Good luck!

---

