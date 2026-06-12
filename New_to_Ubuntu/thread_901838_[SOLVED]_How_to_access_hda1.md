---
title: "[SOLVED] How to access hda1"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by BA Dawg on 2008-08-26
I used Gparted to partition and formated (ext3) my HD which became hda2. I then installed ubuntu on that partition. I am duel booting with Linspire on hda1. I ran Gparted liveCD and know that hda1 is formatted reiserf. I would like to have access to my files on hda1. Is there a way to do that?
 Even though I have used Linspire for a few years I am still a little unsure of myself in terminal never had to use it a lot so treat me like a newbie. 

John

---

### Post by eightmillion on 2008-08-26
I'm not sure why no one responded. This should be relatively easy. Just create a directory to mount that partition to and mount it like this:
```

mkdir ~/linspire
sudo mount -t reiserfs /dev/hda1 ~/linspire

```

---

### Post by nicedude on 2008-08-26
If you wanted it to be available on every boot then you could always mount it and then check your mstab file and copy last line to your fstab file so that it gets done on every reboot as well.

sudo gedit /etc/mtab

and copy last line ( assuming you just mounted it )

then copy that line to the end of fstab

sudo gedit /etc/fstab


Mtab is like what is mounted now & Fstab is like what will be mounted on bootup FYI



PS Hi Bubbles how are your kitties

---

### Post by BA Dawg on 2008-08-27
> **eightmillion said:**
> 
```

mkdir ~/linspire
sudo mount -t reiserfs /dev/hda1 ~/linspire

```

When I try to mount hda1 I get

mount: special device /dev/hda1 does not exist

John

---

### Post by phidia on 2008-08-27
Please post the output of "sudo fdisk -l".

---

### Post by eightmillion on 2008-08-27
Sorry, try:
> sudo mount -t reiserfs /dev/hda2 ~/linspire

---

### Post by mcduck on 2008-08-28
Are you sure about the disk being /dev/hda? Because we are now using SATA/SCSI drivers for PATA disks as well, and the disk is most likely know as /dev/sda in Ubuntu (so the parttiion you want to mount would be /dev/sda1 instead of /dev/hda1)..

Check that with "sudo fdisk -l"

---

### Post by BA Dawg on 2008-08-28
> **mcduck said:**
> Are you sure about the disk being /dev/hda? Because we are now using SATA/SCSI drivers for PATA disks as well, and the disk is most likely know as /dev/sda in Ubuntu (so the parttiion you want to mount would be /dev/sda1 instead of /dev/hda1)..

Check that with "sudo fdisk -l"

mcduck
 I did a "sudo fdisk -l" and all drives show up as sda__.  So I mounted sda1 instead of hda1 and it worked perfectly all of the files are available 
Thanks to all that helped

John :D

---

