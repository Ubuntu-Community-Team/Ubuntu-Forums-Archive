---
title: "how do you mount or to open up ddrescue .img"
date: 2021-04-15
forum: New to Ubuntu
---

### Post by 007casper on 2021-04-15
how do you mount or to open up ddrescue .img

blo@sky:/mnt$ **sudo mount -o loop /dev/sdc1/drive.img /mnt/1tbdata**
mount: /mnt/1tbdata: failed to setup loop device for /dev/sdc1/drive.imgc.

blo@sky:/mnt$ **sudo mount -o loop '/media/sky/easystore/love-1tb-img/drive.img' /mnt/1tbdata**
NTFS signature is missing.
Failed to mount '/dev/loop12': Invalid argument
The device '/dev/loop12' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

blo@sky:/mnt$ **sudo mount -o loop /dev/sdc1 /mnt/1tbdata**
that mounts the drive but I want to open up the .img file

I have used ddrescue to copy the bad hard drive to an external drive. I would like to open up the .img fle.

Thank you.

---

### Post by TheFu on 2021-04-16
What was the ddrescue/dd/cp command used?  Exactly which device file was the source?
Also, may want to specify the type of file system to be mounted. Don't make it guess. 

If the image wasn't of the exact partition/LV, then you'll need to unpack those and look deeper into the partition/LVM structure.  Use kpartx and fdisk and LVM tools as needed to accomplish that.

---

### Post by 007casper on 2021-04-18
**What was the ddrescue/dd/cp command used? Exactly which device file was the source?**
sudo ddrescue -d -r1 /dev/sdb '/media/sky/easystore/love-1tb-img/drive.img' '/media/sky/easystore/love-1tb-img/drive.log'

I have used the similar ddrescue on 3tb... that one worked without issue. The ddrescue on the terminal said the hard drive was read without errors, I have also done the ddrescue reverse... 

sudo ddrescue -d -r1 -R /dev/sdb '/media/sky/easystore/love-1tb-img/drive.img' '/media/sky/easystore/love-1tb-img/drive.log'

sdb is the source... since the img file didnt work... I rsync the img file to another external drive and tried to mount it from there by right clicking and selecting "Open With Disk Image Mount"

it reads the harddrives name correctly, however cant access the data

Unable to access "dbdrive"

**Error mounting /dev/loop12dp1 at /media/unity/dbdrive: Uknow error when mounting /dev/loop12p1**

I wonder why it isnt mounting, while the other one did with the same method... I didnt specify the type of file system to be mounted.

Looking deeper in the partition/LVM structure... not sure how to go about it. I have used lsblk, and fdisk to make sure I copied the right hard drive completely and not just the partition.

These drives have been sitting for a few years and when I plugged them in they usually have problems. So I am backing up the hard drives as img files.
I removed the external drive and tried it on the other computer. Same problem, same message. On the second computer I checked lsblk

```

zeus@zeus:~$ lsblk
NAME                  MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
loop0                   7:0    0  99.2M  1 loop  /snap/core/10958
loop1                   7:1    0  55.5M  1 loop  /snap/core18/1997
loop2                   7:2    0  55.5M  1 loop  /snap/core18/1988
loop3                   7:3    0  98.4M  1 loop  /snap/fslint-unofficial/19
loop4                   7:4    0   140K  1 loop  /snap/gtk2-common-themes/13
loop5                   7:5    0  98.4M  1 loop  /snap/fslint-unofficial/17
loop6                   7:6    0   219M  1 loop  /snap/gnome-3-34-1804/66
loop7                   7:7    0  64.8M  1 loop  /snap/gtk-common-themes/1514
loop8                   7:8    0    51M  1 loop  /snap/snap-store/518
loop9                   7:9    0  32.3M  1 loop  /snap/snapd/11588
loop10                  7:10   0  31.1M  1 loop  /snap/snapd/11036
loop11                  7:11   0 295.3M  1 loop  /snap/vlc/2103
loop12                  7:12   0 931.5G  1 loop  
&#9492;&#9472;loop12p1            259:0    0 931.3G  1 part  
loop13                  7:13   0   2.7T  1 loop  
&#9492;&#9472;loop13p1            259:1    0   2.7T  1 part  /media/zeus/backup1
sda                     8:0    0 465.8G  0 disk  
&#9500;&#9472;sda1                  8:1    0   512M  0 part  /boot/efi
&#9500;&#9472;sda2                  8:2    0     1K  0 part  
&#9500;&#9472;sda5                  8:5    0   731M  0 part  /boot
&#9492;&#9472;sda6                  8:6    0 464.6G  0 part  
  &#9492;&#9472;sda6_crypt        253:0    0 464.5G  0 crypt 
    &#9500;&#9472;vgubuntu-root   253:1    0 463.6G  0 lvm   /
    &#9492;&#9472;vgubuntu-swap_1 253:2    0   980M  0 lvm   [SWAP]
sdb                     8:16   0   7.3T  0 disk  
&#9492;&#9472;sdb1                  8:17   0   7.3T  0 part  /media/zeus/My Book
sdc                     8:32   0   4.6T  0 disk  
&#9492;&#9472;sdc1                  8:33   0   4.6T  0 part  /media/zeus/easystore

```

