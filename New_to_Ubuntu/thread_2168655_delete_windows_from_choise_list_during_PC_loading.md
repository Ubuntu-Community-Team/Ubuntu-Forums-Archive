---
title: "delete windows from choise list during PC loading"
date: 2013-08-18
forum: New to Ubuntu
---

### Post by Marchello_Lippi on 2013-08-18
Hi all, 

you can congratulate me, I've deleted windows from my pc. Actually I've done this by simple deleting directories "windows", "program files" etc. Now how do I delete windows from choise list during PC loading ?

---

### Post by deadflowr on 2013-08-18
If your completely sure Windows is gone then run
```
sudo update-grub
```

If Windows is listed in the output of that command, then try running 
```
sudo parted -l
```
or 
```
sudo fdisk -l
```
And post the out as so we can help remove the leftover bits of Windows.

Either command should do, but if the partition table is GPT rather than MBR then the parted command is able to read it where the fdisk command won't.

---

### Post by sandyd on 2013-08-18
> **Marchello_Lippi said:**
> Hi all, 

you can congratulate me, I've deleted windows from my pc. Actually I've done this by simple deleting directories "windows", "program files" etc. Now how do I delete windows from choise list during PC loading ?
Try running```
sudo update-grub
```

If youve only deleted the files on the drive, it may still show up on the grub menulist because Ubuntu does not detect that youve deleted a few folders off the drive.

If you still need the files on the drive, you can disable the detection of all OSes other than linux on the drive (if you are not going to run Windows on the machine again) by running the below.
```

sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub

```

You can re-enable windows detection by running
```
sudo chmod +x /etc/grub.d/30_os-prober
sudo update-grub
```

If you dont need the files on the drive, post the output of
```

sudo fdisk -l
sudo parted -l
```, which will allow us to help you to remove the windows partition.

---

### Post by Marchello_Lippi on 2013-08-19
user@ubuntu:~$ sudo update-grub
[sudo] password for user: 
Creating grub.cfg...
Found image linux: /boot/vmlinuz-3.5.0-37-generic
Found image initrd: /boot/initrd.img-3.5.0-37-generic
Found image linux: /boot/vmlinuz-3.5.0-36-generic
Found image initrd: /boot/initrd.img-3.5.0-36-generic
Found Windows 8 (loader) at /dev/sda1
Skipping Windows 8 (loader) on Wubi system
done

user@ubuntu:~$ sudo parted -l
Model: ATA OCZ-VERTEX3 (scsi)
Disk /dev/sda: 60,0GB
Size of sector (logical/physical): 512&#1041;/512&#1041;
table of sections: msdos

Number  Begin  End  Size  Type      File system      Notes
 1     1049kB   368MB   367MB   primary  ntfs             boot
 2     368MB    60,0GB  59,7GB  primary  ntfs


user@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60,0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Input/output size (min/optimal): 512 bytes / 512 bytes
Disk identificator: 0xc96e98df

Device Boot  Begin     End     Blocks  Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   117227519    58254336    7  HPFS/NTFS/exFAT


BTW, the Windows Boot Manager is still displayed while reboot (with Windows 8 string).

---

### Post by Cheesemill on 2013-08-19
Was this a Wubi installation?

If so then it's a very bad idea to remove Windows from the machine, if there are ever any problems on the NTFS partition which holds your Wubi installation  these can usually only be fixed from Windows. Also Wubi was never intended to be used as a long term solution, it's just meant for testing Ubuntu before deciding to do a proper installation.

I would highly recommend backing up all your data and then doing a proper installation of Ubuntu if it is going to be the only OS on the machine.

---

### Post by deadflowr on 2013-08-19
It would seem you are running WUBI.

Fully removing Windows will also delete Ubuntu, in this case.
WUBI installs Ubuntu inside a file inside Windows.

Your options would be to do a full fresh install of Ubuntu and overwrite the existing disk.
To do this you'll did to download and burn/put on disk/usb.
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
Read the installation instructions

Another option is migration, which I myself have never tried, and thus, have no knowledge on its success rate.
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

Preferably, though, a fresh install is the best option.

Edit: Cheesemill's advice on backing up what you want is sound.

---

### Post by Marchello_Lippi on 2013-08-19
Cheesemill, deadflowr, 
yes, it is wubi. I agree to perform fresh install. Backup is easy, I've got external drive with enough space. The boring moment is to return to the same list of packages, including proprietary programs and drivers... Could someone please advise me some easy way to save my software list? Thanks.

---

### Post by Cheesemill on 2013-08-19
You can create a list of installed packages by doing...
```
dpkg --get-selections > packagelist
```

Backup this file and then when you have reinstalled you can run the following to re-install the packages...
```
sudo dpkg --set-selections < packagelist
sudo apt-get -f install
```

You can do all of this with Synaptic if you prefer a GUI but I can't tell you the exact procedure as I'm not on a Ubuntu box at the minute.

---

### Post by Marchello_Lippi on 2013-08-21
I've got ssd drive, 60 GB. I need no other OS but Ubuntu. How is it better to map drive after formatting, what sizes of partitions should be?

---

### Post by lego11 on 2013-08-21
Hi,
It depends on your needs. I recommend for beginners to have a single partition with root ( / ) mountpoint and the swap partition as big as the RAM until 6GB, then the half of the total RAM. (ie 12GB RAM -> 6GB swap..)
If you are experienced with partitioning you may want to go with the separate /home partition, but on your little SSD it makes little sense since you are probably going to overflow either the root ( / ) partition or the /home partition. So I'd recommend the first method. Make a root ( / ) partition as big as your drive minus the swap and then make the swap partition. For the filesystem I'd stick with ext4 since I don't know ReiserFS or btrfs too much. Maybe somebody can suggest other FSes.
Let me know... :-)

---

### Post by Marchello_Lippi on 2013-08-21
> **lego11 said:**
> Hi,
I recommend for beginners to have a single partition with root ( / ) mountpoint and the swap partition as big as the RAM until 6GB, then the half of the total RAM. (ie 12GB RAM -> 6GB swap..)
...
For the filesystem I'd stick with ext4 

So it will be single partition with root mountpoint (~57GB) and the swap partition (3GB), ext4 filesystem. 
How should I map it since I don't have other hdd/ssd drives but only this one? 
Sure I've got boot flash drive and cd with Ubuntu. 
I mean, what should I do after I boot from ubuntu flash/cd ? 
Is it possible to map my ssd drive after I boot from ubuntu flash/cd ? 
What is the appropriate console command line? 
Please help me.

---

### Post by Cheesemill on 2013-08-21
If you just want Ubuntu on your drive then it's easy, just boot from the Ubuntu DVD/USB and when you get to the partitioning stage select 'Guided - Use entire disk'. The installer will take care of everything for you.

---

