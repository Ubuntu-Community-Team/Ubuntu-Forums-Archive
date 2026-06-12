---
title: "Wanting to build a home server"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by yakinikku on 2011-12-29
Hi guys,

I currently have an acer easystore running WHSv1.  This works for what I need it to do, but I want more space.  I am planning on building something with considerably more space, but I would like to have the same drive extender feature (or something that does the same thing) that is included in WHSv1.  

My current options are the following:

Amahi
Ubuntu?
Windows Server 2008 R2
Windows Home Server 2011 with Stablebit Drivepool or Drive Bender

I would like your suggestions as for what you would recommend I do?  The server is primarily used for streaming media to multiple devices at the same time, backups and accessing my data remotely.  I would like to use the new server for VPN/SSH and some other things as well, but that shouldn't impact the decision on what operating system to use.  At the moment I am leaning more towards Amahi, but if you have suggestions for me to do something else please let me know.  

I don't mind getting down and dirty with the CLI, but this drive extender type function is mission critical.  I would like to avoid hardware RAID.  What do you recommend?  

Thanks in advance!

---

### Post by 1clue on 2011-12-29
To be completely honest about it, if I were trying to set up something like you say I would just go grab one of the countless multi-disk file servers/sans for small office/home office (SOHO) out there.  There are lots of combinations, several of which are offered on each variant.  These are basically a networked drive array with options for RAID and some sort of limited server tools.

There's a pretty good chance the one you wind up with will be running some sort of Linux, but it will already be set up for you, including for streaming your media.  Or you could buy one and wipe the firmware, installing your own Linux.

There's also a pretty good chance that if you build your own it will cost more than one of the commercially available systems, be physically bigger and noisier.  And use more power.  And not be nearly as handy as what comes stock on the SAN units.

On the other hand, if you're interested in learning how to do this either for professional experience or for curiosity then by all means go ahead.  I've done a few myself.

---

### Post by yakinikku on 2011-12-29
> **1clue said:**
> To be completely honest about it, if I were trying to set up something like you say I would just go grab one of the countless multi-disk file servers/sans for small office/home office (SOHO) out there.  There are lots of combinations, several of which are offered on each variant.  These are basically a networked drive array with options for RAID and some sort of limited server tools.

There's a pretty good chance the one you wind up with will be running some sort of Linux, but it will already be set up for you, including for streaming your media.  Or you could buy one and wipe the firmware, installing your own Linux.

There's also a pretty good chance that if you build your own it will cost more than one of the commercially available systems, be physically bigger and noisier.  And use more power.  And not be nearly as handy as what comes stock on the SAN units.

On the other hand, if you're interested in learning how to do this either for professional experience or for curiosity then by all means go ahead.  I've done a few myself.

Size, power consumption and noise are not a problem.  The pre-fabbed boxes you are talking about do not allow me the space I require.  Most of them top out at 8 drives, which is not what I am going to be building.  I am going to be building a rather large server for the home, 10 drives minimum, probably 24 in a 4u rackmount case on the first go.

I would just like suggestions on the operating system really.  Windows server 8 looks like it is going to have drive pooling again, but it's not clear if it will do what drive extender did.  Amahi has greyhole, which does everything that drive extender did, and they are currently working on a version that will sit atop ubuntu rather then fedora.  

Anyhow, any suggestions about the host OS?

---

### Post by 2F4U on 2011-12-29
I built my home server from an older desktop PC with Pentium 4 processor. I replaced the hard drives with considerable larger ones and put Ubuntu server 10.04 on it. I don't need a GUI and Ubuntu server, by default, comes without GUI, so its perfect for that. As far as I know, LVM on Linux is the equivalent to Drive Extender, and it is per default available.

---

