---
title: "Windows 7 GRUB issue after drive clone"
date: 2016-05-01
forum: New to Ubuntu
---

### Post by danny61 on 2016-05-01
Hi,

 I previously had setup my Windows 7 laptop to duel booting Ubuntu with a GRUB boot menu. Today I cloned my 750GB drive to a 2TB drive and got a GRUBrescue prompt when I tried to boot.

 Using an Ubuntu Live USB boot-able drive I ran the following commands via terminal.

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair After rebooting the GRUB is still not displayed, and windows now keeps displaying a white progress bar on the bottom and it says windows is loading files. Then it goes into some type of recovery mode, and windows says it's trying to repair the startup environment. At the end of that process it says it's not able to repair it.

 
I again booted back into Ubuntu with the Live USB, and tried running the above commands again, but there is no change. Windows again tries to repair, and fails.

 
I have not changed any settings in Boot Repair, I have left everything as default.

 
Please see below for the paste bin.

 
[URL="http://paste.ubuntu.com/16183381/"]http://paste.ubuntu.com/16183381/

[/URL]

 Thank you very much for any assistant you can offer, it is GREATLY appreciated.

Danny

---

### Post by grahammechanical on 2016-05-02
From what I can tell Boot Repair is offering to install a generic bootloader into sda so that you can load Windows. I have no idea if that will succeed. Another thing that I notice is that Ubuntu is not showing up in any of the partitions. Did you see this?

> 1 disks with OS, 2 OS : 0 Linux, 0 MacOS, 2 Windows, 0 unknown type OS. 

Regards.

---

### Post by Bucky Ball on 2016-05-02
Bit of clarity, please. Are you saying you had Win7 and Ubuntu dual-booting on a hard drive, cloned the hard drive and now you can't boot from the cloned copy or you are trying to move Windows from one disk to the other and the cloned copy of Windows is not booting? I'm presuming the latter as you don't have Ubuntu installed anywhere, as previously mentioned. Please confirm.

What software app did you use to clone the drive? When you say you 'cloned the drive', do you mean you cloned the partitions individually?

---

### Post by danny61 on 2016-05-02
I had Win7 and Ubuntu dual-booting on a hard drive, cloned it to a new larger drive and now I can't boot from the cloned copy. I can still boot from the original hard drive to both Win7 and Ubuntu so it's really odd that Ubuntu doesn't show up as both of you have pointed out.

I created the clone using a "Sabrent EC-HDFN SATA Docking Station" I recently got from Amazon. Not sure I'd recommend the product based on my current experience. Nevertheless, it's got a stand alone function that's supposed to clone a drive. Pop the hard drives in, turn it on, hold down the button until it blinks, then once it's done it's supposed to beep, which it did.

This thing is a docking station as well, so maybe I can use it with some other technique that does actually clone bit by bit like this was supposed to. I do have other machines I can connect it to to perform this process if some other more reliable method is available.

It's an ASUS G73JW laptop, that I think comes with a recovery partition, so that *might* be why it's reporting "2 Windows".

I'm technically inclined in other areas, but not this type of  thing so I very much appreciate everybody's help.

Dan

---

### Post by leunam12 on 2016-05-02
I suggest you clone it again using clonezilla's "disk_to_local_disk_clone" method. It has never failed me.

