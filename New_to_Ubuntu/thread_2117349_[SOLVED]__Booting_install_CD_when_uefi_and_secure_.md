---
title: "[SOLVED]  Booting install CD when uefi and secure boot are enabled"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by squakie on 2013-02-18
I had a previous post asking about installing Ubuntu on a new laptop with Windows 8, and was given some pointers and some things to read. With the reading and research I've done, I felt it was more appropriate to open a new thread.
 
My understanding, put in simple terms, is that the problem comes in with secure boot enabled in the BIOS. Microsoft wanted to try to cover some of the security holes, so with secure boot it requires a key in a database that says it's ok to use the binary - in this case the boot loader. In this way malware attempts at modifying the boot will not "take" in that the computer will not boot.The argument is legitimately there that is also Microsoft trying to restrict what OS is being installed. It appears that Fedora and Canonical have 2 different approaches to this, with Canonical's still being questionable in terms of needing the key to be secure versus the Free Software Foundation's GPLv3 usage saying the source must be available - and in this case the argument is about the key. Everything I have read so far hasn't indicated if that issue has been resolved yet. This is being attempted so that the normal user doesn't have to have any knowledge of or any interfacing to the secure boot technology. 
 
I have read that 64-bit Ubuntu 12.04.03(?) and 12.10 have had the ability to detect uefi and secure boot and work around it to some degree.
 
So, with that in mind, and given that I have a new Dell laptop with Windows 8, uefi, and secure boot enabled and that I don't want to do something to that would effect my warranty, will the Ubuntu 12.10 64-bit install CD actually boot when uefi and secure boot is enabled? What I've tried so far has not been allowed to boot.
 
Sorry if this sounds sort of technical - I've tried to dumb it down as best I can. I also hope that my understanding and how I have worded it here are accurate. My concern is for myself, for current users who buy a new PC and for those people with newer hardware (uefi with secure boot enabled) to be able to boot the install CD, install Ubuntu and still be able to boot everything on the system okay when all is done.
 
I believe this applies to systems with Windows 8, but I may be in error there.
 
In looking at the forum, it appears there are a lot of people who have been having problems with uefi and Windows 8 - and I believe some of those are related to secure boot being enabled in the BIOS. So obviously it is a "big" deal. I'm just looking at the simplest usage - just trying to boot the install CD, while I recognize that this "simplest usage" also goes right to the heart of the matter.

---

### Post by grahammechanical on 2013-02-18
> I have read that 64-bit Ubuntu 12.04.03(?) and 12.10 have had the ability to detect uefi and secure boot and work around it to some degree.

To be accurate that is 64 bit Ubuntu 12.04.2. This second point release of Ubuntu 12.04 now has the kernel from 12.10 = Linux 3.5.0 kernel. It is this kernel that has been signed by a key validated by Microsoft. So, there are now 2 versions Ubuntu that should load and install (all things being equal) on a secure boot enabled motherboard. That is 12.04.2 and 12.10.

You say that the live session is not loading? Is there any message or signs and symptoms to indicate what the reason is? The issue might not be anything to do with Secure boot but something else - such as the need to use one of the F10 options.

From my browsing of the forums I see more than just an issue with secure boot being enabled. That should not be an issue at all. I do see issues with Fast boot being enabled and Windows dynamic disks and Windows using up all 4 allowed primary partitions. Then there is a failure to defrag the Windows partitions before moving/resizing them and not using Windows utilities to remove/resize Windows partitions. And do not forget the failure of users to do the research.

Linux has been able to deal with UEFI and GPT for years now. The present the complications come from OEMs deviating from the specifications (such as Samsung) and users having, what I think of, as the unreasonable expectation that they should be able to install Linux on any hardware, even the very latest hardware, with any operating system already installed.

As regards this comment

> with Canonical's still being questionable in terms of needing the key to be secure versus the Free Software Foundation's GPLv3 usage saying the source must be available

Read this and you will see that the Linux Foundation has taken the same approach as Canonical.