### Post by yakinikku on 2011-12-29
> **2F4U said:**
> I built my home server from an older desktop PC with Pentium 4 processor. I replaced the hard drives with considerable larger ones and put Ubuntu server 10.04 on it. I don't need a GUI and Ubuntu server, by default, comes without GUI, so its perfect for that. As far as I know, LVM on Linux is the equivalent to Drive Extender, and it is per default available.

EDIT:  It appears that LVM allows for pooling, but there is no data redundancy.  Drive extender has redundancy without the need for additional hardware (IE RAID cards).

Double Edit:  If I am wrong, please let me know.

---

### Post by 2F4U on 2011-12-29
Maybe ZFS could be interesting for you?

[https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)

---

### Post by Lars Noodén on 2011-12-29
Of the list you provide, I would say definitely Ubuntu.  Another option which is very close to Ubuntu but with a longer release cycle is Debian.  Either way you could go with RAID 5 or 6.  [btrfs](https://btrfs.wiki.kernel.org/) is worth considering, too.

---

### Post by yakinikku on 2011-12-29
> **Lars Noodén said:**
> Of the list you provide, I would say definitely Ubuntu.  Another option which is very close to Ubuntu but with a longer release cycle is Debian.  Either way you could go with RAID 5 or 6.  [btrfs](https://btrfs.wiki.kernel.org/) is worth considering, too.

Do you have any other suggestions that are not on the list?  I am open to suggestions as long as it has drive pooling and redundancy built in (the redundancy is the most important thing to me).  

With DE you can select the folders that you want to be backed up across drives, I would like something similar in linux, at the moment the only thing I have seen is greyhole.  Greyhole can be installed on ubuntu, which is nice.  LVM looks like a no go.  If you lose one drive in the array, you lose everything, which is no good.

It looks like there are plenty of options for spanning, but not so much for redundancy, or am I missing something?

I am really trying to avoid hardware RAID if at all possible.  What would you suggest for that?

---

### Post by yakinikku on 2011-12-29
> **2F4U said:**
> Maybe ZFS could be interesting for you?

[https://wiki.ubuntu.com/ZFS](https://wiki.ubuntu.com/ZFS)

ZFS does look pretty interesting, but it doesn't appear to offer the redundancy I am looking for, or am I missing something?

Could I setup this redundancy using Samba?

---

### Post by 2F4U on 2011-12-29
This article gives some information about ZFS and redundancy:

[http://www.solarisinternals.com/wiki/index.php/ZFS_Configuration_Guide#Choosing_Storage_Array_Redundancy_With_ZFS](http://www.solarisinternals.com/wiki/index.php/ZFS_Configuration_Guide#Choosing_Storage_Array_Redundancy_With_ZFS)

---

### Post by Lars Noodén on 2011-12-29
> **yakinikku said:**
> Do you have any other suggestions that are not on the list?  I am open to suggestions as long as it has drive pooling and redundancy built in (the redundancy is the most important thing to me).

You could have software RAID on OpenBSD or Debian or Ubuntu.  

As far as ZFS goes, it probably won't make it to Linux.  But many of the same capabilities are promoted in [btrfs](http://www.linux-mag.com/id/7308/).

---

### Post by lykwydchykyn on 2011-12-29
Have you looked at FreeNAS yet?  It's built on BSD and the latest release has ZFS.

---

### Post by spillin_dylan on 2011-12-29
Not sure if it's what you want, but I followed an excellent how-to at [http://www.woodel.com/](http://www.woodel.com/) and have had excellent results.  It's a Debian setup, with Webmin for remote administration, but I barely use that anymore, and instead ssh into my box.  It does talk about a software RAID setup, but I skipped that part, as I don't require it.

---

### Post by yakinikku on 2011-12-29
> **lykwydchykyn said:**
> Have you looked at FreeNAS yet?  It's built on BSD and the latest release has ZFS.

I have.  Unfortunately freeNAS does not allow me to access my data from a remote location and is not as powerful as I would like it to be.  Any other suggestions? :)

---

### Post by yakinikku on 2011-12-29
> **spillin_dylan said:**
> Not sure if it's what you want, but I followed an excellent how-to at [http://www.woodel.com/](http://www.woodel.com/) and have had excellent results.  It's a Debian setup, with Webmin for remote administration, but I barely use that anymore, and instead ssh into my box.  It does talk about a software RAID setup, but I skipped that part, as I don't require it.

Thank you for the link, I will give it a look.  Doing it with debian would be nice.  rolling releases are mmm...mmmm good.

---

### Post by yakinikku on 2011-12-29
> **Lars Noodén said:**
> You could have software RAID on OpenBSD or Debian or Ubuntu.  

As far as ZFS goes, it probably won't make it to Linux.  But many of the same capabilities are promoted in [btrfs](http://www.linux-mag.com/id/7308/).

Are there any downsides to going with software raid?  can you mix and match drive sizes/vendors?

---

### Post by yakinikku on 2011-12-29
> **2F4U said:**
> This article gives some information about ZFS and redundancy:

[http://www.solarisinternals.com/wiki/index.php/ZFS_Configuration_Guide#Choosing_Storage_Array_Redundancy_With_ZFS](http://www.solarisinternals.com/wiki/index.php/ZFS_Configuration_Guide#Choosing_Storage_Array_Redundancy_With_ZFS)

Thank you.  Taking a look at it.:guitar:

---

### Post by collisionystm on 2011-12-29
Zentyal

software raid

I always do Raid 10 on my systems.

---

### Post by yakinikku on 2011-12-29
> **collisionystm said:**
> Zentyal

software raid

I always do Raid 10 on my systems.

software RAID 10?  I am looking at the Zentyal site now, thanks.

---

### Post by yakinikku on 2011-12-30
I may just go with hardware RAID 5 or 6 as finding exactly what I want seems to be a tedious process.

---

### Post by lkraemer on 2011-12-30
yakinikku,
You can setyp FreeNAS so you can SSH into it easily.  You just need to assign some
nonstandard Port on your router that is Opened to FreeNAS, and is used to SSH into
your FreeNAS Box.  FreeNAS also allows you to use a Print Spooler as
an addon to the original setup.  Although, I have found you will need to 
remove the LAN Cable to FreeNAS when you reoot your router for some reason.

You can even access the Setup GUI via remote Connection.

Other than it works GREAT!.

Another option might be SMS.  REF: Distrowatch.com

lk

---

### Post by yakinikku on 2011-12-30
> **lkraemer said:**
> yakinikku,
You can setyp FreeNAS so you can SSH into it easily.  You just need to assign some
nonstandard Port on your router that is Opened to FreeNAS, and is used to SSH into
your FreeNAS Box.  FreeNAS also allows you to use a Print Spooler as
an addon to the original setup.  Although, I have found you will need to 
remove the LAN Cable to FreeNAS when you reoot your router for some reason.

You can even access the Setup GUI via remote Connection.

Other than it works GREAT!.

Another option might be SMS.  REF: Distrowatch.com

lk

Not sure what you are linking me to on that last link.  I think I am going to skip freeNAS.  Thanks for the info though, I didn't know that you could SSH into it.  :)

---

### Post by Lars Noodén on 2011-12-31
> **yakinikku said:**
> Are there any downsides to going with software raid?  can you mix and match drive sizes/vendors?

The drives can be different models, brands or sizes, but the actual partitions that go into the array should all be the exact same size AFAIK.  I don't think there is much of any downside to a software RAID except that the units are not hot-swappable.  It's easy to build and maintain though.

---

### Post by lkraemer on 2011-12-31
You have never been to [http://distrowatch.com/](http://distrowatch.com/)

Go check it out.......

lk

---

### Post by memilanuk on 2011-12-31
I'm not all that familiar with the drive extender features of WHS, other than hearing about all the fuss when they dropped it.

What it sounds like you want - to be able to just add a drive (or drives) and have it added to the 'pool' while still having drive redundancy ala RAID - is something I don't think is *easily* achievable under Linux with current mainstream technology.  A combination of software (or hardware) RAID to provide the redundancy along with LVM to provide the ability to 'extend' filesystems to include newly added RAID clusters of drives would work... but being able to take a (for example) 5-drive RAID 6 cluster with LVM over the top and just add a 6th drive and have it automagically integrated into the RAID 6 array without completely backing up and rebuilding the RAID array is something I don't think is currently possible with say, ext4.  Someone correct me if I'm wrong...

This is where ZFS supposedly shines.  It (more or less) combines software RAID and LVM into the base filesystem, adding features like de-duplication, among others.  BTRFS is supposed to have many of the same features and is available in current releases of most major Linux distros, including Ubuntu.  Whether its ready for 'prime-time' or not is still subject to discussion - none of the major distros offer it as the 'default' filesystem, which seems to be the de facto stamp of approval.  Newer releases of FreeBSD have somewhat current versions of ZFS available in them, and there are some open-source Solaris derivatives like OpenIndiana and Nexenta that have newer version (better features, etc.) of ZFS as well.  The folks over @ HardForum in the [Data Storage]("http://hardforum.com/forumdisplay.php?f=29") sub-forum are pretty 'into' that sort of thing - building multi-terabyte systems using RAID, ZFS, etc.  Might be worth looking into...

Another option that sounds almost *exactly* like what you're looking for might be [Greyhole]("http://www.greyhole.net/")...

HTH,

Monte

---

### Post by yakinikku on 2012-01-07
> **lkraemer said:**
> You have never been to [http://distrowatch.com/](http://distrowatch.com/)

Go check it out.......

lk

As a matter of fact distrowatch is in my RSS feed.  Not sure what visiting the site would accomplish.

---

### Post by yakinikku on 2012-01-07
> **Lars Noodén said:**
> The drives can be different models, brands or sizes, but the actual partitions that go into the array should all be the exact same size AFAIK.  I don't think there is much of any downside to a software RAID except that the units are not hot-swappable.  It's easy to build and maintain though.

I think I didn't ask the right question when I asked you this, but I found the answer to the question that I meant to ask on my own.  Thanks for the info though :D

---

### Post by yakinikku on 2012-01-07
> **memilanuk said:**
> I'm not all that familiar with the drive extender features of WHS, other than hearing about all the fuss when they dropped it.

What it sounds like you want - to be able to just add a drive (or drives) and have it added to the 'pool' while still having drive redundancy ala RAID - is something I don't think is *easily* achievable under Linux with current mainstream technology.  A combination of software (or hardware) RAID to provide the redundancy along with LVM to provide the ability to 'extend' filesystems to include newly added RAID clusters of drives would work... but being able to take a (for example) 5-drive RAID 6 cluster with LVM over the top and just add a 6th drive and have it automagically integrated into the RAID 6 array without completely backing up and rebuilding the RAID array is something I don't think is currently possible with say, ext4.  Someone correct me if I'm wrong...

This is where ZFS supposedly shines.  It (more or less) combines software RAID and LVM into the base filesystem, adding features like de-duplication, among others.  BTRFS is supposed to have many of the same features and is available in current releases of most major Linux distros, including Ubuntu.  Whether its ready for 'prime-time' or not is still subject to discussion - none of the major distros offer it as the 'default' filesystem, which seems to be the de facto stamp of approval.  Newer releases of FreeBSD have somewhat current versions of ZFS available in them, and there are some open-source Solaris derivatives like OpenIndiana and Nexenta that have newer version (better features, etc.) of ZFS as well.  The folks over @ HardForum in the [Data Storage]("http://hardforum.com/forumdisplay.php?f=29") sub-forum are pretty 'into' that sort of thing - building multi-terabyte systems using RAID, ZFS, etc.  Might be worth looking into...

Another option that sounds almost *exactly* like what you're looking for might be [Greyhole]("http://www.greyhole.net/")...

HTH,

Monte


You hit the nail on the head as for what I am looking for.  That is why Amahi is on the list as it includes greyhole from the get.  Greyhole has come a long long way since it's inception (I have been following the project for quite a while now), but it still is not quite at the level of refinement I think it needs to be at just yet.  But it's close.  I will check out the link that you suggested.  Thanks :D

---

### Post by rsvancara on 2012-01-07
Depends on your performance characteristics you want for your file server and what features you need.  ZFS is a mature solution.  BTRFS is still very young.  Both solutions offer a tremendous amount of benefit in terms of building a enterprise class storage solution on a small budget.  Features include:

storage pools,
snapshots,
redundancy (RAID)

I would not recommend BTRFS yet, as it does not seem to have an effective FSCK tool yet and it is easy to break your BTRFS volumes (I have 4TB that I have broke many times already and could not repair due to various bugs).  My advice is to wait on BTRFS until they finish a good FSCK tool.  ZFS does seem promising, but the ZFS license is at odds with the Linux Kernel License (cddl vs gpl) so ZFS is maintained separately from the Linux Kernel.  

FreeBSD has ZFS built in, but there are a whole slew of issues with FreeBSD in terms of hardware support.  

Of course there is the traditional RAID controller approach which a good hardware RAID controller can set you back around $300 to $800 dollars.  Not to mention for 10 drives, you are going to probably need a SAS backplane to support all those disks on a single controller.  

Software RAID does have some advantages over HARDWARE RAID in that you can use any controller you want, but just make sure you are using UUIDs for the drive identifiiers and not /dev/sda1, /dev/sdb1, /dev/sdc1 etc, as sometimes those device designations change.  

But whatever you do, factor in a good backup solution.  Nothing is worse than configuring a lot of storage and then have it fail.  I would look at storage and how you are going to back it up.  

Best of luck!

---

### Post by yakinikku on 2012-01-09
> **rsvancara said:**
> Depends on your performance characteristics you want for your file server and what features you need.  ZFS is a mature solution.  BTRFS is still very young.  Both solutions offer a tremendous amount of benefit in terms of building a enterprise class storage solution on a small budget.  Features include:

storage pools,
snapshots,
redundancy (RAID)

I would not recommend BTRFS yet, as it does not seem to have an effective FSCK tool yet and it is easy to break your BTRFS volumes (I have 4TB that I have broke many times already and could not repair due to various bugs).  My advice is to wait on BTRFS until they finish a good FSCK tool.  ZFS does seem promising, but the ZFS license is at odds with the Linux Kernel License (cddl vs gpl) so ZFS is maintained separately from the Linux Kernel.  

FreeBSD has ZFS built in, but there are a whole slew of issues with FreeBSD in terms of hardware support.  

Of course there is the traditional RAID controller approach which a good hardware RAID controller can set you back around $300 to $800 dollars.  Not to mention for 10 drives, you are going to probably need a SAS backplane to support all those disks on a single controller.  

Software RAID does have some advantages over HARDWARE RAID in that you can use any controller you want, but just make sure you are using UUIDs for the drive identifiiers and not /dev/sda1, /dev/sdb1, /dev/sdc1 etc, as sometimes those device designations change.  

But whatever you do, factor in a good backup solution.  Nothing is worse than configuring a lot of storage and then have it fail.  I would look at storage and how you are going to back it up.  

Best of luck!

Thank you for the long, well thought out and informative post.

I have already researched the hardware pretty thoroughly, so at this point it boils down to operating system.  ZFS does sound interesting, but at this point hardware RAID is not in the cards.  I want this thing to be simple enough for my wife to be able to change things out without me around.  Greyhole almost allows for that, except you have to dig into the command line, something she couldn't do.

---

