---
title: "Install puzzle"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by dabazzman on 2008-07-22
I have the Unbunto file ISO on my new harddrive [F] and am wondering how I can get it to run w/o using the cd as it doesn't know where my [F] drive is.
I wan to repartition my second HD and give  Linux 100gb so it has room to grow. Mt current os is XP home, an older os and my experiences w/Vista have been less then inspiring. I want to create a dual boot system and wean myself off of windows.

---

### Post by Troll_the_Great on 2008-07-22
You can install Ubuntu from a memory stick, but I don't know exactly how is done.Search the forums because I'm sure I saw a thread that describes just that.
Cheers!

---

### Post by northern lights on 2008-07-22
I don't quite get what you want to say by your comp not knowing where your "F" drive is, nonetheless:

1. You cannot install Ubuntu from the .iso without either extra tools or burning it to a CD. Given the fact that CDs are dirt cheap nowadays, I'd say this is the easiest solution.

2. However, if you for whatever reason do not want to burn the image, downlaod "unetbootin" from [here]("http://lubi.sourceforge.net/unetbootin.html") (Windows Version).

---

### Post by Bruce M. on 2008-07-22
> **dabazzman said:**
> I have the Unbunto file ISO on my new harddrive [F] and am wondering how I can get it to run w/o using the cd as it doesn't know where my [F] drive is.
I wan to repartition my second HD and give  Linux 100gb so it has room to grow. Mt current os is XP home, an older os and my experiences w/Vista have been less then inspiring. I want to create a dual boot system and wean myself off of windows.

You don't run an ISO file, you burn it to a CD as a bootable file.
If you have NERO for Windows it will burn it properly.

One word of advice, burn it at the slowest possible speed you can. A 1:1 ratio would be the best, it makes for a cleaner burn and less likely to create errors.

Once you have that on a CD, put it in your CD player and reboot your computer.

You may need to check your BIOS settings to make sure your CD boots before your HD.

Good Luck.

More questions, just ask.
Bruce

---

### Post by dabazzman on 2008-07-22
No mem stick here, I do get asked if I wan't to reboot but I'm not sure if I can get it to install [run] on my 'f' drive. The drive is my first dual hd system and I just hooked it up yesterday. Not enough room on 'c' to give it a true chance to show it's stuff.

---

### Post by dabazzman on 2008-07-22
I already have it burnt to a cd as an iso file... so I guess my question is, if I reboot can I get it to open on my secondary 'f' drive.

---

### Post by billgoldberg on 2008-07-22
> **dabazzman said:**
> I have the Unbunto file ISO on my new harddrive [F] and am wondering how I can get it to run w/o using the cd as it doesn't know where my [F] drive is.
I wan to repartition my second HD and give  Linux 100gb so it has room to grow. Mt current os is XP home, an older os and my experiences w/Vista have been less then inspiring. I want to create a dual boot system and wean myself off of windows.

So you want to install Ubuntu 8.04 onto your second hdd without using a cd-rom (or dvd I presume)?

You can do it wit a usb stick, if you computer can do that.

You can also use [Wubi]("http://wubi-installer.org/") in windows xp to install Ubuntu on your hdd. I don't know if you can use wubi to install it to your second hdd.

If you don't want to burn Ubuntu to disk, you can order free disks on the ubuntu.com home page anywhere in the world.

If you don't have a cd-rom player, you should get one.

--

Just letting you know that hard drives aren't named the same as in windows in linux.

What you are referring to as the [f] drive, in linux will be called hda2 or something like that.

It will be under /media/disk (with a short cut in the left plane) in the file manager (nautilus).

---

### Post by RequinB4 on 2008-07-22
The ISO file is an image file, nothing more or less.  You have to burn it to a CD or some other extraction process in order to begin installation in that format.

Here is some information on how to burn it to a CD:[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

And here is the documentation on Installation in general: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) 

Welcome, and good luck.  On installation, all you have to do is specify you want the windows "F:\" drive (which is really a HDD partition) to be the installation location.  If you have any questions, just ask.

---

### Post by billgoldberg on 2008-07-22
> **dabazzman said:**
> I already have it burnt to a cd as an iso file... so I guess my question is, if I reboot can I get it to open on my secondary 'f' drive.

What do you mean "open your secondary f drive"?

