---
title: "How to reformat my partition"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by wariskampar on 2008-05-19
Hello, I would like to reformat my NTFS partition to ext3 because a lot of people said ext3 more stable and secure than NTFS. Below is my current hard disk structure
Local Disk (C)  NTFS Primary       ~15GB
(*)             Extended Primary
New Volume (E)  NTFS Logical       ~30GB
Local Disk (F)  NTFS Logical       ~15GB
Local Disk (*.) Linux Ext3 Logical ~15GB 
SWAPSPACE2 (*.) Linux Swap Logical ~200kb

I plan to convert drive F: and about 20GB from drive E: to ext3 format. Apart from that, is it possible if I change Linux Ext3 from Logical to Primary.

---

### Post by wolfen69 on 2008-05-19
try [GPartedLiveCD]("http://gparted.sourceforge.net/livecd.php")

---

### Post by om1 on 2008-05-19
if you have an install of ubuntu you can install gparted from add/remove

gparted is also on the ubuntu live cd under System Administration Partition Editor

---

### Post by wariskampar on 2008-05-19
Hello, I had install GParted with Synaptic..But all my drive are locked so all the menu is unaccessible. What should I do

---

### Post by Gone fishing on 2008-05-19
Just a word of caution, NTFS is a Windows format ext3 is a Linux format so Windows will not be able to use it unless you install Ext2 IFS [http://www.fs-driver.org/](http://www.fs-driver.org/) (which works very well) Obviously you will need to back up your files before you start changing your partitions formats etc

---

### Post by om1 on 2008-05-19
the drives have to be unmounted before you can change them with gparted... just right click on it and choose unmount

---

### Post by Gone fishing on 2008-05-19
Boot from the Ubuntu boot disk or download the stand alone version of gparted

---

### Post by wariskampar on 2008-05-19
Now I successfully reformat my NTFS partition to ext3(I dont mind about XP can not recognize ext3. will think about that later:)). Here is my new structure
/dev/sda1   ntfs        14.42GB    Primary
/dev/sda2   extended
 /dev/sda5  ext3        9.82GB     Logical
 /dev/sda6  ext3        35.31GB    Logical
 /dev/sda7  ext3        14.30GB    Logical
 /dev/sda8  Linux-Swap  690.29MB   Logical

However, I still got few question need to clarify
1) After re-format, I find lost+found folder in each partition(sda5 and sda6). When I try to open it, I got "No Permission" message. What is this and how to delete because I already back up all my data to external drive before re-format  
2) How to name each partition obvious name (C:, E: etc) rather than 10.5GB Media, 37GB Media.
3) Since sda1 is my XP partition, how to secure it (encrypt etc) so that I will not accidentally damaging its content?

---

### Post by JC Cheloven on 2008-05-19
Hi, first of all, why have you so little swap space? It should be as much as your ram (or twice for hibernation). Anyway:

- I wouldn't care about lost+found if you did a backup of your data.

- On startup, partitions are mounted as stated by /etc/fstab. To give them a different name, you have to substitute in fstab (example) /media/sda5  to media/mydata, thus sda5 becomes mydata. You have also to create a new directory /media/mydata. That's it.

Caution: the partition where the active SO resides has to be /, no other name.
Hint: if you see UUID's in fstab instead of (example) /media/sda5, you can run sudo blkid to identify the volumes. The UUIDs from blkid should match those in fstab.

Greetings

---

### Post by wariskampar on 2008-05-20
Hello, this is fstab:

1) How do I delete lost+found to recover some space. I always get "Permission Denied" warning
2) How do I enlarge SWAP Space. I plan to take aditional space from /dev/sda7(Linux Partition) but unable to unmount it
3) Could you give more detail about substitute other name in fstab and to create directory. I really dont understand. Btw here is my fstab

aznan@aznan-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=a3972a39-4b18-43b1-9848-f5788689ccbf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=177befd4-be3f-4cb6-bc23-0357a348b971 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
 
(why it only shows 2 partition. where are the other?)

---

### Post by forestpixie on 2008-05-20
Lost+Found is where the disc check puts files that have a problem - you can use nautilus as root to see what's in there, if you delete them they return afaik.

```
gksudo nautilus
```

Resize swap - use the [[COLOR="Blue"]gparted[/COLOR]]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779") or [[COLOR="#0000ff"]partedmagic[/COLOR]]("http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads") livecd's - burn whichever one you want as an iso and then you can boot with it - no drives will be mounted and you can do as you wish.

Fstab tells the system where to mount a partition - are you trying to get the 2 other ext3 partitions to mount, but not the ntfs one?

Edit - reread - I see you want to mount the 2 ext3 partitions - this should do that for you, change 'nameofdisc1' to what you want to call it in both places, same for nameofdic2

```
sudo mkdir /media/[COLOR="Red"]nameofdisc1[/COLOR]
sudo mkdir /media/[COLOR="Blue"]nameofdisc2[/COLOR]
```

backup fstab
```
sudo cp /etc/fstab /etc/fstab.2005
```

edit fstab

```
gksudo gedit /etc/fstab
```

> #/dev/nameofdisc1
/dev/sda5 /media/[COLOR="Red"]nameofdisc1[/COLOR]     ext3    defaults        0       2
#/dev/nameofdisc2
/dev/sda6 /media/[COLOR="#0000ff"]nameofdisc2[/COLOR]     ext3    defaults        0       2

