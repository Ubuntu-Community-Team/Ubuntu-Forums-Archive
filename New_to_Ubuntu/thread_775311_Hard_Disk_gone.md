---
title: "Hard Disk gone"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by aimpau on 2008-04-30
Just recently updated to xubuntu 8.04 LTS and I noticed that my other HDD (which has XP) is nowhere to be found. When I was on 7.10, it shows up in my desktop. Now it's gone. Any help? However, I can still boot to XP via grub.

---

### Post by swoll1980 on 2008-04-30
go to /media and see if you see it there it will be called sda1 or sda2 or something simular

---

### Post by wolfen69 on 2008-04-30
look in places>computer

---

### Post by synapse13 on 2008-04-30
I have this same issue.  My secondary hard disk was viewable in Ubuntu 7.10 and Xubuntu 7.10 on my desktop, and with the upgrade to Xubuntu 8.04 I don't see it anymore.  I went to /media, but I didn't see the drive listed there either, just my CDROM, etc.

Any ideas?  I'm at a loss...:confused:

---

### Post by aimpau on 2008-04-30
Done that but still doesn't show.

---

### Post by Mogurijin on 2008-04-30
Boot into Windows and do a clean shut down. If Windows does not shut down properly it will hold a death grip on your drives and Ubuntu won't be able to access them. I hope this solves your problem...

---

### Post by aimpau on 2008-04-30
I'm aware of the safe shutdown protocol of ubuntu. But even then during 7.10, I can see it in my desktop whereas now, i don't see it. I'll give it a shot though.

---

### Post by sujoy on 2008-04-30
are the partitions visible in "computer"?, i mean Places->Computer 

if yes then first check if they are mounted in /media or /mnt, if not then you might need to mount htem manually.

EDIT: oops, guess i am too slow to type eh?

---

### Post by aimpau on 2008-04-30
Don't worry, I'll be online the whole day. :)

[e]
Wow, all posters are online. :)

---

### Post by aimpau on 2008-04-30
Bump.

My BIOS detects both hard disk but when doing

```

fdisk -l

```

the only hard disk that is detected is the hard disk that xubuntu is on.

Am I missing an essential program? Did I forget a step? Need help badly.

---

### Post by DrScottyB on 2008-04-30
> **sujoy said:**
> are the partitions visible in "computer"?, i mean Places->Computer 

if yes then first check if they are mounted in /media or /mnt, if not then you might need to mount htem manually.


I'm having the same issue, not able to access my HDD.  I tried rebooting in Window$ and shutting down fresh, then booting back into Ubuntu...nothing.  I think that it's important to mention that I am using the 8.04 install option to have Ubuntu installed right along with Window$, so I can boot into either...cause I'm too chicken to totally ditch XP yet.

So, I've tried all the suggestions listed in this thread so far... what do you Linux-Wizards think?

***UPDATE***
Ok, I did manage to access my HDD so that I can see all my documents and stuff saved in Window$.  I went to Places->Computer.  That launched the Nautilus file browser.  Then I went to Go->Location and typed /host and BOOM, there's my stuff.  It's not the most stylish way of getting there, but hey, it works.

---

### Post by aimpau on 2008-04-30
Actually, I'm using xubuntu so I don't really know the "place>>my computer" but I know /media.

Anyways, my point is that xubuntu doesn't detect my other HDD which has my Xp on it.

I have a question though:

Does the HDD must be in slave (jumper) mode so that xubuntu can read it? 7.10 detected it plain and simple but now in 8.04, it doesnt. Need help badly.

However, lock ups are no longer occuring to my PC.

Thanks!

---

### Post by aimpau on 2008-05-01
Ok. Just an update:
```

fdisk -l

```
doesn't give anything, but:
```

sudo fdisk -l

```
and yep, it did detect my other HDD. Any advice on the next course of action?

Sorry for my incompetence.

---

### Post by El King on 2008-05-01
> sudo fdisk -l
and post back the result u get

---

### Post by aimpau on 2008-05-01
```

Disk /dev/sda: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01990198

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1744    14008648+  83  Linux
/dev/sda2            1745        1826      658665    5  Extended
/dev/sda5            1745        1826      658633+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb60ab60a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS

```

Sorry if I took so long..Doesn't really bother me that much regarding this problem. It's just it's an 80 GB HDD and I want to learn the workaround regarding linux OS. I'm a noobuntu.

---

### Post by El King on 2008-05-01
Ok let's try this
First make a dir in ur /media so you can mount that partition in it
```
sudo mkdir /windows
```

Bakup ur fstab file
```
sudo cp /etc/fstab /etc/fstab_backup
```

Edit the fstab file
```
gksudo gedit /etc/fstab
```

Add that line to the file
```
/dev/sdb1 /windows ntfs nls=utf8,umask=0222 0 0
```

Save and exit the file
Then auto mount 
```
sudo mount -a
```

Lemme knw if it works

---

### Post by aimpau on 2008-05-01
> **El King said:**
> Ok let's try this
First make a dir in ur /media so you can mount that partition in it
```
sudo mkdir /windows
```

Bakup ur fstab file
```
sudo cp /etc/fstab /etc/fstab_backup
```

Edit the fstab file
**```
sudo mousepad /etc/fstab
```**

Add that line to the file
**```
/dev/sdb1 /media/windows ntfs nls=utf8,umask=0222 0 0
```**

Save and exit the file
Then auto mount 
```
sudo mount -a
```

Lemme knw if it works

BOOM! Wow! Yup! It's solved. Any idea how to change the status of this thread to solved? Thanks so much!

I did some little modification since I'm on xubuntu so that others in xubuntu can see it as well.

Thanks again! I'll be sure to learn how the process works.:lolflag:

---

### Post by El King on 2008-05-01
> **aimpau said:**
> BOOM! Wow! Yup! It's solved. Any idea how to change the status of this thread to solved? Thanks so much!

I did some little modification since I'm on xubuntu so that others in xubuntu can see it as well.

Thanks again! I'll be sure to learn how the process works.:lolflag:

Edit ur first post and then go advanced, and then add [SOLVED] in the title

---

### Post by 2hot6ft2 on 2008-05-09
Thanks El King for the post on how to do this in Xubuntu.

In the process I found that if I use Nautilus to browse to the /media/what_ever_folder I can use the Bookmark feature and it will make the partitions show up under "Places" on the Desktop making them easily available without cluttering the Desktop.

For mine it's Places > Windblow etc...:guitar:

---

### Post by 2hot6ft2 on 2008-05-10
UPDATE
After rebooting the folders were gone and therefore access to the drives in /media but when trying to recreate them it said they already existed.

They weren't hidden I checked that then I found this post here and did it [http://ubuntuforums.org/showpost.php?p=4901742&postcount=1](http://ubuntuforums.org/showpost.php?p=4901742&postcount=1) afterward I found that the folders representing the partitions were up one folder in the base of "File System" so the bookmarks I made earlier no longer worked either.

I removed the bookmarks I had already made and made new ones for where they are now. It's working so far. May be a while before I reboot to see if they stay this time.

---