[http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

---

### Post by LostFarmer on 2016-05-02
You do have a bad clone:

Invalid MBR Signature found.
Empty Partition.

sfdisk: ERROR: sector 889149555 does not have an msdos signature
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Running 'sfdisk' and do a write could fix problem but I have not use sfdisk so can not help.  It looks like the required msdos signature is missing from the extended partition table so the logicl volumes can not be located.

the above errors could also be causing Win 7 to have boot problems.

---

### Post by oldfred on 2016-05-02
You will have drive performance issues with your clone. Better to just reinstall and copy any data you want over.

New drive is a 4K drive.
> Sector size (logical/physical): 512 bytes / 4096 bytes

But you show first partition starting at sector 63 which is not compatible with new 4K drives. Windows changed with Windows 7 to start first sector with sector 2048. And soon after Linux also changed. You show some old XP boot files so I assume you updated from XP to 7. Windows XP did use the old start of sector 63.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by danny61 on 2016-05-02
Thank you for noticing that, I guess the Sabrent docking station isn't doing what it's supposed to do.

I'm sure this won't come as a surprise, but the instructions are extremely vague and don't perfectly match the product itself. It says that during the clone process the green light will flash, then the unit will beep and the green light will go out when it is complete. However, there is not simply a green light, it's a series of lights that goes from 25% to 100%, and the green light pulses from one to the next. After about 30 minutes it begins continuously beeping very loudly but the green lights continue their pulse from one to the other. I've tried this 3 times already, the last time I let it beep for an additional 30 minutes to see if the pulsing lights would show progress or change in any way, but it stayed the same. I even put a powerful fan in front of it in case it was over heating or something (even though the drives only feel moderately warm).

I'll try to use it with the Clonezilla process and see what happens. Either way, I'm sending it back to Amazon or beating it with a sledge hammer, haven't made my mind up just yet.

Thank you again for the feedback, it's been very helpful.

Dan

---

### Post by danny61 on 2016-05-02
> **oldfred said:**
> You will have drive performance issues with your clone. Better to just reinstall and copy any data you want over.

New drive is a 4K drive.


But you show first partition starting at sector 63 which is not compatible with new 4K drives. Windows changed with Windows 7 to start first sector with sector 2048. And soon after Linux also changed. You show some old XP boot files so I assume you updated from XP to 7. Windows XP did use the old start of sector 63.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

I wasn't aware of this, and now has me second guessing my next step. The laptop ( and the source drive) in question was shipped to me with Windows 7 installed, and has a factory Windows 7 recovery partition. So I'm not sure why it's reflecting anything related to XP, that's confusing to say the least.

Thank you for that insight, now I have to figure out what I'm going to do.

Dan

---

### Post by Bucky Ball on 2016-05-02
> **danny61 said:**
> The laptop ( and the source drive) in question was shipped to me with Windows 7 installed, and has a factory Windows 7 recovery partition ...

If it was bought as a new machine I'd be getting suspicious as, looking at oldfred's post, looks like the hard drive at least was running XP at some time and they've simply bunged Win7 on a second-hand hard drive, not a new one. Conjecture at this point and off-topic. Apologies, but thought I'd mention ...

If you only bought it recently as a new machine I would consider digging deeper and taking it further, but that's me. :) Good luck.

---

### Post by danny61 on 2016-05-02
> **Bucky Ball said:**
> If it was bought as a new machine I'd be getting suspicious as, looking at oldfred's post, looks like the hard drive at least was running XP at some time and they've simply bunged Win7 on a second-hand hard drive, not a new one. Conjecture at this point and off-topic. Apologies, but thought I'd mention ...

If you only bought it recently as a new machine I would consider digging deeper and taking it further, but that's me. :) Good luck.

I totally hear what you're saying and agree something seems amiss, but I purchased it myself new from the [Asus site ]("https://www.asus.com/ROG-Republic-Of-Gamers/ROG-G73Jw/")site years ago.

Maybe this is why the clone fails to complete... left scratching my head. :confused:

Dan

---

### Post by Bucky Ball on 2016-05-02
My money's on the dock. As suggested, confirm this by trying something like [Clonezilla]("http://clonezilla.org/") or fsarchiver. fsarchiver can be found with a bunch of other useful stuff on the [SystemRescueCD]("http://www.system-rescue-cd.org/System-tools").

---

### Post by oldfred on 2016-05-02
Is original drive partitioned the same, or is your clone device doing its own thing?
Windows does not like partition changes, and always needs chkdsk. And it particularly does not like start of partition changes. Start & size of partition is also embedded in PBR or partition boot sector and must match partition table. While chkdks often fixes it, some other data can create issues.

Did you or can you from old drive create a recovery disk? But if early Windows 7, it may have been a Windows XP that they converted to Windows 7? Do not know if Asus offers recovery disks or download, only a few vendors do.

---

### Post by danny61 on 2016-05-02
The cloned drive to me, appears to be doing it's own thing. Because I have two partitions on the original drive, one for the OS, and one for data storage. But when I connected the cloned drive to another machine to see what was on it , it only had one partition which makes no sense to me.

I personally didn't resize it, and as I understood the clone process and how it was supposed to happen, it was supposed to be bit by bit, not knowing or caring what those bits were. In the end, the bits were supposed to add up to an exact copy of the original drive. Made sense to me, but for whatever reason that didn't happen.

Yes, I can create a recovery disk from the old drive. I have one laying around somewhere, but based on my experience with all things Microsoft, Ubuntu and Boot Repair became my go-to recovery option. And as you can imagine, I've used that option many times over the years. You all probably understand better than I do why seemingly out of nowhere Windows just decides not to boot. Yes, sometimes it would happen for a valid reason, like after a Windows Update (rolls eyes), but other times I've had it happen just because I powered on the system. None of this is news to you, that's just  "feature" of Windows as we know it.

Okay, rant over... just downloaded Tuxboot and had it load everything it needs onto a USB drive. Going to pop it into the other machine and give it a go.

Dan

---

### Post by danny61 on 2016-05-02
It's chugging along, looks like it's going to be a while. Anything look out of the ordinary?

[ATTACH=CONFIG]268803[/ATTACH]

Thanks!

Dan

---

### Post by Bucky Ball on 2016-05-03
Looks normal to me but I have no experience with Tuxboot and have never seen it.

Only you know whether backing up sda2 to sdb2 is correct.

---

### Post by danny61 on 2016-05-03
It was a bit touch and go there for a while, but somehow Clonezilla seems to have saved the day. I'm happy say that I'm typing to you from the cloned drive computer, the drive boots and seems to be functioning normally as far as I can tell.

However, there were some troubling messages towards the end of the clone process that I'd like to request some feedback on, please see photos.

It reported bad sectors on the drive, but I'm not exactly sure which drive it's referring to, and am not able to locate the referenced log file.
[ATTACH=CONFIG]268828[/ATTACH]

At that point I hit enter, it continued, completed, and seems to work normally at the moment.

Also, somebody had mentioned that because it's a 4k drive, and of the way the previous drive was partitioned I may have performance issues. Is there a way for me to verify the issues exists, and is there any way that I can do something resolve those problems other than a total wipe/ format/ OS reinstall?

Las thing I'd like to say is thank you to everybody that helped out and provided feedback. It may seem like a small thing, answering a forum post, but the world is a better place because there's people like you who are willing to help others they've never even met.

Dan

---

### Post by Bucky Ball on 2016-05-04
As far as the message goes, no, not sure which drive that refers to either. Let's hope it refers to the one you're cloning *from* and not *to* and that someone can confirm one way or t'other.

One way or the other, great news it seems to have worked and you're posting from it now. Please mark the thread as solved to help others as your original issue is solved. This doesn't close the thread to further discussion. If you have other questions not related to this title, though, you'd improve your chances by posting a new thread. 

Good luck. :)

---

