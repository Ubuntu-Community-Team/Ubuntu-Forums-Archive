---
title: "How do I go from dual boot to single Ubuntu boot?"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by Homeroast on 2012-06-28
I just installed Ubuntu on a Lenovo G570 Notebook.  I had to use Wubi to install it since the machine was already running Windows 7.  I looks like Wubi defaulted to a dual boot situation on this computer.

I intended to remove Windows completely and just run Ubuntu 12.04.

What should I do now?  How do I wipe windows and only run Ubuntu?  Do I have to do another installation?

Thanks in advance!

H

---

### Post by keeper7323 on 2012-06-28
I recently installed 12.04 on a box with XP using a jump stick.  Very early in the installation, the installer gives three choices & one of these is to delete Windows.  Select that choice and you should be good to go.

---

### Post by Homeroast on 2012-06-28
That option never came up.  I saw that option when I installed Lubuntu on a really old machine.  However, it never came up on this install.  I wonder if it has to do with WUBI.EXE ... ?

---

### Post by J14e on 2012-06-28
u cant go full ubuntu with wubi download the iso and mount it on a cd then do a full install that way wubi only works under windows

---

### Post by J14e on 2012-06-28
and if you run an intel chipset its the i386 iso if u run amd its the amd64 iso  that matters a lot

---

### Post by Ubun2to on 2012-06-28
Well, I did this. Here's what you need to do.
First, boot onto a live CD/DVD or USB. This is not necessarily, but I think that it could work better, as you don't have to worry about copying files already being used and edited. However, if you choose not to, I'm not sure how.
Also, make sure you backup EVERYTHING before you do this. This has the potential to mess TONS of stuff up. Make sure you don't want Windows anymore.
Anyway, boot to a live CD or USB. Make sure the live CD or USB has the right version of Ubuntu-32 bit or 64 bit. If it's not correct, you will have the wrong version installed.
Note that I am adding swap (which is essentially backup RAM incase you accidentally go over the limit).
1. Go to GParted.
2a. Create a partition for Ubuntu.
2b. If you know how to create partitions, skip to step 3.
2c. Look at GParted-is there unallocated space? If not, right click on your Windows partition, and click Resize/Move.
2d. Leave about 1 GB of free space on the Windows partition, as a cautionary measure (I just think it would be a good idea, although I have no evidence to back it up-but, you will delete this partition later, so it doesn't matter).
2e. Right click on the unallocated space, and click New. The filesystem should be ext4, and you can name it whatever you please (you can name it Pizza for all I care). The free space before should be 0. The free space after should be the amount of RAM you have + 512 MB. This space will be used for swap space.
2f. Press Add. This will create the partition.
3a. Now, it is time to create the swap partition. If you know how to do swap, skip to step 4. 
3b. If you have a factory image partition, right click it and select Delete. You can only have 4 partitions unless you have EFI, which is not very common currently.
3c. Right click on the unallocated space. Press New.
3d. Make the filesystem linux-swap.
3e. Make sure there is no free space before or after the swap partition. Then press add.
4a. Now, it is time to finalize our partition changes. If you know how to do this, skip to step 5.
4b. Press the check mark on the row of buttons above the visual representation of the sizes of the partitions. Now, confirm the changes and let the computer do the work. Note that this might take awhile. If you have a slower computer, you might want to work on reading War and Peace or your novel. If you have a TV in the same room, by all means turn it on and occasionally check on the computer.
4c. Once the computer has done it all, proceed to the next step.
5a. Now, it is time to mount your partitions. If you already know the command, skip to step 6.
5b. Open terminal.
5c. Look at GParted. Identify the name of the Windows parition. This could be /dev/sda2, /dev/sdb3, or anything in between.
5d. Type the following command:
```
sudo mount /partition-name/here /mnt
```
Insert the partition name in the /partition-name/here part.
5e. Now, go to /mnt. Make sure there are a bunch of Windows folders. That means you have mounted the right thing.
6a. Now, it is time to prepare your command. If you already know what to do, skip to step 7.
However, you have to download the following file and extract it to your Downloads directory:
[https://help.ubuntu.com/community/MigrateWubi?action=AttachFile&do=view&target=wubi-move-2.2.tar.gz](https://help.ubuntu.com/community/MigrateWubi?action=AttachFile&do=view&target=wubi-move-2.2.tar.gz)
6b. Insert the following command into terminal:
```
cd /home/ubuntu/downloads/wubi-move-2.2/
```
That changes the directory to where you have extracted the Wubi migration files.
6c. Now, go to /mnt. Go into the Ubuntu or Wubi folder. Then, go to drives, or whatever the file path is. Just search around until you find a file called "root.disk". Record this filepath.
6d. Paste the following command into terminal:
```
sudo bash wubi-move-2.2.sh --root-disk=/mnt/ubuntu/disks/root.disk /dev/sda4 /dev/sda3
```
Replace "/mnt/ubuntu/disks/root.disk" with the filepath for your root.disk.
Replace "/dev/sda4" with the name of the partition you want Ubuntu to be in.
Replace "/dev/sda3" with the name of the partition you want to be your swap space.
6e. Now, you are ready to go. Press enter. Remember that this can take a LONG time. It took several hours for my computer to do it.
You are done with the migration. However, there is one more thing-enable swap space. Reboot the computer, and make sure you are booting onto the hard drive.
7a. Now, enable swap space. If you know how to do this, congrats, you're done.
7b. Paste the following commands into terminal.
```
sudo cp /etc/fstab /etc/fstab-backup
echo "UUID=$(sudo blkid -o value -s UUID /dev/sda3)    none    swap    sw    0    0" |
sudo tee --append /etc/fstab
```
These will enable the swap partition.
7c. Reboot, and you are done!
Also, please note I will make a video tutorial sometime in the near future (hopefully tomorrow).

---

### Post by oldfred on 2012-06-28
Wubi runs inside the Windows NTFS partition and boots with the Windows boot loader. You cannot delete Windows without deleting wubi also.

You can migrate your install with a script.

HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Usually best to fully back up Windows install. A few users some back and want to reinstall as there is one application or game they just cannot live without.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

If a new install, you can dual boot with Ubuntu in separate partitions or erase Windows and just install Ubuntu.

Ubuntu is not Windows
[http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/](http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu/)
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

---

### Post by BBQdave on 2012-06-28
> **Homeroast said:**
> I intended to remove Windows completely and just run Ubuntu 12.04.

Fresh Install would be the easiest. Backup (copy) your data to another drive, if you need to.

Then [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

32-bit (x86) or 64-bit (amd 64) editions of Ubuntu, which 64-bit is sometimes referred to as amd 64, a nod to amd who first introduced 64-bit to consumers - but 64-bit (amd 64) edition Ubuntu is for both amd and intel machines. Basically if you have older hardware that max's out at 2 gigs of ram, go with 32-bit edition. If you have newer hardware that can handle over 2 gigs of ram, go with 64-bit edition.

A fresh install, selecting Ubuntu as your only system at install will wipe your drive and set Ubuntu as the only OS :D

You can boot into the live cd of Ubuntu 12.04 and test your system from the cd. The cd will be slower than an installed system, but you can than see if there are any potential problems with your hardware and Ubuntu 12.04, before you install Ubuntu.

---

### Post by Homeroast on 2012-06-29
I simply ran another full installation (without WUBI)  and that seemed to work fine. 

Thanks for all the wonderful information and help to a newbie.  I'll probably come back to this thread again for the tips.

Best wishes to all!

---

