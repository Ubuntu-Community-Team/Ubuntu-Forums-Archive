---
title: "Next steps"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by eberndl on 2008-04-26
Hey everyone, so I'm making the step to a dual boot, and I just want to make sure that I'm not missing any steps in my plan.

I want a dual boot machine (XP and Heron), where I can use my music, movies and personal documents from either OS.

I've already backed up my Windows settings, and I have my music, movies, and personal documents saved to DVDs.

So, next steps look to be:
Defrag Windows
Run chkdsk /r on windows
Run Hardy Live CD
Partition my disk
    35G XP (NTFS, primary) 
    10G / for Ubuntu (Ext3, primary)
    10G /home (Ext3, logical)
    4G swap (logical)
    rest Shared (Fat32)
Install Heron
Check Windows
Check Ubuntu

Am I missing anything major??

Thanks SOOO much!

---

### Post by scragar on 2008-04-26
you don't need anything more than 1GB of ram total for the most part, and swap acts as ram for when your real ram runs out, so I think a 4GB partition is just a little larger than required.

You can partition your drive using the installer, simply pick manual when it asks about partitioning.

defrag should be run twice, and depending on how long it took, a third time, just to make sure it's all been moved correctly.

---

### Post by Joeb454 on 2008-04-26
If you follow the advise above, as well as what you have already done - you should be fine :)

---

### Post by eberndl on 2008-04-26
Ok, I'm defragging for the 2nd time right now, and I'd originally thought 1G for swap (that's what seems to be recommended here), but my father strongly recommended that I go for twice my RAM... which does seem like overkill to me.

Thanks scragar!

---

### Post by axor1337 on 2008-04-26
the swap file size can be up for debate i use twice my ram size  3gb  for me  my only change would be to use ntfs for my shared data partition instead of fat 32   ubuntu has a ntfc config tool. that allows read and write to ntfs  and work better than fat 32 in my experiance. just make sure you boot partitions are lager enough  i recoment at least 40gb for xp and 20gb for hardy,  i have 50 and 50 with 2 shared ntfs parts  works great    the reason why many of us use double our ram for swap  is because back when memory was more expensive and 64 meg or 128 meg was lots of ram  it made sense to use hard disk for additional memory.  i still put my swap file on a different disk than my os ( i am usinf an old 20 gb disk) foa a little extra speed .

---

### Post by scragar on 2008-04-26
> **axor1337 said:**
> the swap file size can be up for debate i use twice my ram size  3gb  for me  my only change would be to use ntfs for my shared data partition instead of fat 32   ubuntu has a ntfc config tool. that allows read and write to ntfs  and work better than fat 32 in my experiance. just make sure you boot partitions are lager enough  i recoment at least 40gb for xp and 20gb for hardy,  i have 50 and 50 with 2 shared ntfs parts  works great

w0w, 20 GB for ubuntu? I've got a 7GB partition and 35% of it's empty :P having said that I've got a 3GB swap(which is only to make the next number nice and round, honestly I've never used more than about 2% of it) with 30Gb for windows XP(which is using about 1 third of it, I've only got games on it, and it's 2 days old...).

---

### Post by eberndl on 2008-04-27
Ok, so after borking up windows and re-installing it, I'm at the point where I'm making my shared drive... I know it's FAT32, but I really want to confirm that the mount point is /windows...

I really don't want to have to re-install everything again.

Thanks in advance!!

---

### Post by Xiong Chiamiov on 2008-04-27
You can mount it wherever you want, just make sure to create the folder first.  If you'd prefer to call it /snarglybook, that's just fine.  Just don't choose /etc or /boot or something.

---

### Post by eberndl on 2008-04-27
Thanks Xiong!  But... stupid n00b question... how do I do that?

---

### Post by hyper_ch on 2008-04-27
you don't need a fat32 partition anymore... with ntfs-3g you can easily read/write to ntfs...

---

### Post by scragar on 2008-04-27
urg, but ntfs is terrible, far better to teach windows to use ext, even if windows cannot do it very well(ext2 has many advantages over ntfs, including a working permtitions system, a lack of defraging requirements etc). Having said this, it is an opinion, lot's of people disagree with me over it(if M$ could improve ntfs to even ext2 standards(completely ignoring that ext3 is even better than that) I would change my mind, but that doesn't look likly...)

---

### Post by hyper_ch on 2008-04-27
well, I wouldn't not trust Windows to access ext2/3 drives...

---

### Post by eberndl on 2008-04-27
Ok, this is a lovely philosophical debate, and I'm sure that you both have valid points... but how do I make a mount point? Please?

---

### Post by scragar on 2008-04-27
```
mkdir /media/share
```
would make a directory called share in /media, you can then mount to it:
```
mount /dev/hda**N** /media/share
```
where N is the partition number check via: ```
cat /proc/partitions
```

---

### Post by eberndl on 2008-04-27
And I should be able to do this even within a live session?

No, apparently I can't (just tried)...

ubuntu@ubuntu:~$ mkdir /media/share
mkdir: cannot create directory `/media/share': Permission denied

should I mount it in /windows and then change it once Heron's installed?

---

### Post by scragar on 2008-04-27
sorry, you need sudo perms:
```
sudo mkdir /media/share
```
same goes for mounting the drive. just put sudo infront of the line I gave

---

### Post by eberndl on 2008-04-27
So this is the error I got when I tried to install:

The attempt to mount a file system with type vfat in SCSI1 (0,0,0), partition #6 (sda) at /share failed.

You may resume partitioning from the partitioning menu.

Should I just leave it unmounted until after I finish the install?

---

