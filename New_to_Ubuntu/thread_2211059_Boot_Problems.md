---
title: "Boot Problems"
date: 2014-03-13
forum: New to Ubuntu
---

### Post by fbrand on 2014-03-13
I am running 12.04 LTS which has always been upgraded to the latest updates.

I have been having boot problems. The computer will not boot and comes up with Read Error, grub-rescue problems.

I have reinstalled Grub, repaired Grub with Boot Repair and also done the manual Grub repairs by using the install disk and manually mounting the partitions and forcing the Grub reinstall on /dev/sda. These all indicate that the repair was successful.

I am able to get the computer to boot by using this strange process:-

1. Boot off a CD (I am using Puppy Linux but I suspect any live distro will work)

2. Remove the Live CD and reboot

3. Computer comes up with Grub Boot Command

4. Use either the latest entry or even older release entries and press Enter key.

System then boots of the hard drive.

Can anybody offer a comment? I thought maybe my boot sector was stuffed but why does it eventually boot up?

Thanks in advance.

---

### Post by r.stiltskin on 2014-03-13
One possibility is of course that the hard disk may be failing.  But before you try replacing the disk ... how old is your motherboard battery?

---

### Post by mansonfan78 on 2014-03-13
Hard disk failure does seem likely.  It could be taking longer to spin up, loading the live cd could just be giving it extra time.  You could try going into bios and turning off quick post (if that's an option).  That would give your hard drive more time to spin up.  If that works I'd say it's time to replace the drive, if it doesn't work - then it's something else.

---

### Post by fbrand on 2014-03-14
The hard disk seems to be OK, reads and writes seem to be exemplory and this has been happening for over a month now. I would have thought that if the disk was failing it would have died in less than a month of fairly consistent use. The battery is 2 to 3 years old but the BIOS seems to hold time and settings without issue.

Thanks for trying.

---

### Post by fbrand on 2014-03-14
Quick post is already off. The drive has been working perfectly since 2012 and nothing in the setup has changed (other than doing the normal LTS updates). Why would the time it takes to recognise and read the drive be any different than it has been over the last couple of years?

---

### Post by mansonfan78 on 2014-03-14
Can't say for certain, but since you've done boot repair and reinstalled grub the only possibility (that I can think of) is a hardware problem.  Other than drive pre-fail, it could be a problem with the power supply, or a faulty or loose data or power cable.  Although the fact that it does eventually boot up leaves me rather stumped, I would think that it would either boot every time or never.

---

### Post by fbrand on 2014-03-14
Thanks Mansonfan. I am a bit stumped myself. There is no evidence of hardware failure. When things eventually boot up everything works fine. When I boot off an install CD or Linux Mint CD or a Puppy Linux CD everything works fine. I really just wanted this computer to be up for another month until 14.04 LTS arrives!

It never boots of its own accord. Only after I boot up with say Puppy Linux disk but if I turn the computer off and boot up straight away it seems to boot up OK. Maybe it does not like the cold!

---

### Post by mansonfan78 on 2014-03-14
That could actually be the problem.  Hard drives don't work properly below a certain temperature.  Try an experiment:  place a small space heater near the computer (after it's been off for a few hours) and then try to boot up.

---

### Post by fbrand on 2014-03-14
No not really Mansonfan, I am in Brisbane, Australia (subtropical) it is 30 degrees C here.

---

### Post by oldfred on 2014-03-14
To check drive in Ubuntu use Disks or Disk Utility and see what Smart Status is. It can run lots of tests, but all I really know is passed is good and anything else is time for a new drive.

Some BIOS start to get confused on too many warm boots. 
Systems work by having BIOS write info to hard drive. Then that data is used by system to know what you have in the way of hardware.
But if something gets changed (which probably should not) then a warm boot may not work where a cold boot rewrites all that hardware info.
Or it could be the part of drive where BIOS writes info is starting to fail??

---

### Post by fbrand on 2014-03-14
Thanks for your input oldfred but:-

Point 1.   I have checked the SMART status of the drive and done short tests and extended tests on the drive and it is showing all greens with no problems in either the short or extended surface test. The only possible conclusion is that the hard drive is fine.

Point 2.  My issue is just the opposite to what you describe. I am not having and problem with a warm boot after I boot off a Live CD and then reboot the hard drive. The problem is with a cold boot.

---

### Post by r.stiltskin on 2014-03-15
Here's a theory that might explain what's happening.  Unfortunately it's just a theory that rests on two assumptions that may be completely unfounded, but you might want to explore it further.

To begin with, is there anything in SMART to identify a problem in the boot sector?  Since that portion of the disk isn't accessed during normal operation, is it possible that the SMART attributes simply don't detect defects there?  So, assuming that this is the case, and there is something wrong in the boot sector, we still need a plausible theory to explain why a defective boot sector would be consistently reliable while rebooting, yet consistently unreliable while cold-booting.