Will the live cd be able to read all your drives? -> Yes

Will you be able to install Ubuntu to your 2nd hard drive -> Yes (choose manual in the partition dialog).

---

### Post by raptor2552 on 2008-07-22
Why not boot into Windoze and burn the image to CD and then install? Like 'northern lights' said CDs are cheap

---

### Post by dabazzman on 2008-07-22
> **RequinB4 said:**
> The ISO file is an image file, nothing more or less.  You have to burn it to a CD or some other extraction process in order to begin installation in that format.

Here is some information on how to burn it to a CD:[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

And here is the documentation on Installation in general: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) 

Welcome, and good luck.  On installation, all you have to do is specify you want the windows "F:\" drive (which is really a HDD partition) to be the installation location.  If you have any questions, just ask.
That was what I was wondering.
Well no time like the present to start...
I'll be back in a bit to let you know.

---

### Post by northern lights on 2008-07-22
> **dabazzman said:**
> I already have it burnt to a cd as an iso file... 
You aren't supposed to copy the .iso on a CD, you've got to burn its content to the CD. As someone mentioned, Nero will do.

> **dabazzman said:**
> so I guess my question is, if I reboot can I get it to open on my secondary 'f' drive.
don't get it, sorry

---

### Post by dabazzman on 2008-07-22
A bad checksum on my burned cd so no go. Now I try a fresh download and do it again. Yes blank cd's are cheap and I've made more than one in my day. I will get this software up and running this week [XP takes forever to boot]... even w/1.5gb of ram.
Thanks, all posters
 for your help

---

### Post by dabazzman on 2008-07-22
So now I wait, and wait, and wait... for windows explorer to find the checksum software

---

### Post by dabazzman on 2008-07-22
I must have deleted the checksum software, can someone point me in the right direction for a windozzzzze download?

---

### Post by Bruce M. on 2008-07-22
> **dabazzman said:**
> I must have deleted the checksum software, can someone point me in the right direction for a windozzzzze download?

Hi dabazzman,

This page: [HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") will give you everything you need, including a link to download **winMD5Sum**, a free and open source hash verification program for Windows. 

Don't forget: The official md5sum page for Ubuntu, Kubuntu, Edubuntu and Xubuntu is [UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes") to get the "hash" you need to compare to according to the file you downloaded.

Any other questions and we'll be here to answer and cheer you on. :)

Have a nice install.
Bruce

---

### Post by dabazzman on 2008-07-22
The checksums don't match...again
This is getting old. I've downloaded from 2 different websites and drawn unmatching checksums from both.
So my next question is... where can I download an uncorrupted file from?
Oh, and thanks Bruce, got it.. the checksum reader, not an uncorrupted file.

---

### Post by Bruce M. on 2008-07-23
> **dabazzman said:**
> The checksums don't match...again
This is getting old. I've downloaded from 2 different websites and drawn unmatching checksums from both.
So my next question is... where can I download an uncorrupted file from?
Oh, and thanks Bruce, got it.. the checksum reader, not an uncorrupted file.

Oh my, you are having problems.
Have you tried asking for the Ubuntu CD to be mailed to you if that is what your are looking for? Obviously it will take a bit longer. Then you can try a 3rd, 4th or 5th site (which is what I would do in the meantime).

What are you looking for?

[Ubuntu]("http://www.ubuntu.com/") - [Requesting an Ubuntu CD]("https://shipit.ubuntu.com/")

The following don't have the option to ship a free CD:

[Xubuntu]("http://www.xubuntu.org/")
[Kubuntu]("http://www.kubuntu.org/")
[Edubuntu]("http://www.edubuntu.org/")
[Ubuntu Studio]("http://ubuntustudio.org/")

Wish you luck.
Bruce

---

### Post by fidamehran on 2008-07-23
I think it's quite possible to install through Wubi. There are a few options:

1. 
You can download another CD image and burn it to CD. The new CD has Wubi built in. So while you have your F drive plugged in, you can run the CD and Wubi will autorun. Then you can select the F drive from the location drive menu.

2.
You can download Wubi from [http://wubi-installer.org/]("http://wubi-installer.org/")and use the menu within to download a complete ISO to your hard drive and install from it through Wubi (and not burn it on CD)

3.

Like BruceM. said, you can request a CD from "shipit.ubuntu.com".

---

