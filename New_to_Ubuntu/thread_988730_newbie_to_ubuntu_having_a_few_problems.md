---
title: "newbie to ubuntu having a few problems"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by michaelt196 on 2008-11-20
So I'm pretty much a complete beginner to linux and ubuntu but I was looking around today and someone suggested that I try it out. 
I wasn't really sure if I wanted it so I tried that wubi ******** (excuse my language, but it isn't being too nice to me.) and it just hasn't worked at all. I did the install and it brought me to the boot list and I picked ubuntu and then I got that grub dos prompt and looked around in the wubi forums and tried some of the things they suggested to other people with similar problems but it still wouldn't work.

I'd still like to try it without uninstalling xp so i'd guess I'd have to dual boot it.

Can you make a separate partition on the c: drive and install it to that?

Basically I need help with either wubi or dual booting it with an actual installation.

Thanks in advance!

*puts on flameshield just in case because I didn't read the stickies all that well*

---

### Post by Eisenwinter on 2008-11-20
First you'll need to change the boot order in BIOS, make the CDRom boot device be the first boot device.

Enter the Ubuntu CD into the tray, and reboot.

You'll get a menu with several options, you can choose to try out the LiveCD, just to play around with Ubuntu, without actually modifying your hard-disk contents just yet.

Should you choose to install it, just follow the easy installation guide, and when you get to the partition part, choose Manual partitioning, and set up a new partition for Ubuntu.

Make sure to review your partitioning scheme before installation, though - once you choose to start the installation, the changes you will have made to the disk are **final and _cannot_ be reversed**.

If you're unsure, come here and ask for help before modifying the partitioning scheme.

---

### Post by bennachie on 2008-11-20
Did you follow the recommended sequence; that is, boot into Windows, then insert the LiveCD and wait for the dialogue that invites you to embed Ubuntu as a "normal" Windows application, and accept the offer? If you do that, you are never actually aware of "Wubi". The process has worked just fine for me on three machines, now, and I have Ubuntu 8.10 running under XP Home, XP Pro and Vista (as well as running in a dual-boot mode on an older machine).

Your best approach might be to uninstall Ubuntu (just using the normal add/remove function in Windows) and start again. 

Incidentally, I suspect that there would be no harm in cleaning up your Windows installation first, and running the defragmenter - but I expect you do that on a reasonably regular basis anyway.

---

### Post by michaelt196 on 2008-11-20
I was under the assumption that with wubi you didn't even need a live cd.

I also haven't defragmented in god knows how long. You'd think after building the computer I'd take care of it :P

I'll have to defragment it tonight. Recommendations on whether or not I should use the built in defragmentor or a third party one?

---

### Post by handydan918 on 2008-11-20
> **michaelt196 said:**
> I was under the assumption that with wubi you didn't even need a live cd.Right! Of course, you also don't need the system to work....I agree with your assessment of Wubi, I'm afraid. > 

I also haven't defragmented in god knows how long. You'd think after building the computer I'd take care of it :P

I'll have to defragment it tonight. Recommendations on whether or not I should use the built in defragmentor or a third party one?
If you have a good 3rd party defragger, use it. If not, use the built in lame one, but use it at least 4-6 time consecutively. After this, You can insert a Ubu cd, reboot, and add a REAL partition so you can have a REAL Ubu system.


I know, I shouldn't beat around the bush so much. I just really have a hard time saying what I really think.:)

---

### Post by michaelt196 on 2008-11-20
I only have about 80 gigs of space left on my hd, think that will be substantial enough for the partition?

*edit*

you almost mentioned getting REAL ubu with a REAL partition, but what happens if I get things up and running and then dont like it? The other guy said partitions were permanent. I know it really isnt that much of a hassle to have multiple partitions, but still

---

### Post by Paqman on 2008-11-20
> **michaelt196 said:**
> I only have about 80 gigs of space left on my hd, think that will be substantial enough for the partition?

*edit*

you almost mentioned getting REAL ubu with a REAL partition, but what happens if I get things up and running and then dont like it? The other guy said partitions were permanent. I know it really isnt that much of a hassle to have multiple partitions, but still

