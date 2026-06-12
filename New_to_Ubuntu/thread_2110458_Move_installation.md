---
title: "Move installation"
date: 2013-01-30
forum: New to Ubuntu
---

### Post by dlw on 2013-01-30
Ubuntu 12.10 currently on 80gb hd.
Would like to move to 1tb hd.

Can this be done?
If so, how?

TIA
dlw

---

### Post by ibjsb4 on 2013-01-30
[clonezilla]("http://clonezilla.org/")

---

### Post by oldfred on 2013-01-30
I am not a fan of copying system and prefer a new install and copy /home which has your data and settings. Also with such a huge change in drive size, reorganizing partitions and the housecleaning that a new install does is worth the bit of effort on a new install. A clone also requires some effort so the effort is about a wash.

Are you keeping 80GB drive? If so any image copy will create duplicate UUIDs and  cause issues. If immediately disconnecting the old drive then the duplicates may not matter.

Will you be dual booting with Windows, storing lots of data in separte data partitions, or installing other Ubuntu or Linux versions to test? Answers to those questions may determine better ways to repartition. 

       discussion of alternatives/strategy backups - full image backkups also
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

    
       Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
Tar backup script:
[https://help.ubuntu.com/12.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/12.04/serverguide/C/backup-shellscripts.html)

    
You can also just use gparted to copy partitions.

       Move entire OS to another drive - but new install often easier
[http://ubuntuforums.org/showthread.php?t=1929671](http://ubuntuforums.org/showthread.php?t=1929671)
    
       Files that may need update on image copy
 fstab, reinstall grub and grub's reinstall location. Or change UUIDs
If different computer:
/etc/hostname and /etc/hosts,

---

### Post by audiomick on 2013-01-30
I would also re-install and then copy the contents of /home across.

---

### Post by Laobi on 2013-01-30
You can use [Redo Backup]("http://redobackup.org/") too, it seems a bit simpler than Clonezilla.

But I would also really recommend you to do a clean install. You will loose a little more time to setup again everything to your liking, but you might save yourself a lot of head scratching that could otherwise take you even more time.

---

### Post by dlw on 2013-01-30
Are you keeping 80GB drive? If so any image copy will create duplicate UUIDs and cause issues. If immediately disconnecting the old drive then the duplicates may not matter.

Will you be dual booting with Windows, storing lots of data in separte data partitions, or installing other Ubuntu or Linux versions to test? Answers to those questions may determine better ways to repartition. 

Yes, on keeping the 80gb for backup purposes along with Ubuntu One cloud.
I got rid of windows years ago.
I am a USER not a TECHIE, will only be using 12.10 and accepting updates.
I just want to move everything over to the 1tb hd.

---

### Post by ibjsb4 on 2013-01-30
> I am a USER not a TECHIE

Not no more :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=change+UUID&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=change+UUID&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by dlw on 2013-01-30
I have a 12.10 iso cd.
However, there has been a ton of updates since it was installed.
If I download 12.10 again, will it contain the upgrades?
Are there any recent such as 12.10.*?
Going to Ubuntu site to look around.

dlw

---

### Post by DominikST95 on 2013-01-30
No, the updates will be downloaded during the installation of Ubuntu ;)

---

### Post by dlw on 2013-01-30
I thank everyone for their input.
Backing up Home directory now.
Then do a fresh install to hdc.

Thanks again,
dlw

---

### Post by dlw on 2013-01-30
Did a fresh install.
Box still boots up to sda (80gb) instead of sdb (1tb).
I did something wrong

Can this be changed in grub?
Or, what has to be done?

dlw

---

### Post by oldfred on 2013-01-30
Did you install grub to the new drive? If so change BIOS to boot from that drive.

If not, run this and it should add the new install to the menu.

sudo update-grub

Then boot into your new install and install grub to the MBR of the new drive. Confirm if sda or sdb and use correct drive to install from within your new install.
       sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
    
If still issues run BootInfo report:
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by dlw on 2013-01-30
Did you install grub to the new drive? If so change BIOS to boot from that drive.

[COLOR="SeaGreen"]I thought I did.[/COLOR]

If not, run this and it should add the new install to the menu.

sudo update-grub

don@don-HP:~$ sudo update grub
sudo: update: command not found
don@don-HP:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-3.5.0-22-generic
Found kernel: /boot/vmlinuz-3.5.0-21-generic
Found kernel: /boot/vmlinuz-3.5.0-19-generic
Found kernel: /boot/vmlinuz-3.2.0-34-generic-pae
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

don@don-HP:~$

Then boot into your new install and install grub to the MBR of the new drive. Confirm if sda or sdb and use correct drive to install from within your new install.

The sys still boots into sda, not sdb.

[COLOR="SeaGreen"]sudo fdisk -l[/COLOR]


don@don-HP:~$ sudo fdisk -l
[sudo] password for don: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4cf176b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   146486422    73242187+  83  Linux
/dev/sda2       146487294   156301311     4907009    5  Extended
/dev/sda5       146487296   156301311     4907008   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00022359

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     1118207      558080   82  Linux swap / Solaris
/dev/sdb2         1120254  1953523711   976201729    5  Extended
/dev/sdb5   *     1120256  1953523711   976201728   83  Linux

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x43c7d366

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   488394751   244196352    7  HPFS/NTFS/exFAT
don@don-HP:~$

---

### Post by arpanaut on 2013-01-30
In your bios make sure that your second drive is first in the boot order.

---

### Post by oldfred on 2013-01-31
If you installed 12.10, you should not have a menu.lst? That is from grub legacy which has not been used since 9.04 unless you upgraded from before that or forced the install of grub not grub2.

Best to see all the details.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

