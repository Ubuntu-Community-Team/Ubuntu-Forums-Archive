---
title: "boot problem with usb hardrive"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-30
if i boot with the drive plugged in i cant boot into ubuntu on my main drive,it shows it but i get an error when i choose it,i can only boot into my main drive with the usb drive unplugged wich is fine but i would like it to boot correctly.
rick

---

### Post by rixtr66 on 2008-07-30
please somebody help me with this
rick

---

### Post by neurostu on 2008-07-30
What is on your usb drive?

where does booting fail when your drive is plugged in?

You can try editing the boot order of your devices in your bios and placing USB below your HDD

---

### Post by cdtech on 2008-07-30
Thats because your using the GRUB Bootloader from your USB drive, which is listing the wrong devices within the menu.lst.

You need to plug your USB drive in and at a command line reinstall GRUB using your primary drive or which ever you choose to be the boot device and install the GRUB Bootloader on that one.

---

### Post by rixtr66 on 2008-07-31
on the usb drive is ubuntu studio,when i boot with the usb drive plugged in it shows both partitions but when i click on the primary drive i get
error 11,i reinstalled grub and now i have to use the disk to get in
i screwed up i really dont know what im doing,how do i reinstall from the
command line? and what is the right way to set it up for both drives?
rick

---

### Post by rixtr66 on 2008-07-31
i really need some help with this,please??????
rick:confused:

---

### Post by gn2 on 2008-07-31
> **rixtr66 said:**
> i really need some help with this,please??????
rick:confused:

See your other thread....
[http://ubuntuforums.org/showthread.php?t=876003](http://ubuntuforums.org/showthread.php?t=876003)

---

### Post by bobnutfield on 2008-07-31
If you will boot into your main system, then plug in the USB drive, open a terminal and type:

> fdisk -l

and post the results

The post the contents of you /boot/grub/menu.lst file.  I *MAY* be able to give you an entry to add/change in your menu.lst that *MAY* get it booting.  In all liklihood, the UUID of the disks have been misread by grub.

---

### Post by rixtr66 on 2008-07-31
rick@ubuntu-studio:~$ sudo fdisk -l 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d8a1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29648   238147528+  83  Linux
/dev/sdb2           29649       30401     6048472+   5  Extended
/dev/sdb5           29649       30401     6048441   82  Linux swap / Solaris
rick@ubuntu-studio:~$

---

### Post by rixtr66 on 2008-07-31
ok ive tried super grub and gparted,and still have the same problem.
ive also searched around and found solutions to older os's
im stumped!!!!!s.o.s
rick:confused:

---

### Post by cdtech on 2008-07-31
You need to check your boot order within your bios. It sounds like you have the USB device to boot first if it's present. Change the boot order so that your primary drive boots first and nothing before it.

Hope this helps........

---

### Post by rixtr66 on 2008-07-31
ok i changed the boot order and now i cant access the usb drive.
im trying to enable usb support by editing the etc/mkinitramfs/modules
with vim but even as root it wont let me save the file so now im stuck again.anyone got any ideas????
rick:confused:

---

### Post by rixtr66 on 2008-08-01
ive done some editing and reinstalled ubuntu studio to the usb drive.
when it came time to install the final grub bootloader i said no to 
have it go to the mbr and installed it to /dev/sdb1.
so now when i boot both partitions show up but i get a disk error 
message.im getting closer but something is missing,and i could use some help.so please give me a hand with this.
rick:confused:

---

