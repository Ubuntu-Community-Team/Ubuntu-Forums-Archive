---
title: "HOWTO: Install Hardy 8.04 without a CD-ROM, from an .iso file with Grub"
date: 2008-05-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Kidaf on 2008-05-05
* Tuto heavily based on [john_spiral one]("http://ubuntuforums.org/showthread.php?t=316093"), that did not work for Hardy 8.04


Howdy,

My debut will be with this simple adapt from john_spiral's tuto to fit Hardy 8.04 install, within the same idea he had back there. This is the link to his original tutorial: [http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)


**_Things you'll Need:_**


**1)**  Ubuntu Hardy Heron (8.04) ALTERNATE .iso (see below)

**2)**  At least 2 partitions on your HD

**3)**  vmlinuz & initrd.gz files from Hardy - NOT the ones included on the .iso (see below)




**_Steps:_**



**1)**  Download the **ALTERNATE** .iso from the Ubuntu download site:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

**REMEMBER**: mark the "*Check here if you need the alternate desktop CD.*" option, at the botton.


**2)**  Download both **vmlinuz** & **initrd.gz** files, Hardy's version, from this site:

[http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/)


**3)**  Create an /boot folder on your secondary HD partition, and move the alternate .iso and the vmlinuz & initrd.gz from step (2) onto it.


**4)**  If you don't have Grub already installed, install it on a removable media or Hard Disk. Then, edit your /boot/grub/menu.lst and add the following entry:

```
title Install Ubuntu Hardy
root (hd0,2)
kernel /boot/vmlinuz vga=normal ramdisk_size=149720 root=/dev/rd/0 rw --
initrd /boot/initrd.gz
```


Where, here I quote john_spiral: 
> **(hd0,2) refers to the 1st hard drive 'hd0' and the 3rd partition '2'.

The counting of partitions and hard drives starts at zero. Linux loves making life complicated

Change (hd0,2) to match the drive and partition of your .iso file.

e.g (hd1,3) Refers to drive 2 and partition 4.


**5)**  OK! You are ready to go! Now reboot your system (with the removeable media if you installed Grub on it) and choose the "Install Ubuntu Hardy" entry.


**6)**  Now follow the installation as usual, which should be working as if the disk was in the CD-ROM tray.


Any trouble, I may try to help! Just leave a post!


**Thanks** to **Kacike**, and to **john_spiral**, whose tuto helped me install Gutsy and heavily based this one.

---

### Post by john_spiral on 2008-05-16
Looking good!

I'll keep my eye on this thread to see if I can lend a hand.

John

---

### Post by Kidaf on 2008-05-19
Again, thanks john_spiral. I just hope this tuto helps those orphans of your tuto, that won't work quite right on installing Hardy.

---

### Post by ulinthetechmage on 2008-06-12
will this work with the regular desktop iso file?

---

### Post by Kidaf on 2008-06-12
I don't think so. I didn't try, though, but if you have already downloaded the LiveCD, you can try it. Else, just download the alternate one, as explained on the tuto, and use it. =)

If you have any success with the LiveCD or any trouble with the alternate, feedback. =)

---

### Post by john_spiral on 2008-06-14
> **ulinthetechmage said:**
> will this work with the regular desktop iso file?

Hi ulinthetechmage,

if the .iso file is a bootable image of an operating system it's got a good chance it will work.

---

### Post by Deadlocked on 2008-09-16
Im pretty sure from reading other threads that only the alternate iso works.

But i have a problem.

When installing I get 

Error while running 'modprobe -v yenta_socket' 
Googling gives me something about the pcmia.. 

Continuing the install seems ok but im not sure about the partitioning.

This is due to only getting the console when install is finished and am unable to find the orginal iso.


Any ideas?

---

### Post by john_spiral on 2008-09-16
> **Deadlocked said:**
> Im pretty sure from reading other threads that only the alternate iso works.

But i have a problem.

When installing I get 

Error while running 'modprobe -v yenta_socket' 
Googling gives me something about the pcmia.. 

Continuing the install seems ok but im not sure about the partitioning.

This is due to only getting the console when install is finished and am unable to find the orginal iso.


Any ideas?

Hi deadlocked,

did you use the alt .iso file?

---

### Post by Deadlocked on 2008-09-16
I did.


But after starting from scratch im stuck in console mode.

Im really not familer with it so i cant seem to find the orginal iso.

im trying to follow these posts

[http://ubuntuforums.org/showthread.php?t=316093&page=13](http://ubuntuforums.org/showthread.php?t=316093&page=13)

Cheers for help.

Basically I followed guide.

When i restart and expect normal gui i get console mode.

This happens everytime i try installing ubuntu. 

Since i have no expierence with the ubuntu console im stuck. :(

all help is appreciated.

---

### Post by john_spiral on 2008-09-16
if you have access to a floppy/floppy drive try booting off the full fat ubuntu .iso file using this technique:

[http://ubuntuforums.org/showthread.php?t=666267](http://ubuntuforums.org/showthread.php?t=666267)

---

### Post by Deadlocked on 2008-09-16
No the reason i used that method is because i dont have a floppy nor a cd drive.

Whats the commands to look for orignal iso and mount that?

---

### Post by john_spiral on 2008-09-17
did you check the md5sum of the .iso file before proceeding with the install?

If you have windows running on the machine you might consider the Wubi installer (install Ubuntu from within Windows):

[http://wubi-installer.org/](http://wubi-installer.org/)

come back to us.

John

---

### Post by Deadlocked on 2008-09-17
yes i did.

nope the drive has been formatted, partitioned etc.

I just have a 2.5 to usb connector.

---

### Post by john_spiral on 2008-09-17
> **Deadlocked said:**
> yes i did.

nope the drive has been formatted, partitioned etc.

I just have a 2.5 to usb connector.

Deadlocked,

Do you have access to another Linux or Windows machine?

Can your machine boot off a USB drive?

If yes to both of the above, it might be possible to boot off an external USB drive, having it run like the live Ubuntu CD.

Once booted, run the Ubuntu installer.

---

### Post by Deadlocked on 2008-09-17
I have access to a machine with windows.

But my laptop does not does not have a usb boot option.

Basically this is my only option.

I think it can pick up my isb drive once the console has loaded up. 

I just need to no how to look through other partitions and drives so I can try this

> sudo mount -o loop cd.iso /mnt/image
sudo rm /cdrom
sudo ln -s /mnt/image /cdrom
sudo apt-cdrom -m add

---

### Post by john_spiral on 2008-09-18
> **Deadlocked said:**
> I have access to a machine with windows.

But my laptop does not does not have a usb boot option.

Basically this is my only option.

I think it can pick up my isb drive once the console has loaded up. 

I just need to no how to look through other partitions and drives so I can try this

You will need to use the "sudo fdisk -l" command to list all the partitions/drives attached to the machine. 

Then use the 'mount' command to mount the partition with the .iso file. You might need to create a directory as a mount point below /mnt.

Read the following doc:

[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

Once the partition with the .iso file is mounted you can proceed with:

> sudo mount -o loop cd.iso /mnt/image
sudo rm /cdrom
sudo ln -s /mnt/image /cdrom
sudo apt-cdrom -m add

In the above command you will need to specify the path to the cd.iso file.

hope this helps

---

