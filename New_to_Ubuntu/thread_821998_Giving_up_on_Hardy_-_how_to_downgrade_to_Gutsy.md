---
title: "Giving up on Hardy - how to downgrade to Gutsy?"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by mgbridges on 2008-06-07
Hi,

I've finally reached the end of my tether with Hardy. It locks up way too much, making the machine practically unusable. I've searched the forums and tried all sorts of suggestions but nothing makes it more stable. I can't go on like this so I've decided to go back to Gutsy, which was stable for me.

The question is, how to do this while retaining at least some of my settings (e.g. Samba settings)? Has anyone gone through this process and can offer any tips?

Ubuntu is installed on one drive and all my data is on a separate drive. It's a single-boot setup (no Windoze anywhere near the machine).

Cheers for any advice.

Martin

---

### Post by avtolle on 2008-06-07
You'll need to do a fresh install of Gutsy in the "normal" manner; that is, if you don't still have your Gutsy disk from before, d/l the iso, burn to CD, etc. With the data on a separate drive, it should be OK, but as I've no experience with this, I'd back it up as a precaution. Good luck.

---

### Post by Frak on 2008-06-07
Unfortunately, it is practically impossible to downgrade a system. You may want to back up your /home folder to a USB/CD/DVD and reinstall Gutsy.

---

### Post by mgbridges on 2008-06-07
Are there some folders I should backup to save myself having to set up Samba and my RAID array etc. from scratch after doing the re-install?

Martin

---

### Post by stmiller on 2008-06-07
Backup the entire /etc directory. This has all of the system configuration files. 

Be aware though, that things like samba, cups, etc in Gutsy are a different version than hardy. So some things in your config file from Hardy may not work when forced on Gutsy.

---

### Post by avtolle on 2008-06-07
Beat me to it, stmiller. :-)

@OP: thought of this after my earlier post, and was on my way to edit, but stmiller saved me the trouble.

---

### Post by mgbridges on 2008-06-09
OK, I've downloaded a 7.10 ISO and created a CD - how do I get the PC to detect that I want to boot from this, rather than booting normally? Whenever I reboot the PC just goes straight to the Hardy logon screen.

I'm obviously missing something simple.

Martin

---

### Post by Kevbert on 2008-06-09
To boot from CD first is normally a setting in bios.  When you first start the machine this will be an option (normally hold down delete key, F1 or something like that).  Then you need to set the boot order (normally removeable media - floppy, CD and then finally hard disk).

---

### Post by mgbridges on 2008-06-09
Although I'm a bit of a Linux newbie, I know the basics of dealing with PCs. I realize that I have to get into the BIOS somehow in order to set the boot order, but I'm not getting given the option during the startup sequence. I'm not seeing the motherbpoard splash screen, and I've tried holding down CTRL, DEL, F1, Tab and anything else I can think of during boot, but it just goes straight (after quite a delay) to the logon screen.

What could I be doing wrong??

Martin

---

### Post by takitez on 2008-06-09
Once you are in the Linux start up (actually in the GRUB boot loader or later) it is too late.  Getting into the BIOS setup on my machine requires hitting the del key, but it could be different depending on your manufacturer.  What is the first screen you see when you boot?  It should say on there how to get into setup...

On the topic of giving up on Hardy, I have had two freezes so far, so yes it is frustrating.  On both occasions I was running several applications, including heavy network use.  Looking in my system log after rebooting, I see some scary messages right at freeze time:

Jun  8 05:20:09 photon1 gdm[5626]: GLib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed 
Jun  8 05:20:09 photon1 gdm[5626]: GLib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed 
Jun  8 05:20:09 photon1 gdm[5626]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed 

... but I have no idea what they mean or what to do about them.  Those who have not "given up on Hardy" quite yet, but are seeing freezes, are you seeing these messages?  Let's compare entries in this discussion and see if we can't give the Ubuntu developers something to go on in fixing this.

---

### Post by Midwest-Linux on 2008-06-09
Regarding the lockup... it sometimes happens when there is too little RAM, the wrong RAM, not enough speed. Suggesting those possible problems. What are your computer specs..RAM, Speed, Pentium version , Hard drive space ? 

 If hardware is the problem, it should be able to fix. If not you at least eliminated one potential problem area and can go to the next item.

 Also was the Hardy install disc checksum number OK? Was the disc burned properly and at a low speed? Did you use the live or alternate install CD?

---

### Post by Kevbert on 2008-06-09
> **mgbridges said:**
> Although I'm a bit of a Linux newbie, I know the basics of dealing with PCs. I realize that I have to get into the BIOS somehow in order to set the boot order, but I'm not getting given the option during the startup sequence. I'm not seeing the motherbpoard splash screen, and I've tried holding down CTRL, DEL, F1, Tab and anything else I can think of during boot, but it just goes straight (after quite a delay) to the logon screen.

