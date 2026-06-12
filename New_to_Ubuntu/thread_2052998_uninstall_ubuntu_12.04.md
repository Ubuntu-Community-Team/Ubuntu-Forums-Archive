---
title: "uninstall ubuntu 12.04"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by aakashg on 2012-09-04
Hi,

I had my new laptop with DOS, i installed ubuntu 12.04 (64-bit) on new machine.
Please help me with un-installing  ubuntu , as now i want to install windows.

I have a CD of ubuntu12.04 burned from iso image.

---

### Post by black veils on 2012-09-04
as far as i know, you just boot the ubuntu live disc, find the application **gparted**, use that to delete all partitions. you may need to first **swap-off** a swap partition in case it is mounted.

delete partitions, leave as unallocated space, then try the windows disc.

---

### Post by aakashg on 2012-09-04
tried with gparted
sudo apt-get install gparted ( package was not installed previously).

gives me error :
E: Unable to locate package gparted.

---

### Post by black veils on 2012-09-04
what about **disk utility** ?

when i get errors like that, it is either lack of internet, a server down or i forgot to first ```
sudo apt-get update
```

---

### Post by TheMTtakeover on 2012-09-04
Can you just put in your windows install disc and overwrite the Ubuntu partition?

---

### Post by coffeecat on 2012-09-04
> **aakashg said:**
> tried with gparted
sudo apt-get install gparted ( package was not installed previously).

gives me error :
E: Unable to locate package gparted.

That looks as though you are trying to install Gparted to your hard drive system. You cannot delete the Ubuntu partition from inside a running system. You need to boot up with the live CD, as black veils said, and use Gparted from that. Gparted is included in the live CD and does not need to be installed.

> **TheMTtakeover said:**
> Can you just put in your windows install disc and overwrite the Ubuntu partition?

Indeed. From what I remember of the XP, Vista and Windows 7 installers, you can delete all pre-existing partitions with that and then create your NTFS partition(s) for Windows. There's probably no need for Gparted and the Ubuntu CD at all if only Windows is going to be installed.

---

### Post by aakashg on 2012-09-04
I did that very first but did not work..:(
putting the installtion CD it directly goes to login screen of ubuntu, rather booting with windows CD.

I also tried changing the booting option from BIOS but
i am unable to see any booting preferences, instead i see only 
1. Ubuntu ( in startup option of BIOS).

---

### Post by coffeecat on 2012-09-04
> **aakashg said:**
> I did that very first but did not work..:(
putting the installtion CD it directly goes to login screen of ubuntu, rather booting with windows CD.

I also tried changing the booting option from BIOS but
i am unable to see any booting preferences, instead i see only 
1. Ubuntu ( in startup option of BIOS).

This is a BIOS issue. You need to have another look in the BIOS. There will be an option to give priority to booting from optical drive, hard drive(s) and USB. You need to set the optical drive as first boot.

---

### Post by TheMTtakeover on 2012-09-05
It may also make you hit a key on the key board to boot from a disk

---

### Post by aakashg on 2012-09-08
Thanks to all of you.. :) for helping me out....

What miskake i made was i installed Ubuntu on the whole HDD, hence when i boot it
with my WINDOWS DVD it did not booted.. ( as my BIOS also did not have other preferences to boot from other devices..)
Hence,
Its better to leave some unpartioned space or 
better one is first install WINDOWS and then UBUNTU to have a dual boot...

---

