---
title: "Data rescue mission"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Fred the blarney owl on 2008-06-29
I have a Dell Inspiron 6000 with a corrupt XP installation. I also have an Ubuntu live CD.


I can connect my wife's Inspiron to my Apple macbook via a crossover cable. 


How do I access the data in XP's documents and settings folders via this setup or should I be doing something different?

---

### Post by kuja on 2008-06-29
Well, You can try to mount the partition with [ntfs-3g](https://help.ubuntu.com/community/MountingWindowsPartitions), a linux driver for the ntfs filesystem. Good luck!

---

### Post by jimrz on 2008-06-29
Your best / easiest bet might be a Knoppix [[COLOR="Sienna"]***[I]_"live" cd_*[/I]**[/COLOR]]("http://www.knopper.net/knoppix/index-en.html"). It will auto-mount all the partitions on your drive. You can then grab all your files and copy to them to an external device.

---

### Post by dominiquec on 2008-06-29
In my own experience with Hardy (and a Windows 2000 Server installation), you should be able to mount the NTFS partition immediately.

Probably easier and better to copy it to an external hard disk rather than over the network, though.

---

### Post by king leoric on 2008-06-29
You can use you ubuntu live cd booting from it and then you can now access to XP's documents and copy them to any external drives. This would be the best and easiest:)

hope this helps

---

### Post by iaculallad on 2008-06-29
Just boot your Ubuntu LiveCD on your Inspiron unit, it would be best if you're using Hardy Desktop LiveCD so it would automount your NTFS drive. You can also setup your "cross-over" network afterwards when you boot onto your LiveCD to connect to your Apple MacBook.

Just remember that both IP's should belong to the same subnet using same mask.

---

### Post by Fred the blarney owl on 2008-06-29
> **iaculallad said:**
> Just boot your Ubuntu LiveCD on your Inspiron unit, it would be best if you're using Hardy Desktop LiveCD so it would automount your NTFS drive. You can also setup your "cross-over" network afterwards when you boot onto your LiveCD to connect to your Apple MacBook.

Just remember that both IP's should belong to the same subnet using same mask.

I downloaded and burned the disk via my Macbook. I loaded the live CD onto the Inspiron 6000. I tried mounting the volume (36.1gb) and was told "cannot mount the volume". 

$volume_information attribute not found in 
$volume: no such file or directory Failed to mount '/
dev/sda2': No such file or directory

I did verify the CD. I burned it from the ISO ubuntu-8.04-desktop=i386.iso.

What's up? Doesn't Ubuntu like NTFS?

Edit:

It then tried to mount and came up with a message stating there was a Dbus error and something about a no reply.

Ah well... looks like I'd better just spend $20 on a USB to 2.5" IDE cable.

---

### Post by iaculallad on 2008-06-29
> **Fred the blarney owl said:**
> I downloaded and burned the disk via my Macbook. I loaded the live CD onto the Inspiron 6000. I tried mounting the volume (36.1gb) and was told "cannot mount the volume". 

$volume_information attribute not found in 
$volume: no such file or directory Failed to mount '/
dev/sda2': No such file or directory

I did verify the CD. I burned it from the ISO ubuntu-8.04-desktop=i386.iso.

What's up? Doesn't Ubuntu like NTFS?

-Ubuntu loves NTFS- It's just a matter of correct mount point and NTFS driver.

Try to boot using your LiveCD and drop on the terminal to issue the command below and post whatever displays.

```
sudo fdisk -l
```

l = Small letter L

---

### Post by Fred the blarney owl on 2008-07-10
I tried various things and cannot even read the disk. I tried repairing the boot sector with XP but to no avail. I can see the data with Windows data recovery software but as I haven't paid for the software, I can't actually use it.

In the end I put a new hard drive in the laptop and installed windows on that. I'm scratching my head about rescuing the data from the drive I took out though.

---

### Post by kansasnoob on 2008-07-10
Oh, try > ntfs-config or if you need to read/copy encrypted files you can even use > ntfsprogs both are available in syanptic!

Ubuntu is not only a great OS it's a darn good data recovery device!

---

### Post by Fred the blarney owl on 2008-07-10
> **kansasnoob said:**
> Oh, try  or if you need to read/copy encrypted files you can even use  both are available in syanptic!

Ubuntu is not only a great OS it's a darn good data recovery device!

What's synaptic? Can I do this with a live CD?

---

