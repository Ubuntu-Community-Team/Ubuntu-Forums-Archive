---
title: "Mounting a USB"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Jimmy9pints on 2008-06-16
OK, this isn't 100% a Ubuntu question...but it is related. 

Basically, I am trying to convert all of my computers to Ubuntu - so far my desktop and girlfriend's new laptop have been done. This old laptop I use for work however has no functional CD drive (since I dropped it out of a van...oops). 

Now I want to install from a USB drive and I think I know how to do that. But I had some problems with this 80G USB drive partially because there are loads of viruses going around our office computers. Every time I had the USB plugged in and Windows running, it wouldn't "safely remove hardware" or unmount. I think something was writing to the disk - probably a virus. As a result, it would rarely mount in Ubuntu. 

On the occasions it did mount however I was able to see the recycler folder and system information volume were full of files and tonnes of .exe's. Some of them were indeed trojan horses and malware downloaders. I deleted the contents of the entire folders. 

Now however I cannot get the USB disk to mount in Windows, and I really want to use it to install Ubuntu on the aforementioned old laptop.

What can I do?

Thanks in advance.

James.

---

### Post by trdc on 2008-06-16
Is formatting it out of the question?

---

### Post by Jimmy9pints on 2008-06-16
Well it's out of the question in Windows...because Windows can't see the drive when it's connected.

---

### Post by bumanie on 2008-06-16
Put the usb in your girlfriends ubuntu computer > sudo apt-get install gparted Then under System --> Administration you will be able to open the partition editor, which is in fact, gparted. You then should be able to format the usb stick/drive to whatever file system you wish. This needs to be done with the usb device unmounted, which in your case, doesn't seem to be an issue, as it won't mount at all - hopefully it will mount post formatting.

---

### Post by Jimmy9pints on 2008-06-16
But if it's not mounted, Ubuntu (and gparted) cannot see the drive and I therefore can't format it...I think.

---

### Post by ukripper on 2008-06-16
> **Jimmy9pints said:**
> But if it's not mounted, Ubuntu (and gparted) cannot see the drive and I therefore can't format it...I think.

can you plug in the usb and do following in terminal:
```
lsmod | grep usb
```

lets see if it is detected in ubuntu first.

---

### Post by azurepancake on 2008-06-16
> **Jimmy9pints said:**
> But if it's not mounted, Ubuntu (and gparted) cannot see the drive and I therefore can't format it...I think.

From what I remember it is actually the other way around. I recall wanting to format a USB drive back in the day with Gparted and I learned that it can not format a drive that is mounted.

---

### Post by Gannon8 on 2008-06-16
Yes, you cannot format or do any changes relating the partitions or filesystems to any mounted drive. There is a right-click option to unmount it though.

---

### Post by Jimmy9pints on 2008-06-17
OK, it makes sense...thinking about it. Any partition editor waits until you restart to make changes. 

But, when I unmount it the system cannot "see" the USB disk so I can't do anything with it. Even when it's mounted (which I have to force by the way) Gparted cannot see it.

I seem to be going round in circles.

---

### Post by hyper_ch on 2008-06-17
here you have all kinds of install options:  [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by Jimmy9pints on 2008-06-17
OK forget what I said, Ubuntu wasn't mounting the USB drive at all - it was just another partition on the same disk...sorry.

> **ukripper said:**
> can you plug in the usb and do following in terminal:
```
lsmod | grep usb
```

lets see if it is detected in ubuntu first.

ok, this is the output:

```
 lsmod | grep usb
usbcore               169904  4 ndiswrapper,ehci_hcd,ohci_hcd 
```

What does that tell us?

---

### Post by ukripper on 2008-06-25
> **Jimmy9pints said:**
> OK forget what I said, Ubuntu wasn't mounting the USB drive at all - it was just another partition on the same disk...sorry.



ok, this is the output:

```
 lsmod | grep usb
usbcore               169904  4 ndiswrapper,ehci_hcd,ohci_hcd 
```

What does that tell us?

Can post output of the follwoing commands after connecting your usb:

```
cat /var/log/messages | tail
```



```
dmesg | tail
```

> sudo mount

and 

> sudo fdisk -l

it is 'ell' not one

---

