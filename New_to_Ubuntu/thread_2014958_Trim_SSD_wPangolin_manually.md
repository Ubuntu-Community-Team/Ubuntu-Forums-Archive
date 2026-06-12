---
title: "Trim SSD w/Pangolin manually"
date: 2012-07-02
forum: New to Ubuntu
---

### Post by Deskjockey on 2012-07-02
I put 12.04 on a x25-m SSD. I  read tips a tricks the past few days and will do the manual Trim method. I removed a swap partition using Parted Magic (w/donation).  The only other trick so far is using a ram disk. 

I'm not sure how best to do the Trim and I'm not sure if I have a problem seeing my fdisk and fstab show different partitions and then hdpram shows yet a third variation. The good news is everything so far works fine.  
 
 fdisk:
 Device         Boot                   Start                   End      Blocks     Id   System 
 /dev/sda1   *        2048           56000511         27999232     83    Linux 
 /dev/sda2        56002558     206049279      75023361      5      Extended 
 /dev/sda5        64002048     206049279      71023616      83     Linux 
 

 etc/fstab:
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 proc                  /proc              proc                     nodev,noexec,nosuid 0       0 
 tmpfs              /tmp              tmpfs                nodev,nosuid,noatime,mode=1777             0       0 
 # / was on /dev/sda1 during installation 
 UUID=2f4166ed-9e1e-4ea0-802f-f6d435bc3f7e   /                            ext4       noatime,errors=remount-ro   0 1 
 # /home was on /dev/sda6 during installation 
 UUID=b6e59f89-322b-47aa-9707-d94a42f01128  /home              ext4        defaults,noatime         0       2 
 # swap was on /dev/sda5 during installation 
 UUID=fdae0f97-586d-4fec-af79-0cafce6fdb6b      none                  swap        sw                                         0       0 
 

 I noticed that sda5 swap on fstab is gone on fdisk and rolled into what I assume is /home that is consistent with what I did. Also sda6 on fstab is sda1 on fdisk.  
 

 I then ran sudo hdparm -t /dev/sda to observe what it sees:
 
 /dev/sda:
 
Timing buffered disk reads: 692 MB in  3.01 seconds = 230.08 MB/sec
 

 /dev/sda1:
 
  Timing buffered disk reads: 724 MB in  3.00 seconds = 241.20 MB/sec
 

 /dev/sda2:
 
[COLOR=#000000]Timing buffered disk reads: read(2097152) returned 1024 bytes[/COLOR]
 

 /dev/sda5:
 
Timing buffered disk reads: 764 MB in  3.00 seconds = 254.27 MB/sec
 

 That introduced yet another item, sda. As an aside, all my data and files are on a second rotating drive.  
 

 Questions:
 

1. Do I need to  make any changes to fstab seeing that it may be looking for the swap partition not there anymore.

 2.  I have seen folks Trim using using this:       
   
[COLOR=#000000]sudo fstrim /dev/sda1[/COLOR]
 

 [COLOR=#000000]sudo fstrim /dev/sda2[/COLOR]
 

 [COLOR=#000000]sudo fstrim /dev/sda5 [/COLOR] 
 

 [COLOR=#000000]others use this:[/COLOR]
 

 [COLOR=#000000]sudo fstrim /[/COLOR]
 

 [COLOR=#000000]sudo fstrim /home[/COLOR]
 

 [COLOR=#000000]If I use the first method do I also need to do it for sda or does that not get writing activity? Is the second method better? Will I actually be trimming anything if the partitions are mislabeled between the three ways I looked at them?[/COLOR]


[COLOR=#000000]deskjockey
[/COLOR]

---

### Post by oldfred on 2012-07-07
The fstrim, I believe is just another way to trim instead of using the fstab entries for noatime and discard. I used it just to houseclean as I had not implemented discard right away.

[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
sudo hdparm -I /dev/sdX
Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed
test if trim working using hdparm
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)

---

