---
title: "Q Connecting NTFS hard drive via USB"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by paker on 2012-01-21
I have an extra hard drive. I want to use it for external USB storage. But computer wouldn't recognize it. Setup is

Samsung 750 GB serial hd
NTFS formatted with Windows Vista laptop
Thermaltake 2-disk docking station
USB connection

I have other hard drives in EXT format. They work well in the dock, same USB connection. What can I do? 

System > Administration > Disk Utility doesn't show the hard drive.
System > Administration > Gparted doesn't show it, either.
Synaptic Package Manger shows "ntfs-3g" marked installed.

Thanks.

---

### Post by paker on 2012-01-22
This is what I have found so far.

1) The hard drive used to be the main (and the only one) hard drive of another ubuntu machine.
2) The only way to get the hd recognized is to connect it directly to the motherboard. I formated and partitioned in EXT4. 
3) Is still has "lost and found" folder and it is locked. No way I can access/delete it. 

Would someone kindly tell me how to wipe a used hard drive clean? I searched and read about "shred" "wipe" etc, but I am not sure if it can remove the locked folder, too.
Thanks.

---

### Post by Double.J on 2012-01-22
Hi there parker, I'm a bit confused, is the drive ntfs or EXT4? in post 1 you say ntfs, but in post 2 it's EXT4?

With the lock issue, have you tried
```

gksudo gparted
```and deleting the partition? if that fails, so long as you don't want any other partition on the device, you could reset the partition table?

Device->Create Partition Table

and choose mbr (default)

In terms of the drive not showing up over USB at all, that sounds like a problem with the caddy -is the drive fitted correctly/receiving power?

All the best !

---

### Post by oklokl on 2012-01-22
mbr partition bug

umount -l /dev/sdbX
sudo -i

fidks -l

dd if=/dev/zero of=/dev/sdbX bs=512 count=2345311

old hdd
dd if=/dev/zero of=/dev/sdbX bs=446 count=2345311

gksu gparted
make mbr >ms-dos

mbr.. error?
rebootting pc
remove partition > new mbr

---

