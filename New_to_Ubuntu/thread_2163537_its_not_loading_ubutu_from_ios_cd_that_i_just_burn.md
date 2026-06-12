---
title: "its not loading ubutu from ios cd that i just burnt"
date: 2013-07-18
forum: New to Ubuntu
---

### Post by blake7 on 2013-07-18
hi i have burn a iso of the lastest ubuntu 
but when i put cd in to drove and click on it 
it jsut keeps trying to go on the internet to find the right program to make it work


can you help

ps im on windows xp and r trying to dual load

---

### Post by Bashing-om on 2013-07-18
blake7; Hi !

Did you verify the downloaded checksum ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Is this a desk top install; did you check the disk file integrity (disk's boot menu)?
Did you burn the .iso to disk as an image ?
Did you burn at a low burn speed ?
Did you set in bios to boot the DVD as the 1st boot priority ?

If all the above is "true" then you should at least boot to the option screen try/install ubuntu.

[INDENT][INDENT]has to be a reason[/INDENT][/INDENT]

---

### Post by ajgreeny on 2013-07-18
At the moment you are attempting to dual boot using WUBI (**W**indows **UB**untu **I**nstaller) which is a good way to check your hardware, but not really meant as a long term dual boot system.

I suggest you try booting your machine with the CD/DVD in the drive.  If your machine is set to boot a CD/DVD first it should load the Ubuntu live system from which, if it works, you can run some simple commands to show us what the current disk setup is at the moment.

Open a terminal with Ctrl+Alt+T and type ```
sudo fdisk -l
``` and report back the output here.

---

### Post by Boab1993 on 2013-07-18
If your able to click on it, i don't think you've got the right idea.
You can't access the install via windows im afraid, you have to access the BIOS, in there access the boot order and put cd/dvd as top priority.
For your specific computer you'll have to google how to access the boot menu, you access it by holding down a function key during booting up.
If you can give any more details it would help loads in fixing your problem.

Hope this helps

---

### Post by newb85 on 2013-07-18
If Windows won't load WUBI from the disc, it makes me think something's wrong with the .iso you downloaded or the disc you burnt from it, as Bashing-om suggested.

Meanwhile, I will join the chorus of voices urging you to install by booting from the install media, *not* using the WUBI installer.

P.S.--I'm confused.  How is it you have 643 beans with absolutely no other posts in your history?

---

### Post by 3rdalbum on 2013-07-19
Boab is right, you need to boot up your computer from the CD. You can't install it in Windows.

---

### Post by ajgreeny on 2013-07-30
Wubi has now disappeared from the options for dual boot, (since 13.04, I think) and it was only ever meant as a way of testing hardware, not as a long term dual boot option.

---

### Post by Chris of Arabia on 2013-07-30
Just as an alternative suggestion, whilst I was trying to rebuild my server over this last week, I was also encountering problems trying to boot into a CD I'd burnt from an iso download. I had far more success when I tried using an image burnt to a USB stick using LiLi USB Creator, and then booting to that. Make sure the USB stick is in the port before you boot, change the boot settings in BIOS (I usually only leave the USB option available and the rest turned off), then let it boot. You should end up at the Ubuntu Install menu and follows the steps from there.

---

### Post by t0p on 2013-07-30
> **Chris of Arabia said:**
>  I had far more success when I tried using an image burnt to a USB stick.

This.  Burning CDs can be problematic, whereas I don't think I've ever had a problem booting from a usb stick.

I think CDs/DVDs are on their way out.  Just my opinion.

---

