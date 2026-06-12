---
title: "2 ubuntu instaled one same pc  and windows 7 boot problem"
date: 2013-12-24
forum: New to Ubuntu
---

### Post by adrianrn on 2013-12-24
Hello. I really don''t know what i did but somehow i installed ubuntu 13.10(after i already had it installed on another partition) and now windows won't boot. Any ideas how I can restore windows boot? thanks

---

### Post by grahammechanical on 2013-12-24
You really need to explain what you mean by "Windows will not boot." Does Windows appear in the Grub menu? Or were you using a Windows boot manager? Please explain your set up more fully.

Regards.

---

### Post by adrianrn on 2013-12-24
Well al first I installed ubuntu on an empty partiton. When I restarted it would boot directly in ubuntu with no option to boot windows. I used this and then I could boot into windows - [http://askubuntu.com/posts/124630/revisions](http://askubuntu.com/posts/124630/revisions) ( number 3). Then I could boot windows but no ubuntu. Also the partition for ubuntu wasn't visible from windows. So I used a live cd(usb) and treid to uninstall ubuntu from there using the Install option and that's when I think I installed another ubuntu maybe in the windows partition. And now from ubuntu I can only see one partition and I had 3.. I hope I explained it more clearly as English isn't my native language. thanks

---

### Post by oldfred on 2013-12-24
We seem to be seeing a lot of users who reinstall and totally erase hard drive with new install.
Did you use an auto install option, or Something Else the manual install where you choose to over install to a specific partition?
If it did not say install side by side with Windows you may have overwritten it.

Post this from terminal. If no NTFS partition then Windows is gone. You did fully back it first?

sudo parted -l

---

### Post by adrianrn on 2013-12-24
Number  Start   End     Size    File system     Name  Flags
 1      1049kB  512MB   511MB   fat32                 boot
 2      512MB   996GB   996GB   ext4
 3      996GB   1000GB  3725MB  linux-swap(v1)


Model:  USB DISK 2.0 (scsi)
Disk /dev/sdb: 16,0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32,3kB  16,0GB  16,0GB  primary  ntfs


I didn't back anything :( any solutions to undo what i just did? thanks

---

### Post by Mark Phelps on 2013-12-24
From the command results, Windows partitions are GONE.  You overwrote and reformatted them repeatedly installing Linux.

There is no simple way to get Windows back, especially since you probably made no attempt to create a Win7 Repair CD when Win7 was working.

There are Windows utilities you could try to see if you can recover any of the files.  In my experience, they work a lot better on Windows filesystems than do Linux utilities.  But ... you have to recover the files to a different drive, you have to connect this drive to a working PC (running Windows), and you have to be prepared to purchase a license if you see it finds the files you need.

---

### Post by adrianrn on 2013-12-24
So I've lost all data.. now I have another problem. I tried this method [http://askubuntu.com/questions/289559/how-to-create-a-windows-8-bootable-usb-stick-with-ubuntu](http://askubuntu.com/questions/289559/how-to-create-a-windows-8-bootable-usb-stick-with-ubuntu) to create a bootable usb with windows 8 but when I restart my pc it won't boot from that usb. I also selected that as my primary boot device. So any solutions? Thanks

---

### Post by atconley on 2013-12-24
Priority one is to try to recover your files; only once you're sure that  that is hopeless should you  worry about reinstalling.  I suggest  the  following:

Post the *full* return from this command (your post #5 does not appear to contain the full return):
```
sudo parted -l
```
And run these commands to try and mount your NTFS partition:
```
mkdir ~/mnt_ntfs
sudo mount /dev/sdb1 ~/mnt_ntfs
```
Look at ~/mnt_ntfs.  What can you see?

---

### Post by fantab on 2013-12-25
You can try [Mini Tool]("http://www.minitool-partitionrecovery.com/") to recover your lost partition. The tool is free to use, to recover upto 1Gb data, if you have more data found to be recovered then you have to buy the license.
-------OR-------
Try [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") and [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec") for free to recover as much data as you can... you may not be able to recover full data but you can whatever you can.

---