[http://blog.hansenpartnership.com/linux-foundation-secure-boot-system-released/]("http://blog.hansenpartnership.com/linux-foundation-secure-boot-system-released/")

As regards the Fedora approach, read this

[http://mjg59.dreamwidth.org/19448.html?thread=724984]("http://mjg59.dreamwidth.org/19448.html?thread=724984")

And note this:

> As originally envisaged it would do nothing other than load and execute **appropriately signed binaries**, but it's got a little more complicated than that now. It is, however, basically feature complete at this point - I don't expect it to grow significantly further.

I do not know of any way to install a Linux distribution without getting a kernel key from Microsoft so that appropriately signed binaries will be recognised as valid. And then there is this comment:

>  the Free Software Foundation's GPLv3 usage saying the source must be available - 

That has been resolved long ago. Canonical was not going to use Grub in 12.10 because of the FSF's lack of clarity on this matter. Then the FSF cleared things up (indicated that they would not take Canonical to court for not revealing the secure boot key) and so Grub was put back as the boot loader for 12.10 and is still the boot loader for 13.04.

Regards.

---

### Post by oldfred on 2013-02-18
From what I have seen a few systems just work, a few have issues and some just do not work.

But the issue is the vendors implementation of UEFI. The Microsoft spec says that the user must be able to turn off secure boot. And some users have posted that they can dual boot with secure boot on or off.

       Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries

            Lenovo ThinkCentre M92p only boots Windows or Redhat. Hard coded into UEFI.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

    
       UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)
[http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html](http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html)
The problem also appears to affect Ubuntu 12.10 and other Samsung models. The Ubuntu bug report includes posts from users reporting that the problem also affects 300E5C, NP700Z5C, NP700Z7C and NP900X4C series laptops.

    
       Protection against Samsung UEFI bug merged into Linux kernel
[http://www.h-online.com/open/news/item/Protection-against-Samsung-UEFI-bug-merged-into-Linux-kernel-1795332.html](http://www.h-online.com/open/news/item/Protection-against-Samsung-UEFI-bug-merged-into-Linux-kernel-1795332.html)
Since these patches have not yet been integrated into the installation media for these distributions, users should always use the UEFI firmware's Compatibility Support Module (CSM), which emulates a BIOS mode, when booting on affected laptops. 
The current state of UEFI and Linux = Feb 1, 2013 - Matthew Garrett
Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)
Matthew Garrett's Blog
[http://mjg59.dreamwidth.org/](http://mjg59.dreamwidth.org/)
New Linux UEFI boot loader
[http://mjg59.dreamwidth.org/23113.html](http://mjg59.dreamwidth.org/23113.html)
    
Even after some of the fixes in Ubuntu, it now turns out that Samsung can brick itself even with Windows.

---

### Post by squakie on 2013-02-18
Thank you both for the information - it was helpful.  I will try downloading 12.10 again and see if it will boot the livecd now.  I accidently trashed (like in actually put in the trash!) the last  one I had for 12.10 - perhaps it was too early a version?  I remember I got a message - the text of which I don't recall - which basically said I was not allowed to boot the OS.
 
I'll let you know what happens with a new download.
 
I guess the information I read may have been somewhat out of date.  I'm glad to see that the Linux community been able to  to use a key without having to release it publicly.
 
I have uefi on the Asus M5A97 motherboard on my desktop and it has always booted everything fine.  When I built that a little over a year ago I did more than just overkill for me (16gb, 8 core 3.1ghz cpu 1.5tb hard drive 60gb SSD), so I ordered this new laptop (it's just a Dell 15R) to just use and not the desktop, so I just sold the desktop on Ebay.
 
The laptop has uefi and also has secure boot enabled.  The livecd boot failed with a message indicating it could not boot the OS - this happens almost immediately.
 
I was looking to see what progress has been made (and apparently a lot) on Ubuntu loading without turning secure boot off in the BIOS.  If I can get the livecd to run so I can check things out, then would I be able to have Ubuntu installed on an external USB hard disk and still have Windows 8 be able to boot without the drive plugged in, or will it still be dependent on where grub is installed?  Not sure I'm stating that correctly but I think you understand.
 
Thanks again!

---

### Post by squakie on 2013-02-18
Ok, I downloaded the 64-bit 12.10 ISO and burned it - this time at the BIOS boot selection screen showed uefi with ubuntu 12.10 so that's different then what I had before. I'm guessing my old disk was 12.04 or 12.10 prior to the change for the key being included. So, the good news is that the Live disk booted fine, wireless works and I'm posting this while running off the Live disk.  Now I guess I could use some pointers to either a how-to for installing (things like how to partition in Windows 8, actually installing - I assume no different from any other install) and being sure I haven't messed up the ability to boot Windows 8, all with the uefi and secure boot still enabled.  

I'm sure this has all been asked a zillion times by now, but I can't seem to find a document that says with uefi do this to partition and install, if Windows 8 is installed and uefi and secure boot do this to partition and install, etc..   I'm hoping someone can point me to one already in existence that hopefully also has comments regarding special things needed for certain PCs.

I've tried my best to try to understand all of the things that have changed since I "worried" much about learning the details.  Windows 8 is at least to me a PITA.  I would assume with a new PC with Windows 8 preloaded it is using the "new" partitioning scheme - I think that may be the dynamic partitions but I don't know.  So, some pointers to threads/docs that explain that in relation to making room for ubuntu partitions would be greatly appreciated.

I'm sorry I sound so dumb - normally this wouldn't be a problem for me at all, but before I ordered the PC I read many horror stories on the forums about installing and trying to dual-boot ubuntu and Windows 8.

If it would be ok, I would like to try to create some sort of "how-to" thread at least for my model of laptop - perhaps the majority, if not all, of the specifics would be generic enough for it to be a how-to to which everyone could add things - that is, of course, if no such thing exists.  So far the things I've been reading aren't really the whole picture.  One of them even talks about just "forcing" the installation.  I want to do it so that I have the absolute best possibility of success before I start (like almost everyone, I fought those battles when I first started using linux, and I'd prefer not to make similar mistakes that render my PC useless until a lot of manual work is done).

Thanks again!

---

### Post by squakie on 2013-02-19
Okay - the partitions were of basic layout, and there were 4 system/oem partitions and a primary partition that Windows is on.  I ran the optimize and defrag tool in Windows 8, rebooted, then went in via Windows 8 disk management and shrank that partition by 50gb (it's a 1tb drive, so I have plenty of space).  Then rebooted again to be sure Windows was ok.

Booted the livecd for ubuntu 12.10 64-bit downloaded today, selected install, went to the manual partitioning (I believe it's always been called "Something Else").  I created a new swap partition (logical), a root partition (/) (logical) and a home partition (logical).  I let the install continue from there.

Upon reboot, no grub menu - boots straight into Ubuntu.  I know I didn't wipe out the Windows partitions.  Right now I don't understand why no grub menu.  I'm going to try update grub and see what happens.  I've seen mention of this in other threads when installing for dual boot with Windows 8, so I need to go back and re-read a ton of those to try to figure this out.

---

### Post by squakie on 2013-02-19
Just trying to document every step I am taking so others can see if they are experiencing similar problems.

I restarted the PC and (on my PC it's press F12) went to the boot selection menu.  Windows 8 is still there and boots fine when I select it there.

Ubuntu is the first OS on the boot selection menu (not grub - it never gets there).  Windows 8 is 2nd.  If I select Ubuntu, it boots fine as well - but no grub menu.

I ran update-grub and it only found the Ubuntu installation.  It said it was updating grub so that it included EFI boot.

So, now it's back out to try to find something else to try.

---

### Post by squakie on 2013-02-19
Found posts saying to run the boot-repair disk.  Downloaded and burned it, but it's not uefi so it doesn't show in the boot options.

Which also leaves me a little confused:  I thought secure boot is what said you needed a key, and while it is against my aim (installing this without needing to know much - like a new user!) I did turn secure boot off.  However the CD doesn't show in the BIOS boot menu - so this must be something with uefi, and I didn't think uefi was supposed to lock you out of anything - just provide a means to extend the BIOS on board.

Going to try installing boot-repair directly in my running Ubuntu and see what happens then.

---

### Post by squakie on 2013-02-19
Well, it is working, but not the way intended.  I now have to leave secure boot disabled in the BIOS in order to boot ANY OS.

I assume it has something to do with this sequence of events:

- when I couldn't find the boot-repair disk in the BIOS boot selection menu, I thought "well, it probably doesn't have a key, so I should disable secure boot" - and that's what I did.

- still ended up having to install boot-repair in Ubuntu - and here is where I think I made my mistake:

[LIST]
[*]I installed it to my RUNNING ubuntu installation
[*]I ran it from my RUNNING ubuntu installation but had forgotten to re-enable secure boot.   I can only assume (don't have a clue) that this resulted in something in the boot repair not building something somewhere (a EFI table?) with the secure boot key for windows and for ubuntu since secure boot was off.
[/LIST]
To me, and I'm not saying this is ubuntu's fault - I think it's more of a matter of a combination of EFI/UEFI, my PC, and yes - the secure boot option and the signing keys.  Any way you cut it, there's no way to expect a new user with a new PC with Windows 8 to be able to install ubuntu and get things dual booting, at least by my experience.  I had to try some things a newbie both wouldn't know and SHOULDN'T need to know.  That's why I'm not putting details here - because I ended up with my PC saying that neither Windows or Ubuntu could boot because they didn't meet the current security.  I had to turn off secure boot to get around that, and personally I'd rather leave secure boot on.


So, since things are already messed up, I'm going to try the following and see if it works or not:

[LIST]
[*]enable secure boot in the BIOS
[*]boot using the ubuntu 12.10 to the desktop via "Try Ubuntu"
[*]reconfigure and update grub
[/LIST]
If that doesn't work, I'll have to add boot-repair to the mix when running off the livecd.


Just shooting in the dark right now, and feeling both extremely stupid and extremely frustrated that there don't appear clear instructions for a novice to install ubuntu in dual-boot with Windows 8, UEFI and secure boot.  Like I mentioned, the user shouldn't have to know squat about UEFI and secure boot, and shouldn't need to try to understand boot repair - a lot of the users aren't engineers - myself included.  Those days are long in the past for me and I really hadn't planned on being that again on something new.


So excuse my rant, but I am frustrated.  I'm not a new user.  I'm not a big-time expert, but I am far from a beginner.  At least in the "old" days the frustrations were things like wireless not working and graphics drivers.  Right now I have a PC I can't even boot with secure boot on - and I shouldn't have to know anything about any of those things in the background.


I'll post back after I try the latest.  It may be that I'll have to recover my PC (sure hope the "Factory Restore" disks I created in the Dell menu work!) back to as-delivered and skip ubuntu for now (and that would make me frown).

---

### Post by squakie on 2013-02-19
Well, that got me back to secure boot for Ubuntu, however selecting any of the Windows entries results in an error about cannot load - not a security issue like before - it almost looks like it can't FIND something - a boot loader? - I have no idea.

Time for me to backup a few things via ubuntu, then use the restore disks and put my system back where it was.

I really just don't have an interest in "fighting" an install again - I thought we were past that.

---

### Post by oldfred on 2013-02-19
Have you turned both secure boot & fast boot off?
       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

    
You need Boot-Repair or manually update grub's efi entries as per bug report.
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

### Post by squakie on 2013-02-19
I had Ubuntu 64-bit 12.10 working with UEFI secure boot both on, just no grub menu - the bug explains that - thanks!
 
However, after running boot-repair selecting Windows on the grub menu resulted in an error line about image not found.  I then just gave up and removed Ubuntu - the grub menu was still there for some reason but nothing would boot.  So, I restored from my Factory reset disks, but grub was still there.  So I did the factory reset again and told it to run from the DVD and do a complete wipe and install.  That worked and I'm in the process of putting things back now.
 
So, to summarize:
 
[LIST]
[*]UEFI and secure boot both enabled
[*] Ubuntu installed and the partition showed as UEFI in the BIOS boot selection and I could boot from that menu to grub
[*]the Windows partitions showed as UEFI in the BIOS boot selection and I could boot from that menu to Windows (I'm hoping I remember this correctly - I tried a lot of stuff in a short period of time).
[*]no grub menu (explained by the bug you pointed me to)
[*]booted straight in to Ubuntu
[*]I downloaded and installed boot-repair within Ubuntu itself
[*]with UEFI and secure boot *on* I ran boot-repair then rebooted
[*]When I just left the PC boot on its own I got the grub menu
[*]I could boot Ubuntu
[*]I couldn't boot Windows - image not found error messages
[/LIST]So, my desktop is sold and right now I'm without Ubuntu, which I hate not having.  I'm going to do a lot more reading again and again until I think there is a method that won't leave me with the same problems as I don't want to go through a reload of Windows 8 again.  The mess I had last night was worse than when I was a complete newbie trying to figure out how to get Slackware installed back in 1994.
 
Thanks for those tips - I' going to read through all of that again and again, and re-read everything I read on the net, and when I'm regrouped and confident enough it will work "this time", I will repartition and try installing Ubuntu for dual-boot again, following the information you provided for both the grub bug and using boot-repair.
 
When I did try stand-alone boot repair it would show on the BIOS boot menu, even with secure boot off.  I did not at that time turn of UEFI however (there must be more going on there than what I read).  I did install it within Ubuntu with UEFI on and secure boot off, then re-enabled secure boot and that's when I got the first set of errors - the BIOS wouldn't boot either OS because of a security error, I assumed from secure boot.  So I re-enable secure boot (so I had both uefi and secure boot enabled) then booted into Ubuntu and re-ran boot repair.  That's what generated the mess I got in to.
 
I'm not sure how I could run boot-repair with UEFI and secure boot both disabled. I know that with both disabled I would then be able to boot the boot-repair disk itself, but won't it still generate the same BIOS boot security problem when I try to boot with UEFI and secure boot on again?
 
BTW - thanks again for the help!

---

### Post by oldfred on 2013-02-19
Supposedly if Ubuntu is installed in UEFI mode it should boot with secure boot on. It actually uses the the same UEFI key as Windows so it is authorized. 

But we are finding that vendors modify UEFI to only boot Windows. For many of those cases Boot-Repair renames the Windows file to a backup and copies in the shim efi file which has the Microsoft key and those systems boot Ubuntu. Then from grub menu you can boot the renamed Windows file. Boot-Repair renames or unrenames on multiple runs.

       How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

    
But even then some systems just do not work.
       Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries
Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)
    
       The current state of UEFI and Linux = Feb 1, 2013 - Matthew Garrett
Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)
Matthew Garrett's Blog
[http://mjg59.dreamwidth.org/](http://mjg59.dreamwidth.org/)
New Linux UEFI boot loader
[http://mjg59.dreamwidth.org/23113.html](http://mjg59.dreamwidth.org/23113.html)
    
Some have posted that Both Ubuntu & Windows boot with secure boot on or off. Some seem to be able to boot with secure boot off. And some have major issues. 

Dell's seem to be one of the better ones for using UEFI.
       Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell XPS14
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache) - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)
Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)

---

### Post by squakie on 2013-02-19
Thanks!  I see I have a lot more reading to do ;)  It appears that UEFI goes far beyond what I read on the web as my understanding was that it and secure boot were separate animals, but it appears they are somehow intertwined.  More reading! ;)
 
The laptop is a new Dell Inspiron 15R with 8 gb memory, 1tb hard drive, Intel i5, if that makes any difference to how things should go.  The wireless and the graphics seemed fine when I did boot Ubuntu.
 
Thanks again!

---

### Post by oldfred on 2013-02-20
UEFI has been around for a while. Many Windows 7 systems with Intel i-series chips have UEFI, but were all using the BIOS/CSM/legacy mode. Only a few  used UEFI and those did not have secure boot. or secure boot enabled.

Since Windows only boots withUEFI with gpt partitioning or with BIOS from MBR(msdos) partitioning it is difficult to convert from BIOS to UEFI or vice-versa.

Ubuntu will boot from gpt partitioned drives with either BIOS or UEFI, but UEFI requires gpt for all systems.

Since BIOS or UEFI write details of system differently onto drive for operating system to use, you really need to boot both Windows and Ubuntu in the some mode either BIOS or UEFI. 
You can dual boot when not same mode, but have to go back into BIOS/UEFI and change boot mode to correct mode for the install or a real hassle.

---

### Post by squakie on 2013-02-21
Thanks again!  For now, I guess it's just not to be for me.  My new laptop is dual core i5, but running Ubuntu in VirtualBox on it is a disaster - at least to me.  It is unbelievably slow - I mean REALLY slow.  I have an old Dell 1501 laptop I use for controlling me telescope (or maybe I should say, I'm TRYING to use it to control my telescope - so far that's been hit and miss, and I suspect I will need to spend quite some time testing it indoors before I go outside with it).  That's single core Sempron, and even with 1 core Ubuntu in a VirtualBox VM on it (Windows XP host) runs a lot faster.
 
I guess the new laptop is working fine - it seems to be.  It's just unfortunate that for the time being I can't run Ubuntu on it.  My desktop has been sold, so I've lost the ability to dual boot unless I install it on the 1501 for the telescope, but then I'd be defeating the purpose of the new laptop.
 
I suspect there are still many wrinkles to work out with UEFI  - vendor, Ubuntu and all, not just one.  I may have to wait until those things get worked out before I can run Ubuntu again, and that's a disappointment for me.
 
Almost makes me wish I hadn't sold the desktop, but it was just overkill for me.  At the time I built it I used some good stuff:  AMD FX-8120 8-core CPU, 16gb memory, M5A97 motherboard, 1.5 tb hard disk, 60gb SSD, DVD-RW/DL, etc., and a Samsung 23.6" viewable area monitor.  Just turns out the monitor was actually TOO big for my diabetic eyes.  Power wise, I wasn't hardly touching it even with some of my most demanding tasks.  So it just seemed like a good idea to get a laptop to replace it and sell the desktop.  The laptop is fine for me - I just wish everything would cooperate so that Windows 8, Ubuntu, UEFI and secure boot would all work together.
 
Again, thanks for the help.  I'm just going to mark the thread solved for now.  Hopefully down the road something will improve and I can go back to using Ubuntu again.

---

### Post by oldfred on 2013-02-21
Are you using the Intel graphics?

Some reported with newer systems this helps. 
       For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

    
There may be other fixes also, I have not stayed up to date on Video issues other than my nVidia.

---

### Post by squakie on 2013-02-21
Yep - it's using Intel HD Graphics 4000 or some such - an integrated GPU.

---

### Post by squakie on 2013-02-21
OK, I reopened this as I'm at a point where perhaps it's either clear what's wrong or perhaps gives more hints(?).
 

Here's what I've done:
[LIST]
[*]downloaded and burned the 64-bit version of the 12.10 desktop install ISO
[*]in Windows 8, used disk management to optimize the disk
[*]in Windows 8, shrank the Windows 8 main partition (I've got like 5 or 6 partitions out there that the Windows 8 install created) by 70gb
[*]boot by selecting the UEFI Ubuntu on the DVD drive via the BIOS boot menu (via F12 when the hardware is booting)
[*]installed Ubuntu to the free space with a logical partition for "/", swap and "/home"
[*]tried booting - got the grub menu, but only Ubuntu would boot. I expected this based on the bug.
[*]booted the livecd and selected "Try Ubuntu"
[*]installed boot-repair
[*]ran boot repair and took the default recommended action
[*]tried booting - this time with the same results. This time trying to boot Windows just gave a bunch of security errors having something to do with the /EFI/Ubuntu/shimx64.efi file because of secure boot.
[*]disabled secure boot in the BIOS (I don't see anything for fast boot)
[*]booted the livecd and selected "Try Ubuntu"
[*]installed boot-repair
[*]ran boot repair, selecting Windows 8 as the operating system to boot first and continuing with the default
[*]booted the livecd and selected "Try Ubuntu" again
[*]downloaded and installed boot-repair again
[*]rebooted - the laptop went straight into Windows 8 (so I can at least boot it again)
[*]rebooted, but used the BIOS boot menu to select uefi Ubuntu (there are 2 entries for it in the boot menu - both give the same result)
[*]this brought up the grub menu
[*]selected Windows, got: error: can not find command "drive" followed by "error: invalid EFI file path" followed by a message to press any key (or it times out and does the same anyway) to go back to the grub menu. Ubuntu still works fine.
[/LIST]So, I really would prefer to run with secure boot on (when I did the actual install UEFI and secure boot where both enabled - without that, if I turn secure boot back on the system won't even get to the grub menu). Right now I think it has something to do with the EFI file that Ubuntu creates. 
 

When I ran boot-repair, there were 2 things that I can post here if it helps:
[LIST]
[*]the location for the boot info script output is [http://paste.ubuntu.com/1703660](http://paste.ubuntu.com/1703660)
[*]the message "Please do not forget to make your BIOS boot on sda1/EFI/Ubuntu/shimx64.efi file"
[/LIST]I do not see an option in the BIOS boot disk (in the actual BIOS setup) for that option, so I just rebooted using the BIOS boot selection menu to select either of the UEFI Ubuntu options.
 
I turned secure boot back on now. At least it will boot to Windows 8 by default now. If I want Ubuntu I have to actually go to the BIOS boot selection menu and select 1 of the 2 UEFI options.
 
With all that in mind, it seems to me it must be something with the EFI file that Ubuntu is creating, and how the grub entries are either created or where they point to when boot-repair is used.
 
Any suggestions would be greatly appreciated. Things are "usable" but not easily like it would be with grub. I'm not going to try anything else on my own now as I don't want to make things worse. So, I am "desperately" waiting for suggestions on how to get this straighten out - at which point I will try the suggestions.
 
I really have read all kinds of the things you've pointed to and a lot of other posts on the net itself, and I thought it best to just leave things as-is until I hear more.
 
Thanks again! ;)
 
EDIT: forgot to mention that in the boot-info output there are warnings about a gui partition table (GPT) (?) being found on /dev/sda and to use gnu parted instead of fdisk.  Is this something I would have need to set somehow (I don't have a clue where) when I installed Ubuntu?

---

### Post by squakie on 2013-02-22
As soon as this dumb external USB disk (Toshiba 750gb a couple of years old) gets done with a full format (the dang thing has been running for literally HOURS already and still not done!), I'm going to try the thing mentioned in the how-to:
 
- rerun boot-repair, double checking the option for the EFI table.
- if I don't have the separate Ubuntu EFI partition it says I need to create it
 
I don't know what any of that is going to do, but I'll try it.  I've read more on UEFI and secure boot, and what a mess.

---

### Post by oldfred on 2013-02-22
Depending on what options you are checking in Boot-Repair, it renames the windows efi files to a backup and installs shim. When Boot-Repair says to boot with shim, it probably should just say ubuntu from UEFI menu as that is what UEFI will show. Or if only able to boot Windows the shim file may really be named the Windows boot. See below for more explanation.

But there really are 3 main efi files, grub's shim which includes the "key" which is the Microsoft key to boot in secure boot mode, the standard grub, and the Microsoft efi files. But only those systems that only boot from the Microsoft efi file is where Boot-Repair will rename the Windows efi file and use the shim file. Then when booting from Windows entry in UEFI  your really get grub menu and from grub menu you boot the Windows backup.

If system will boot ubuntu entry you have two choices. The shim should work with secure boot on or off. The standard grub will only work with secure boot off. Then you do not have to rename the Windows file and copy shim into the Windows directory. 

       How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

    Depending on how you view efi partition these are the files used for booting. Normally from Ubuntu the efi partition is mounted at /boot/efi so you may see /boot/efi/efi/ubuntu for example. If you see files with bkb then Boot-Repair is making backups and renaming files. Always best to have full backup of efi partition as it is vital for booting.

 # UEFI Boot files UEFI sees folder for efi files, so it will show, ubuntu, Windows, Boot and maybe others for recovery.
# for grub/ubuntu
/efi/ubuntu/grubx64.efi
# New secure boot grub version:
/efi/ubuntu/ shimx64.efi.
# for Windows, but for UEFI systems that only boot this file, grub or shim may get renamed to this and this backed up.
/EFI/Microsoft/Boot/bootmgfw.efi
# Both Windows & Ubuntu may provide this shell file, not sure of differeneces.
/efi/Boot/bootx64.efi
# There also may be other files in each directory to support booting.

If Vendors would correctly implement UEFI, even with secure boot we would not have all this hassle of renaming files or having to do other work arounds. Only a few computers seem to work correctly, many need the work arounds, but then that often complicates the install process for everyone.

---

### Post by squakie on 2013-02-22
Thanks again!  I think I'm going to try just using the BIOS boot menu to boot Ubuntu for now until I get a better understanding of all of this and the various partitions and how to set the BIOS to use a certain one.  Currently I have gotten myself a "little" lost and need to regroup.  At least for now it will boot Windows automatically and I can get to Ubuntu via the BIOS boot menu.  I'm afraid with not understanding all of this from the get-go I may already have hosed up something with those Windows EFI files/partition - I think that's why the first time through this I had to completely rebuild the disk just to get Windows back.  
 
I *thought* I understood this stuff when I started out, but It's way beyond what I thought.  Hopefully with enough more reading I'll be able to get a better handle on this so I can hopefully get to dual-boot.
 
Thanks so much!

---

### Post by oldfred on 2013-02-23
That makes good backups of efi partition, Windows partition and your data in /home even more important.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by squakie on 2013-02-23
I've always used Macrium Reflect, and with a 750gb external drive I should have room for a few of it's files before recycling.  I'm pretty sure I need to pretty much leave as-is unless I want to re-install Ubuntu again, because it would appear that the default EFI partition was changed from what I can see.  If I remove Ubuntu the grub menu is still showing (at least, that's what happened last time) and I can't boot Windows from it.  If I completely reload the disk it gets rid of grub, but then I also don't have any access to Ubuntu.  This has gotten REALLY confusing.  To create an UEFI partition for Ubuntu, from at least what I've read, it needs to be at the beginning of the disk, and guess what's already there?  Of course the Windows UEFI partition, so I haven't been able to try that yet - I think I would get in a deadly embrace - run gparted, remove the partition, allocate the ubunu uefi partition, but then if it doesn't work I would lose everything and have to do the factory reset again.
 
I can see where this is a multi-layer problem.  Trying to sort through those layers to get an understanding of all of this seems to be a bit challenging.

---

### Post by squakie on 2013-02-24
You know, I was a systems programmer and systems administrator on big iron for many years, but I guess I just haven't kept "that part of my brain" working since I am no longer working.  It's a little frustrating to me because I know I should understand all of this with no problem - perhaps I just haven't read enough yet ;)
 
oldfred - thanks so much!

---

### Post by oldfred on 2013-02-25
With BIOS and MBR it has actually been pretty simple at least compared to UEFI. Maybe because it has been the same for nearly 30 years but also because it is implemented pretty much the same on most systems.

But UEFI is new, gpt partitioning is new and every vendor seems to have made UEFI a bit different even though it is a standard. Some do not work well yet. Then Ubuntu is trying to work around the secure boot issues and each vendor's issues as best as it can, but it is all new. Boot-repair does some of the work arounds.

---

### Post by squakie on 2013-02-25
BTW - I tried 12.10 in virtualbox again last night (Windows 8 host).  Tried the things recommended to get around the llvm(?) issue of graphics going through the CPU instead of the GPU, but nothing actually worked - still no 3d rendering.

---

### Post by sms88 on 2013-02-25
> **oldfred said:**
> 
If Vendors would correctly implement UEFI, even with secure boot we would not have all this hassle of renaming files or having to do other work arounds. Only a few computers seem to work correctly, many need the work arounds, but then that often complicates the install process for everyone.

I found one other issue that was causing me grief with a Lenovo desktop. I booted the LiveCD (actually now a LiveDVD as a CD lacks sufficient capacity), but unbeknownst to me it was doing a non-UEFI installation because the DVD drive was a legacy device (with no option to change it to a UEFI boot device).

I don't know if it's simply not possible to do a UEFI installation if the DVD drive is a non-UEFI device, or if the Ubuntu installer simply assumes that if the LiveDVD is booted in legacy mode that it need to do a non-UEFI installation. I finally figured out what was going on when I specified UEFI boot devices only, and the system would not boot from the DVD drive;. I made a Live USB stick and things improved. The UEFI installation went smoothly, but the system would not boot. Boot Repair (run with the Windows 8 drive disconnected) fixed this. then I edited the 40_custom file to manually add the EFI boot partition information for Winodws 8, set the Windows drive to a non-boot device, and Grub came up and allowed either OS to boot. 

But this was a desktop with a separate drive for Ubuntu. On a single drive laptop it would likely be much more complicated.

But I think the key thing is that if you can get Grub to load, and Ubuntu to boot, you can manually configure Grub to boot Windows. You just need the UUID of the Windows 8 EFI boot partition. But if Ubuntu is sharing the same boot partition then you're likely out of luck. Even specifying a separate EFI boot partition for Ubuntu may not help because how will the system know which boot partition to use on a bootable UEFI drive? Perhaps going in and managing the flags to disable the Windows EFI boot partition?

When I first ran Boot Repair, with the Windows drive connected, Boot Repair damaged the drive and nothing would boot. Running the Windows 8 recovery from the recovery partition completed, but Windows 8 would still not boot. Only by making a USB recovery key and allowing it to wipe the drive, could I get back to a working Windows 8 system. What I took away from this was MEVER run Boot Repair on a system with Windows 8 pre-installed.

---

### Post by oldfred on 2013-02-25
@sms88
Boot-Repair has worked on many UEFI installed systems, including some Lenovo.

Not sure what your issues was, but Boot-Repair does not know for sure what issues you have and may rename Windows files to use the grub shim file to boot as that also has the Microsoft key. But it can also un-rename files just as easy.

You can only have one efi partition per device. And you can chain load from one drive's efi partition to the efi on anther drive to boot systems on that drive. If installing to a second drive, it really should not be modifying the Windows drive at all. But even with BIOS that was an issue if manual install was not used.

---

### Post by sms88 on 2013-02-25
> **oldfred said:**
> @sms88
Boot-Repair has worked on many UEFI installed systems, including some Lenovo.

Not sure what your issues was, but Boot-Repair does not know for sure what issues you have and may rename Windows files to use the grub shim file to boot as that also has the Microsoft key. But it can also un-rename files just as easy.

You can only have one efi partition per device. And you can chain load from one drive's efi partition to the efi on anther drive to boot systems on that drive. If installing to a second drive, it really should not be modifying the Windows drive at all. But even with BIOS that was an issue if manual install was not used.

The Lenovo system I have is UEFI but does not have Secure Boot enabled. If I enable it, Windows gets upset and says something about not having a valid key.

Boot Repair invariably damaged the Windows drive almost beyond repair. What finally worked was an Ubuntu install with the Windows drive disconnected, then running Boot Repair to get Ubuntu to boot, then manually adding the Windows entry to Grub, making the Windows drive non-bootable in the CMOS setup, then connecting the Windows drive.

I don't know what Boot Repair did to the EFI boot partition on the Windows drive. I did post three of the URLs with the log it creates but I don't think anyone has the time or inclination to figure out what happened.

The Boot Repair dumps are at:

[http://paste.ubuntu.com/1694319/](http://paste.ubuntu.com/1694319/)
[http://paste.ubuntu.com/1694354/](http://paste.ubuntu.com/1694354/)
[http://paste.ubuntu.com/1694436/](http://paste.ubuntu.com/1694436/)

Chaining is what I eventually did, I think. If you call Grub calling the EFI boot partition on the Windows drive chaining.

One question I have is can you have only one EFI boot partition on a drive _period_ or can you only have two EFI boot partitions on a drive with only one having the boot flag set? If you're telling Grub where the boot partition is by specifying the UUID Windows will still boot even if the boot flag is not set (however it won't shut down!).

---

### Post by oldfred on 2013-02-25
It is gparted or parted that makes the efi or ESP partition look like it has a boot flag. That is only because users know boot flag is for booting.

It really is a gpt partition code that defines efi partition. Some UEFI systems have efi boot files in another recovery/data partition and may somehow move boot flag to convert data partition and boot into recovery.

> In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

    And in actuality it is a long GUID code that defines partitions.
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

Pastebin does not seem to be working. May be due to pending upgrade to forum.

---

### Post by squakie on 2013-02-25
While we're at it here, since my last try again with a vm running 12.10 and still being extremely slow (still couldn't get 3d going and I understand something about 12.10 not having 2d so it uses the CPU [llvm?] versus the GPU.  So, do you know if 12.04 is the same?  If not perhaps I can at least Ubuntu in a vm for now until I try to figure the rest out more.  BTW - is there anyway to test the UEFI "stuff" in a vm - so that I could have the logical disk looking like a UEFI disk and then try to install Ubuntu within the vm?  I don't believe it would be possible at this time, nor do I think you can dual-boot in a vm, but I thought I'd ask anyway.  It would stop me from having to completely reload my disk image every time something screws up.
 
I'm hoping 12.04 in a vm works without llvm - if so I'd sure like to have someway to get to Ubuntu without having my EFI stuff questionable.
 
Thanks again!

---

### Post by squakie on 2013-02-25
BTW - my laptop seems to indeed have an EFI partition at the very start of the disk.  I'm thinking part of what I've been doing is messing that up some how.  I've done more reading on the Windows 8 and another OS "thing" and see this can be difficult to get working (thanks to makers of another OS whose name I won't use because we're not supposed to talk bad about them in the forum ;) ).  I am also seeing where what the vendor does to implement all of this on their PCs just throws another ripple in the ocean.  I hope someday there will be a set of REAL standards (like ANSI) so that these things are indeed all standard in how they are implemented so that other OSs don't have to jump through hoops to install and use it along with Windows 8.  It's becoming clearer to me that while there is a definition for all of this there are still no standards on the vendor's side.  I hope that day comes soon (as I'm sure everyone is dealing with this does!).

---

### Post by squakie on 2013-02-26
I got 12.10 64-bit installed in a vm and it is running much better now.  I still have some kinks in it (mouse very erratic, losing the unity panel, the top bar disappeared so now I have to force power off via VirtualBox instead of shutting down Ubuntu).  I have a ton of updates being downloaded right now, so I'm waiting until they complete so I can see where things stand again and then work from the "fixing" things.  

One things I can't quite figure out - the virtualboxlinux additions.  I can't find anywhere to download them - I thought that the Oracle site worded it to sound like there is only a single download to do Windows, Linux and Mac.  So, since I had already downloaded it for my XP vm, I tried adding them in the ubuntu vm but it says the file isn't found on the CD when I don't have a physical CD in the drive or a logical drive assigned.  But at least I do have 3d acceleration apparently working.

---

### Post by gnueliafnak on 2013-02-26
Hi, I'm a new user to Ubuntu as of yesterday. I mainly use it as my HTPC in my living room.

I installed 12.10 with secure boot enabled yesterday on my Lenovo. I just hit F12 and it brought up the boot from screen which allowed me to select a legacy device to boot from.

---

### Post by squakie on 2013-02-26
> **gnueliafnak said:**
> Hi, I'm a new user to Ubuntu as of yesterday. I mainly use it as my HTPC in my living room.
 
I installed 12.10 with secure boot enabled yesterday on my Lenovo. I just hit F12 and it brought up the boot from screen which allowed me to select a legacy device to boot from.
 
Yeah - I've been able to use the BIOS boot menu via F12 - what I'm trying to do is get a true dual-boot on a UEFI enabled PC with secure boot on.

---

### Post by squakie on 2013-02-27
if you're still following, OldFred, I'd like your opinion on this I extracted from [this]("http://superuser.com/questions/415198/make-uefi-gpt-bootloader-ssd-usb-linux-and-windows-work-together?rq=1") post from another site on the net:
 
2 Answers 
[active]("http://superuser.com/questions/415198/make-uefi-gpt-bootloader-ssd-usb-linux-and-windows-work-together?answertab=active#tab-top")[oldest]("http://superuser.com/questions/415198/make-uefi-gpt-bootloader-ssd-usb-linux-and-windows-work-together?answertab=oldest#tab-top")[votes]("http://superuser.com/questions/415198/make-uefi-gpt-bootloader-ssd-usb-linux-and-windows-work-together?answertab=votes#tab-top")
up vote17down voteaccepted
OK, it was a very involving process, but I solved my problem and everything works together just as it should.

I'm documenting the solution for everyone:[LIST=1]
[*]One must begin with GParted Live and create a fresh GPT partition table. This will wipe everything on the HDD resp. SSD. Then one must create a small 8 MB 'unpartitioned' partition and flag it with 'bios_grub'. Afterwards, one creates a 100 MB fat32 partition labeled 'EFI' and flagged 'boot'. (This is the modern and more transparent equivalent of what the MBR used to do, [see here for reference]("http://www.uefi.org/specs/esp_registry").)
[*]Optional: Install a Linux distribution that works correctly on GPT UEFI systems from USB. I don't know which ones do. I installed Chakra Linux to try it out. While installing make sure to mount the 100 MB fat32 as /boot/efi. Do the rest as usual. I left some unformatted room for Windows 8 (300 GB), created a linux-swap of 1 GB afterwards, created an adjoining ext4 (25 GB) and mounted it as /. After installation it will not boot, but we will fix that with ease. Do the entire step again for installing more distributions.
[*]Install Windows 8 in the unformatted space we left in the previous step. It will automatically identify the EFI system partition, create a MSFTRES, and a NTFS where it installs itself. After installation we can only boot into Windows, but we will fix that later.
[*]Ubuntu will fix it all. While installing select the 100 MB fat32 and change it into 'use as efi'. Create an ext4, install Ubuntu. Upon rebooting we are presented a nice working GRUB2 which detects Ubuntu and Chakra Linux.
[*]Now we will configure GRUB2 to detect Windows. [It is a known bug, however, Rasmus Pedersen's workaround is functional.]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801") Be aware of a typing error he made: It is /etc/default/grub without an s instead of /etc/defaults/grub. When writing "chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi" I wrote /EFI/ in capitals just to be sure. When done this will present us a working GRUB2 with a working Windows 8 entry.
[*]GRUB2 does not look very nice with so many boot options and it is not in my preferred order. Thus I install and use grub-customizer in Ubuntu [as shown here]("http://ubuntuforums.org/showthread.php?t=1664134"). I configure it so to hide the memtest, the recovery and the old kernels, and I reorder it to put my custom script with Windows on top. Done.
[/LIST][share]("http://superuser.com/a/415588")|[improve this answer]("http://superuser.com/posts/415588/edit")
answered Apr 23 '12 at 9:46 
 
Here's the info from Rasmus Pedersen's work around - note that he changes things a little by adding the info on booting Windows correctly.
 
[Rasmus Pedersen (rasmuslp)]("https://launchpad.net/~rasmuslp") wrote on 2012-04-07: [#7]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801/comments/7") 
I have solved this temporarily.
The GRUB menu can be unhidden by commenting out the two lines regarding GRUB_HIDDEN in /etc/defaults/grub and running update-grub as root.
Next, the entry for windows can be manually added by appending the following lines to /etc/grub.d/40_custom:
menuentry "Windows" {
    search --fs-uuid --no-floppy --set=root YOUR-EFI-PARTITIONS-UUID-HERE
    chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}
Find your EFI partitions UUID by running 'ls -la /dev/disk/by-uuid/'. As the EFI partition is a FAT32 partition, the UUID is of the form XXXX-XXXX. If you have more than one FAT partition, you can verify if one is the EFI partition by checking the partition map with gdisk (not installed by default). Run gdisk on the device, 'sudo gdisk /dev/DEVICE', press 'p' to print the partition table, and then 'q' to quit. DON'T make any changes to the partition table. The EFI partition will have the code type 'EF00' and most likely a name/label that says it is a EFI system partition.


[Rasmus Pedersen (rasmuslp)]("https://launchpad.net/~rasmuslp") wrote on 2012-04-07: [#8]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801/comments/8") 
Regarding #7 > Then you ofcourse need to run 'update-grub' after editing the 40_custom file for this change to take effect.



[URL="http://superuser.com/users/129552/gbag"]
[/URL]

---

### Post by oldfred on 2013-02-27
Your first link added a huge complication by using btrfs not ext4. Some still cannot use btrfs with BIOS boots.
       BTRFS, not ready for prime time
[http://ubuntuforums.org/showthread.php?t=2111487](http://ubuntuforums.org/showthread.php?t=2111487)
EXT4 Still Leads Over Btrfs File-System On Linux 3.8
[http://www.phoronix.com/scan.php?page=article&item=linux_38btrfs_ext4&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_38btrfs_ext4&num=1)

    
Some UEFI systems have to be installed in BIOS mode with a bios_grub partition to get grub to install correctly. Some Samsungs should only be BIOS mode until Samsumg fixes its UEFI.
Then Boot-Repair can convert to UEFI by uninstalling grub-pc and installing grub-efi. 

Windows has its own requirements for files in UEFI/gpt installs.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

    
I prefer to manually edit entries in 25_custom or 40_custom. But some prefer the gui with Grub Customizer.

---

### Post by squakie on 2013-02-27
I reinstalled Ubuntu 12.10 64-bit again as normal for dual boot with Windows 8, then tried that manual edit of the 40-custom file.  My entry name shows, but it still says something about can't load image - the error goes away so fast I can't get it written down.
 
I'm glad you thought the first part was a bad idea as I don't know how I could repartition the entire drive like they suggest, and after Ubuntu is installed load Windows 8.  Just didn't seem like a good idea, especially when all I have are the Windows 8 recovery disk images I created from Dell's utility on my laptop.  It just would have been a no-win for me.  I was curious about the things you mentioned but really just kind of let them go when I determined I couldn't do what they wanted anyway.
 
I suspect that maybe there is a problem with boot flags as you mentioned previously.  I seem to have more than 1 partition it has marked as bootable, even though it doesn't mean the same now.  Going to check some more on that tonight.  I'm kind of hoping that as my patience allows to keep digging at this until it works.  Then I could at least say for this one little teeny Dell product you can do "this" (like anyone else will probably need it anyway ;) ).
 
Thanks again!

---

### Post by Jay_E on 2013-03-04
Hey there,

About booting windows....
May I suggest:
1) Is windows still bootable? To find out:
    - burn an bootable CD that has the Gparted (partition editor)
       Like [http://www.sysresccd.org/](http://www.sysresccd.org/)
      You can run gparted (as root) from ubuntu - but having a separate, bootable cd is useful.
    - boot this and run gparted.
    - Check to see if the bootable flag is still on for the windows partition. If not, set it
       under manage flags.. Its safe to do this

About not seeing the grub menu
Maybe the timeout is too short?
I set mine to 20 seconds
This setting is in /etc/default/grub
  you probably need  a sudo for editing
mine is
     GRUB_TIMEOUT=20


About setting what is the default boot
I used  startupmanager
to do this. The numbering starting-with-zero and starting-with-one changed
so I let the app deal with it

About your approach
 Good approach - just go ahead and try it.
  Be prepared for bumps in the road and bear traps in the tall grass.
  (Its not that bad.)

I have a new motherboard and AMD 64 on a custom built frame.
I could not get 12.04 to boot from the hard drive.
I went to Debian while I'm waiting for the dust to settle and to see if anyone had 
answered my posts that had tried with my set of hardware.

Good luck
Jay

---

### Post by squakie on 2013-03-05
If I just let the laptop boot, there is no grub menu - it goes straight in to Windows.  I have to press F12 while the system is booting to get to the boot device selection menu, then select either of the 2 (don't ask me why there's 2) Ubuntu UEFI devices (partiitons) to get a grub menu.  From the grub menu I can boot Ubuntu, but selecting Windows results in a long error message that only lasts about 5 seconds on the screen, so I never catch all of it, but the last part says something about image not found. And just to clarify, I didn't run boot-repair this time around - I just edited that one file for grub.  No problem with time-out , etc., - that part all works, it just I can't boot Windows from the Grub menu and instead have to let the system itself (again, no Grub menu at all) boot Windows.  So the grub menu is visible and not timing out when I select one of the Ubuntu devices as the boot device.

---

### Post by UltimateCat on 2013-03-05
I'm still learning about how to get around this issue but from what I do understand you have to **disable the secure boot-**

This might help-
[http://www.zdnet.com/linux-foundation-releases-windows-secure-boot-fix-7000011084/](http://www.zdnet.com/linux-foundation-releases-windows-secure-boot-fix-7000011084/)

And this discussion in this thread is helpful too-
[http://www.linuxquestions.org/questions/linux-general-1/2013-installing-linux-on-windows-8-pc-is-still-a-pain-4175443966/](http://www.linuxquestions.org/questions/linux-general-1/2013-installing-linux-on-windows-8-pc-is-still-a-pain-4175443966/)

Hope this helps

---

### Post by squakie on 2013-03-06
Yeah, I already tried that as well with no luck (this caused me to completely reload the hard disk from the factory default image).

---

### Post by squakie on 2013-03-08
Great - can't get Dell to send me a Windows 7 image so I don't have to keep using this Windows 8 crap and the problems associated with it.  They did recommend 2 firmware updates to the BIOS, which I did this evening.

So, I thought what the heck - updated BIOS - may be this dang dual boot thing will work now.  Nope.  So I ran boot repair from within my running Ubuntu.  Again, I've now lost the ability to boot Windows even by selecting the Windows partition in the boot selection menu (the F12 one for me - not the BIOS itself).  Only Ubuntu works from the grub menu.  Turned off secure boot again - still no difference.  It keeps coming up with a message about /EFI something something something and saying no image found.  I made sure the file I created in the sructures for grub still was showing Windows and the correct partition - it does, but selecting it does nothing - no error message, etc., just back to the grub menu.

So, I did what I didn't want to again - completely lost the ability to get to Windows.  Is there ANY way to at least get things to where I can boot Windows via the F12 boot selection at least again?  I REALLY don't want to have to restore the image again for the nth time.  If I have to do that, then I guess it will be the end of Ubuntu for me - and I DON'T want that - but I can't keep going in circles with this.

---

### Post by oldfred on 2013-03-08
Post the latest BootInfo report.

You are the first Dell that I have seen with issues. In fact of all the UEFI systems those with Dells seem to be the easiest. But any of the high end systems with Ultrabook, dual video or Intel SRT complicate the process immensely. 

One user with a Dell 14 (?) just reported it could just install and it worked with UEFI. Not sure if he just turned secure boot off or not.

Was this originally Windows 8? Microsoft has the vendors restricted on new drivers for Windows 7 for new Windows 8 systems. Any of the new features may not get new drivers for Windows 7. So only those systems with the same configuration as a Windows 7 system will work. They do not want users changing back like they did with Vista back to XP.

         Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)
Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)

---

### Post by squakie on 2013-03-08
I didn't see anything in the BIOS setup about rapid start, etc.  It's just pretty basic in the BIOS setup.  It does have a "Restore Factory Defaults" option and a "Delete All Security Boot Keys" option - I've never touched either.

When I power on the system now I get the following (took several boots so I could catch it all):

failed to open \EFI\Microsoft\Boot\grubx64.efi
failed to load grub
failed to open \EFI\BOOT\grubx64.efi
failed to load grub
checking media [Fail]
checking media [Fail]
Secure boot not enabled 

then I get a grub menu, Ubuntu at the top, a crap load of various Windows boot options, and finally the Windows option I added via 40_custom in \etc\grub.d

Please note the messages (except for the Secure boot message) are the same at power up with Secure boot enabled or disabled.

The link to the boot info (just ran fresh) is [http://paste.ubuntu.com/5596684 ]("http://paste.ubuntu.com/5596684")

I'll try to look at all this stuff again.  The laptop was new the 2nd week of February of this year.  Dell 15R 5521.  I have found no mention of rapid start, etc..  The only thing that appears to be from Intel in the BIOS setup is an option for cpu throttling (at least that's what it appears to be to me).  It did come with Windows 8 pre-installed.  Dell itself has no Windows 7 drivers listed for it that I could find.  I did find references for Windows 7 drivers for it from other sources on the net.  Dell also doesn't seem to want me to have any form of Windows 7 from them either unless you have Windows 8 Pro.  I really hate the idea of getting another OEM Windows 8 at the wholesaler again - sent the previous one with the desktop I just sold.  I was SO hoping that if I had Windows 7 I could turn all of this UEFI crap off, create a legacy partitioned disk, install Windows 7 and install Ubuntu as normal for dual boot.  I hate to say it, so I'll preface it with it's just my opinion with my experience, but I absolutely HATE Windows 8.  I mean REALLY hate.  I'm not an OS bigot, and have always had Windows available on 1 of my PC's (down to 2 now, with 1 being for "supposedly" ;) controlling my meager telescope. 

I don't know why this thing is being so difficult.  Since Windows 8 currently won't boot from anywhere - including the F12 boot selection screen - I'm pretty sure I'm going to have to re-install the disk image again, which means it will be back to as-delivered condition.  I can do that and then just leave it there, or I can do that, optiize the disk and shrink the disk to make room for Ubuntu and leave it there if preferred to start the Ubuntu installation all over again, in case there is anything I could have messed up that you might want me to try from that point.

I also thought Dell would work the best - I researched this online and in the forum before I ordered it and it seemed people were having problems with other systems and even some Dell's, but not the model I ordered.  It's nothing fancy like the XPS line, etc..

---

### Post by oldfred on 2013-03-08
What makes a 15R different than the links I posted above that all worked to dual boot?

But it may just be Windows 7 will not work on that system.

---

### Post by squakie on 2013-03-08
Don't ask me.  I've done some more reading elsewhere as well as re-re-reading the information and links you posted.  What I have found is:

only the grub menu entries that reference the backup files:

 menuentry "Windows UEFI recovery bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 5A35-6AF0
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

menuentry "Windows Boot UEFI recovery" {
search --fs-uuid --no-floppy --set=root 5A35-6AF0
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}

Will boot Windows.  The rest either have root defined differently or they don't reference one of the backup files (bkp.......efi).

Please note I have done EVERYTHING as mentioned in this thread and in the links you provided.  I don't know why it doesn't work on a Dell Inspiron 15R 5521 - but it's not in the XPS series.  It also doesn't have any options for Intel Smart Connect Technology or Intel Rapid Start Technology.  The are only 3 things it has that have even remotely been mentioned in the various discussion of this problem:

- Intel Speed Step - I thought this was only CPU automatic throttling, but I disabled it any way

- UEFI - that's how it's set up.  The install CD was the UEFI 64-bit 12.10 CD - had to boot it via the F12 boot selection menu (on this PC) and selecting the UEFI ubuntu dvd.  

- secure boot - it has made no difference whether this is enabled or disabled.

So, to summarize again how things were installed (matches the links):

- Windows 8 (not the Pro edition though) was pre-installed
- using the Windows 8 tools, ran Optimize (crunches and defrags) 2 times
- using the Windows 8 disk management tools I shrank the existing relavent partition
- using the UEFI "enabled" 64-bit 12.10 CD, installed Ubuntu.  Typical Windows boot problem from the bug.  Ran boot-repair selecting the default.

This was done with secure boot on and with secure boot off.  It always behaved the same.

This all matches everything I have read on how to do this.  The "extras" have always involved Intel Smart Connect (I don't have it that I can find anywhere in the BIOS setup) and Intel Rapid Staart Technology (again, I don't have it that I can find anywhere in the BIOS setup).

The grub menu entries, and apparently however they coexist with UEFI, don't work.  Only the backup efi files work.

So, I can get to Windows, but not by anything that closely resembles "normal" grub menu entries - these are all labeled something like recovery or backup - don't remember the exact words.

What I need to do know is to stop grub-mkconfig and update-grub from finding anything but Ubuntu entries and rely solely on the 40_custom file in /etc/grub.d so I would only have 2 options for Ubuntu and 1 for Windows.  I currently don't know how to override the searching and creating of grub menu entries for the various Windows as it does now.  I'm sure I'll find that somewhere.

So, without reloading the disk image and doing this all over again (as I have already done), the only thing I can do is have the grub  menu reference the backup (bkp) .efi files so I can boot Windows.

If you know another way to correct this, please let me know.  boot-repair doesn't.

---

### Post by squakie on 2013-03-09
I took the cheap way out and set the 30-  osprober file in /etc/grub.d to non-execute permissions.  Reran grub-mkconfig, then update-grub.  It's still showing all the non-functional entries in the grub menu.  I noticed that all of the ones that don't point to the efi partition are the ones that don't work.

For now, the grub menu is really ugly, but at least I have 1 option for Ubuntu that works and 1 option for Windows (via the bkp file) that works.  I have a hunch that if I manualle edit grub.cfg (yep - know it's not the way to do it) to point to efi partition they will probably work as well.

---

### Post by oldfred on 2013-03-09
Do not edit grub.cfg.

It is great that it works. I think it has to use the backup files with secure boot on many systems as the UEFI is modfied to only boot Windows which it should not be.

All the entries in 25_custom can be edited and then on sudo update-grub will change grub.cfg. Not sure why script calls some of the entries recovery, but it only does that for some systems. But it has to find files in the efi partition that look like they may boot, assign a name and create the chain load boot stanza.

       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/25_custom_backup
# turn off execute bit or it will run backup also, creating duplicate entries
sudo chmod a-x /etc/grub.d/25_custom_backup
gksudo gedit /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

### Post by squakie on 2013-03-10
Good news!  FINALLY have a clean grub menu with working Ubuntu option and a SINGLE  and  *WORKING* Windows 8 option.

I still get those error messages at power up, but currently it all works as I needed, so I'm not in a hurry to fix those right now.

All I can say is:  what a mess! 

Followed by:  THANKS OLDFRED!  I know this was probably just as frustrating for you as it was me.  I also had to turn the execute bit off on the /etc/grub.d/30_uefi-firmware file (don't know if that is a "standard" file, generated by boot-repair, or what).  That file created all of the screwy UEFI entries in the grub menu.

Thanks again!  If you have any idea on the error messages at boot as mentioned previously I'll sure be all ears!

---

### Post by oldfred on 2013-03-10
With everyone else BootInfo shows this. And that entry is to get you back into UEFI as some systems with fastboot on can only get to UEFI thru Windows and if Windows does not boot, you have a brick.

 > ### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {

 fwsetup

 }
### END /etc/grub.d/30_uefi-firmware ###

The entries in 25_custom are added by Boot-Repair. 

And the entries from 30_os_prober are os_prober and those currently are the old BIOS boot which do not work. With os-prober off script or a sudo update-grub should just show this:

> ### BEGIN /etc/grub.d/30_os-prober ### 
### END /etc/grub.d/30_os-prober ### 

Boot-Repair will add extra entries but it is not sure what works so it adds every .efi or any file that may be a boot file to menu. Some systems have recovery in same folder so it also adds all the recovery entries, others have a separate folder, but it still adds those also.

---

### Post by ViliX64 on 2013-03-10
I was preparing to install Xubuntu.. so I turned secure boot off and when I tried to boot live USB it said: 'Secure boot not enabled.' and then nothing. So I turned it on and it worked. (I have UEFI bios by the way.)

---

### Post by squakie on 2013-03-10
with things at least working, even with the error messages at power up, I'm going to mark this as solved.  if something comes up relevant to this is thread, then I'll open it again.

thanks again for the help oldfred!  I don't know why turned out different, but at least I can boot both Ubuntu and windows from the grub menu.

---

### Post by oldfred on 2013-03-11
Glad you got it working. :)

---