Well, when you perform a warm reboot, we know that POST is skipped, and various hardware discovery steps are skipped.  Is it possible that reading GRUB Stage 1 is also skipped and instead Stage 1.5 (or even Stage 2) is accessed directly?  

I don't know.  Can anybody shed any light on this?

---

### Post by fbrand on 2014-03-15
Thanks for coming back in Rumpel (if you want to be more formal, Mr Stiltskin). I have assumed that when a disk check is done, the MBR is also checked but I have not seen anything definitive on this. However, I think I can discount your theory because if I load up a Live CD and then issue a reboot command (ie warm boot) the system boots up correctly but if I shut the system down and boot again immediately (I will call this a warm cold boot) so that the full POST and boot process occurs, the system still boots up OK. Thus, it seems whether the system goes through the full boot process or just a partial process does not seem to make any real difference.

---

### Post by r.stiltskin on 2014-03-15
Well, then what do you have to do to make it *not* boot up correctly?  After booting just once with the cd, can you cold-boot successfully from the hard disk repeatedly?  5 times without failure? 10 times?  Is it only after lying powered-down for some length of time that it will fail to boot?  Do you have an estimate of how much down time is required?

Also, is booting from the cd *always* successful?  How about booting from a live usb?  Do you have a spare hard disk that you can use for testing?  You can set up a small installation on another disk, configure the bios to boot from that and see if that one has any difficulty booting.

If any of those fails to boot with any "reasonable" frequency you can assume the hard disk isn't the culprit and try 
- replacing the cmos battery
- reflashing the bios
- replacing the power supply

But if all other boot options, including another hard disk, work reliably, then it will be pretty clear that the disk is defective.  You can try using a Windows installation disk or Partition Wizard to rewrite the MBR, then reinstall Grub yet again and see if that solves the problem.  If not, it's probably time to throw in the towel and get a new hd.

---

### Post by r.stiltskin on 2014-03-15
Oh, and taking a cue from Mansonfan, before doing anything else I would unplug and then reconnect the hard disk data cable (both ends), (or even replace it if you have a spare) and its power cable.  Just to be sure.

---

### Post by fbrand on 2014-03-16
After loading the Live CD it always boots up. I have not once not been able to boot up after first loading the Live CD.

I am not sure what length of time I need to wait before it does not boot up. Certainly after 12 hours it does not boot. I customarily just boot off the CD every day now and I have been doing that for a couple of weeks so you can see booting off the Live CD looks pretty fail-safe. I do have another drive I can try and may try that. I have done a lot of looking at the existing hard drive and I have developed a fair degree of confidence in it...my mind is now fixed on the reliability of the motherboard.

I do notice some error messages when I boot after the CD but they go past so quickly I can not read them. I do notice something about DMA so maybe it has something to do with the disk controller. When I look at dmesg none of the error messages are there.

I do have another computer ready to install 14.04 LTS on after 17 April and then I will decommission this current computer and maybe run some checks on all the components

---

### Post by mansonfan78 on 2014-03-17
The way I see it, your problem could be the power supply.  When you first turn it on (from a "cold boot") it might not be providing enough power to initialize the hard drive and only after "warming up" for a couple minutes is it able to.  Simply turning it on and waiting wouldn't work because the drive would have to be accessed at a certain time during boot up, once that time has passed it wouldn't matter if the drive is working properly or not.  You could try testing this by disconnecting the power to the optical drive(s) so that more power could go to the hard drive and see if it can "cold boot".

---

### Post by r.stiltskin on 2014-03-17
I agree, the power supply could be the culprit.  And if that's the case, it might be sufficient to simply wait at the grub menu for a while (hit 'c' or 'e' or down-arrow so it doesn't go immediately to the default), wait for a few minutes to give the psu some time to warm up and stabilize, and then try to boot.

---

### Post by fbrand on 2014-03-19
I have a new power supply and will switch out the old one to see how things go. r.stiltskin, since this problem it no longer exhibits the default behaviour of going straight to the login page. When it boots now it goes to the Grub menu and I need to select whatever I want from the menu and then it goes to the purple login screen. My original concern was not for the hard drive or even the computer. I have a new rig ready for 14.04 in any case and I have all my data backed up and can access the hard drive using Puppy Linux easily to recover anything I have missed. My original concern was that the drive was trying to boot but, for some reason, could not find the boot files on a cold boot...it got to the MBR and then was looking for a file it can't find. I was starting to lose confidence in Grub2 and there does seem to be quite a lot of trouble with booting if you look through the forum pages. I was starting to lust for the simplicity of LILO or Grub1.

