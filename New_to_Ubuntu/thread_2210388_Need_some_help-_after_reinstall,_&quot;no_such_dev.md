---
title: "Need some help- after reinstall, &quot;no such device&quot; and &quot;grub rescue&quot;"
date: 2014-03-10
forum: New to Ubuntu
---

### Post by ra7411 on 2014-03-10
I had previously successfully installed Ubuntu 12.04, but it installed as 32 bit.
I decided to re-install as 64 bit.

I deleted the installed ubuntu partitions - I couldn't find any method of normal uninstall.

All went well until I booted up - I got an error that said something like: "no such device" and "grub rescue".

I googled, found a "solution", and tried to follow it, with the following bad results shown on the terminal output, below.
solution: [http://askubuntu.com/questions/143667/boot-error-no-such-device-grub-rescue](http://askubuntu.com/questions/143667/boot-error-no-such-device-grub-rescue)

How do I fix this without wrecking my non-ubunutu partitions/files? 

Terminal:

Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xddca895a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1015136282   507567117+   7  HPFS/NTFS/exFAT
/dev/sdb2      1015138302  1953525167   469193433    f  W95 Ext'd (LBA)
/dev/sdb5      1230787908  1953525167   361368630    7  HPFS/NTFS/exFAT
/dev/sdb6      1015138304  1222434815   103648256   83  Linux
/dev/sdb7      1222436864  1230786559     4174848   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ mkdir /home/ubuntu/temp
ubuntu@ubuntu:~$ sudo mount /dev/sdb6 /home/ubuntu/temp
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/home/ubuntu/temp /dev/sdb6
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.

xxend

---

### Post by oldfred on 2014-03-10
Easier to use Boot-Repair.
But you do not install grub to partitions, but to the MBR with BIOS based systems.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

      
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by ra7411 on 2014-03-10
I got the disk repair program, re-booted with it, and it's not going well.
I haven't gotten a GUI as shown on it's page, I have a n on-GUI interface, with some option keys at the bottom.
It's doing something, and slowly speeling out:
EDD: error 1000 reading sector  245635
for a succession that looks like it will fill the page.

How do I get my computer back? I don't need to get the ubuntu working - I just want to be able to boot win 8.1 up again.
How do I do this?

Thanks

---

### Post by oldfred on 2014-03-10
Is error from Boot-Repair on CD, flash drive or hard drive?
 That seems like either the downloaded ISO is defective or your drive you are using to boot is defective.

---

### Post by ra7411 on 2014-03-10
I don't know what the problem is, but this taking too much time and effort.

Will a re-install of win 8.1 be likely to get rid of whatever ubuntu did to the boot process?

Thanks again for helping - I was getting a little concerned by the lack of responses.

---

### Post by ra7411 on 2014-03-10
I have a 64 bit machine, so I was using a 64 bit download boot-repair-disk.
The install I was originally trying to replace was 32 bit, so I downloaded the 32 version,burned a cd, and it seemed to work.

Here's the data you requested:

[http://paste.ubuntu.com/7070949](http://paste.ubuntu.com/7070949)

---

### Post by snazzierella on 2014-03-11
You can use a windows install or repair disk to restore the original boot loader.

---

### Post by oldfred on 2014-03-11
Since you have two drives and each install on separate drives I would leave the Windows boot loader on sda and grub on sdb. And set BIOS to boot sdb.
Boot-Repair likes to install grub2's boot loader to every drive as some users seem not to know how or want to change default boot drive in BIOS. So best not to run auto fix, but advanced and manually choose install and drive to install boot loader into.
Boot-Repair will install a Windows type boot loader to sda, or you can use your Windows repairCD or flash drive to run fixMBR on sda. If installing a new copy of WIndows it will also overwrite MBR.

With two drives and mulitple installs you always need to use Something Else or manual install to choose drive and (change or add) partitions that you want to use for / (root) and /home. And on that screen is the location of the bootloader and you want sdb.

My screen shot installing into sdc partition with an older install. It still shows sda in combo box for grub boot loader as I had not changed it.

---

