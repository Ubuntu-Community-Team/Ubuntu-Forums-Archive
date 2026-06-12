---
title: "ubuntu 11.04 - USB memory stick"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by UbunGax on 2011-09-27
Evening,

I have just installed Ubuntu and put in my USB memory stick into the USB slot, but nothings happened.

How do I browse to it?  I thought it would be in Media, but it isn't - would really appreciate a pointer to it.

thanks in advance

---

### Post by seawolf167 on 2011-09-27
Is it under /mnt? Has a link been created on your desktop? Assuming it is formatted, if you type in 

```
mount
```you can see if it is mounted or not, if it is not mounted, you can manually [mount ]("https://help.ubuntu.com/community/Mount")it

```
sudo mkdir /media/my_flash_drive
sudo mount /dev/sda /media/my_flash_drive
```where you should change /dev/sda to reflect the flash drive's location and /media/my_flash_drive to reflect the directory you want it mounted it

---

### Post by UbunGax on 2011-09-27
Thanks, that's superb.  One quick question.  

By typing in Mount, did that make the flash drive 'appear' in the media folder?

Cheers

---

### Post by seawolf167 on 2011-09-27
I don't think it would - typing *mount* with no options simply lists mounted devices

```
man mount
```though it could have already been there by UUID perhaps?

---

### Post by Paqman on 2011-09-27
> **seawolf167 said:**
> I don't think it would - typing *mount* with no options simply lists mounted devices


Indeed it would.
```
sudo mount -a
```
Is what you need to mount everything that can be mounted.

---

### Post by seawolf167 on 2011-09-27
> **Paqman said:**
> Indeed it would.Wait - it would mount everything or wouldn't? I know the '-a' switch attempts to mount everything in /etc/fstab, but I'm unclear on your phrasing

---

