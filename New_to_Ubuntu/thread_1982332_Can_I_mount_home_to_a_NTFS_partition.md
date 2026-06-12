---
title: "Can I mount /home to a NTFS partition?"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by jienchi on 2012-05-18
Hi all, am installing Linux (Ubuntu 12.04) for first time ever so please be patient with me! Have gone for dual boot using Live USB as per [these instructions]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")  (shrunk the Windows partition down then installed Ubuntu). I've got  Windows 7 on sad1 and sda2, then sda3 as my NTFS 'Storage' partition.   Then sda5 for Ubuntu and sda6 for swap. 

I want to keep all my pictures, documents etc on Storage so I can access them from Windows or Ubuntu. I've had a look online for guides to do this but it seems a bit confusing - read [here]("https://help.ubuntu.com/community/Partitioning/Home/Moving") that its not a good idea to access NTFS from ext 3. But then [here]("http://www.linuxquestions.org/questions/linux-desktop-74/mounting-an-ntfs-partition-as-home-user-862218/") suggests its OK. I tried to make links as suggested [here]("http://askubuntu.com/questions/77290/how-do-i-mount-the-documents-folder-on-a-different-partition") but that said that the link didnt work as it couldnt find the media/home/documents file.  I'm not very keen to mess around with Ctrl+Alt+T when I dont know exactly what I'm doing.

 At the moment I havent put anything I cant remove easily on the 'Storage' partition.

Any help much appreciated

Jienchi

---

### Post by idoitprone on 2012-05-18
> **jienchi said:**
> Hi all, am installing Linux (Ubuntu 12.04) for first time ever so please be patient with me! Have gone for dual boot using Live USB as per [these instructions]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")  (shrunk the Windows partition down then installed Ubuntu). I've got  Windows 7 on sad1 and sda2, then sda3 as my NTFS 'Storage' partition.   Then sda5 for Ubuntu and sda6 for swap. 

I want to keep all my pictures, documents etc on Storage so I can access them from Windows or Ubuntu. I've had a look online for guides to do this but it seems a bit confusing - read [here]("https://help.ubuntu.com/community/Partitioning/Home/Moving") that its not a good idea to access NTFS from ext 3. But then [here]("http://www.linuxquestions.org/questions/linux-desktop-74/mounting-an-ntfs-partition-as-home-user-862218/") suggests its OK. I tried to make links as suggested [here]("http://askubuntu.com/questions/77290/how-do-i-mount-the-documents-folder-on-a-different-partition") but that said that the link didnt work as it couldnt find the media/home/documents file.  I'm not very keen to mess around with Ctrl+Alt+T when I dont know exactly what I'm doing.

 At the moment I havent put anything I cant remove easily on the 'Storage' partition.

Any help much appreciated

Jienchi

So you want ntfs as a home partition? Impossible because ntfs is not postfix or else you get a piece of crap that is called hfs+

Make all your filesystems ext3 on linux

