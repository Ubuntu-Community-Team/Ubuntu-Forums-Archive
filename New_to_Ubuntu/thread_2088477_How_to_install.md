---
title: "How to install"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by JeffreyDB on 2012-11-26
Hello,

I've wanted to install Ubuntu for a long time, and am serious about trying to do so on my new ultrabook which runs Windows 8.

I need to use Windows apps for companies I deal with from my home business. Ideally I would have liked to set it up as the main OS and have Windows 8 run as a window within Ubuntu. Don't know if that is possible or not. I do not have a Windows intallation disk. Next best would be to have an option to run Ubuntu as a window within Windows I believe. It seems like it would be a lot easier to switch back and forth rather than to have to close everything down and rebooting to switch between operating systems.

If those aren't feasible, I'd certainly be open to using it as a dual boot system, though I'm a little leery of partitioning the hard drive. I have never done so before, and that is what kept me from setting up Ubuntu in the past. I've typically been low on hard drive space as well. For now, I should have plenty of room to do so, however.

This has 6 GB of Ram, and is made by Acer.

Thanks for any help &/or recommendations.

---

### Post by bnosam on 2012-11-26
If you would like to run Linux inside of Windows, look into VirtualBox. It will basically create a file on your computer that will act as the filesystem for Linux, and you install Linux to it (with no partitioning) and it runs in a window.