---

### Post by r.stiltskin on 2014-03-19
> **fbrand said:**
> I have a new power supply and will switch out the old one to see how things go. r.stiltskin, since this problem it no longer exhibits the default behaviour of going straight to the login page. When it boots now it goes to the Grub menu and I need to select whatever I want from the menu ...
I'd like to try to understand why that's happening.  Please post the files /boot/grub/grub.cfg and /etc/default/grub.

---

### Post by fbrand on 2014-03-20
For you r.stiltskin.

When I tried to attach grub.cfg it was not of a file type that could be uploaded. I have re-saved it as grub_cfg.txt but then it was too large for the upload.

I have uploaded it to a web site and you should be able to get it at:-

[http://www.molonga.info/grub_cfg.txt](http://www.molonga.info/grub_cfg.txt)

/etc/default/grub is attached as grub.txt to change it to an uploadable file type.

Regards
fbrand

---

### Post by r.stiltskin on 2014-03-20
Got it.  I was puzzled at first when I read that the file was too big but now I see -- it seems you like to save stuff. :)

I don't have time to get into the details right now.  I don't see anything wrong with /etc/default/grub.  But, wow, your grub menu must be as long as your arm.  Nobody needs 31 kernels.  I don't recall ever reading that there is a limit to how many grub can handle, but considering that each of those entries entails about 25 MB of files in your /boot directory I'm wondering whether your boot problem might be a symptom of running out of disk space.

I'll examine it more closely later, but in the meantime you might want to consider that possibility -- and consider uninstalling some of those old kernel images.

---

### Post by fbrand on 2014-03-20
Firstly, let me add that I have checked the disk with the Seagate Seatools suite and found not issues with the hard drive.

I was also a bit surprised with the file  but the grub.cfg file that was too big was only 31.6kb (which of itself is not large) but the upload maximum size for this site is 19 kb. The issue you raise is of interest. My Grub Menu is not massive on screen...only 5 entries

1. Latest Kernel
2. Latest Kernel (rescue mode)
3. Previous kernels
4. Memtest something
5. Memtest something else

I am not necessarily a hoarder of kernel images and until this issue I was not even aware that they were all still in my boot directory. I have always done the LTS updates as they are advised. However, it seems that the updates do not remove all the other kernel that have been put in there. My /boot directory is 671 MB with 35 kernel images, 35 configuration files, a whole host of system map files, 35 compressed initrd.img generic files and a 30 abiword update files (23.9 MB in total).

I am really surprised that the normal update procedure seems to leave all these files in the boot directory rather than remove them at some stage. I am more than just a touch surprised that these have to be manipulated manually. I see now where there are references to it but on none of the references does it warn about it causing Grub non-booting issues and the only problem mentioned is that it uses up disk space. I will clean out the majority of kernels but somehow I don't see it being the source of my problem...time will tell.

---

### Post by r.stiltskin on 2014-03-21
The old kernels aren't automatically removed, you have to do that yourself.  Just keep the latest 2 or 3 entries and uninstall the rest.

There is nothing wrong with your /etc/default/grub, and aside from the excessive number of entries I see nothing wrong with grub.cfg.  I  doubt that this problem results from a Grub bug (no pun intended).  It turns out that your failure to automatically boot the first menu entry is a feature, not a bug.  When there is a problem during booting, grub sets an environment variable **recordfail=1** in /boot/grub/grubenv, and that causes it to wait indefinitely until you manually choose a kernel image to boot.  You can reset it by running this command

```
sudo grub-editenv unset recordfail

```
and that should cause the first (default) kernel to be chosen automatically the next time you boot, but it will probably be reset to 1 the next time there is another failure to boot.  In other words, this is a symptom, not a cause of the underlying problem.

As to the number of images, I'm not aware that Grub has a built-in limit.  But I don't know how your disk is partitioned.  If you have a single partition occupying the entire disk you would know if you're running out of space because other programs would be reporting problems.  But if you've split it into multiple partitions, and particularly if you have your /boot directory in a separate partition (which is not uncommon), disk space might be an issue.  So, is it?

And have you tried changing the power supply?  Any luck with that?

---

### Post by fbrand on 2014-03-21
I have cleaned out the boot directory, reducing it to just the last kernel...been reduced in size from 671 MB to 28 MB. I did not need to keep anything but the last kernel as I have been using it for a couple of weeks and it was working OK (as long as it booted).

The disk is 500 GB on one partition plus a Swap partition. There are hundreds of GB free on the drive so having extra kernels in there would not be an issue.

To be sure of any change I need to wait (maybe) 12 hours after the last boot. I will change the power supply before the next boot to see what influence that has and on the next day I might pop in a different hard drive to see if that makes a change but if nothing else works and changing the hard drive does work that still does not tell me whether it is the drive (which I really doubt as I have tested it several times using several different methods) or whether it is some configuration of the software on the drive.