No partitions aren't permanent. They can be created, destroyed, moved, shrunk and expanded. Removing Ubuntu entirely is as simple as deleting it's partition and then (optionally) restoring the MBR using a Windows disk.

As for 80GB, you could probably install Ubuntu five times in that much space without any trouble at all.

---

### Post by bennachie on 2008-11-20
If you do install "within Windows" (and Wubi works just fine for me, with limited overheads - Ubuntu still seems to run much faster than Windows) you're likely to see the system take over a block of about 15MB, so Paqman's estimate is spot-on. Overall disk space shouldn't be a problem, but extensive fragmentation might be.

---

### Post by michaelt196 on 2008-11-21
Some files were not able to be defragmented and were all over 3 gigabytes in size. Could this mess up my ability to create a partition?

---

### Post by Keen101 on 2008-11-21
> **michaelt196 said:**
> Some files were not able to be defragmented and were all over 3 gigabytes in size. Could this mess up my ability to create a partition?

no, but the main reason to defragment before installing ubuntu, is so there is less risk there will be files near the end of the partition that we are going to shrink. In other words less risk that you will loose some files.

---

### Post by michaelt196 on 2008-11-21
so I burned the ubuntu iso onto a cd and defragged, am I ready for an install? Anything I need to know of in particular while installing it?

---

### Post by jmszr on 2008-11-21
michaelt196,
            If you didn't run winMd5sum during your burn I would suggest using the "Check CD for defects" option before installing. Heck, even if you did run winMd5sum it doesn't take long and can save time in the long run.

---

### Post by michaelt196 on 2008-11-21
I ran both of them and it was fine both times, so I started up the install, got to the screen and when I got to the part where I resize the partition I just to make it 160gb instead of 250gb it started it for a while and then it said it was unable to resize it and then it aborted.

Now I'm running just with the live cd.

What went wrong?

*edit* it also apparently corrupted my itunes library

don't know what else is messed up :-/

---

### Post by Keen101 on 2008-11-21
> **michaelt196 said:**
> What went wrong?

is your system windows vista?

if yes, a lot of people are having trouble with gparted being able to resizing the partition. Try using vista's built in partitioner to shrink the partition.

---

### Post by Bölvaður on 2008-11-21
1. _back u_p your most beloved data (people normally take it for granted that other people know it.. but I want to be good for the ones that dont know that secret)

2. do the partitions in windows (depends on your system, but because of your problems this should be your 1st choice)
If you just want something simple_ make swap partition_ that is equally size as your page file, or _same size as your ram_.
Then _make ext3 partition_ of what ever size you want, this is where the entire os will be kept. But you will see tutorials that suggest more partitions for better longterm use (well and it is safer for hd corruptions)

3. During the installation _use manual partitioning_, auto partitioning is something I do not encourage.



then after that I suggest going System -> Administrator -> Synaptic Package Manager and look for flashplugin-nonefree for watching youtube ^.^

---

### Post by michaelt196 on 2008-11-22
Is there any way I can check to see what was corrupted by the failure to create the partition? Chkdsk?

also how should I make the partition in windows?

afaik the disc management tool does not allow you to resize current partitions

oh, and keen, I have xp



just tried to run guitar pro in xp, got a message telling me to run chkdsk so I did which ended up giving me and error and restarting my computer. On reboot it said a file was corrupted and needed to be replaced :O

The only thing I needed backed up was my music and that's on my ipod so should I just go ahead and format the hard drive and start off with a fresh ubuntu installation?

---

### Post by michaelt196 on 2008-11-22
bump :(

---

### Post by handydan918 on 2008-11-23
> **michaelt196 said:**
> Some files were not able to be defragmented and were all over 3 gigabytes in size. Could this mess up my ability to create a partition?

And if you haven't already pulled the pin and dropped the grenade, hear this:


NEVER! 
Perform any partitioning operation without a VERIFIED backup.

If you do, your blood's on your own hands. [-X

---