save file and close

```
sudo mount -a
```

and they should now be mounted and do so on reboot

---

### Post by wariskampar on 2008-05-20
1) I manage to Resize my SWAP partition to 1.29GB with GParted Live CD. Thanks everybody! 


2) This is what I get;

aznan@aznan-laptop:~$ gksudo nautilus 
Initializing nautilus-share extension

** (nautilus:6948): WARNING **: Unable to add monitor: Not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

seahorse nautilus module shutdown

Btw, now I can view lost+found folder and it is empty. Can I just delete the folder altogether.

3) "I see you want to mount the 2 ext3 partitions". They are already mounted (mount mean I can access the partition in nautilus right?). I just want to rename the partition so that can easily recognize it in Desktop (please see attachment)

---

### Post by forestpixie on 2008-05-20
Can't help with the nautilus error.

Re - mounting partitions - I see that they are mounted - how did you get them to mount, they are not in fstab at present?

Can you do this from a terminal

```
ls /media
```

---

### Post by wariskampar on 2008-05-20
aznan@aznan-laptop:~$ ls /media 
cdrom  cdrom0  disk  disk-1  disk-2
aznan@aznan-laptop:~$ 

Do you see any problem with my sys

---

### Post by forestpixie on 2008-05-20
Not sure how they are getting mounted in the first place, but assuming that they are mounted when you boot then to cahnge name you can use tune2fs

```
sudo e2label /dev/sda5 newlabel
sudo e2label /dev/sda6 newlabel
```

change newlabel to suit

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

But if the partitions do not mount when you reboot you're installation then use information I gave earlier

---

### Post by wariskampar on 2008-05-20
Actually when I first login, I dont see any the partition on Desktop. Only if I click them in Nautilus, did they appear on Desktop. Does it mean, they are automatically mount during startup.

---

### Post by om1 on 2008-05-20
that means they are not mounted when you boot your system... thats why they are called disk disk-1 disk-2... there is a problem with your fstab... post a copy of what your fstab looks like

---

### Post by forestpixie on 2008-05-20
That's what I've been trying to get to the bottom of :)

That is what post 11 is all about, you need to do that to get them mounted at login.

---

### Post by wariskampar on 2008-05-20
i follow your instruction on post 11 but get stuck at edit fstab. 
may i know what the different between code and quote

---

### Post by forestpixie on 2008-05-20
code is a command you need to run from terminal - probably best to copy and paste until you know what the commands actually are, the quote is what you need to add to the fstab file to get your 2 partitions to mount - add those lines to the end of the existing fstab

Be very careful where you change the nameofdisc stuff - it has to be exactly the same for each partition in both the mkdir commands and in fstab.

Sorry was trying very hard to revise this morning - kept finding other things to do that interested me more :D

If there is anything you need to know - don't hesitate to ask

If you run the sudo mount -a command at the end and get an error please post the exact message you get from terminal

When you've done if you want to go over the commands you've run I  am more than happy to do so with you

---

### Post by wariskampar on 2008-05-20
Hello, This is my /etc/fstab:

aznan@aznan-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=a3972a39-4b18-43b1-9848-f5788689ccbf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=177befd4-be3f-4cb6-bc23-0357a348b971 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

OK, now in my media folder i got 2 additional folder(sda5 and sda6) which i create using
sudo mkdir /media/nameofdisc1
sudo mkdir /media/nameofdisc2

but i i type gksudo /etc/fstab in terminal, no file appear(i assume it will so that i can add the quote). what maybe wrong

---

### Post by forestpixie on 2008-05-20
D'oh so sorry 

```
gksudo gedit /etc/fstab
```

Wher I've put nameofdisc1 and nameofdisc2 - you have I assumed changed them to what you want to call them both

---

### Post by wariskampar on 2008-05-20
ok!:) now my sda5 and sda6 automount during startup. Thank you vey much:):)
But, instead of sda 5 and sda6, both partitions are named 10.5GB Media and 36.5GB Media respectively. How to change them to SDA5 and SDA6

---

### Post by forestpixie on 2008-05-20
You're welcome - to rename the partitions - 

```
sudo e2label /dev/sda5 newlabel
```

```
sudo e2label /dev/sda6 newlabel
```

and reboot

---

### Post by JC Cheloven on 2008-05-25
Sorry for the interference, and sorry for my delay in answering. I've been outside a couple of days. 

I'm worried about your swap, because after resizing it, its UUID has probably changed. In this case, it's likely that the system won't use it (so you'll have no swap at all when needed). Please type this on a terminal: ```
top
```
You should see on the 5th line something like this:
> Swap  1229744k total, 0k used ...(& some more things)
The actual amount of total swap will not be exactly that, but should be about 1.2Gb (matching the size of the swap partition you made). If it reads '0k total', your swap is being ignored. If so, you need to type in a terminal ```
blkid
``` to find out the actual UUID of your swap partition. Then edit etc/fstab as superuser (gksudo gedit etc/fstab, as forestpixie explained you), and change the UUID of the swap partition to match the one given by blkid (copy and paste is the best way).

As to the rest, forestpixie already made all the work :-) Only note that the particular partition of the OS you're currently running will always appear in nautilus as 'file system', despite whatever you have specified using the e2label (or tune2fs) command.
Greetings

---

