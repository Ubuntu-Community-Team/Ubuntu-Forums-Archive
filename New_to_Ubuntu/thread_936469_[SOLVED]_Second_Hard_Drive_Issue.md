---
title: "[SOLVED] Second Hard Drive Issue"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by metalnate on 2008-10-02
Hi,
  I just installed Ubuntu 8.04 and I have two hard drives in my computer.  One is 120g and the other is only 6g.  The six gig HD I had an old install of Ubuntu on it, I am using Gparted and I formated the HD into ext3 and when I go to Places>Computer the HD is not there anymore, I just want to use it for extra storage.  I'm also having an issue resizing my Ubuntu partition.  I am deleting Windows altogether and am going to be all Linux from now on (yay) but I have some large files in my XP partion that I need before I can delete the partition, but my Ubuntu only has 20gigs and the folder is 28 gigs.  Gparted won't allow me to resize the windows partition.  All I wanna do is get my media and delete windows forever.  Also Even though I deleted my old Ubuntu partition on the 6gig HD, it still shows up in the grub loader.  How can I save my files and give Ubuntu all of the HD's?  thanks. 
                      Nate

---

### Post by drs305 on 2008-10-02
Is Windows using all but 20GB of the first drive? If so, you could run defrag on it and then create a separate partition via windows or something like partitoin magic at the end of it to temporarily save your data files. The cd versions of gparted or the livecd will work on ntfs partitions although I think to get the synaptic version to work on ntfs partitions you need to install ntfsprogs.

Your 6GB drive may not be seen any longer depending on how it was listed in fstab. Were you using a UUID to identify it? The reformatting probably changed the UUID and would need to be replaced in fstab. If you need help getting it back in fstab, provide the following and the mountpoint you would like for it:
```

sudo blkid
sudo fdisk -l
cat /etc/fstab

```

---

### Post by houbysoft.xf.cz on 2008-10-02
Hi, if GRUB doesn't allow you to resize your windows partition (which is strange, I tried it and it worked for me), I think the easiest thing to do is to keep it, and only delete Windows' system folders (essentially /WINDOWS, /Documents and Settings), and keep the files you need. Ubuntu still can read fat32 or ntfs partitions without problems, so I think you don't really have to move to ext3 immediately.

For solving the problem of your 6g hd not showing up, please post the output of the command
```

fdisk -l

```.

For solving the GRUB issue, you just need to edit a file /boot/grub/menu.lst, which you can do so by this (you MUST have root privilegies)
```

sudo gedit /boot/grub/menu.lst

```. After running this command, an editor window will appear. Just find there the entries that correspond to your old ubuntu, and delete them. If you feel confused, feel free to post here the contents of this file, and I will show you what to delete.

Hope that this helped.

[EDIT]I was too late :)[/EDIT]

---

### Post by metalnate on 2008-10-02
Yes, Windows has all but 20 gigs.  I ran the code you posted in terminal, but it still doesnt show, I must tell you im a total noob at Linux my friend, maybe I'm not setting the mountpoint right?  with sudo fdisk -l it reads the drive, how may I set the mount point?  Thank you for the quick response.

---

### Post by metalnate on 2008-10-02
Sudo fdisk -l:> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11874    95377873+   7  HPFS/NTFS
/dev/sda2           11875       14593    21840367+   5  Extended
/dev/sda5           11875       14474    20884468+  83  Linux
/dev/sda6           14475       14593      955836   82  Linux swap / Solaris

Disk /dev/sdb: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde4209ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         784     6297448+  83  Linux
nathan@nathan-desktop:~$ 


---

### Post by metalnate on 2008-10-02
sudo gedit /boot/grub/menu.lst brings up a blank screen.  I am so confused guys, the commands are very unfamilar to me.  I'm sorry to be bothersome.  THanks for the quick replies

---

### Post by drs305 on 2008-10-02
We were all new once. No problem there! If you have questions, it means we weren't clear enough. Ask away.

Here's how to get your 6GB drive to mount at boot by adding it to fstab:

Make the mountpoint. This is where you want to see the partiton. Usually it's in the /media folder, so I will use a mountpoint called ***sdb1***. Change it to whatever you want, but replace ***sdb1*** with whatever you decide to use. For example, if you want it to be "data", you would make the following command read "sudo mkdir /media/data" and also replace any of the bold ***sdb1*** entries with "data" (but not the very last one which is not in bold).:
```
sudo mkdir /media/sdb1
```

Change ownership of mountpoint to yourself and set permissions. Replace *username* with your logon name:
```
sudo chown -R *username:* /media/***sdb1***
chmod -R 750 /media/***sdb1***

```

Backup fstab and open for editing (example uses gedit but you can use any text editor):
```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```

Add this line:
```

/dev/sdb1 /media/***sdb1*** ext3 defaults,users 0 2 

```
Save the file and close gedit.

Mount the new partition:
```

sudo mount /dev/sdb1

```

You should be able to see the drive...

---

### Post by metalnate on 2008-10-02
Thank you drs305 I can now see the drive!  I have no idea what I was doing but it worked.  The commands are so foreign to me in linux right now, but I'm confident in my skill enough to convert totally to Ubuntu, it's the most stable system I've ever used. I'm unable to edit my GRUB menu, that command brings up a blank window.  I think I'm going to boot into windows and just d/l the folder I need to my other pc over the network then d/l it into linux.  If i can do that, I installed Samba but I cannot see my other pc in network places.  Thank you so much for you help.

---

### Post by houbysoft.xf.cz on 2008-10-02
If menu.lst is blank, try opening something like
/boot/grub/grub.conf or simply post what do you have in the /boot/grub directory.

---

### Post by drs305 on 2008-10-02
Glad you can now see your drive. Just an afterthought on houbysoft.xf.cz's post. When you try to edit menu.lst are you using a small L for .lst ? Sometimes it's mistaken for the digit 1.

Not saying you are ready to do so yet, but when you make a post and have all your questions answered it is helpful if you mark the thread 'Solved'. You do this with the link near the top right of the first post, using the ' Thread Tools' link.

Welcome to the Ubuntu Forums. I think you will find the people here very willing to help you through any problems you may have.

---

