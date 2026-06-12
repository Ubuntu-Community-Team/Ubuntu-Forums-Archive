---
title: "Migrating Wubi Installation: Creating &quot;type 83 - Linux&quot; partition to move Wubi into."
date: 2013-04-02
forum: New to Ubuntu
---

### Post by AndrewLisenby2013 on 2013-04-02
I've been an Ubuntu fan since 10.04 but I've never had to use Wubi (nor the forum, sorry if I leave anything out) to install Ubuntu before (Can't install from USB anymore); I'm now running 12.10.

I'm running two HDDs in my Gateway FX, and I assume that "sdb" is the drive I am migrating to ('/host' is mounted on sdb2).

When I followed the "Simplified" (meaning vague) instructions on migrating Wubi, I got an issue in the terminal saying "/dev/sdb1 is mounted - please unmount and try again," as well as "partition /dev/sdb1 must be type 83 - Linux." After 2 hours of relentless searching, all I've learned is that it MUST be a clean, "type 83 - Linux" partition.

My question that I submit to you: "How do I create a 'type 83 - Linux' partition and how big should it be?" In addition, what is a 'swap' drive and is it necessary for migrating the Wubi installation? I've got no shortage of RAM if that is a factor at all for the 'swap.'

Sorry if this is a repeat.

Thanks in advance
Andrew Lisenby

---

### Post by bcbc on 2013-04-02
You can create a partition using GParted. If you create an ext4 partition it will be assigned type '83' by GParted.

You only really need a swap partition if you want to hibernate. In that case, the swap partition must be greater than the size of your RAM. e.g. 4GB RAM = 4.5GB swap. (or 4.2 - I'd err on the larger size as sometime hibernation fails if there is swap overflow).

Here's a guide that shows step by step how to create partitions using GParted. It's run from a live CD/USB (which I guess you can't run?) but you can install and run gparted from the Wubi install as long as you're not trying to split a locked partition (i.e. whatever /host is mounted on). [http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html) 

If you need more info, let me know.

---

### Post by Impavidus on 2013-04-03
Boot into windows and use the windows partitioning tool to create continuous unallocated space on one of your drives. Also make sure you have at most 3 primary partitions there. Then boot ubuntu (wubi), install gparted, create an extended partition in the unallocated space and create a logical linux partition (ext4) in the extended partition. You can also add a swap partition and, if you like, a /home partition. Partition sizes are up to you. Then you can migrate wubi: [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---

### Post by bcbc on 2013-04-03
+1


PS I forgot the link I referred to in my own post so I've edited it now.

---

### Post by AndrewLisenby2013 on 2013-04-03
Okay, so I am recreating my live-usb, and if I can manage to get it to boot, all I have to do is create another partition using Gparted from the USB (as this won't mount my HDD)? Afterwords, will I have to restart my computer without the boot-disk, or should I redownload wubi-move from the boot-disk and migrate wubi from there so that my HDD being mounted doesn't interfere with the process?

Furthermore, how many Gig should I dedicate to the Wubi installation?

Thanks and sorry for all the questions,
Andrew Lisenby

--------------------------------------------------------------------------- 

Sorry, I posted the above clumsily before even bothering to refresh the page to see that you had posted again.

Unfortunately, I recently installed Windows 8 (which is somewhat lacking, in my opinion), and the OS became corrupted. For whatever reason, THAT boot disk doesn't work either (my disk drive just makes a tocking sound every time I insert the disk) so obviously I cannot repair the OS. To reiterate I have one corrupted OS containing my Wubi installation, and another that is running out of disk space because I can't manage aforementioned Wubi installation. If I could uninstall Windows altogether without corrupting or interfering with Wubi then I would do so. If I have to I'll just scrap this OS and re-install it if that would be any easier in your opinion (I just installed it about 3 weeks ago, so I wouldn't be losing much).

What course of action would you recommend?

Thank you,
Andrew Lisenby

---

### Post by bcbc on 2013-04-03
IMO it's easier to reboot in the Wubi install before migrating (but it's not required if you use the --root-disk= option). The new partition must be at least as big as the Wubi install (used space) - the script checks this - but I wouldn't limit it to that. Maybe 40-50GB minimum. This really depends on whether you'll be dual booting and sharing data between Windows, because if that's the case NTFS partitions are easier for that. If not you could make the ext4 partition larger. Some people like to setup a separate /home partition as well in which case the main / partition can be smaller e.g. 20-30GB.

Reinstalling or migrating... if you haven't done a lot of configuration, then it is probably easier to just backup data and reinstall. If you have everything setup the way you want it and don't mind creating the partitions, then migrating is easier.

---

### Post by AndrewLisenby2013 on 2013-04-04
Okay, so by managing my partitions with my live-USB, all I evidently did was destroy any possibility of me ever being able to boot that installation of Ubuntu ever again, oops. So anyways, it turns out the most painless thing to do was reinstalling Ubuntu 12.10 with the live-USB.

We can add 'Creating Boot Disk' to the list of things that Ubuntu will always do better than Windows.

I'll mark your last comment as the answer (If I can figure out how to do so).

Thank you bcbc,
Andrew Lisenby

----------------------------------------------------------

How do I mark this solved? I went to the "thread tools" and there is no button there to mark this solved. Am I too new of a user?

Thanks,
Andrew Lisenby

---

### Post by bcbc on 2013-04-04
Oops... that's not good. 

But glad you got it installed again. To mark a thread solved you have to go to the **Thread tools** drop down menu (top right above post #1) and look for it there.

---

### Post by AndrewLisenby2013 on 2013-04-07
Yea, I see where it's supposed to be, but under **Thread Tools **all I have is 3 options: **Show Printable Version, Email This Page, **and **Unsubscribe from this Thread.** Like I said, I just joined, so perhaps I don't have the option to do so until I've had more experience posting in the forum (just speculation).

I'll mark this as soon as I can.
Thank you for all the help bcbc,
Andrew Lisenby.

---

### Post by Impavidus on 2013-04-07
No, it's a temporary problem with the forum. To mark your thread as solved, you'll have to edit your first post, click "advanced"  and set the "solved" prefix.

---