What could I be doing wrong??

Martin

Are you seeing the POST screen when the PC checks how much memory is available ?  Do you know the motherboard make/model or PC make/model ?

---

### Post by stalkingwolf on 2008-06-09
on some computers hitting f12 at boot will get you a onetime boot menu.  On some compaqs if you alternate hitting alt and del during
boot you will get this boot option also.

---

### Post by melrom on 2008-06-09
yep. it's F12 for my Dell XPS.

---

### Post by takitez on 2008-06-09
Well, forget the log entries, this last time it froze I was more methodical about looking at the timestamps, and there were no messages right before the freeze, all the messages were too old to be part of the freeze or after the boot.

I did checksum my i386 Ubuntu 8.04 disk prior to install, the main one on the Ubuntu site: 

Ubuntu 8.04 LTS Desktop Edition - Supported to 2011, standard x86

Again, heavy network use, multiple applications doing something on the Internet, preceded the crash.

I was monitoring the system, was using less than half my 2 gig memory, and none of my 4 gig swap.  Disk space well below 10% used.

---

### Post by mgbridges on 2008-06-10
> **Kevbert said:**
> Are you seeing the POST screen when the PC checks how much memory is available ?  Do you know the motherboard make/model or PC make/model ?

Nope, not seeing the POST screen at all. Motherboard is an Asus M2A-VM.

Cheers,

Martin

---

### Post by mgbridges on 2008-06-10
> **Midwest-Linux said:**
> Regarding the lockup... it sometimes happens when there is too little RAM, the wrong RAM, not enough speed. Suggesting those possible problems. What are your computer specs..RAM, Speed, Pentium version , Hard drive space ?

My PC is an AMD 64X2 4800+ with 2Gb RAM and over 60Gb of free diesk space, so I doubt that's an issue.

> **Midwest-Linux said:**
> Also was the Hardy install disc checksum number OK? Was the disc burned properly and at a low speed? Did you use the live or alternate install CD?

I didn't install Hardy from CD. I installed Gutsy from a Live CD and used it happily for a couple of months then did the online upgrade to Hardy via Synaptic.

Martin

---

### Post by Kevbert on 2008-06-10
Hi Martin.  Just had a quick look at your [motherboard manual]("http://support.asus.com/download/download.aspx?SLanguage=en-us")  That's one mighty fine mobo.  According to the manual it suggests that you just need to press the delete key when post occurs.  I assume you've updated the bios at some stage.  It may be worth resetting the bios to default settings (as detailed in manual).  Seeing as you may need to change the bios via flash, CD or floppy I would have thought that booting from CD would be left on by default.  Are you sure the 7.10 CD is fine ?
Best of luck
Kevin.

---

### Post by d.kusummmanth@gmail.com on 2008-06-10
Checkout my thread: 
[How many of YOU are still using 7.10 like me, or even earlier versions???]("http://ubuntuforums.org/showthread.php?t=821682")

**I'm happy that I never made "the leap" to 8.04.** I can't understand why Ubuntu developers don't care about users with older hardware. Maybe, they should release a separate version of Ubuntu for users with [COLOR="DarkRed"]**'not-so-latest hardware'**[/COLOR], and the normal version for users with [COLOR="DarkRed"]**'Yes!-I-have-the-latest-and-the-fastest-hardware-in-the-market!!-Yuppiee!!'**[/COLOR] kind of users. That way both of us will be happy.

And why the bloody hell does Ubuntu not have downgrading option( that's so much like Microsoft's policies)???? Why can't they tweak the OS to allow users like this, who are unhappy with the latest OS and want to 'go back'.

---

### Post by mgbridges on 2008-06-10
> **Kevbert said:**
> Hi Martin.  Just had a quick look at your [motherboard manual]("http://support.asus.com/download/download.aspx?SLanguage=en-us")  That's one mighty fine mobo.  According to the manual it suggests that you just need to press the delete key when post occurs.  I assume you've updated the bios at some stage.  It may be worth resetting the bios to default settings (as detailed in manual).  Seeing as you may need to change the bios via flash, CD or floppy I would have thought that booting from CD would be left on by default.  Are you sure the 7.10 CD is fine ?
Best of luck
Kevin.

I've solved this problem, at least. It seems that my mobo was not displaying the POST screen when connected to the monitor via the DVI cable. So I couldn't see when it had gone into the BIOS setup screen, so it timed out and carried on booting. Connecting to the screen via an RGB output allowed me to see the POST screen, enter the BIOS, change the boot order so CDRom was first, then boot from the 7.10 Live CD.

