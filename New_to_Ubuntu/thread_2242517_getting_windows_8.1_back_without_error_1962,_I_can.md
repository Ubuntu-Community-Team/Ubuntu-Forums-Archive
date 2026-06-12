---
title: "getting windows 8.1 back without error 1962, I can't boot into windows"
date: 2014-09-02
forum: New to Ubuntu
---

### Post by david281 on 2014-09-02
Ive done a little research not much ( i work 12 hours nights and its bed time) I installed Ubuntu 14:04 Tahr. I dont dislike it i just am not able to dual boot. When i wanted to go back to windows 8.2 i couldnt book into it. Did i mess up the MBR? Is windows still on my pc? How can i boot into windows again? afll i get is error 1962 at times i can get into ubuntu ( otherwise i wouldnt be typing) but i have not been able to get into windows Lenovo Ideacentre K410 I feel like im searching for kevin flynn in tron legacy. Ill post my paste, someone please help the noob. [http://paste.ubuntu.com/8209926/](http://paste.ubuntu.com/8209926/)

---

### Post by sotiris2 on 2014-09-02
Unfortunately it appears as you have deleted the windows partitions on the drive. Maybe windows was hibernated when you installed? I am not sure if it is possible to recover the old partitions with tools such as [testdisk](http://www.cgsecurity.org/wiki/TestDisk) but to save any chances you have you should stop using the installed ubuntu and use the try ubuntu option on the install disk.

---

### Post by ibjsb4 on 2014-09-02
Look to see if you have a windows partition.  This can be done using the terminal.  Copy and paste this code to terminal.
```
sudo fdisk -l
```
[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by david281 on 2014-09-02
After running sudo fdisk this is what i got

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1dad6cd4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

---

### Post by ibjsb4 on 2014-09-02
<snip>

I do not run EFI, sorry, but cannot help with this.

---

### Post by Mark Phelps on 2014-09-02
The fdisk command doesn't understand GPT drives, so that will not help you.  If Windows was previously on sda, it's gone now as all the previous NTFS partitions are gone.

What MIGHT work is the following:
1) Using a working PC with a CD burner, download and burn a CD from the Minitool Partition Wizard Boot CD
2) Burn that ISO image to CD.  IF you don't have an image burning program on the Windows PC, instal ImgBurn and use that.
3) Boot your PC from that CD and see if Partition Wizard will recover your former partitions.
4) If that works, you should be good to go.

If that does not work, to get Windows back, you would have to do a complete clean reinstall. You would need Windows install DVD or USB to do that.

You might be able to save some data from the former partitions by connecting your SDA drive to a working Windows PC, installing RecoverMyFiles and seeing if it finds the files and folders you want to save prior to reinstallation of Windows.  You will have to go online and purchase a license to save the files and folders.

---