As I have indicated previously I am not especially concerned for the computer or even the data but I was more interested in knowing that it was not a Grub issue for my own confidence in Grub.

---

### Post by fbrand on 2014-03-21
I have switched to another power supply (a Coolermaster 500W) which made no difference at all to the boot behaviour. Also, this was the first time I have booted since cleaning out the boot directory it can be seen that that had no affect either. Next step is to try another hard drive but, as I have already suggested, that will not discriminate between a faulty hard drive and some software fault.

---

### Post by fbrand on 2014-03-22
Interestingly at the end of this post on [http://paste.ubuntu.com/6993410](http://paste.ubuntu.com/6993410) where somebody else had boot issues I found the following:-

"The boot files of [The OS now in use - Ubuntu 12.04.4 LTS] are far from the start of the disk. 
Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). 
This can be performed via tools such as gParted. 
Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)"

Looking at the boot files in that paste this guy had exactly the same number of kernels in his boot partition as I had before cleaning it out
ie 3.2.0.25 to 3.2.0.59. I am wondering wether this might be the issue as, I assume, that when you delete all the kernels from the boot directory, 
the remaining kernels are not moved closer to the start of the boot directory but remain in their original positions far from the start 
of the disk.

This guy also has exactly the same disk as I have - ST3500413AS and the same partition arrangement.

---

### Post by r.stiltskin on 2014-03-23
I remember that it used to be necessary for boot files to be located near the beginning of the disk, but I think that's rather "ancient" history.
In my HP notebook as well as both of my newest (home-built) desktops I have installed Linux in extended partiitions more than 100GB away from the beginning of the drive, so unless it's some peculiarity of your BIOS or of the hard disk controller, I doubt that's the problem.  I also doubt that Grub is the problem.  I still have "gain a thorough understanding of Grub" on my to-do list, mainly because configuring it has gotten so damned obtuse in recent years but also because I want to understand the entire boot process more fully.  But I have never found Grub to be unreliable.  I think most of the problems people have been having with it are related to newer motherboards based on EFI rather than traditional BIOS.  Correct me if I'm wrong, but I assume that doesn't apply in your case.  In my experience Grub is sometimes a little difficult to configure just the way I want it, but once it's working ... it works.

I might have that same Seagate disk in one of my old machines but I'm not at that location now.  I'll check it tomorrow or Tuesday.  That machine too has its Linux installation fairly distant from the beginning of the disk.

It seems to me that since you have cleared the power supply, it's most likely that the disk itself is failing.

---

### Post by oldfred on 2014-03-23
We have seen cases where boot files must not be beyond 137GB. While newer BIOS should not have that issue, it still pops up. It may be just that BIOS has drive set for IDE not AHCI, so it emulates the older IDE with the issue. Check your BIOS settings for drive.

I normally suggest smaller / (root) partitions fully within first 100GB of a drive or a separate /boot partition that is fully inside the first 100GB. Rest of drive can then be /home or data partition(s).

Post BootInfo script and we can see where grub & boot files are on drive.

---

### Post by r.stiltskin on 2014-03-23
> **oldfred said:**
> We have seen cases where boot files must not be beyond 137GB. 

But, oldfred, have you seen cases where boot files must not be beyond 137GB only when the disk is "cold", but OK to be beyond that region when warm?

---

### Post by oldfred on 2014-03-23
No, but I have not seen why it occurs or even had a user test that. Most reinstall or shrink / to 100GB or less. That has worked for about 50% of those I have suggested it for. A few do change BIOS settings and have system work.
Boot-Repair added the message after we saw more than just the very old BIOS that the issue should only apply to.

I also have not seen the issue with any new system with UEFI, even though Boot-Repair sometimes reports the same message.

There also was a bug on grub, supposedly fix several versions ago on very large / partitions (over 500GB). The standard install of / & swap was fine years ago when drives were smaller, but now with TB sized drives than can make a too large / partition.

---

### Post by mansonfan78 on 2014-03-23
Since the power supply has been ruled out I'm still of the belief that it's a drive spin-up problem.  I don't think SMART tests can test for every possible problem with a drive.  If that does turn out to be the problem your existing drive could still be used in an external enclosure if it's just left on and spinning all the time (I have one I keep on all the time - works perfectly like that).

---

### Post by fbrand on 2014-03-24
Thanks for all your thoughts.

To Mansonfan78: I have not just run SMART test I have actually used Seatools from Seagate and run the short SMART test plus also the extended test (like about 2 hours). The number of tests I have done on the drive has given me some confidence (possibly misplaced confidence) in it.

