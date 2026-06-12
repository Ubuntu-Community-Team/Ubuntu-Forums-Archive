---
title: "Second HDD won't work."
date: 2008-04-26
forum: New to Ubuntu
---

### Post by JustStep25 on 2008-04-26
I usually have a 320GB NTFS second HDD for storage and that works fine. My dad wanted me to backup his VERY old business data from his FAT16 HDD. I turned off the computer and switched the two HDDs, but now when I go to sdb1 all I get is an empty folder.

---

### Post by frup on 2008-04-26
Did you make sure the jumpers are correct? (probably if grub didn't go crazy :p)

You might need to remount the drive, if the ntfs drive was in your fstab it is trying to mount the drive as ntfs instead of fat16. have a look at /etc/fstab and look for sdb1.

to check where/how the fat 16 drive is located type sudo fdisk -l and look for it on the list, possibly it's not sdb1 anymore anyway and you need to mount it some otherway.

---

### Post by JustStep25 on 2008-04-26
You're right the second HDD is listed as the other NTFS in the fstab. How do I fix this?

---

### Post by frup on 2008-04-26
Well the easiest way would be to comment out the second hdd in fstab (using gksudo gedit /etc/fstab) and then rebooting. When you reboot it won't try to load the wrong FS/drive.

you may need to manually mount the drive after rebooting. maybe copy fstab first to back it up so that if you do something wrong, nothing is permanently broken 

type sudo cp /etc/fstab /etc/fstab.backup in terminal first then.

---

### Post by JustStep25 on 2008-04-26
Ok it looks like a made a huge mistake and read your advice wrong. Instead of commending out the second HDD I moved the fstab file to the desktop. Now when I boot it can't find it and in the recovery mode when I try to move it back I get an error saying "Read-only file system" even if I try to sudo.

---

### Post by frup on 2008-04-26
Use a liveCD. Mount the main drive and place it back.

---

### Post by JustStep25 on 2008-04-26
The only livecd I have is a Kubuntu one, so I tried to mount on that but I got an error saying "hal-storage-fixed-mount refused uid 999"

---

### Post by frup on 2008-04-26
try mounting the drive manually (I googled this what I got)

sudo mount -t ext3 /dev/sda1 /media/sda1

---

### Post by JustStep25 on 2008-04-26
I got an error saying "mount: mount point /media/sda1 does not exist"

When I just tried sudo mount /dev/sda1 I got "can't find /dev/sda1 in /etc/fstab or /etc/mtab"

---

### Post by frup on 2008-04-26
Well what is your main partition? The one ubuntu was installed on?

another sudo fdisk -l can help you again. Maybe post it on here if you want.

---

### Post by JustStep25 on 2008-04-26
The main partition is /dev/sda1 and I can see it in fdisk -l, so I don't know why I can't mount it.

---

### Post by frup on 2008-04-26
it's not already mounted is it?

---

### Post by JustStep25 on 2008-04-26
I can't access it so I don't think so. Sorry for the inconvenience I'm causing you. It seems like a simple little thing but I don't know why it won't just let me mount it and move the file back.

---

### Post by frup on 2008-04-26
So you see nothing in the places menu > computer that represents a mounted drive? Strikes me as rather odd and probably reaching the limit of my ability to give you much more help sorry. If you can get that fstab back in it's right place, everything should work fine.

---

### Post by JustStep25 on 2008-04-26
ok I figured it out. I had to do "mkdir /media/sda1" then I could mount it. It was cake from there. I got the second HDD working too. Thanks a lot for the help.

---

### Post by frup on 2008-04-26
ok in the live CD terminal type

sudo unmount -A and manually remount the drive via the terminal with the commands I gave before.


I don't use KDE but as far as I can tell this a kde error. This is your ubuntu drive isn't it? not an NTFS drive? All the bits I find on google seem to be related to NTFS drives not ext3

---