loop12                  7:12   0 931.5G  1 loop  
&#9492;&#9472;loop12p1            259:0    0 931.3G  1 part   

??

---

### Post by TheFu on 2021-04-18
/dev/sdb  is the whole drive, not the partition. You cannot mount the whole drive. You'll need to figure out the offsets for each partition that has a file system and mount those.

Please edit your "quote" into "code" tag so the **lsblk** output lines up above.  I can't be certain, but it appears that sda6 is an encrypted container, so you'll need to open that using **cryptsetup** before you can attempt to access the root LV.  I've posted steps for that in these forums, but not with using an imaged file, so you'll need to be very clear which things you want to mount.

Code tags: [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)

BTW, please remove all the loop/snap lines that aren't relevant. They just clutter up the output.

---

### Post by 007casper on 2021-04-18
```

&#9492;&#9472;sda6                  8:6    0 464.6G  0 part  
  &#9492;&#9472;sda6_crypt        253:0    0 464.5G  0 crypt 
    &#9500;&#9472;vgubuntu-root   253:1    0 463.6G  0 lvm   /
    &#9492;&#9472;vgubuntu-swap_1 253:2    0   980M  0 lvm   [SWAP]
```

thats the main drive. I login to the computer without a problem. It mounts during boot.

```

loop12                  7:12   0 931.5G  1 loop  
&#9492;&#9472;loop12p1            259:0    0 931.3G  1 part 
```

1tb drive doesnt mount. It says loop12... 
I have backed up the 3tb the same way to the 8tb drive. The 3tb drive mounts. They are both western digital hard drives.
On 3tb drive I didnt need to offset anything.

The 1tb does come up on the "gui files" app but it just sits there and doesnt show eject icon, so I figure it isnt fully mounted. When I click on it, I get that error. 
**Error mounting /dev/loop12dp1 at /media/unity/dbdrive: Uknow error when mounting /dev/loop12p1**

At least this time around the drive shows up by right clicking on img file and selecting "Open With Disk Image Mount"

how about... I wonder if... I do...
sudo mount -o loop /dev/loop12 /mnt/1tbdata

would that work... I am just making it up and hesitant to go for it... last thing I need more hard drive issues.

Thank you.

---

### Post by TheFu on 2021-04-18
Thanks for the clarity.  I'll ignore sda.

If you backed up the whole drive, not just the partitions that you want, you'll need to use some math or kpartx to figure out where the partition(s) are under loop12p1.

For example, I have a flash drive and don't have any clue what might be on it.  After inserting it, I know it uses sdc for the whole device.
```
sudo kpartx -a /dev/sdc

```will add all the partitions as devices under /dev/mapper/ .... somewhere.

---

### Post by 007casper on 2021-04-18
should I?.... 

```
sudo kpartx -a /dev/loop12 
```  

or just...

```
sudo kpartx -a loop12 
```  

???

---

### Post by TheFu on 2021-04-19
The manpage for that command says:
```
NAME
       kpartx - Create device maps from partition tables.

SYNOPSIS
       kpartx [-a|-d|-u|-l] [-r] [-p] [-f] [-g] [-s] [-v] wholedisk

DESCRIPTION
       This  tool,  derived  from util-linux' partx, reads partition tables on
       specified device  and  create  device  maps  over  partitions  segments
       detected. It is called from hotplug upon device maps creation and dele&#8208;
       tion.
...
```

So it appears that the required "wholedisk" parameter  needs to point at the file which represents the wholedisk. I might get in trouble here, but anyone using these techniques really needs to read the manpages for these commands. There are caveats which should be followed.

---

### Post by 007casper on 2021-04-21
I am not really sure how to go about it. I used ddrescue same way for the 3tb drive and that img seemed to work without a problem.
I get that these are two different drives, different partitions but same manufacturer, western digital.

