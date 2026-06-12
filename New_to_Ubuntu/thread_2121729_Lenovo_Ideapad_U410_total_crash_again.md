---
title: "Lenovo Ideapad U410 total crash again"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by WesternRyno on 2013-03-02
So after a few software downloads, Skype, Google Earth, Opera, nothing sinister at all, I restarted to refresh my system and have experienced yet another complete crash where I get a black or purple screen of complete inactivity.

This notebook comes with a 750GB hard drive and a 24GB SSD.  Did I possibly do something to mess up partitions and make this computer inoperable?

After a bunch of issues, I formatted both drives to wipe Windows 8 and to give me a fresh platform for an install and really have had no end of problems.  I'm a noob so I'm starting to suspect I've done something quite wrong and am in over my head.

There is a RAID on this computer, could that be it?  I will now begin to research this and will do a boot repair from a thumbdrive, but any advice would be quite welcomed.  Thanks.

---

### Post by fantab on 2013-03-02
Well, RAID is known to cause problems during Dual-Boot.  But I am no authority on using RAID. Wait for a better response. However, I wonder why do you need RAID. Did it come preinstalled or did you create RAID for some reason?

In the meantime [**Read These**]("http://ubuntuforums.org/search.php?searchid=39200").

---

### Post by WesternRyno on 2013-03-03
No, I didn't create the RAID and I don't know anything about them...yet.  If I get into it, not sure if it is going to be worth it.  Is it possible that some computers just aren't going to be compatible with Linux?  I've had nothing but problems the whole way.  I know a lot of that has been my inexperience, but the juice ain't worth the squeeze at this point and I'm a bit of a loss as to where to go next.  I can't really be spending weeks just trying to get the system stable, I gots ta get to work!  Have a feeling that someone with expertise needs to sit down with it and have a look.

From what I've been reading, yes, RAIDs are an issue, Nvidia cards are an issue, the trackpad is an issue, Memtest is an issue, SSD's are an issue, Intel Smart Response Tech is an issue, Optimus tech is an issue.

So I should have done more checking with compatibility issues before purchasing this laptop, but I was under the assumption that one could just install the Ubunut OS on anything and start rolling.  Yes, I am a novice.  Fortunately I can take this laptop back, but it leaves me curious about which one to get next.  Obviously many people install and enjoy Ubuntu without too much issue but I wonder if those people are the advanced types.  Starting to see the appeal of a mac at this point, despite the hefty cost.  Not a fan of windows really.  Ok, ramble over.

---

### Post by fantab on 2013-03-03
Ok... Linux works on most of the machines. The problem is with 'closed source proprietary' firmware/drivers. We can undo RAID- not a huge problem. Not all Nvidia cards create problems in Linux, most work and work well because Nvidia AFAIK makes 'closed source drivers for Linux users. Perhaps you got a 'lemon' in your hands.

[**Read Here**]("http://www.ubuntu.com/certification/desktop/") to find out what Hardware works 'out of the box' with Ubuntu in particular. This does not mean that other Hardware does not work.

Good Luck...

---

### Post by WesternRyno on 2013-03-03
Thanks for this link, I'll be doing a much better job researching before my next purchase with this recent experience in mind.  I am starting to think I have a lemon on my hands.  Either that or the way I installed did something irrevocable to my hardware or simply compatibility issues.

---

### Post by oldfred on 2013-03-03
These have worked.
 Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)
Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)

While not a Lenovo, it has the Intel SRT.

  HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache) - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)

Quotes:

 > Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

---

### Post by WesternRyno on 2013-03-03
Ok, thanks for these.

---