[https://www.virtualbox.org/](https://www.virtualbox.org/)

---

### Post by LuciferRex on 2012-11-26
You can install alongside Windows, or even run Windows inside a virtual machine within linux. Heck, you can even install Ubuntu to run inside Windows for that matter.

Edit: just realized you said no install CDs for Windows, so nix the virtual machine inside of Linux.  I would do the multi-boot install, personally.

---

### Post by LuciferRex on 2012-11-26
[http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

Link to the Windows installer for Ubuntu!

---

### Post by monkeybrain2012 on 2012-11-26
> **bnosam said:**
> If you would like to run Linux inside of Windows, look into VirtualBox. It will basically create a file on your computer that will act as the filesystem for Linux, and you install Linux to it (with no partitioning) and it runs in a window.


[https://www.virtualbox.org/](https://www.virtualbox.org/)

OP says he wants to run Windows inside Ubuntu, not the other way around. VBox would work with WIn7, not sure with Win8 though.

---

### Post by LuciferRex on 2012-11-26
> **monkeybrain2012 said:**
> OP says he wants to run Windows inside Ubuntu, not the other way around. VBox would work with WIn7, not sure with Win8 though.

True, but:

> **JeffreyDB said:**
> I do not have a Windows intallation disk. Next best would be to have an option to run Ubuntu as a window within Windows I believe.

---

### Post by monkeybrain2012 on 2012-11-26
> **LuciferRex said:**
> [http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

Link to the Windows installer for Ubuntu!

This is WUBI and it is only for testing. It runs Ubuntu off a virtual disk within Windows and it is limited and buggy. I certainly won't recommend it. If OP is serious about running Ubuntu I recommend either dual booting or use Ubuntu with Win in Vbox.

Now with machines that come with Win8 there may be some new hassles involved in setting up Ubuntu because of MicroSoft's new attempt to lock down hardware with its appropriately Orwellian named "secure boot" so I can't offer any help (I haven't gotten such a machinel) except that it can be done rather easily based on other threads. I am sure someone who knows will come along and help.

---

### Post by LuciferRex on 2012-11-26
> **monkeybrain2012 said:**
> This is WUBI and it is only for testing.

Didn't know that, Thanks!

---

### Post by monkeybrain2012 on 2012-11-26
> **LuciferRex said:**
> Didn't know that, Thanks!

The next thread following this one happens to be about WUBI. It is probably quite helpful if OP considers that option.

[http://ubuntuforums.org/showthread.php?t=2088414](http://ubuntuforums.org/showthread.php?t=2088414)

---

### Post by monkeybrain2012 on 2012-11-26
Ok here is a thread on how to install Ubuntu on machines with "secure boot" (restricted boot)  Also  happens to be just several threads below this one(right now)

[http://ubuntuforums.org/showthread.php?t=2088352](http://ubuntuforums.org/showthread.php?t=2088352)

---

### Post by JeffreyDB on 2012-11-26
> **bnosam said:**
> If you would like to run Linux inside of Windows, look into VirtualBox. It will basically create a file on your computer that will act as the filesystem for Linux, and you install Linux to it (with no partitioning) and it runs in a window.

[https://www.virtualbox.org/](https://www.virtualbox.org/)

Thank you! 

No partitioning does make me feel more comfortable about it.

Will it run just as well within Windows, other than having a bit less memory to work with?

---

### Post by JeffreyDB on 2012-11-26
> **LuciferRex said:**
> You can install alongside Windows, or even run Windows inside a virtual machine within linux. Heck, you can even install Ubuntu to run inside Windows for that matter.

Edit: just realized you said no install CDs for Windows, so nix the virtual machine inside of Linux.

But they never include install disks with Windows machines anymore, do they? Do you know if they sell the disks separately for a reasonable price?

  [QUOTE=LuciferRex;12374368]I would do the multi-boot install, personally.

What is the advantage of that over running it in a virtual machine? I was thinking being able to bounce back and forth would be pretty slick. ie. If a printer, scanner or whatever only worked in Windows and I was doing something in Ubuntu, I could pop over there to do so, and then hop right back without having to reboot a couple of times.

But I've never really run Linux except on a temp live disk and only for a few times, because I had to fix the display settings etc. every time I ran it. But maybe Ubuntu could run everything out of the box, or with a few tweaks here and there.

Thanks for the reply.

---

### Post by Slim Odds on 2012-11-26
> **JeffreyDB said:**
> [QUOTE=LuciferRex;12374368]<cut>

But they never include install disks with Windows machines anymore, do they? Do you know if they sell the disks separately for a reasonable price?
<cut>
On these newer machines, there is normally a utility to burn a set of installation disks.

---

### Post by JeffreyDB on 2012-11-26
> **LuciferRex said:**
> [http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

Link to the Windows installer for Ubuntu!

Thank you. That looks quite simple compared to downloading and burning a partion disk etc. Does this partition the disk, or is that no longer necessary?

---

### Post by Slim Odds on 2012-11-26
I would highly recommend running Ubuntu using VirtualBox. That way you can use both Windows and Ubuntu at the same time.

---

### Post by JeffreyDB on 2012-11-26
> **Slim Odds said:**
> I would highly recommend running Ubuntu using VirtualBox. That way you can use both Windows and Ubuntu at the same time.

Thanks.

Does VirtualBox automatically set up the partitions, or would I need to partition the disk before hand?

Do you think it would be best to run Ubuntu in the virtual box, or Run Windows 8 in the Virtual Box?

I'm not sure if I could burn a Windows 8 install disk from a download, but perhaps that's possible. This site had a download for the consumer preview version:

[http://www.winiso.com/support/tutorials/burn-Windows8-iso.html](http://www.winiso.com/support/tutorials/burn-Windows8-iso.html)

Maybe I could check with Best Buy & get the serial number or whatever and license and upgrade the download or something along those lines.

---

### Post by Slim Odds on 2012-11-27
> **JeffreyDB said:**
> Thanks.

Does VirtualBox automatically set up the partitions, or would I need to partition the disk before hand?

Do you think it would be best to run Ubuntu in the virtual box, or Run Windows 8 in the Virtual Box?

I'm not sure if I could burn a Windows 8 install disk from a download, but perhaps that's possible. This site had a download for the consumer preview version:

[http://www.winiso.com/support/tutorials/burn-Windows8-iso.html](http://www.winiso.com/support/tutorials/burn-Windows8-iso.html)

Maybe I could check with Best Buy & get the serial number or whatever and license and upgrade the download or something along those lines.
VirtualBox uses a virtual file system inside a standard file on the host file system.

Like I mentioned in a previous post, most new Windows computers come with a utility to burn a set of install disks (DVD's) from the hard drive. You don't have to download anything.

---

### Post by StinkySQL on 2012-11-27
You may also find it helpful to read some of the problem / solution threads here re: WIndows 8. I did that for my first install on my Dell and it helped me avoid some issues.

---

### Post by JeffreyDB on 2012-11-28
> **Slim Odds said:**
> VirtualBox uses a virtual file system inside a standard file on the host file system.

Great, thanks for the info. Doing the partitioning worries me a bit. It sounds like things sometimes go awry and I don't have enough space on any external drives to back things up. I'm working on moving photos & things, so hopefully I'll eventually get there, though.

I'm also not sure I could actually add another partition. Someone mentioned in a post here somewhere that you can only have 4 partitions per disk. I found a Disk Management link in Control Panel and when I opened it up, it looked to me like Disk 0 had 4 partitions on it. One for Disk C, another 400 MB for Healthy Recovery partition, another for 300 MB Healthy EFI System Partition, and the 4th a 20 GB Healthy Recovery Partition.

There's also a Disk 1 of 18.64 GB that has 2 partitions, 3.74 GB Healthy (Primary Partition) and another 14.9 GB Healthy (Primary Partition).

My computer is an Acer Ultrabook that is supposedly a hybrid. Disk one is apparently the smaller solid state drive that should help things boot up quicker and store the most frequently used programs, as I understand it.

If there really is a 4 partition limit, it looks to me like a dual boot system might not be an option, if I understand the Disk Manager info correctly. Maybe Windows is trying to preclude people setting up dual boot systems by using up all the available partitions themselves?

I don't know if I can upload files here, but here's a link to a screenshot of the Disk Management utility: 

[http://www.mediafire.com/view/?9h7m9n7vamb60#](http://www.mediafire.com/view/?9h7m9n7vamb60#)

> **Slim Odds said:**
> Like I mentioned in a previous post, most new Windows computers come with a utility to burn a set of install disks (DVD's) from the hard drive. You don't have to download anything.

I can't find anything on my computer to do that, though I'm struggling a bit to navigate Windows 8. I did find a utlity to burn recovery disks, and posted on the Acer Forums to see if that might work, but it has very little traffic there and no answer by anyone after a couple of days or so. I also called Best Buy's Geek Squad and told them what I was trying to accomplish but the guy who answered the phone said they couldn't help at all with that. I told him I didn't want any help setting it up, I just wanted to know if there was a way to get the Windows 8 install disks. He put me on hold forever before they finally hung up on me.

I found an old thread on here where someone posted that the recovery disks probably would not work:

[http://ubuntuforums.org/showthread.php?t=466564](http://ubuntuforums.org/showthread.php?t=466564)

"That depends. If these DVDs came with the computer and I assume their  made by a company (dell or HP or such) then they usually rely on a small  or hidden partition on your computer to verify its your computer and to  prevent you from using the restore disks on any other machine. If this  is the case, no. It won't work on virtual box."

It sounds like maybe I'll need to just go ahead and make Windows the host and run Ubuntu in the virtual box. At least I could still do that without a new partition apparently.

---

### Post by JeffreyDB on 2012-11-28
> **StinkySQL said:**
> You may also find it helpful to read some of the problem / solution threads here re: WIndows 8. I did that for my first install on my Dell and it helped me avoid some issues.

Thanks for the heads up.

Are there issues for the Virtual Box option also, or just when running Ubuntu on a dual boot setup?

---

### Post by Bartender on 2012-11-28
What's the exact brand of Acer machine?  I'd be surprised if there is not a utility to make recovery discs.

Maybe Acer has changed their ways, but our 2006 Acer laptop came with 4 primary partitions.  I made the recovery discs, then ran them.  When I was done there was just one NTFS partition, which made dual-booting much easier.

EDIT - We probably need to figure out whether your ultrabook is the old-school BIOS or UEFI.  I'm guessing UEFI.  Since BIOS has been around forever and UEFI is relatively new, there's a smaller pool of shared knowledge about dual-booting UEFI than BIOS.  Also, if I'm not mistaken, W8 introduced Microsoft's Secure Boot, aka "Our latest strategy to kill Linux".  So that might be another hurtle for you.

BTW, wubi isn't "for testing".  wubi is an option for people who are put off by the idea of partitioning.  IMO wubi is inferior to a "genuine" dual-boot.  I've never run a virtual rig so can't weigh in on that option.

---

### Post by JeffreyDB on 2012-11-28
> **Bartender said:**
> What's the exact brand of Acer machine?  I'd be surprised if there is not a utility to make recovery discs.

It is an Aspire M5-581T "ultrabook".

There us a utility to make recovery disks, but I'll need to buy a 16 G or better usb disk to do so. I imagine it's pretty important to do, so I will, but haven't yet.

Unfortunately, I don't think it will work as far as allowing me to make Ubuntu as my primary system and using Virtual Box to run Windows in a window as a virtual system, at least per a post on [this thread]("http://ubuntuforums.org/showthread.php?t=466564"):

"That depends. If these DVDs came with the computer and I assume their made by a company (dell or HP or such) then they usually rely on a small or hidden partition on your computer to verify its your computer and to prevent you from using the restore disks on any other machine. If this is the case, no. It won't work on virtual box." 

I believe I could still run Ubuntu in Virtual Box, but that would require always having Windows running to do so. I guess I can live with that, but it wouldn't be my preferred option.

>  Maybe Acer has changed their ways, but our 2006 Acer laptop came with 4 primary partitions.  I made the recovery discs, then ran them.  When I was done there was just one NTFS partition, which made dual-booting much easier.

Thanks. That's very good to know. It sounds like making the recovery disks will solve that major problem.

> EDIT - We probably need to figure out whether your ultrabook is the old-school BIOS or UEFI.  I'm guessing UEFI.  Since BIOS has been around forever and UEFI is relatively new, there's a smaller pool of shared knowledge about dual-booting UEFI than BIOS.

I'm not sure where to look to find that out. According to the tag this was manufactured in August 2012, so it's pretty new. The disk manager lists one of the partitions on the main drive as: "300 MB Healthy (EFI System Partition)". I have no idea, though, if that is somehow related to UEFI.

>   Also, if I'm not mistaken, W8 introduced Microsoft's Secure Boot, aka  "Our latest strategy to kill Linux".  So that might be another hurtle  for you.

I've heard people allude to that, though I haven't searched it out yet. It sounds like they've figured out workarounds for it, thankfully.

I'm not sure if that's an issue for the Virtual Box method either. Maybe I'll get lucky and not have to deal with it.

> BTW, wubi isn't "for testing".  wubi is an option for people who are put off by the idea of partitioning.  IMO wubi is inferior to a "genuine" dual-boot.  I've never run a virtual rig so can't weigh in on that option.

It sounds to me as if Wubi is similar to Virtual Box in that it runs within Windows. I did see a couple of people complain that it caused them some issues when Windows crashed unexpectedly and messed things up. Supposedly you can install and uninstall it like you would a regular program. 

In some ways it sounds attractive to me in that I could install it and see if Ubuntu has drivers for all of the things on this computer. If the keyboard, or pointer device thingie won't work, I might not be able to use it and would just uninstall it. If other things such as the sound card or CD/DVD drive won't work I could still use it, but it would alert me to a definite downside before installing the more stable version via Virtual Box.

Thanks again for your input.

---

### Post by Bartender on 2012-11-28
> **JeffreyDB said:**
> It is an Aspire M5-581T "ultrabook".

There is a utility to make recovery disks, but I'll need to buy a 16 G or better usb disk to do so. I imagine it's pretty important to do, so I will, but haven't yet.

The disk manager lists one of the partitions on the main drive as: "300 MB Healthy (EFI System Partition)". I have no idea, though, if that is somehow related to UEFI.



I googled that Acer model - it has an optical drive, so I don't understand why you need a 16GB+ USB thumbdrive to make recovery discs.  Is that how some of these new rigs work now?  They "write" the recovery data to a thumb drive instead of discs?  If so, that's something I've never heard of before but I'm not exactly in tune to every new development.  Regardless of your future plans, it's important to make the recovery discs (or thumb drive) and stash them/it away in a safe place. 

"EFI System Partition" means the laptop boots from the UEFI partition instead of the old BIOS EPROM chip.  I have no hands-on experience dual-booting one of those so can't offer any advice, except please be careful and keep researching until you feel like you have solid instructions.

Do you have an older PC laying around?  Even if it boots from BIOS rather than UEFI, and even if you don't do a dual-boot, it'd be useful to practice installing a few times.

---

### Post by JeffreyDB on 2012-11-28
> **Bartender said:**
> I googled that Acer model - it has an optical drive, so I don't understand why you need a 16GB+ USB thumbdrive to make recovery discs.  Is that how some of these new rigs work now?  They "write" the recovery data to a thumb drive instead of discs?  If so, that's something I've never heard of before but I'm not exactly in tune to every new development.  Regardless of your future plans, it's important to make the recovery discs (or thumb drive) and stash them/it away in a safe place.

Yeah, I had a hard drive that died on me once and a guru put in a new one for me but I didn't have a copy of the operating system, nor a backup. He installed Windows XP on it for me again, and it became a big problem later when Microsoft kept telling me it was a pirated copy and asking me to pay for it again... more than the computer itself was probably worth. I think they did something to it and it runs veeeeerrryyy slow now. I don't have any free hard disk space anywhere, though, and want to try to salvage some old pictures and things from it. Once I do I would love to put Ubuntu on it. I have a few other old computers around that I'd like to try as well, but with similar issues.

I think I read somewhere that there's a server program that could be used where the older computers could be run as terminals pretty well despite having little speed in the processors and small amounts of memory. My kids would love that as they tend to fight over a computer come homework time. But I guess that'll have to wait for another day.  

> "EFI System Partition" means the laptop boots from the UEFI partition instead of the old BIOS EPROM chip.  I have no hands-on experience dual-booting one of those so can't offer any advice, except please be careful and keep researching until you feel like you have solid instructions.

It looks like the > Virtual Box setup won't require partitioning. I think I'm going to try that first and if it doesn't slow down the speed too much from having two operating systems running I'll be a happy camper. This has 6 GB of memory, so I'm hoping that will be plenty. So far I'm really pleased with the speed, but realize it will tend to slow down with time.

If it slows it down too much, or it looks like I can migrate most things to Ubuntu I may go ahead and switch to a dual boot system later. If I could retire Windows I'd be an even happier camper.

>  Do you have an older PC laying around?  Even if it boots from BIOS rather than UEFI, and even if you don't do a dual-boot, it'd be useful to practice installing a few times.

Yeah, I've got a few of them that the kids won't use any more because they're too slow. It sounds like Ubuntu or maybe one of the older Linux operating systems might speed them up a bit and make them more useful.

Thanks again for your help and insights.

---

### Post by Slim Odds on 2012-11-28
Operating Systems, by themselves, don't eat resources that much. It's when you doing something with them that they do..... i.e., running resource intensive applications.

So if you're using the OS that is in the VirtualBox and NOT the other one, they will get along just fine. If you have BOTH of them working hard, that's a different story.

If you're mostly using either one or the other, you'll be great.

---

### Post by JeffreyDB on 2012-11-29
> **Slim Odds said:**
> Operating Systems, by themselves, don't eat resources that much. It's when you doing something with them that they do..... i.e., running resource intensive applications.

So if you're using the OS that is in the VirtualBox and NOT the other one, they will get along just fine. If you have BOTH of them working hard, that's a different story.

If you're mostly using either one or the other, you'll be great.

Thanks Slim. I installed Virtual Box which was a piece of cake. Now I just need to install Ubuntu. Interestingly, I won't even need to burn an installation disk. I can just save it to my hard drive and install it from there.

I'm reading the Virtual Box manual and it doesn't appear like it will be too bad. They do say you need to pre-allocate memory, though, and potentially the amount of disk space for each virtual operating system installed. I have 6 GB of memory so I was thinking of allocating 4 GB to Windows & 2 to Ubuntu since it sounds like it's a little less resource intensive. It sounds like you can reallocate that later if you like. The disk space can either be a set, static number or can by allocated dynamically, growing as needed. Dynamic sounds great, but it supposedly does have a small system resource overhead slowing things down a bit, more at first, but gradually dropping as more space is allocated. I'm not clear whether allocating 2 GB to Ubuntu will hold it in reserve even if I haven't opened Ubuntu, but I guess I'll find out soon enough.

This looks like a great option for me if it works well. I can have access to Linux programs and Windows programs and can use both without having to reboot. You can even have more operating systems installed if you want to experiment, ie. Ubuntu versions 12.10 & 12.04.1, &/or 32 bit vs 64 bit to see which you prefer. It's supposedly very easy to just delete any you're no longer interested in as well.

I'm excited. I've wanted to do something like this for a long time. Thanks again for your help.

---

### Post by Bartender on 2012-11-29
Let us know how it goes if you proceed with virtualization, OK?

As far as the older PC's go, I'd suggest Lubuntu.  I'm running Lubuntu on a home-brew PC from 2005.  3Ghz Pentium 4, 2GB RAM.  I originally installed the standard version of 12.04 Ubuntu.  12.04 is LTS so it will be supported for 5 years.  The original plan was to just leave it be until support ran out or the PC was retired/recycled/given away.  

But it was notably slower running 12.04 than the previous LTS.  So I went to Synaptic (had to install Synaptic first from the Ubuntu Software Center) and downloaded lubuntu-desktop.  

After installing, I logged out of Ubuntu and logged into Lubuntu.  It's snappy and easy to navigate.  I don't miss the Ubuntu desktop environment.  The latest version of Lubuntu is NOT LTS, so when it runs its course I'll log out of Lubuntu, log into Ubuntu, uninstall lubuntu-desktop, then install the latest version.

If you install Lubuntu from a Lubuntu LiveCD rather than installing Ubuntu first you won't have the Ubuntu desktop environment as a backup when Lubuntu support runs out.

---

### Post by teacherjeff on 2012-11-29
I hesitate to comment since others here know so much more about Ubuntu than I do.

But I liked the WUBI experience very much. It gave me an easy (and safe: no repartitioning) introduction to Ubuntu, and for my limited needs, it seemed to work just fine. And if you do mess something up or decide you just don't like Linux, you can uninstall it under Windows with no hassle.

I ran it happily for several months. I did eventually do a real dual-boot installation, but there was no urgent need for me to do so.

---

### Post by audiomick on 2012-11-29
> **teacherjeff said:**
> 
I ran it happily for several months. I did eventually do a real dual-boot installation, 

This is exactly what is supposed to happen with WUBI. It is only intended for trying out Ubuntu, not for long term productive use. I personally don't like the idea myself at all, but that is just me.

I like a good solid dual boot. That way, if one or the other of the OS's breaks, the other one will probably still work. Even if that is not the case, my stuff is all in plain sight on normal partitions, and I can get to it from a live environment if I have to.

---

### Post by JeffreyDB on 2012-11-29
> **teacherjeff said:**
> I hesitate to comment since others here know so much more about Ubuntu than I do.

But I liked the WUBI experience very much. It gave me an easy (and safe: no repartitioning) introduction to Ubuntu, and for my limited needs, it seemed to work just fine. And if you do mess something up or decide you just don't like Linux, you can uninstall it under Windows with no hassle.

I ran it happily for several months. I did eventually do a real dual-boot installation, but there was no urgent need for me to do so.

Thanks for the feedback, teacherjeff. Wubi does sound like a great way to try it out. I tried a LiveCD a few years ago, but I couldn't save any settings and had to change the screen resolution etc. everytime I booted up with it. Wubi ought to be an improvement over having to tinker with the settings every time. I imagine it's faster that way as well.

I came across a thread, though, where someone was complaining that Windows had crashed and messed up his Wubi setup. He feared he couldn't recover some 30 GB of diskspace, but he may have been mistaken, as others said it was no different than uninstalling a regular program. It did push me to try something different, though, whether justified or not.

Does your dual boot system seem to run faster than it did under Wubi? Did you have to run both at the same time, or could you boot up in Ubuntu? Could you switch back and forth between Windows and Ubuntu on the fly, or did you need to reboot to do so?

---

### Post by teacherjeff on 2012-11-29
> **JeffreyDB said:**
> Does your dual boot system seem to run faster than it did under Wubi? Did you have to run both at the same time, or could you boot up in Ubuntu? Could you switch back and forth between Windows and Ubuntu on the fly, or did you need to reboot to do so?

I am told that performance is better under a real dual-boot installation than with Wubi, but I didn't really see a noticeable difference. (Of course, I rarely do anything more resource-intensive than run the Gimp.)

Others here can explain better than I the architecture of Wubi. While it does install and can be removed as a Windows application, it's not just a an Ubuntu emulator running under Windows. You can't move back and forth between the two on the fly. You are asked at startup whether you want to boot into Windows or into Ubuntu. (In that sense, it acts the same as a "real" dual-boot installation.)

I suppose that if you destroyed your Windows installation, it would take the Wubi installation down with it. But to me, as a relative beginner, that is much less of a concern than the possibility that I might mess up my Windows installation during a "real" installation.

I guess I just feel that for a non-expert user (like me) to be messing with disk partitions on a computer I need for work or school and for which I didn't have recovery disks would be asking for trouble. I wouldn't risk it until I felt very sure I knew exactly what I was doing.

---

### Post by Slim Odds on 2012-11-29
> **JeffreyDB said:**
> Thanks Slim. I installed Virtual Box which was a piece of cake. Now I just need to install Ubuntu. Interestingly, I won't even need to burn an installation disk. I can just save it to my hard drive and install it from there.

I'm reading the Virtual Box manual and it doesn't appear like it will be too bad. They do say you need to pre-allocate memory, though, and potentially the amount of disk space for each virtual operating system installed. I have 6 GB of memory so I was thinking of allocating 4 GB to Windows & 2 to Ubuntu since it sounds like it's a little less resource intensive. It sounds like you can reallocate that later if you like. The disk space can either be a set, static number or can by allocated dynamically, growing as needed. Dynamic sounds great, but it supposedly does have a small system resource overhead slowing things down a bit, more at first, but gradually dropping as more space is allocated. I'm not clear whether allocating 2 GB to Ubuntu will hold it in reserve even if I haven't opened Ubuntu, but I guess I'll find out soon enough.

This looks like a great option for me if it works well. I can have access to Linux programs and Windows programs and can use both without having to reboot. You can even have more operating systems installed if you want to experiment, ie. Ubuntu versions 12.10 & 12.04.1, &/or 32 bit vs 64 bit to see which you prefer. It's supposedly very easy to just delete any you're no longer interested in as well.

I'm excited. I've wanted to do something like this for a long time. Thanks again for your help.
You're welcome....

The memory (RAM) is only used then the Virtual Machine is running. The disk space allocated is permanent (until you delete it yourself).

---

### Post by JeffreyDB on 2012-11-29
> **teacherjeff said:**
> I am told that performance is better under a real dual-boot installation than with Wubi, but I didn't really see a noticeable difference. (Of course, I rarely do anything more resource-intensive than run the Gimp.)

Others here can explain better than I the architecture of Wubi. While it does install and can be removed as a Windows application, it's not just a an Ubuntu emulator running under Windows. You can't move back and forth between the two on the fly. You are asked at startup whether you want to boot into Windows or into Ubuntu. (In that sense, it acts the same as a "real" dual-boot installation.)

Thanks, that's good to know. That's one difference between Wubi & Virtual Box, which does allow you to switch back and forth on the fly.

> I suppose that if you destroyed your Windows installation, it would take the Wubi installation down with it.

It sounded to me as if Windows shutting down improperly messed up the Wubi installation even though the Windows system would still boot up correctly.

> **teacherjeff said:**
> But to me, as a relative beginner, that is much less of a concern than  the possibility that I might mess up my Windows installation during a  "real" installation. I guess I just feel that for a non-expert user (like me) to be messing with disk partitions on a computer I need for work or school and for which I didn't have recovery disks would be asking for trouble. I wouldn't risk it until I felt very sure I knew exactly what I was doing.

That is very much my feeling as a complete newbie as well. It looks to me as though the Virtual Box option has that same advantage of ease of installation without having to mess with the partitions. It looks like it has the advantage of allowing running Ubuntu in a Window within Windows (or Windows within a Window in Ubuntu if you have the actual original installation disks), with the downside of using up some additional memory for the privilege.

---

### Post by Slim Odds on 2012-11-29
The primary difference between WUBI and running Ubuntu using VirtualBox is that WUBI runs Ubuntu natively, whereas VirtualBox provides a virtual machine (i.e., not real hardware, but access to most of it).

For example, with VB you will NOT be able to use high performance video drivers.

Both use the Windows file system to store their entire system data (programs and data).

---

### Post by JeffreyDB on 2012-11-29
> **Slim Odds said:**
> The primary difference between WUBI and running Ubuntu using VirtualBox is that WUBI runs Ubuntu natively, whereas VirtualBox provides a virtual machine (i.e., not real hardware, but access to most of it).

For example, with VB you will NOT be able to use high performance video drivers.

Both use the Windows file system to store their entire system data (programs and data).

I got the impression from a thread or two on here that WUBI wasn't quite the same as running it stand alone. Someone was saying something about the file structure and how things were stored and that it wasn't as secure for some reason or other. Perhaps the same is true of running it virtually in VB.

In any event I did download and install VB & then downloaded and installed Ubuntu 12.04.1 64 bit in it. It seemed like it opened up in a bit smaller window, even when maximized, sort of like a regular movie on a widescreen TV with black sections on each side. The settings window is different than the control panel, of course, and there were only two options for the video resolution, and it was already in the highest resolution.

Playing around with it, I saw an icon for downloading drivers and there was only one option, for a Guest package. I had read in the manual it had to be downloaded after everything else was already installed, so I went ahead and clicked on that. It had to be restarted to take effect, but the restarts are for the Ubuntu only and it is very quick. I think that is what fixed the screen size issue. Now it works in full screen, yay!

It's a little bit different than just having an Ubuntu window within Windows, but not much. The keyboard is "captured", so hitting the alt + backtab will scroll through open windows within Ubuntu, but won't go out to any Windows windows unless you hit the "escape key" or whatever they call it, first. By default it is the right control key (which can be changed if you like). It's not really any big deal, but takes a little getting used to at first.

I looked at a pretty high quality Youtube video and it looked like the video was very good. The default setting during setup for the guest Ubuntu was 5xx MB of memory and I bumped it up to 1 GB.

I'll have to play around with the programs some to see if I can get everything to work. Audacity wasn't recording, but that was before I did the guest package thing, so maybe that will fix it. It took me a day or two getting it to work when I moved from XP to Vista, and then again when I just moved to Win 8, so I guess that's par for the course.

I was a little disappointed that I couldn't venture off of that virtual disk to look at Windows files. I had burned a Live CD of Ubuntu some years ago when I first wanted to install it, but never did unfortunately. When someone gave us a computer and it wouldn't boot up a couple of weeks or so later I tried that Live CD and it not only booted up to it, but I could browse around all of the Windows files with no problems. That surprised me, and I guess gave me unreasonable expectations I might be able to do that here. It certainly would have made it easier to switch back and forth seamlessly. Oh well. I guess I could do the same thing to an extent, by using Ubuntu One &/or other cloud storage options, though I'm leery of doing so with sensitive documents.

Now I guess I'll have to play around with it and try and learn a lot more about Ubuntu and some of the new programs available to me.

Thank you everyone for helping me. It is most appreciated. Hopefully I can return the favor some day.

---

### Post by Slim Odds on 2012-11-30
> **JeffreyDB said:**
> I got the impression from a thread or two on here that WUBI wasn't quite the same as running it stand alone. Someone was saying something about the file structure and how things were stored and that it wasn't as secure for some reason or other. Perhaps the same is true of running it virtually in VB.
Like I mentioned, WUBI uses the Windows file system but runs directly on the hardware. Unlike VB which uses the Windows files system but runs on a "virtual machine" (i.e., not directly on the hardware).

> **JeffreyDB said:**
> <cut>
I was a little disappointed that I couldn't venture off of that virtual disk to look at Windows files. I had burned a Live CD of Ubuntu some years ago when I first wanted to install it, but never did unfortunately. When someone gave us a computer and it wouldn't boot up a couple of weeks or so later I tried that Live CD and it not only booted up to it, but I could browse around all of the Windows files with no problems. That surprised me, and I guess gave me unreasonable expectations I might be able to do that here. It certainly would have made it easier to switch back and forth seamlessly. Oh well. I guess I could do the same thing to an extent, by using Ubuntu One &/or other cloud storage options, though I'm leery of doing so with sensitive documents.
<cut>
You can share a windows directory with VB and mount it in the virtual instance of Ubuntu.

---

