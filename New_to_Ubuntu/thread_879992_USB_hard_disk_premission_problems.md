---
title: "USB hard disk premission problems"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by fred_miller on 2008-08-04
I have a couple USB2 hard drives and am running 8.04.  I can not save/move files to or from the usb drives.  A box opens saying I do not have permission.  I even tried making the whole drives empty space and formatting them with ext2 and ext3 using gparted in Ubuntu and I still get the message I don't have permission.    A usb stick works fine as does a USB dvd burner, printer, and scanner.  I can boot knoppix live and access the drives fine, that's how I am using them now, shut down, boot knoppix, move file to onboard hdd or to USB drive, reboot ubuntu, do my thing, shut down and reboot knoppix, Im getting sick of this.  I also tried opening a terminal and typing sudo su and logging in with the same results.  They do automount and I can open files from them, I just cant save, move, or copy to them as I don't have permission.  My system is up to date.

I also have a USB drive formatted NTFS and it works fine, but it seems... ignorant to have to use NTFS to save data?

---

### Post by bodhi.zazen on 2008-08-04
Add an entry in fstab for your external hard drive.

```
UUID=xxx.yyy.zzz  /media/USB  ext3  noauto,users  0  0
```

Change UUID to the device UUID, "/media/USB" to the mount point

Mount the driver and change permissions :

```
# You may not need to do this first step
sudo mkidr /media/USB

mount /media/USB

sudo chown user.users /meida/USB
sudo chmod 770 /media/USB
```

Change "user" to your log in name (leave "users" as is).

---

### Post by fred_miller on 2008-08-04
What is fstab?
How would one know the UUID?
I have more than 1 usb HDD that i use, do i need to do this every time I want to plug one or another in?
Why does another linux distro work and ubuntu have this issue?

---

### Post by bodhi.zazen on 2008-08-04
> **fred_miller said:**
> What is fstab?

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

> How would one know the UUID?

Use ```
sudo blkid
```[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

> I have more than 1 usb HDD that i use, do i need to do this every time I want to plug one or another in?Probably yes. In general this *should* be a one time configuration though.

> Why does another linux distro work and ubuntu have this issue?I have no idea why. I have seen it posted that FAT and NTFS file system are auto mounted flawlessly, but linux native systems are not, go figure.

---

### Post by fred_miller on 2008-08-04
Thanks for the info.  I saved it an will read it later and see if i can get it working.  I was hoping it was just a simple configuration issue and I could type in a simple incantation and it all start working.  If I can't get it going it's good to know it just isn't my silly box and I can always reformat them all to NTFS and use them that way even if it it a really bone chilling way of doing it.  Still faster than live booting to move files. Later I can save up get a 500 GB drive and forget it i guess. :)

---

### Post by coffeecat on 2008-08-04
> **bodhi.zazen said:**
> I have no idea why. I have seen it posted that FAT and NTFS file system are auto mounted flawlessly, but linux native systems are not, go figure.

It's extraordinary, isn't it? Every distro I've used that automounts USB drives, automounts ext3 formatted ones with root-only access. Surely it's not beyond the wit of the devs to configure udev, hal or whatever needs configuring to mount ext3 drives for the logged-in ordinary user? Whatever - but I'm afraid it's far beyond my wit. :( Which is why I use fat32 and NTFS on my external drives.

**fred_miller**, if you really want to use ext2/ext3 on your usb drives, there is another way. Let the drive be automounted and, as root (using sudo) create a folder - call it what you will. Now:

```
sudo chown yourusername: /media/mountpoint/foldername
```Note the colon after yourusername. Replace /media/mountpoint with whatever mountpoint the USB drive is mounted to. The advantage of this is that this is a one-time only operation and you don't have to bother with fstab. The root of the drive will still be owned by root, but whenever you remount the drive the folder you've created and chowned will still be owned by you and you can save into it, create subfolders in it and delete files in it.

---

### Post by fred_miller on 2008-08-05
Ok, I read what coffecat posted and that looked easier, but I hate typing in a terminal, so i booted knoppix and created a folder on the usb drive, i then dragged all my files into it.  I then rt clicked on properties and allowed full access to all users to the folder and everything in it.  I then rebooted ubuntu and all is well.  thanks guys

---

### Post by bodhi.zazen on 2008-08-05
> **fred_miller said:**
> Ok, I read what coffecat posted and that looked easier, but I hate typing in a terminal, so i booted knoppix and created a folder on the usb drive, i then dragged all my files into it.  I then rt clicked on properties and allowed full access to all users to the folder and everything in it.  I then rebooted ubuntu and all is well.  thanks guys


LOL

Next time you might enjoy running :

```
gksu nautilus
``` in Ubuntu. This will allow you to run nautilus as root, and thus change ownership and permissions from a graphical interface.

---

