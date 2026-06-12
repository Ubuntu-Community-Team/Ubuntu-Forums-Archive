---
title: "Select the external HDD for recovered files with Photorec"
date: 2017-05-01
forum: New to Ubuntu
---

### Post by andrew2622 on 2017-05-01
Hello everybody,

I am new to Ubuntu and need to recover files with Photorec and save them on an external HDD.

I've got System Rescue CD and I know how to enter into the graphical interface with "startx" and could you please tell me how 
to mount/access the external HDD from here in order to be found by the PHotorec - ir the external drive is not mounted it cannot be used 
by Photorec to save the recovered files on it.

thanks a lot ,

Andrew

---

### Post by oldfred on 2017-05-01
Have you partitioned (gpt or MBR), and formatted external drive (ext4 or NTFS if to be used with Windows), so you have a partition to mount.
But NTFS does not support Linux ownership & permissions, so those will be lost. If just your data files, you can restore those, but if anything related to system, it is just about impossible.

And if ext4 given yourself ownership & permissions so you can use it?

---

### Post by andrew2622 on 2017-05-02
Hello,

thanks Oldfred for your answer.

The external HDD I'm trying to use is FAT preformatted and connects to the USB port. Neither Testdisk nor PHotorec could access it unless the HDD partition has
been previously mounted - before launching Photorec from the System Rescue CD prompt.

Could you help me to mount the external HDD from the graphical interface of System Rescue Cd.

Thanks a lot,

Andrew.

---

### Post by oldfred on 2017-05-02
I ran Photorec from my Ubuntu installer and that was several years ago. 
With Nautilus, and external drive you can just click on partition(s).  Do not know what file browser is in System Rescue.

You should be able to manually mount.
Find partition:
sudo parted -l
If shown as sdb1
 mount -t vfat /dev/sdb1 /media/disk

Not sure if you have to create mount point first if in /media, normally you do. With Ubuntu you need sudo and it usually default mounts by finding correct partition format.
      
 sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data 
    
 Is drive large?
FAT is not recommended for large drives.
It has no journal and does not support any file over 4GB. 
Years ago I was doing a tar type backup as one large file and eventually noticed even though I had more data file was always 4GB. Never had a good backup, luckily I never needed it, but changed the way I backup.

---

