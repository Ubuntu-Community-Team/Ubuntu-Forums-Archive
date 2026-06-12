---
title: "operating system not found !!!"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by vivekpandey1991 on 2012-03-17
hi all .. i have a dual boot , windows 7 and ubuntu 11.04..... today morning when i booted my laptop . i go a error saying operating system not found,, then i took  a 11.10 live installation cd and booted off from it. but the problem is i dont see my hard disk in the places option...is my hard disk corrupted or there may be any other problem ? please help... i have a lot of important data in my hard disk

---

### Post by coldraven on 2012-03-17
That does not sound good :(
You could try removing the disc drive and re-inserting it, maybe the connector got loose.
If it's your drive controller that has died you could get a USB HDD enclosure from eBay for less than £5 , make sure you get the correct one for your drive. IDE or SATA.
Install your drive in the enclosure, plug it to your laptop and boot from live CD. Then see if it appears in "Places".
I don't want to say what the alternative is, it's bad.

---

### Post by 2F4U on 2012-03-17
Is neither Windows nor Ubuntu booting? Can you see the harddisk in the BIOS?

---

### Post by vivekpandey1991 on 2012-03-17
> **2F4U said:**
> Is neither Windows nor Ubuntu booting? Can you see the harddisk in the BIOS?

when i booted off from a live cd , i couldnt see the hard disk . even gparted doesnt show any partition. however disk manager shows it as generic multicard /dev/sda ..... i tried to install both ubuntu as well as windows again but i dont get a hard disk to install . it just shows 0 mb space :confused:

---

### Post by chipbuster on 2012-03-17
Ummm....better start looking at data recovery tools dude, this sounds pretty bad :(

Can device lists see the drive? Try things like "blkid" "ls /dev/[sh]d*" "fdisk -l" and so on. If they can't see it, I'm afraid your hard drive is probably hosed.

---

### Post by vivekpandey1991 on 2012-03-18
also i have found out a new thingy... whenever i start my laptop , i just get a strange sound besides the disk sound as if something is trying to rotate but there is some impedance

---

### Post by vivekpandey1991 on 2012-03-18
also i have found out a new thingy... whenever i start my laptop , i just get a strange sound besides the disk sound as if something is trying to rotate but there is some impedance

---

### Post by asifnaz on 2012-03-18
Just put out and re-install your HD . In worst case your hard disk is dead

---

### Post by vivekpandey1991 on 2012-03-18
> **asifnaz said:**
> Just put out and re-install your HD . In worst case your hard disk is dead
is there some tutorial on how to reinstall hdd ? i mean all that unscrewing of laptop and then fixing it back again?

---

### Post by winh8r on 2012-03-18
Boot from the Live CD

open a terminal

enter the following:

```
sudo e2fsck -C0 -p -f -v /dev/sdb
```

where /dev/**[COLOR="Lime"][COLOR="Indigo"]sdb[/COLOR][/COLOR]** is the name of [COLOR="Red"]YOUR [/COLOR]partition, as seen in gparted.

Allow this to complete and report any errors.

Hope this helps.

---

### Post by vivekpandey1991 on 2012-03-18
> **winh8r said:**
> Boot from the Live CD

open a terminal

enter the following:

```
sudo e2fsck -C0 -p -f -v /dev/sdb
```where /dev/**[COLOR=Lime][COLOR=Indigo]sdb[/COLOR][/COLOR]** is the name of [COLOR=Red]YOUR [/COLOR]partition, as seen in gparted.

Allow this to complete and report any errors.

Hope this helps.
as i mentioned earlier , i dont se any partition in gparted or else i would have solved the problem myself.. anyways i ran your command and i get this error and thats very obvious
```

 ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda
e2fsck: No medium found while trying to open /dev/sda
/dev/sda: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


```

---

### Post by winh8r on 2012-03-18
Can you enter this command and post the output please:

```
dumpe2fs /dev/sda | grep superblock
```

---

### Post by whathaveugot on 2012-05-27
Hi All,

I am currently having this same problem of 'Operating System Not Found'. Recntly I migrated my netbook from Ubuntu 10.04 to 12.04, and following that was experiencing system freeze/hang. Tried rebooting couple of times and after one of the reboots I got this message and its still the same. On booting up with live cd, my partitions are not showing up in 'Places'. So went for a dig and found this thread here.

@winh8r...I tried both the commands you gave and the following is what I got:

root@ubuntu:/home/ubuntu# e2fsck -C0 -p -f -v /dev/sda
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda
Could this be a zero-length partition?

root@ubuntu:/home/ubuntu# dumpe2fs /dev/sda | grep superblock
dumpe2fs 1.41.11 (14-Mar-2010)
dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda
Couldn't find valid filesystem superblock.

I am guessing my HDD has crashed but FYI its showing up in the BIOS. So is there any possible way that could help me out of this. Any help would be highly appreciated.

Thanks.

---

### Post by lisati on 2012-05-27
Old thread closed.

@whathaveyougot: Your circumstances seem to be slightly different. Please start a new thread.

---