To everyone: I have shrunk my root patition and added a 1GB /boot partition starting at the first track of the drive and that had no beneficial affect on behaviour. I am like you all, I just can't understand that it wont boot cold but warm boot after a Live CD it is OK. After I did the shrinking of the hard drive I lost my modules and the mouse and keyboard did not work but after reinstalling and doing a modprobe, they returned.

I have been using Linux since Slackware 1.2 so I am a 15 year plus user and I have never struck anything like this before.

I don't want to blast everything on this disk away just yet but when 14.04 comes out in another 3 weeks and I am certain that I have all I need from this disk I will format and do another fresh install on this disk. That should settle it for good as to whether it is something peculiar to this disk. If the re-install works fine then it is a software issue (not sure what though) and if it fails in the same way that it does now then it will look like the disk is the problem.

I did find it strange that the case I cited earlier had the same hard drive and the same issue (paste.ubuntu.com/6993410) but I can not find that original post to see what the outcome was. My boot info file is at [http://paste.ubuntu.com/7144926/](http://paste.ubuntu.com/7144926/). You will see the / partition starts well back from the start of the drive but that is because I shrunk it to use a separate boot partition but I removed that partition when it did not help matters (in fact just put me into basic Grub).

Just for interest I will post again after 14.04 is released.

---

### Post by oldfred on 2014-03-24
Is that most current BootInfo report?
It only shows a large / (root) and swap. 
And on line 269 you show boot files at 415 & 319 as well as some near beginning of drive.

I normally suggest 20 or 25GB for / and rest for /home or data partition(s). I prefer data partitions and keeping /home inside / but that is a bit more advanced as you have to manually create mounts and mount those partitions. A /home can be configured as a separate partition during install.

---

### Post by fbrand on 2014-03-25
Yes, that is the latest BootInfo report with a large / and a swap drive. It was just accepting the defaults in 12.04

Initially / was at the start of the disk (and I think ext3) but I shrank and moved it to create a 1GB area before the root directory and in the change it was converted to ext4.

I then created a separate 1GB boot directory before the root directory and tried to boot from that but it was not at all successful (ie not booting at all except to put me into Basic Grub where I could do nothing - not even a Grub menu) so I left the root directory where it was (1GB from the front of the drive), deleted the boot directory and went back to the original boot arrangement.

Don't know what you see regarding boot files. From my reading of the file it refers only to files in the /boot directory.

Since 14.04 will be released in a few weeks I decided to revert to what I can get booting, put up with the inconvenience of the Live Cd and then do a reinstall after I no longer need this drive to see if the drive is the problem. When I first encountered this problem (about a month ago) I suspected that maybe an update caused the problem as I had been using this system for over 2 years, installed with the 12.04 defaults. Then things went haywire although, when I boot using a Live CD, the computer performs fautlessly. I have not been able to find any hardware faults and this has sparked my interest as I began using LTS because of longer support and reliability and, if it turns out that the hardware is operating OK, then maybe I need to reconsider using Ubuntu LTS.

I have been booting from Live CD ever since this all happened and the computer has continued to perform faultlessly other than the boot issue.

As I have said, I am no longer worried about seeking to fix this system as in a few weeks I will move a new computer onto an upgrade path and I can put up with the inconvenience in the short term. My main aim now is to restore my faith in Grub. The fact that I am having this issue and I have seen another post having the same issue with a similar hard drive configuration makes me wonder!

---

### Post by r.stiltskin on 2014-03-26
Well, this topic has remained far more intriguing (for me, at least) than it probably should be.  I don't share your worries about Grub, primarily because from a programming point of view I can't think of any plausible reason that a piece of code (Grub Stage 2) whose job is essentially to use the bios to read other code (the kernel image) from the disk and then to load it into memory, and which used to work consistently would now consistently fail when "cold" and succeed when "warm".  After all, it's not a treasure hunt searching for some elusive code whose location is constantly changing such that you might claim that its search algorithm is buggy.  Instead it is (or should be) performing a dull ministerial task of taking the same code from the same location and copying it to another (same) location every time.  But, Grub has been updated from time to time.  Maybe something got corrupted, or maybe there is some strange bug in it, so you might try reverting it to the previous version & see if that makes a difference.

There are a couple of details that we have glossed over which might be useful to someone at some time, such as:
what is the exact Grub version
what is the exact model of your motherboard (or of your computer if it's a brand-name machine)
what is the name and version of your bios

Suppose you try booting from the (cold) hard disk repeatedly instead of using the cdrom.  Does that eventually get the disk warmed up, or loosened up enough to boot?

_Exactly_ what is the error message when it fails to boot?

I realize now that since even when it fails to boot, you are getting to the Grub menu, this tells us that Grub stages 1 and 1.5 are working, since it's Grub stage 2 that presents the menu and the Grub command line.  Grub stage 2 is in your /boot directory.  So I believe this means that there's nothing wrong with the boot sector of the disk and the MBR.  It's the kernel image (or all of the kernel images) that for some reason can't get loaded into memory.  

  You can play around a bit with the command line (Press 'c' when you see the Grub menu. Press 'escape' to return to the menu.)   At the command line, run **ls** and you should see a list of your partitions, something like:
(hd0,msdos1) (hd0,msdos2) (hd0,msdos5)

Run
ls (hd0,msdos1) [or whichever one of the above entries you figure represents your / partition] and you should see some basic info about that partition such as filesystem type, location, size, last modification time, and so on.

Run
ls (hd0,msdos1)/  and you should see a listing of your root filesystem.

Run
ls (hd0,msdos1)/boot/ and you should see your /boot directory listed.

Maybe playing around with that will show something interesting.  Maybe that will generate enough disk activity to get the thing to boot.  Who knows?

---

### Post by fbrand on 2014-03-26
Hi r.stiltskin, I totally agree with you that, to those of us interested, this has provided much more use of time than it probably should have. I pretty well much agree with your first paragraph. Originally, my motivation was to sort it out and just get the boot process working until 14.04 appeared. Now that release is imminent and I am not so motivated by getting the boot process working as wondering what it is that is going on. My initial thought was (like you) something along the line of a possible corruption of part of the process due to some upgrade.

To answer your questions:-

1. Grub version is grub2 v1.99
2. My motherboard is MSI G31M3 -l v2 with Xeon E3110 CPU (the same CPU is designated E8400 Core 2 Duo)
3. BIOS is AMI v 2.4 (according to dmidecode)

4. The first error message is "Read error"
5. If I reboot from that I get "grub rescue>" further reboots sometimes might do other things but I am not too sure. I have tried booting into the BIOS to give the disk time to spin up but that makes no difference to the boot behaviour.

You are correct to note that, since we are getting grub error messages that implies the boot sector is OK and grub is at least getting somewhere. Interestingly both my own case and also the other guy having the same trouble had done all the upgrades and had lots of kernels and core.img files in the boot directory and had the problem at the same stage (ie we both had up to kernel 3.2.0.59 [see paste.ubuntu.com/6993410]). This means our boot directories were pretty full and the last entry (which would be the active entry) would be far from the start of the disk.

When I get to the grub commands I can do all those ls commands and see my disk structure OK. One of the frustrating issues is that any change I make I need to wait until I can cold boot to see if anything changes.

To test out the various boot scenarios I will need to wait until tomorrow when I can do a "cold" boot as, if I reboot now, it will just boot OK "warm".

I wish I could find the post associated with the other guy's problem (paste.ubuntu.com/6993410) but, alas, I can not find it because it is identical to my issue and happened at the same time...just not a coincidence I  don't think.

---

### Post by oldfred on 2014-03-26
Did you try the smaller root partition?
And what is BIOS setting for drive, should be AHCI.

---

### Post by r.stiltskin on 2014-03-26
Fwiw, I just booted up an _old_ desktop running an Athlon XP 2600 cpu on an Asus A7N8X-E "deluxe" mobo which I'm guessing is at least 10 yrs old, with a maybe 5-year old 500 GB WD5000AAKS hard disk.  It's booting 12.04 LTS on an extended partition beginning about 29 GB from the beginning of the disk.  No problems.  I realize that doesn't shed any light on your mobo/bios but just thought I'd mention it.  Anyway, I think you said that you tried moving /boot to a new partition at the beginning of the disk and that made no difference, correct?  So that seems to suggest that location of the image is not the problem.

Maybe more relevant is this, which I found on the Wikipedia page for [American Megatrends (AMI)]("http://en.wikipedia.org/wiki/American_Megatrends"):
> In July 2008 Linux developers discovered issues with ACPI tables on certain AMIBIOS BIOSes supplied by Foxconn, ASUS, and MSI. The problem is related to the ACPI _OSI method, which is used by ACPI to determine the OS version (in case an ACPI patch only applies to one specific OS). In some cases, the OSI method caused problems on Linux systems, skipping code that was only executed on Windows systems. Foxconn and AMI worked together to develop a solution, which was included in later revisions of AMIBIOS. The issue affected motherboards with Intel Socket 775. Actual system behavior differed based on BIOS version, system hardware and Linux distribution.[17]


After you set up your new machine you can try updating this bios.

Another thought: I notice that you're using the 3.2 kernel.  My ancient 12.04 desktop has 3.2, 3.5 and 3.8 kernels installed, and is booting 3.8 by default.  I don't recall the history of when or why I installed all those kernels, but maybe you should try one of the newer versions.

---

### Post by fbrand on 2014-03-27
Thanks for your interest in this r.stiltskin, although it is rapidly reaching the stage of being more of academic interest as 14.04 approaches.

The reason I am using 3.2 is because that is what 12.04 LTS is updated with. Not sure why but maybe because it is an LTS release they are more conservative with things like kernel versions etc.

I have just tried booting and rebooting "cold" and the first three times I got :-

1. Read error
2.Read error
3. error: hd0 is out of disk space

The fourth reboot took me into the Grub menu (just about easier to boot up Puppy Linux, that system is 100% reliable...only 2 boots needed).

Your find regarding Foxconn, ASUS and MSI boards is interesting (this motherboard is probably 2011 build). From this I might assume that Foxconn makes the boards for MSI and ASUS. I do know Foxconn is a huge organisation and makes lots of components for other manufacturers including being Apple's largest supplier.

However I doubt that is the issue here as the board booted correctly for over 3 years, never a problem until recently. If it was related to a BIOS issue you would think that it would it might have happened before this.

The separate boot partition is not necessary according to a Ubuntu developer (Jorge Castro) :-

"Generally speaking, you shouldn't bother with a separate /home or /boot partition unless you're running multiple Linux distributions at once.

  The Ubuntu installers for both the desktop CD and server/alternate CD  have the ability to install over an existing system, preserving your  home directory (and the local system driectories: /usr/local, /usr/src, and /var/local).   This functionality also reuses the user ID and group ID of an existing  user, if it has the same username as the user you're creating during  installation."

and

"As for a separate /boot partition, that's a relic of  hardware constraints of the past (the bootloader 1024 cylinder limit).  I  can think of no practical advantage a separate /boot would have on a  modern system, and if not given an arguably excessive amount of space,  it will potentially fill up and create problems of its own, given that  Ubuntu does not automatically remove old kernels."

---

### Post by Navneet_Kumar on 2014-03-27
I think that there might be a hard disk problem....and more specifically in the MBR section.....so that the boot manager doesn't responding as it should..........try fixing the MBR table

---

### Post by r.stiltskin on 2014-03-27
> **fbrand said:**
> Thanks for your interest in this r.stiltskin, although it is rapidly reaching the stage of being more of academic interest as 14.04 approaches.I agree -- purely academic interest.

> The reason I am using 3.2 is because that is what 12.04 LTS is updated with. Not sure why but maybe because it is an LTS release they are more conservative with things like kernel versions etc.3.2 was the kernel originally packaged in 12.04.  But the 3.5, 3.8 and now also 3.11 kernels are also available in 12.04 LTS.  My laptop runs Kubuntu 12.04 LTS and I see all of those kernels available in my Synaptic Package Manager (btw I recommend Synaptic over any other "software center").

> 
I have just tried booting and rebooting "cold" and the first three times I got :-

1. Read error
2.Read error
3. error: hd0 is out of disk space

The fourth reboot took me into the Grub menu (just about easier to boot up Puppy Linux, that system is 100% reliable...only 2 boots needed).I didn't mean to suggest that multiple-rebooting would be easier.  I just wanted to see if any kind of disk activity, as long as there's enough of it to "warm up" the disk, would get the system to boot.  I take this to be additional evidence that some component of the disk is failing.

> Your find regarding Foxconn, ASUS and MSI boards is interesting (this motherboard is probably 2011 build). From this I might assume that Foxconn makes the boards for MSI and ASUS.I don't know if that assumption is valid (or relevant), but maybe.  To me, it just says that AMI supplied the bios for those 3 board manufacturers.

> However I doubt that is the issue here as the board booted correctly for over 3 years, never a problem until recently. If it was related to a BIOS issue you would think that it would it might have happened before this.I agree, but I have to admit the slight possibility that there is a bios issue that only became apparent in conjunction with a recent kernel update.  You never mentioned whether you have attempted to cold-boot any of the relatively-old kernel images, or only the latest one or two.  (Although it would still be hard to understand why such a problem would go away after the system warms up.)

> 
The separate boot partition is not necessary according to a Ubuntu developer (Jorge Castro) :-

"Generally speaking, you shouldn't bother with a separate /home or /boot partition unless you're running multiple Linux distributions at once.

  The Ubuntu installers for both the desktop CD and server/alternate CD  have the ability to install over an existing system, preserving your  home directory (and the local system driectories: /usr/local, /usr/src, and /var/local).   This functionality also reuses the user ID and group ID of an existing  user, if it has the same username as the user you're creating during  installation."

and

"As for a separate /boot partition, that's a relic of  hardware constraints of the past (the bootloader 1024 cylinder limit).  I  can think of no practical advantage a separate /boot would have on a  modern system, and if not given an arguably excessive amount of space,  it will potentially fill up and create problems of its own, given that  Ubuntu does not automatically remove old kernels."
I agree that a separate /boot  partition is generally unnecessary.  In this particular instance, however, since it was suggested that the problem might have arisen because your large number of kernel images pushed the latest one "too far" (whatever that means) from the beginning of the disk, creating a /boot partition at the very beginning of the disk, particularly one that doesn't contain so many kernel images, seemed like a good way to rule out that possibility.

But I'll say again that I doubt that the problem is the kernel's location on the disk.  I would bet that if you pop in a new disk the problem will disappear, even if you clone the entire contents from the old one.

---

### Post by fbrand on 2014-03-28
I am not sure that a new disk booting proves anything other than it is not a motherboard issue. The question is, if I reinstall on this disk, will it boot.

If it does not then it sounds like there is a problem with the disk somewhere but if it does, it sounds like the issue might be a software issue.

To settle onet issue I will put a new disk in tomorrow and see what happens.

---

### Post by r.stiltskin on 2014-03-28
> **fbrand said:**
> I am not sure that a new disk booting proves anything other than it is not a motherboard issue.
That's true if you do an ordinary clean installation on the new disk.  That would be the practical approach.  But since we seem to be engaged in a primarily academic investigation, what I had in mind was creating an exact clone of the old disk on a new one using, for example, [dd (the infamous "disk destroyer")]("http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/"), or any other disk cloning utility.

Just be sure you know which drive is which before cloning, and also have all your valuable files backed up elsewhere.

---

### Post by fbrand on 2014-03-28
I have just installed 12.04 on another disk. Booted up perfectly with the original kernel 3.2.0.23, then updated and booted perfectly with the latest update kernel 3.2.0.60. So looks like it is associated with the disk.

The question now is whether it is the disk or the software on the disk. Maybe I will try a clone but with just a few weeks to go until I change computers I am reticent to take the risk of losing something. I have my stuff backed up on my server but I have had long experience of building new computers and asking if everything has been copied over and then 3 months down the track the owner asking if I saved her grandmother's wedding photo. So I may wait until I upgrade to do the checks.

Another alternative is to just reinstall 12.04 over the top of the existing drive without reformatting, thereby preserving /home and the local system directories and hope that there was nothing else I wanted.

---

### Post by fbrand on 2014-03-29
LATEST UPDATE...

I thought using a new drive had resulted in a good boot as in my last post but that was just not true. I t obviously only booted because they were warm boots. When I left the computer for a few hours and tried to reboot, the boot problem returned:-

Boot 1: Read error
Boot 2: hd0 out of disk space
Boot 3: booted OK

So looks like it has nothing to do with the disk. Is it the motherboard? But other than booting the motherboard performs faultlessly. Maybe change the motherboard battery? Or is it the software? Maybe try another kernel. I am now more confident than ever that the disk is OK. I will try loading Puppy Linux and Windows to see what happens.

---

### Post by fbrand on 2014-03-29
Very frustrating!!!

---

### Post by mansonfan78 on 2014-03-29
I doubt it would be the battery - nowadays it's just used for the clock anyway.  Motherboard is possible, but unlikely.  I'd try using a different drive cable if you have one.  But at this point, process of elimination would have to say software.  Or gremlins.

---

### Post by Navneet_Kumar on 2014-03-29
i think you might need to repartition the disk....and allocate a larger space to Linux

---

### Post by fbrand on 2014-03-29
Thanks Nav but I have already tried repartitioning and this is a second disk not the original so I am certain it is not the disk or the partitioning.

I have loaded Windows XP and it booted OK "warm" but when I left it a few hours and "cold" booted it showed Read error. So really looks like the motherboard.

I am now sending this out of Mint Linux and will cold boot that in a few hours but I really expect that it will get read errors too and that it may well prove to be the motherboard.

Mansofan78, I agree with you that it is probably not the battery as the BIOS is quite stable and the clock time is OK so it looks like a motherboard might be finding the garbage shortly.

Will get back after I try cold booting again later.

Thanks all.

---

### Post by fbrand on 2014-03-29
I tried cold booting Mint Linux and needed to boot four times before it would load the kernel. This behaviour has now been established with two disks over several operating systems and different kernels (12.04 was using 3.2.0.58/59/60 Mint was using 3.11.0.12). It is now reasonably clear to me that the problem is caused by the motherboard. Most likely by the disk controller on-board. For some reason it seems to take some time to be able to read the disk.

I will continue to force booting for the next three weeks until 14.04 is released and then retire this motherboard. If the board eventually gives up the ghost completely I will start on whatever 14.04 is available. 

Thanks everyone for your interest and feedback to eventually track down the culprit.

---

