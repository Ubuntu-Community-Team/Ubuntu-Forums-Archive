---
title: "Need to format my external hard drive without access to the GUI"
date: 2018-09-03
forum: New to Ubuntu
---

### Post by trent65 on 2018-09-03
So, without getting too much into it, I'm stuck in a login loop after I updated to 18.04. My research has led me to believe this is due to an old BIOS version. That's not the problem. I'm pretty sure I know how to update that. My problem is that I need to backup my home directory before I update my BIOS and then do a clean reinstall of 18.04. 

I went out and bought an external hard drive. It's a WD 2TB (My Passport) external Hard drive ([https://www.amazon.com/Black-Passport-Portable-External-Drive/dp/B01LQQHF2W](https://www.amazon.com/Black-Passport-Portable-External-Drive/dp/B01LQQHF2W)). When I plug it into the USB port, I immediately get an error. So I killed that process and mounted it to /media/$USER/external. Then I backed up my home directory using tar, creating the file: 'backup.tgz'. When I tried to move the file to the mounted folder, I got an Input/output error. Then I just navigated to the folder (/media/$USER/external) and tried to run just a mkdir command. I got the same input/output error.

So, now I'm trying to format the external hard drive to remove anything that is expecting Windows or OSX. I tried following this tutorial: [https://ubuntuforums.org/showthread.php?t=1220077](https://ubuntuforums.org/showthread.php?t=1220077), but it has some GUI implementation and I don't have access to the GUI, I only have tty. Any advice as to how I can replicate **System > Administration > Partition Editor** and then the following deletion commands via the command line? Or honestly, I'm just looking to see if I am on the right track here. How would you handle this? Does anyone have experience with these EHDs and have some advice as it pertains to Ubuntu?

Any help would be appreciated!
Thanks for looking!

System specs:
[COLOR=#1A1A1A][FONT=&quot]AMD Ryzen 5 1600 3.2 ghz processor[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]Radeon RX 570 4GB Video Card[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]ASRock AB350 Pro4 ATX Motherboard[/FONT][/COLOR]

---

### Post by oldfred on 2018-09-03
With external attached & mounted run this:

sudo parted -l

Note it says with Mac you have to reformat. It has Windows compatible format that may work, but not best if you are just using Ubuntu.

---

### Post by trent65 on 2018-09-04
Thanks for replying!

running parted -l I got: (I'm transcribing because I can't copy/past as I can't get into a browser on my Ubuntu machine right now):
Model: WD My Passport 25E1 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt:
Disk Flags:
Number | Start | End           Size | File system | Name | Flags
1 | 1049KB | 2000GB | 2000GB | ntfs | My Passport | msftdata

---

### Post by Dennis N on 2018-09-04
> Any advice as to how I can replicate System > Administration > Partition Editor and then the following deletion commands via the command line?

I would just format the existing partition sdb1 as ext4. I don't see the need to delete and recreate. You don't need a partition editor for this: 
```
sudo mkfs.ext4 /dev/sdb1
```
should do it.

---

### Post by trent65 on 2018-09-04
Great. Thanks Dennis! I'll give that a try when I get off work today.

---

### Post by oldfred on 2018-09-04
When you make it ext4, you also have to give yourself ownership & permissions to use it.
NTFS does not have ownership nor permissions and that is part of why Linux is safer.

I like to give labels to partitions I do not permanently mount, so when I mount with Nautilus I know what they are.
I often use Disks, gparted or command line for labels. And now gpt partitions have two labels, one for partition and one inside gpt. Disks shows both with gpt, so I mostly use that if partition already exists.
       
   e2label <dev> <label>
  tune2fs -L <label> <dev> 
    sudo e2label /dev/sda4 bionic 

This shows Disks screen
[https://askubuntu.com/questions/147319/how-can-i-give-other-drives-and-partitions-short-meaningful-names-in-nautilus](https://askubuntu.com/questions/147319/how-can-i-give-other-drives-and-partitions-short-meaningful-names-in-nautilus)

Label becomes a default mount point if using Nautilus to automount. But  I have used command line to mount also. And mixed up, I labeled partition data, but mounted as Data. Those are not the same.

      
 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points, my example is making a mount point of /mnt/data. Default mount with Nautilus will be /media/$USER/label
If labeled & mounted, this will show it.
mount
this was an automount of my backup partition on sdc drive labeled backup_c, but I in my backup script assume unmounted and mount in script at /mnt/backup_c, must not be mounted or my script will not work.
/dev/sdc4 on /media/fred/backup_c type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)

# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data
[http://askubuntu.com/questions/324705/first-full-backup-on-usb-permission-denied/324942#324942](http://askubuntu.com/questions/324705/first-full-backup-on-usb-permission-denied/324942#324942)

---

### Post by trent65 on 2018-09-06
Got there! Thank you oldfred and Dennis N! oldfred, I have a lot to learn about everything you posted. I'll be sure to read up!
Thanks again!

---