The 1tb drive is western digital caviar green, and the 3tb drive is western digital red nas hard drive.

It reads the 1tb hard drive name, it just doesnt mount. As far as mapping the drive, it is a little beyond me.

---

### Post by TheFu on 2021-04-21
Did you do what it said in post #6 above?
Did you look in the /dev/mapper/ directory after that?
Show your work if you'd like help. Please.

---

### Post by 007casper on 2021-05-04
```

zeus@zeus:/media/zeus/My Book$ lsblk
NAME                  MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
loop0                   7:0    0   219M  1 loop  /snap/gnome-3-34-1804/66
loop1                   7:1    0  98.4M  1 loop  /snap/fslint-unofficial/17
loop2                   7:2    0  64.8M  1 loop  /snap/gtk-common-themes/1514
loop3                   7:3    0  55.5M  1 loop  /snap/core18/1997
loop4                   7:4    0  55.5M  1 loop  /snap/core18/1988
loop5                   7:5    0  65.1M  1 loop  /snap/gtk-common-themes/1515
loop6                   7:6    0  99.2M  1 loop  /snap/core/10958
loop7                   7:7    0    51M  1 loop  /snap/snap-store/518
loop8                   7:8    0  98.4M  1 loop  /snap/fslint-unofficial/19
loop9                   7:9    0 295.3M  1 loop  /snap/vlc/2103
loop10                  7:10   0  32.3M  1 loop  /snap/snapd/11588
loop11                  7:11   0  31.1M  1 loop  /snap/snapd/11036
loop12                  7:12   0   140K  1 loop  /snap/gtk2-common-themes/13
loop13                  7:13   0 931.5G  1 loop  
&#9492;&#9472;loop13p1            259:0    0 931.5G  1 part  /media/zeus/bckup-disk
loop14                  7:14   0 931.5G  1 loop  
&#9492;&#9472;loop14p1            259:1    0 931.3G  1 part  
sda                     8:0    0 465.8G  0 disk  
&#9500;&#9472;sda1                  8:1    0   512M  0 part  /boot/efi
&#9500;&#9472;sda2                  8:2    0     1K  0 part  
&#9500;&#9472;sda5                  8:5    0   731M  0 part  /boot
&#9492;&#9472;sda6                  8:6    0 464.6G  0 part  
  &#9492;&#9472;sda6_crypt        253:0    0 464.5G  0 crypt 
    &#9500;&#9472;vgubuntu-root   253:1    0 463.6G  0 lvm   /
    &#9492;&#9472;vgubuntu-swap_1 253:2    0   980M  0 lvm   [SWAP]
sdb                     8:16   0   4.6T  0 disk  
&#9492;&#9472;sdb1                  8:17   0   4.6T  0 part  /media/zeus/easystore
sdc                     8:32   0   7.3T  0 disk  
&#9492;&#9472;sdc1                  8:33   0   7.3T  0 part  /media/zeus/My Book



sudo kpartx -a /dev/loop14p1
device-mapper: reload ioctl on loop14p1p4  failed: Invalid argument
create/reload failed on loop14p1p4


zeus@zeus:/media/unity/My Book$ cd /dev/mapper
zeus@zeus:/dev/mapper$ ls -al
total 0
drwxr-xr-x  2 root root     160 May  3 22:40 .
drwxr-xr-x 22 root root    5040 May  3 22:40 ..
crw-------  1 root root 10, 236 May  3 13:02 control
lrwxrwxrwx  1 root root       7 May  3 22:40 loop14p1p1 -> ../dm-3
lrwxrwxrwx  1 root root       7 May  3 22:40 loop14p1p2 -> ../dm-4
lrwxrwxrwx  1 root root       7 May  3 13:02 sda6_crypt -> ../dm-0
lrwxrwxrwx  1 root root       7 May  3 13:02 vgubuntu-root -> ../dm-1
lrwxrwxrwx  1 root root       7 May  3 13:02 vgubuntu-swap_1 -> ../dm-2


```

so easystore external hard drive has an image disk that is rescued by ddrescue. That one mounts to loop13.

Then, I tried to mount another image disk that has been rescued by ddrescue. As mentioned before, it still gives me issues. However, it still reads the hard drive name. But when clicked on it, pop up show up with an error like the last time.

**Error mounting /dev/loop14p1 at /media/unity/dbdrive: Uknow error when mounting /dev/loop14p1**

---

### Post by 007casper on 2021-05-11
bump. 

Please, help. Thank you.

---

