---
title: "Problems mounting drives during boot sequence"
date: 2013-12-26
forum: New to Ubuntu
---

### Post by obsidian razor on 2013-12-26
Hi!

I'm a somewhat newbie trying to install ubuntu on my old computer (which is mostly used by my mum, so I really need to make sure everything is working smooth as silk in a couple of days, at least for casual user day to day things).

I've installed Cinnamon and, for the most part, everything is working fine and dandy.

However, I have 4 hard drives:

- My main hard drive where Ubuntu is.
- A secondary Ext4 500 GB drive where most of the big stuff (videos and whatnot) will go.
- 2 NTFS drives with all stuff from my windows days that I really don't want to get rid off and I don't have any external drives big enough to put in.

When I boot the system, I usually get one or more messages (the number is really random) telling me that the system has failed to Mount Drive X (X being a weird assortment of characters and numbers) and that I can skip or do it manually.

I've been skipping it, and found out that one or more of my hard drives (again, random) seem to remain unmounted, but opening them in Nautilus mounts them just fine.

Strangely enough, my secondary drive (the one that's Ext4) is the one giving me the most trouble, getting to the point where a couple of times it has refused to mount.

I really have no idea where to even begin here...

Do please tell me where I can find information or logs that might help you guys.

Many thanks in advance!

---

### Post by yoreei.grigorov on 2013-12-26
Seems like there is something messed up with your fstab file. In terminal type:
```
sudo leafpad /etc/fstab
```

This file says which partitions will be mounted and how.
Assuming your HDDs are:
sda (Your main drive)
sdb (Your secondary drive)
sdc
sdd Your NTFS
your fstab should look like this:

UUID=0e3927fd-0878-4a0d-bc38-e69c76e2cee6 /               ext4 defaults 0       1

UUID=997bafe4-ecc9-4208-9cab-4d206031b8d8 /home           ext4    defaults        0       2

where on UUID you should write the IDs of your partitions(I copy-pasted mine here). These are the numbers you called 'random'. You can see what the UUID of each of your partitions is by typing

```
sudo blkid
```
in terminal.
If you wish to mount the ntfs partitions too, I think you can figure out how to do it by looking at how it is done for the ext4 drives.

NOTE: I also assumed that you use your second drive for /home (you mentioned that there is music, movies and such there). If it is not so, delete where it is writen /home and add none.
I tried to explain it as simple as I can. If you couldn't get it from my explanation, there are many tutorials on the internet on the fstab file.

---

### Post by obsidian razor on 2013-12-26
Since I'm not sure what I'm changing, I though it might be a good idea to post this here:
> 
UUID=18098f1b-09ce-49d5-b7b2-c7512ea83f57 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=95d6cdb2-2573-46e8-a9eb-7b5b45b9b35d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/disk/by-uuid/e8982b22-1ef3-436b-b4fc-a64255b3f582 /mnt/e8982b22-1ef3-436b-b4fc-a64255b3f582 auto nosuid,nodev,nofail,x-gvfs-show 0 0


I installed leafpad and extracted that from my file, does it look right? What do I need to change exactly? The UUID so it matches the one given by blkid?

Thanks!

---

### Post by obsidian razor on 2013-12-26
This is what I get with blkid:
> 
/dev/sda1: UUID="18098f1b-09ce-49d5-b7b2-c7512ea83f57" TYPE="ext4" 
/dev/sda5: UUID="95d6cdb2-2573-46e8-a9eb-7b5b45b9b35d" TYPE="swap" 
/dev/sdc1: LABEL="Simple - 2010" UUID="60660F57660F2D7A" TYPE="ntfs" 
/dev/sdb1: LABEL="Simple-2009" UUID="ea1ab8de-8d35-4f69-934c-7c50e42ebf83" TYPE="ext4" 
/dev/sdd1: LABEL="Simple-2004" UUID="162B153A416FF7ED" TYPE="ntfs" 


---

### Post by deadflowr on 2013-12-26
First change the last entry to UUID=And-put-the-long-uuid-number-here.
Second, Do you have a folder in the /mnt directory with that name?
If not, make one, or better yet, make one with an easier name.
```
sudo mkdir /mnt/foldername-you-like
```

Thirdly, after the mountpoint(/mnt/#####), you need a file system type, in the case I think it's EXT4.

I'm sure there are other things that need to be done, but that's the basics I got from a simple look.
From this
```
[COLOR=#000000]*/dev/disk/by-uuid/e8982b22-1ef3-436b-b4fc-a64255b3f582 /mnt/e8982b22-1ef3-436b-b4fc-a64255b3f582 auto nosuid,nodev,nofail,x-gvfs-show 0 0*[/COLOR]
```
to this
```
**UUID=**[COLOR=#000000]*e8982b22-1ef3-436b-b4fc-a64255b3f582 /mnt/**some-folder-name-here** **ext4** auto nosuid,nodev,nofail,x-gvfs-show 0 0*[/COLOR]
```
Something like that.

---

### Post by obsidian razor on 2013-12-27
Thank you! :)

I've had partial success, but the critical part is covered.

Seeing your suggestion made me have a light bulb moment, there was no e8982b22-1ef3-436b-b4fc-a64255b3f582 drive anywhere in my system and it didn't match anything under blkid, so I took it out and cleaned the fstab a bit.
Then I fiddled with the options for my secondary drive, which was the most important one, and managed to auto-mount it on boot 3 times in a row, so I'd call success :)

My fstab looks like this now:

> UUID=18098f1b-09ce-49d5-b7b2-c7512ea83f57               /                                          ext4  errors=remount-ro                0  1  
UUID=95d6cdb2-2573-46e8-a9eb-7b5b45b9b35d               none                                       swap  sw                               0  0  
/dev/fd0                                                /media/floppy0                             auto  rw,user,noauto,exec,utf8         0  0  
/dev/sdb1 /media/casa/Simple-2009 ext4 rw,nosuid,nodev,uhelper=udisks2 0 0

Now I'm having problems automounting my NFTS drives, which is not such a big deal, but still, I'd like them automounted if possible.

Several attempts have failed, and actually blocked me from them a couple of times (had to delete them  from fstab, reboot, and mount them the old fashion way). Now with fstab as it is I can log in and mount them with nautilus, which is ok I guess.

My blkid reads as such:

> /dev/sda1: UUID="18098f1b-09ce-49d5-b7b2-c7512ea83f57" TYPE="ext4" 
/dev/sda5: UUID="95d6cdb2-2573-46e8-a9eb-7b5b45b9b35d" TYPE="swap" 
/dev/sdc1: LABEL="Simple - 2010" UUID="60660F57660F2D7A" TYPE="ntfs" 
/dev/sdb1: LABEL="Simple-2009" UUID="ea1ab8de-8d35-4f69-934c-7c50e42ebf83" TYPE="ext4" 
/dev/sdd1: LABEL="Simple-2004" UUID="162B153A416FF7ED" TYPE="ntfs" 

Could I just copy paste the info here into fstab so it automounts them?

I'm a bit afraid about fiddling more than necessary.

Thanks!

---

### Post by Bucky Ball on 2013-12-27
The easy way for NTFS mounting is by using ntfs-3g and ntfs-config, both available in the repos. Install them and run ntfs-config. Once you've selected which drives you want mounted at boot ntfs-config will add those entries to the /fstab for you. Reboot and check it worked. ;)

PS: If you're a bit nervous about tweaking the fstab, make a backup of a working version like so:
```

sudo cp /etc/fstab /etc/fstab.backup
```

That will make a copy of the original, working fstab. Tweak away. If anything breaks, simply copy the original back with:
```

sudo cp /etc/fstab.backup /etc/fstab
```

... and start again. Good to get into the habit of making a backup copy of any file you're tweaking before tweaking.

---

### Post by obsidian razor on 2013-12-27
That worked! 

Thank you! :D

3 boots with all drives automounted and working fine! :D

---

### Post by Impavidus on 2013-12-27
I think there's a slight risk in using ntfs drives on a computer with no Windows installed. Linux has no problem reading or writing to ntfs drives, but it has some more difficulty fixing them, which may be necessary after an ungraceful shutdown. If you only have Linux on that computer, it may be better for the long term to use only native Linux file systems.

---

### Post by obsidian razor on 2013-12-27
Agreed.

Problem is right now I don't have any media where I can make copies of everything and then format those drives.

I'll do it eventually next time I drop by my parents place :)

---

