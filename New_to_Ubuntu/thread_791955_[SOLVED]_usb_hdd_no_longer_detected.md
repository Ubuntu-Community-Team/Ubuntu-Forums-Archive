---
title: "[SOLVED] usb hdd no longer detected"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by shillizzle on 2008-05-12
I have a cavalry 500gig usb hdd that came pre-formatted in ntfs and would auto-mount every time i plugged it in. i need it to be fat32 to be recognized on my ps3. I didnt know how to do it with linux, so i used windows (virtualbox) but there was a read/write error while formatting, (using a prog called swissknife) and now my ubuntu doesnt even detect it when plugged in, which i understand because in windows when i go to my computer and click on the drive it says "the drive is not formatted, do you want to format it now,...the drive cannot be formatted." I hope i can get it to format somehow as it would be an expensive paper weight :)  Im new to linux and only have a basic understanding of the terminal and using scripts, any help would be greatly appreciated. If i didnt explain things well, please feel free to tell me what info you need.
Thanks.

---

### Post by tamoneya on 2008-05-12
go into terminal and type```
sudo fdisk -l
```
That is a lowercase "L" not an "I".  You can copy and paste the result from terminal to here by using ctrl-alt-c in terminal to copy

---

### Post by shillizzle on 2008-05-12
this is what i get. I have the usb hdd plugged in.

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45c7f99c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

---

### Post by tamoneya on 2008-05-12
hmm according to that the device isnt even connected to your system.  Lets move back a step.  What do you get when you type:```
lsusb
```

---

### Post by shillizzle on 2008-05-12
shillizzle@ubuntu-Laptop:~$ lsusb
Bus 003 Device 003: ID 04fc:0c25 Sunplus Technology Co., Ltd 
Bus 003 Device 002: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000

i know that the Sunplus Tech is the usb hdd. it shows up here at least. but arrgghh i have to to work for a few hrs, ill check back in a while and seee what you think i can do next. Thanks soo much for helping me so far. 
*cheers*

I tried rebooting with the usb plugged in and i still cant get ubuntu to detect the usb drive, I really hope I can get this sorted out.

---

### Post by shillizzle on 2008-05-12
if i can see my usb hdd in lsusb, does that mean that i should be able to mount it manually in the terminal, and if yes, what is the command to do that?

---

### Post by shillizzle on 2008-05-12
I used a program in windows called "testdisk" and it came up that it had been changed to fat32 but it has bad boot sectors. so im guessing that its corrupted and thats why its not mounting. any suggestions as to a way to repair the hdd?? any terminal commands or even windows apps that might help?

---

### Post by inportb on 2008-05-12
> **shillizzle said:**
> i need it to be fat32 to be recognized on my ps3. I didnt know how to do it with linux, so i used windows (virtualbox)

See if mkfs.vfat does what you need. After formatting, run fsck.vfat on it.

---

### Post by shillizzle on 2008-05-12
im lost, this is the output, 
shillizzle@ubuntu-Laptop:~$ sudo mkfs.vfat
[sudo] password for shillizzle: 
mkfs.vfat 2.11 (12 Mar 2005)
No device specified!
Usage: mkdosfs [-A] [-c] [-C] [-v] [-I] [-l bad-block-file] [-b backup-boot-sector]
       [-m boot-msg-file] [-n volume-name] [-i volume-id]
       [-s sectors-per-cluster] [-S logical-sector-size] [-f number-of-FATs]
       [-h hidden-sectors] [-F fat-size] [-r root-dir-entries] [-R reserved-sectors]
       /dev/name [blocks]
i was just guessing that i should be root. im wayyyy over my head i guess.

---

### Post by tamoneya on 2008-05-12
here is the thing.  The device was supposed to show up in sudo fdisk -l.  Once it does you can then mount it but until we can get it there we cant read anything.  That is why we then took a step backward to see if it was actually detected by the system which it is.  There must be some sort of driver error.  Can you try a restart or something and then post ```
sudo fdisk -l
``` again.

---

### Post by shillizzle on 2008-05-13
shillizzle@ubuntu-Laptop:~$ sudo fdisk -l
[sudo] password for shillizzle: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45c7f99c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31164c10

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    c  W95 FAT32 (LBA)


ummmm i think this a good thing, but hey im not getting too excited yet, lol

---

### Post by sam_delta on 2008-05-13
try formating it

sudo mkfs.vfat -F 16 /dev/sdb1

replace the "16" with a "32" if you prefer fat32 instead of fat16

sam

---

### Post by tamoneya on 2008-05-13
yes this is good.  Notice how /dev/sdb has now shown up.  This is your harddrive.  Type sudo gparted.  In gparted you should format and partition /dev/sdb.  If you want to share this with windows you should probably make it a FAT32 partition. This can be selected in the pull down box located in the upper right.  Once it is formatted run the following command:```
sudo mkdir /externaldrive
sudo mount /dev/sdb1 /externaldrive
```

---

### Post by shillizzle on 2008-05-13
Thank you soooooo much Tamoneya, too bad i can only thank you once!, i can see it and access it, but one small question, how come i cant unmount it in the "right-click" menu?? how can i safely remove it from the laptop??
Thanks again, you are awesome.


thats weird, i tried to unmount again and this time it worked,, oh well, hehe, now how do i make this thread [solved]??

nm got it.lol

---

### Post by tamoneya on 2008-05-13
umounting:```
sudo umount /dev/sdb1
``` In order to get it to automount add the following line to /etc/fstab```
/dev/sdb1 /externaldrive vfat defaults 0 0
```

---

