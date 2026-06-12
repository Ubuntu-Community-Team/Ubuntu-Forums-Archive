---
title: "fdisk doesn't see drive, lsusb does...any help?"
date: 2013-11-24
forum: New to Ubuntu
---

### Post by imrunningoutofname on 2013-11-24
Hi, fairly new to Ubuntu and I'm attempting to recover a drive....I've got a 2tb WD Elements drive that suddenly appears in Windows as 'unitialised'.

All advice I see suggests to clone it with dd then attempt recovery on the clone.  Fair enough....

Except fdisk doesn't see the drive at all.

lsusb does....so not too sure where to go from there.

I found a thread where a user suggested to unplug the drive, run    dmesg | tail 
plug it back in, wait a bit then run
   
dmesg | tail -n 20 

I've got the output from that, though I'm not really sure what I'm looking for....

Any help would be hugely appreciated

   
xx@ubuntu:~$ dmesg | tail 

 [  915.160309] sd 11:0:0:0: [sdh]   
 [  915.160311] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE 
 [  915.160314] sd 11:0:0:0: [sdh]   
 [  915.160316] Sense Key : Data Protect [current]  
 [  915.160321] sd 11:0:0:0: [sdh]   

 [  915.160324] Add. Sense: Logical unit access not authorized 
 [  915.160328] sd 11:0:0:0: [sdh] CDB:  
 [  915.160330] Read(10): 28 00 00 00 00 00 00 00 08 00 

 [  915.160340] end_request: critical target error, dev sdh, sector 0 
 [ 1016.219357] usb 1-1: USB disconnect, device number 6

 

 xx@ubuntu:~$ dmesg | tail -n 20 

 [ 1070.989502] sd 12:0:0:0: [sdh] CDB:  
 [ 1070.989504] Read(10): 28 00 00 00 00 00 00 00 08 00 
 [ 1070.990844] sd 12:0:0:0: [sdh] Unhandled sense code 
 [ 1070.990848] sd 12:0:0:0: [sdh]   
 [ 1070.990850] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE 
 [ 1070.990853] sd 12:0:0:0: [sdh]   
 [ 1070.990855] Sense Key : Data Protect [current]  
 [ 1070.990859] sd 12:0:0:0: [sdh]   
 [ 1070.990863] Add. Sense: Logical unit access not authorized 
 [ 1070.990866] sd 12:0:0:0: [sdh] CDB:  
 [ 1070.990868] Read(10): 28 00 00 00 00 00 00 00 08 00 
 [ 1070.992221] sd 12:0:0:0: [sdh] Unhandled sense code 
 [ 1070.992225] sd 12:0:0:0: [sdh]   
 [ 1070.992227] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE 
 [ 1070.992230] sd 12:0:0:0: [sdh]   
 [ 1070.992232] Sense Key : Data Protect [current]  
 [ 1070.992236] sd 12:0:0:0: [sdh]   
 [ 1070.992240] Add. Sense: Logical unit access not authorized 
 [ 1070.992244] sd 12:0:0:0: [sdh] CDB:  
 [ 1070.992245] Read(10): 28 00 00 00 00 00 00 00 08 00

Using Ubuntu 12.10

Also, the drive appears if I use lsblk:
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   2.7T  0 disk 
&#9500;&#9472;sda1   8:1    0   128M  0 part 
&#9500;&#9472;sda2   8:2    0     2T  0 part /media/6AF0D55EF0D53155
&#9492;&#9472;sda3   8:3    0 754.4G  0 part /media/0CC4D7E6C4D7D056
sdb      8:16   0 931.5G  0 disk 
&#9492;&#9472;sdb1   8:17   0 931.5G  0 part /media/Data and Cache
sdc      8:32   0 931.5G  0 disk 
&#9500;&#9472;sdc1   8:33   0   102M  0 part /media/System Reserved
&#9492;&#9472;sdc2   8:34   0 931.4G  0 part /host
sdh      8:112  0   1.8T  0 disk 
loop0    7:0    0    29G  0 loop /

---

### Post by Mark Phelps on 2013-11-24
My guess, presuming the 2TB drive is "sda" in your lsblkoutput, is that it was formatted with MS Windows filesystems and that the small partition at the beginning is the MS Windows boot partition, the second is the OS partition, and the third is a Data partition.

My own experience has been that Windows utilities do the best job of recovering Windows filesystems; Linux utilities, Linux filesystems.

If you can hook this drive to an MS Windows PC, then you should download and install the Minitool Partition Wizard free software on that Windows PC, and see if that gives you the options of recovering the partitions.

---

### Post by imrunningoutofname on 2013-11-24
Sorry, didn't even think to clarify.  'sda' looks like the 3tb drive I've just plugged in.  Windows Home Server seems to have set up the partitions that way for some reason.  That's the drive I plan on cloning to.

'sdh' looks like it's the faulty disk.

While there's a few Windows options I can try to recover it, I was hoping to have the opportunity to clone it first - as I know repair attempts can just damage it further.  I'll keep that program in mind though - I tried Partition Magic and no luck.

---