So I have re-installed 7.10 and am currently trying to re-establish my settings. Let's hope it's as stable now as it was first time round.

Thanks for all the suggestions. It certainly was a weird problem.

Martin

---

### Post by jflarm on 2008-06-10
> **d.kusummmanth@gmail.com said:**
> Checkout my thread: 
[How many of YOU are still using 7.10 like me, or even earlier versions???]("http://ubuntuforums.org/showthread.php?t=821682")

**I'm happy that I never made "the leap" to 8.04.** I can't understand why Ubuntu developers don't care about users with older hardware. Maybe, they should release a separate version of Ubuntu for users with [COLOR="DarkRed"]**'not-so-latest hardware'**[/COLOR], and the normal version for users with [COLOR="DarkRed"]**'Yes!-I-have-the-latest-and-the-fastest-hardware-in-the-market!!-Yuppiee!!'**[/COLOR] kind of users. That way both of us will be happy.

And why the bloody hell does Ubuntu not have downgrading option( that's so much like Microsoft's policies)???? Why can't they tweak the OS to allow users like this, who are unhappy with the latest OS and want to 'go back'.

The downgrade is not a good option, because it gives the impression that every new release is not stable (even if it's true).
And there is an ubuntu for the not-so-latest-hardware...it's the xubuntu, I've tried it, and works quite well.

---

### Post by forestpixie on 2008-06-10
> Maybe, they should release a separate version of Ubuntu for users with 'not-so-latest hardware', and the normal version for users with 'Yes!-I-have-the-latest-and-the-fastest-hardware-in-the-market!!-Yuppiee!!' kind of users.

@d.kusummmanth - I'm running hardy on a 6 year old motherboard and 5 year old graphics card and have had no real problems other than a blip[ when I installed the nvidia driver. It runs better now than it did before. The trouble with watching the forum to see how many people have had problems - is that is all you get to see. Those who have been ok have no need to report the fact.

> It seems that my mobo was not displaying the POST screen when connected to the monitor via the DVI cable.

@mgbridges - that's a little fact worth remembering :)

---

### Post by Frak on 2008-06-10
> **d.kusummmanth@gmail.com said:**
> Checkout my thread: 
[How many of YOU are still using 7.10 like me, or even earlier versions???]("http://ubuntuforums.org/showthread.php?t=821682")

**I'm happy that I never made "the leap" to 8.04.** I can't understand why Ubuntu developers don't care about users with older hardware. Maybe, they should release a separate version of Ubuntu for users with [COLOR="DarkRed"]**'not-so-latest hardware'**[/COLOR], and the normal version for users with [COLOR="DarkRed"]**'Yes!-I-have-the-latest-and-the-fastest-hardware-in-the-market!!-Yuppiee!!'**[/COLOR] kind of users. That way both of us will be happy.

And why the bloody hell does Ubuntu not have downgrading option( that's so much like Microsoft's policies)???? Why can't they tweak the OS to allow users like this, who are unhappy with the latest OS and want to 'go back'.
1. It really depends on the kernel modules included. I can forsee the dev's leaving out some because they are waaaaaaay out there hardware (such as a network card make by Amiga. Why support that?). Xubuntu should help you.

2. Downgrading is much harder on Linux for a million different reasons.
   1. You would need to install reverse packages for nearly your entire system. - Hours
   2. Just upgrading guarantees breakage, so you can understand a downgrade.

---

### Post by timzak on 2008-06-10
Just an FYI--at least on my system, just because I cannot see the POST screen doesn't mean you can't enter the BIOS.  My system uses F2 to get into the BIOS, so I just repeatedly press F2 during the POST process (even though I can't see anything on the screen).  It never fails to get me into the BIOS.  I just hope to save you having to switch monitor cables if you ever have to do it again.

Good luck with Gutsy.  Hope it works like it used to for you.

> **mgbridges said:**
> I've solved this problem, at least. It seems that my mobo was not displaying the POST screen when connected to the monitor via the DVI cable. So I couldn't see when it had gone into the BIOS setup screen, so it timed out and carried on booting. Connecting to the screen via an RGB output allowed me to see the POST screen, enter the BIOS, change the boot order so CDRom was first, then boot from the 7.10 Live CD.

So I have re-installed 7.10 and am currently trying to re-establish my settings. Let's hope it's as stable now as it was first time round.

Thanks for all the suggestions. It certainly was a weird problem.

Martin

---

### Post by philinux on 2008-06-10
I'm running Hardy on my main machine and my 1999 relic pentium 3 320meg memory and it runs fine if a tad slow at booting and launching apps. but its fine for web browsing etc.

---

