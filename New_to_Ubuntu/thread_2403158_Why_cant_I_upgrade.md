---
title: "Why cant I upgrade"
date: 2018-10-08
forum: New to Ubuntu
---

### Post by robert1305-gmail on 2018-10-08
Hi after a forced absence of nearly 3 years from my OS of choice (Linux) I am now back on track.

The problem is two year ago I had a stroke, although I have improved physically really well I have no short term memory and very little attention span, and things have moved on in the PC world. LOL

The thing is I am dual booting with Linux mint and Ubuntu gnome 17.04, I did purchase a DVD from Linux for Ubuntu 19. but the disk would freeze on reaching desktop, I now have received a message that an upgrade is available, tried this but get the message that this is not compatible with my equip, having just purchased 4 weeks ago a new all in one Hp PC, can anyone explain whats happening I took the PC back to PC and they did a two hour diagnostic check, every thing perfect !!

So it lt looks like a software problem? or a setting needs altering some where. 

Any help would be gratefully appreciated.

Regards Bob

PS I have a few old DVD of Linux distros and they load up OK?????

---

### Post by Geoffrey_Arndt on 2018-10-08
Hello Robert.   I am assuming you actually meant to say "I did purchase a DVD from Linux (? who ?) for Ubuntu 16" (instead of Ubuntu 19 won't be released until April next (2019) year.    Given that, you can't upgrade from Ubuntu 17.04 to anything . . . it's already out of date.  The interim releases are supported for nine months from release date. (so it was out of date since February 2018).

So, what's needed is to get the latest 18.04 LTS iso on either DVD or on usb stick.

---

### Post by Autodave on 2018-10-08
Assuming that your present install is working and you have internet, just download a version of 18.04 and install it.

---

### Post by Topsiho on 2018-10-10
I agree with the other posters that you should download Ubuntu 18.04 (or 16.04, which is maintained until 2021, 18.04 until 2023), and install that instead of Ubuntu 17.04.
You can see on [https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index](https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index) whether your HP-printer is supported by the HPLIP-version that comes with Ubuntu. If it is a new printer your chances are greater with Ubuntu 18.04.

Glad you are coming back on track :)

Topsiho

---

### Post by jglen4902 on 2018-10-10
I can understand your issues.  I'm of an age where many things have escaped from memory, and I find the need to make notes and keep them visible.

I recently did a clean install of Kubuntu 18.04.1, after using Kubuntu 16.04 from .1 through .5.  Much of what I will relate here will pretty well work with Ubuntu.  Both 16.04 and 18.04 are LTS and both will be supported for a long time.  but since I only use LTS anymore, it's just simpler for me to make use of the latest.

I have in recent years started only at the first point release after the LTS is released - thus 18.04.1.

I downloaded from the Kubuntu download site (you can get the Ubuntu from the Ubuntu site).  Once I had it on disk, I verified the checksum with sha256sum on the command line.

The next step was to burn it to a USB thumb drive.  I used the standard Unetbootin that was on my 16.04.5 desktop PC.  I had zero problems burning to the thumb drive, but there are plenty of options.  I did experiment with using dd on the command line, and it did the job, too.  I just used the Unetbootin-burned thumb drive.

My desktop unit's Gigabyte motherboard does use UEFI or legacy BIOS, I just configured UEFI and had no problems.

1) First, I did a complete backup of my /home to an external drive.  When that was done, I unmounted that drive, and shut the computer down.

2) I cold booted the PC with the thumb drive in a USB port, and the Live 18.04.1 version showed up fairly quickly.  I then started my wifi, poked around the Live 18.04.1 a little and hit the Install option.

3) Since I already had a separation of the / and /home directories on separate partitions, I selected the "Something Else" option, which is essentially a manual install.

4) I use the ext4 filesystem - I don't mess with BTRFS or Raid configurations or anything else - it's just my PC with my data and it works perfectly without the fancy stuff.

5) I selected the current sizes already being used for each partition, and ext4, and formatted ONLY the / partition.  The /home was simple selection WITHOUT selecting the format option.  I also kept my 16GB SWAP partition.  I confirmed that this what I wanted, and let the install start, following the prompts, including downloading updates while installing.  Since the wifi was already started, everything installed wirelessly.

6) At the end of the install, it was simply a matter of removing the USB thumb drive, and restarting the PC.

Aside form some configurations, removing applications that I don't want, installing some applications that I do want, some minor config changes.  "It just works."  The builtin print application recognized my HP printer without the need for the full HP software.

Truth be told, there are some details that I have not listed, because they were choices associated with UEFI.  But I did some research and made notes before starting, and my own checklist which proved very useful.

Like I said - IT JUST WORKS :KS

---

