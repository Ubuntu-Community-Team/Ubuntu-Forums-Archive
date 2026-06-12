---
title: "Splitting up partitions and installing"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by mpn_1990 on 2008-06-10
I'm a relatively new linux user, but a very experienced windows user. I would like to try the newest Ubuntu. I thought about using wubi but I heard people outgrow it quickly and I heard (but not sure if it's true) that it trashes the entire NTFS filesystem it's in if the power goes out. Not too enticing. I've also tried running Ubuntu in virtual pc 2007, but the experience was *real* bad. The sound didn't work, the video didn't work, it was a mess. It was also slow and generally pokey. But that's with anything I try to run in VPC that was made after 1999.

So, I've decided to bite the bullet and do it the right way by splitting up my partitions and stuff. I've used a knoppix disc before to resize a partition on my old PC using gparted/ntfsresize. Went over without incident, however it still lingers in the back of my head that ntfsresize can end up screwing up everything. Norton Ghost can remedy that if anything happens, right?

However, that was pretty straightforward compared to what I've run up against now. My old PC was a compaq with the HD having one lone NTFS partition. I have a Dell XPS 410 with all the factory software and stuff, and to put it bluntly, the partitioning Dell did is a mess. Here's what I'm up against: it's in the attatched image.

This is confsing me. How can all the partitions be marked "primary"? What is this "EISA Configuration"? That last one, the FAT32, I think is what the factory recovery disc uses.

I'd like to shrink the (C:) partition and squeeze a 15GB ext3 between it and the FAT32 partition. As in, when all is done, I want it to look like the above except C: is 15GB smaller and an "unknown partition" (ext3 linux) is to the right of C:. But here's where I'm confused.

Is this as easy as it looks? I'm afraid when I shrink the C: and add in the other one, it's going to throw the other two off kilter for whatever they're used for. Like, if I ever try to restore my computer, it's going to be like "where on earth is the fat32 partition?" If I use gparted to shrink C: and make the remaining space ext3, will windows even boot next time because of all this? And where does primary/secondary partitions factor into all of this? Does primary just mean you can boot an OS from it?

After that, I'd like to use the NTLDR instead of GRUB/LILO to choose between Ubuntu and Windows. Is this possible?

Sorry for the tl;dr post, but I'm just really confused and don't want to screw up my system.

---

### Post by forestpixie on 2008-06-10
I think you'll find that the partition on the end is the restore/repair vista one if that's what you are running. When you run your file manager does it see the 5Gb FAT partition?

You should be fine to resize the partition, obviously make sure you have backups of stuff you don't want to lose, just in case you understand.

If you are running vista use the vista tool to do the resizing - I believ it is better that way.

Not sure about the NTLDR thing though.

Hope that helps a bit.

Primary partitions - a harddrive can have 4 maximum - buntu will install itself in an extended partition on logical partitions, of which I think the maximum is a ridiculous number :)

---

### Post by Corrupt3d on 2008-06-10
Hey, glad you finally decided to do a full Ubuntu install.
I originally had 3 partitions on my HD: C: Windows, D: recovery, and a Direct play partition. I had Partition Magic software so I decided to go with that, but gparted should work just as well. I ended up deleting my 2 other partitions and then shrinking my C drive, it all went through without any incident and Windows XP booted up fine. (I made a copy of my system...just in case ;)) 

I think that unless you get a powersurge or something of that nature your system should boot up fine.

---

### Post by Duck2006 on 2008-06-10
With the older pata drivers and ide drivers you could have 63 partitions, but these days with sata drives it has been cut down to 15 i think.

---

### Post by forestpixie on 2008-06-10
> I think that unless you get a powersurge or something of that nature

Exactly why you should have backups - we don't really want another "Nothing works, everything is gooooooone" thread :)


> With the older pata drivers and ide drivers you could have 63 partitions, but these days with sata drives it has been cut down to 15 i think.Aaah didn't know that - the most I had was 10, which was more than enough.

---

### Post by mpn_1990 on 2008-06-10
Well, I found [this]("https://help.ubuntu.com/community/WindowsDualBoot") gude to dual-booting the two OSs, and it includes info relevant to my case.

I trashed Norton Ghost...it didn't update right and kept crashing...awful, awful, awful software, waste of money.

So, I just decided to copy over important documents and stuff. I don't have the space to back up a 300GB HD image filled to the top. What is the failure rate of ntfsresize/gparted? This data is kinda important. If something happens during the resize, can it be reversed?

And if NTLDR can't be used, does Ubuntu install GRUB by default, and does it still let me boot into XP without incident?

---

### Post by rohitsb on 2008-06-10
> 
I think that unless you get a powersurge or something of that nature your system should boot up fine.

Exactly, and I don't see how Wubi can mess up the partitions. It's the power surge isn't it ? :) 

But seriously, threads indicate that all mounted partitions are at risk theoretically. So even if you boot into a pure Linux installation and mount the windows partition, you're still screwed.

In fact, hard reboots will also take out the windows file systems, when logged in to windows - no telling what they could do.

Just wondering...

RSB

---

