---
title: "[SOLVED] 2nd HD"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by AnLGP on 2008-07-07
I've got a second HD installed and I basically just want it to be a backup for my 1st one.  I want to format the drive. There's nothing on it I really care about but before I format it I want to know what I'm formatting, exactly.  Could you guys take a look at this and tell me what's what?  

[http://s297.photobucket.com/albums/mm213/musicauniversalis/?action=view&current=screen.png](http://s297.photobucket.com/albums/mm213/musicauniversalis/?action=view&current=screen.png)

What's throwing me off are the linux partitions.  Those aren't on the 2nd HD, just the new (1st) HD and I want to be sure not to delete those partitions if that is them.

Thanks.

---

### Post by neurostu on 2008-07-07
So it looks like the 2nd hard drive has an extended partition on it but I'm not sure... 

What you can do is install gparted:
```

sudo apt-get install gparted

```
Then open System-->Administration-->Gnome Partition Manager. (Or something like that).

Then you can look at the HDD, and reformat it. I would recommend you format it ext3.

Also if you don't know how to back up yet I would recommend looking into rsync.  its a great tool that can be used in scripts and setup to run automatically with cron jobs.

rsync is nice because after your initial backup it only copies the changes and keeps your backup up to date.  Its a really slick program.

---

### Post by AnLGP on 2008-07-07
I've asked about an ideal backup situation on another thread and someone else has recommended rsync w/cron jobs as well.

My main OS isn't Ubuntu its Debian.

---

### Post by neurostu on 2008-07-07
Gparted could be in the debian repos

---

### Post by AnLGP on 2008-07-07
oh i'll get the live CD good idea!  Thanks.  It is in the debian repos I don't know what I was thinking.  :)

---

### Post by neurostu on 2008-07-07
When you say liveCD I hope you mean the Gparted liveCD its only 45 mb or so and won't take nearly as long to download as the ubuntu/debian liveCD

---

### Post by AnLGP on 2008-07-07
Yes.  GpartED live CD

---

### Post by bobpur on 2008-07-07
Looking at the picture, the bottom 3 lines are your linux partitions. The "extended partition" encompasses the SWAP Partition. What this looks like in a graph is SWAP will be a brown block encircled by a turquoise(I think) block. That's the way it looks in Ubuntu, anyhow. Notice that your "extended partition" line has the entries after it and the SWAP line doesn't? It's because they're the same.
You can download a stand-alone bootable live cd of Gparted, System Rescue CD or Parted Magic (Pmagic) at: [www.distrowatch.com](www.distrowatch.com). Download your choice and burn the ISO to a cd and check your partitions.
I saw a FAT32 partition line in your graph. I don't think that is needed anymore as newer distros will read/write to NTFS. I can go into my Windows drive ,from linux, and move files from/to my linux drive. I don't think I can do it from Windows, though.
Oh yeah, I just noticed, in your graph, one drive is labeled "hda" and the other is labeled "sda." These are two different drives in the way they hook up to your computer. SDA is a SATA drive and HDA is a PATA drive (with a wide flat ribbon cable and a 4-pin molex connector for power). It looks like linux is on the SATA drive along with a Win95 FAT32 partition???? :) If that's the case, wipe everything with the "HDA" label. You might take that Win95 FAT32 thing too :)

Good luck!

---

### Post by bobpur on 2008-07-07
In the words of Steve Erkol; "Did I do that?"
I hope I didn't, accidently, mark this post SOLVED 
I'm not sure how to fix it if I did. My apologies.

---

### Post by wannadumpwindows on 2008-07-07
> **bobpur said:**
> In the words of Steve Erkol; "Did I do that?"
I hope I didn't, accidently, mark this post SOLVED 
I'm not sure how to fix it if I did. My apologies.

You can't mark a thread as "Solved" unless you started it. You couldn't have done it.:)

---

### Post by AnLGP on 2008-07-08
I marked it as solved.  You were correct about PATA and SATA.  I figured out how to do it thanks guys :)

---