install this driver for windows
[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

this will let you to freely write and read on both oses

---

### Post by wyliecoyoteuk on 2012-05-18
NTFS does not support the Linux file permission structure, so no, /home can't really live on it.
Either follow the above suggestion, or use a separaate storage partition formatted with FAT32, which both can access, and make a shortcut to it in your /home folder.

---

### Post by oldfred on 2012-05-18
I have used a shared NTFS partition for years with my XP. Even though I now do not boot XP, I still have my Firefox & Thunderbird profiles in the shared partition as I boot multiple systems.

You just need to add the storage partition to fstab.

You need to have a mount point. I would suggest storage, but it can be anything. Also if your mount is in /media or /home you will see it in the left panel of naulitus. I use /mnt as I do not want it in the left panel as I link all the folders in my data partition into /home.

sudo mkdir /mnt/storage

To see your UUID and partitions:
sudo blkid -o list
sudo fdisk -l
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

#any time you edit fstab run this to verify everything is correct. Its ok if it does not give any messages.
sudo mount -a

This is my entry, I also set c: drive to read only so I do not  accidentally do something I should not in Windows, but still read it, you can copy but use your UUIDs:

```
# Entry for /dev/sda1 :
UUID=04B05B70B05B6768 /mnt/cdrive ntfs-3g ro 0 0
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657 /mnt/shared ntfs-3g defaults,uid=1000,nls=utf8,windows_names 0 0

```
If you just want shared as an entry in /home:
# from home so default location will be /home/fred
ln -s /mnt/shared

But if you create a bunch of folders like Music, Documents, Videos you can link all the folders, but have to change or delete the existing folders in /home. Make sure you do not have anything in them first. Folders must exist in shared partition to be able to link to them.

#from home so default location of link is in /home/fred
mv Music oldMusic
# Music is a folder in the partition mounted as /mnt/shared
ln -s /mnt/shared/Music
#Or link all folders with one command:
for i in `echo /mnt/shared/*`;do ln -s $i; done

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by choppyfireballs on 2012-05-18
If you want to save all your pictures I recommend using some of your ubuntu one cloud storage to do so. it's free for you and you get 5 gigs of pictures and anything you want to store. you could use it as a transferring agent if you don't have a flash drive big enough for holding movies etc. you can indeed install this folder in windows.

---

### Post by flemur13013 on 2012-05-18
FWIW, here's what I do:

Leave all the Linux stuff as it should be: / and /home are extX, with /home/user/Documents, etc all left unmodified (not links, not NTFS, etc).  (extX = ext3 or ext4)

Make /home big enough to hold temporary songs, movies, etc.

Make (or use existing) an NTFS partition (DON'T make iit w/linux tools - use windows or the "Partition Wizard" boot CD).   Move your shared files here after dealing with them in linux (e.g. downloaded to the extX filesystem ~/Downloads, then transfer to shared NTFS).  Windows has a bad design by default in that your data files are on the same partition as the OS, unless you (rather laboriously) change it (as you should!)

Mount the NTFS partition like this (/etc/fstab)
```
UUID=funnynumber         /yourmountpoint   ntfs-3g defaults     0 0
```

The only problem I've had is linux writing a file with an illegal filename (containing ":") to the NTFS partition, and that confuses windows.  You'll lose the "delete to trash" function, but I haven't seen any speed or reliability differences by using NTFS for data under linux, rather than extX.   

Even though I rarely boot windows, using an extX partition in common with windows is more hassle than using an NTFS partition.  Windows has better backup software (NOT the MS software!) and you can defrag an NTFS partition, unlike extX partitions (yes, they get fragmented).

---

### Post by oldfred on 2012-05-18
If you use windows_names it avoids the issue of illegal names.

Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
UUID=66E4DC83E4DC56C1 /media/Data ntfs defaults,uid=1000,[COLOR=DarkRed]windows_names[/COLOR],umask=000 0 0

---

### Post by Morbius1 on 2012-05-18
> **flemur13013 said:**
> You'll lose the "delete to trash" function, but I haven't seen any speed or reliability differences by using NTFS for data under linux, rather than extX. 
oldfred's use of uid=1000 should fix the trash problem as well:

UUID=66E4DC83E4DC56C1 /media/Data ntfs defaults,[COLOR=Blue]uid=1000[/COLOR],[COLOR=Black]windows_names[/COLOR],umask=000 0 0

---

### Post by forrestcupp on 2012-05-18
At one time, I made all of my Ubuntu Documents, Music, etc. folders into symlinks pointing to the ones in my Windows partition, after setting that partition to be automatically mounted. It worked out pretty well, and I could hardly tell that they weren't just the normal Ubuntu /home folders.

---

### Post by 29732 on 2012-05-18
> **idoitprone said:**
> So you want ntfs as a home partition? Impossible because ntfs is not postfix or else you get a piece of crap that is called hfs+

Make all your filesystems ext3 on linux

install this driver for windows
[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

this will let you to freely write and read on both oses

The problem is that on Windows XP (as far as I know), when you're trying to mount ext3 partitions, they show up as ext3, and when you mount them, Windows comes in and complains that "The drive is not formatted. Format now?". 
**EDIT, reading the documentation just now, I read that you have to start the ext2fsd service. Not very user-friendly that it doesn't do it automatically. It also looks like it doesn't support ext4 like it says it does.**

I, myself, use ext2read. It works, but doesn't support writing to ext partitions, as ext2fsd doesn't either.

---

### Post by Cheesemill on 2012-05-18
> **29732 said:**
> I, myself, use ext2read. It works, but doesn't support writing to ext partitions, as ext2fsd doesn't either.

Yes it does. I use ext2fsd to read and write my ext4 partitions

---

### Post by jienchi on 2012-07-06
> **oldfred said:**
> If you use windows_names it avoids the issue of illegal names.

Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
UUID=66E4DC83E4DC56C1 /media/Data ntfs defaults,uid=1000,[COLOR=DarkRed]windows_names[/COLOR],umask=000 0 0

Thanks everyone, especially oldfred. I edited fstab as you explained and everything working fine, able to access 'Storage' partition form both Ubuntu and Windows with no problems.

Cheers

Jienchi

---

### Post by oldfred on 2012-07-06
Thanks, but the credit should go to Morbius1. 

My original post was from one of his older posts. I think he understands mounting & fstab where I just try to spread the word on what works. :)

---

