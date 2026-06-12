---
title: "How to get rid of jdb2/sda6-8 (100% I/O usage)?"
date: 2014-04-07
forum: New to Ubuntu
---

### Post by vgezer on 2014-04-07
I have 14.04 Beta 2 64-bit and Intel i7 Processor with 2.2Ghz clock, 4 GB RAM and 500 GB Harddrive.

After using Ubuntu for some time, everything goes so slow and I cannot even move my USB mouse cursor, but only touchpad. Not possible to open even a terminal window.

Here is the iotop output:

[http://i.imgur.com/dJzuEYZ.png](http://i.imgur.com/dJzuEYZ.png)

How do I get rid of this thing?

It always stays there like 3 4 hours and this started becoming annoying.

---

### Post by sandyd on 2014-04-07
Sounds like something is syncing to disk too often

What programs are you running?

Also - post the output of
```
ls -la /var/log
```

---

### Post by grahammechanical on 2014-04-07
This is what that is

[http://en.wikipedia.org/wiki/Journaling_block_device](http://en.wikipedia.org/wiki/Journaling_block_device)

I have just installed iotop on my trusty tahr (14.04) and I do not see jdb2 running at all. There is more to your setup then a default install of Ubuntu 14.04 beta. Do you have sda6 - sda8 as an LVM and is there a lot of read and writes happening to those partitions that would cause the Journaling utilities of Ext4 to write to the disk so much?

Regards.

---

### Post by vgezer on 2014-04-07
Thanks for response.

I am running apache, owncloud-cli, dropbox, chromium and some other background tasks. What kind of processes do I need to write actually?

Here is the output:

```
volkan@ubuntu:~$ ls -la /var/logtoplam 11708
drwxrwxr-x 24 root          syslog           4096 Nis  7 15:48 .
drwxr-xr-x 14 root          root             4096 Oca 16 00:32 ..
-rw-r--r--  1 root          root                0 Nis  1 14:48 alternatives.log
-rw-r--r--  1 root          root            58723 Mar 30 21:51 alternatives.log.1
-rw-r--r--  1 root          root              270 May  7  2013 alternatives.log.10.gz
-rw-r--r--  1 root          root             7673 Nis 29  2013 alternatives.log.11.gz
-rw-r--r--  1 root          root              527 &#350;ub 24 12:14 alternatives.log.2.gz
-rw-r--r--  1 root          root              774 Oca 19 13:04 alternatives.log.3.gz
-rw-r--r--  1 root          root             1870 Ara 31 20:56 alternatives.log.4.gz
-rw-r--r--  1 root          root             3305 Kas 29 03:04 alternatives.log.5.gz
-rw-r--r--  1 root          root             4462 Eki 31 17:29 alternatives.log.6.gz
-rw-r--r--  1 root          root              219 Eki  2  2013 alternatives.log.7.gz
-rw-r--r--  1 root          root             2240 A&#287;u 28  2013 alternatives.log.8.gz
-rw-r--r--  1 root          root             2708 A&#287;u  1  2013 alternatives.log.9.gz
drwxr-x---  2 root          adm              4096 Nis  6 15:51 apache2
-rw-r-----  1 root          adm                 0 Nis  6 15:51 apport.log
-rw-r-----  1 root          adm             12946 Nis  6 15:37 apport.log.1
-rw-r-----  1 root          adm               249 Nis  4 01:58 apport.log.2.gz
-rw-r-----  1 root          adm               303 Nis  2 20:13 apport.log.3.gz
-rw-r-----  1 root          adm               447 Nis  1 22:07 apport.log.4.gz
-rw-r-----  1 root          adm               398 Nis  1 00:57 apport.log.5.gz
-rw-r-----  1 root          adm               762 Mar 31 00:24 apport.log.6.gz
-rw-r-----  1 root          adm               311 Mar 30 15:05 apport.log.7.gz
drwxr-xr-x  2 root          root             4096 Nis  1 14:48 apt
-rw-r-----  1 syslog        adm             66964 Nis  7 19:50 auth.log
-rw-r-----  1 syslog        adm            294302 Nis  6 15:51 auth.log.1
-rw-r-----  1 syslog        adm             21036 Mar 30 15:26 auth.log.2.gz
-rw-r-----  1 syslog        adm             53218 Mar 25 12:30 auth.log.3.gz
-rw-r-----  1 syslog        adm             29776 Mar 16 15:09 auth.log.4.gz
-rw-r-----  1 root          adm                31 Eki 17  2012 boot
-rw-r--r--  1 root          root             1589 Nis  5 17:56 boot.log
-rw-r--r--  1 root          root            49450 Eki 17  2012 bootstrap.log
-rw-rw----  1 root          utmp                0 Nis  1 14:48 btmp
-rw-rw----  1 root          utmp             1920 Mar 31 17:08 btmp.1
drwxr-xr-x  2 clamav        clamav           4096 Nis  6 15:51 clamav
drwxr-xr-x  2 root          root             4096 Nis  1 14:48 ConsoleKit
drwxr-xr-x  2 root          root             4096 Mar 30 15:30 cups
drwxr-xr-x  2 root          root             4096 A&#287;u  6  2013 dbconfig-common
drwxr-xr-x  8 root          root             4096 Mar  9 23:06 dist-upgrade
-rw-r-----  1 root          adm             58163 Nis  5 17:56 dmesg
-rw-r-----  1 root          adm             57884 Nis  1 22:06 dmesg.0
-rw-r-----  1 root          adm             15937 Mar 30 16:07 dmesg.1.gz
-rw-r-----  1 root          adm             15724 Mar 30 15:46 dmesg.2.gz
-rw-r-----  1 root          adm             15768 Mar 27 19:50 dmesg.3.gz
-rw-r-----  1 root          adm             15635 Mar 22 00:53 dmesg.4.gz
-rw-r--r--  1 root          root            10902 Nis  5 15:47 dpkg.log
-rw-r--r--  1 root          root          4544297 Mar 30 21:51 dpkg.log.1
-rw-r--r--  1 root          root             5030 May 10  2013 dpkg.log.10.gz
-rw-r--r--  1 root          root           270476 May  1  2013 dpkg.log.11.gz
-rw-r--r--  1 root          root            51427 Mar  1 02:24 dpkg.log.2.gz
-rw-r--r--  1 root          root            26501 Oca 23 18:20 dpkg.log.3.gz
-rw-r--r--  1 root          root            85443 Ara 31 20:56 dpkg.log.4.gz
-rw-r--r--  1 root          root           118082 Kas 30 03:17 dpkg.log.5.gz
-rw-r--r--  1 root          root           239134 Eki 31 17:29 dpkg.log.6.gz
-rw-r--r--  1 root          root             6506 Eki  2  2013 dpkg.log.7.gz
-rw-r--r--  1 root          root            91351 A&#287;u 29  2013 dpkg.log.8.gz
-rw-r--r--  1 root          root            92567 A&#287;u  1  2013 dpkg.log.9.gz
drwxr-s---  2 Debian-exim   adm              4096 Oca  3 16:04 exim4
-rw-r--r--  1 root          root            32128 Oca 11 15:12 faillog
-rw-r--r--  1 root          root             5615 Mar 30 21:50 fontconfig.log
drwxr-xr-x  2 root          root             4096 Eki 17  2012 fsck
-rw-r--r--  1 root          root             1289 Nis  5 17:56 gpu-manager.log
-rw-r--r--  1 root          adm                 0 May  5  2013 hibernate.log
-rw-r--r--  1 root          adm              2421 May  1  2013 hibernate.log.1
drwxr-xr-x  3 root          root             4096 Eki  3  2013 hp
drwxr-xr-x  2 debian-inadyn debian-inadyn    4096 Tem 27  2013 inadyn
drwxr-xr-x  2 root          root             4096 Nis 17  2013 installer
-rw-r--r--  1 root          root                0 &#350;ub  7 18:15 jockey.log
-rw-r--r--  1 root          root            40635 &#350;ub  7 18:15 jockey.log.1
-rw-r--r--  1 root          root             3777 Kas  1 16:32 jockey.log.2.gz
-rw-r--r--  1 root          root             3814 Eki 23 18:32 jockey.log.3.gz
-rw-r--r--  1 root          root             3709 A&#287;u  7  2013 jockey.log.4.gz
-rw-r--r--  1 root          root             5522 A&#287;u  6  2013 jockey.log.5.gz
-rw-r--r--  1 root          root             3694 Tem 29  2013 jockey.log.6.gz
-rw-r--r--  1 root          root             4027 Nis 18  2013 jockey.log.7.gz
-rw-r-----  1 syslog        adm             43201 Nis  7 19:50 kern.log
-rw-r-----  1 syslog        adm            584029 Nis  6 15:37 kern.log.1
-rw-r-----  1 syslog        adm             53571 Mar 30 15:29 kern.log.2.gz
-rw-r-----  1 syslog        adm            115628 Mar 25 12:24 kern.log.3.gz
-rw-r-----  1 syslog        adm             73955 Mar 16 12:48 kern.log.4.gz
-rw-rw-r--  1 root          utmp           293168 Nis  1 21:49 lastlog
drwxr-xr-x  6 root          root             4096 Eki  3  2013 libvirt
drwxr-xr-x  2 root          root             4096 Nis  5 17:56 lightdm
-rw-r-----  1 syslog        adm                 0 Nis  6 15:51 mail.err
-rw-r-----  1 syslog        adm                87 Nis  6 13:47 mail.err.1
-rw-r-----  1 syslog        adm               127 Nis  5 02:07 mail.err.2.gz
-rw-r-----  1 syslog        adm                94 Oca  3 13:56 mail.err.3.gz
-rw-r-----  1 syslog        adm               139 Kas  2 01:28 mail.err.4.gz
-rw-r-----  1 syslog        adm             29842 Nis  7 15:55 mail.log
-rw-r-----  1 syslog        adm            152897 Nis  6 14:58 mail.log.1
-rw-r-----  1 syslog        adm              2562 Mar 30 14:31 mail.log.2.gz
-rw-r-----  1 syslog        adm               532 Mar 22 00:54 mail.log.3.gz
-rw-r-----  1 syslog        adm               492 Mar 10 21:52 mail.log.4.gz
drwxr-s---  2 mysql         adm              4096 Nis  7 15:48 mysql
-rw-r-----  1 mysql         adm                 0 Mar 10 11:05 mysql.err
-rw-r-----  1 mysql         adm                 0 Nis  7 15:48 mysql.log
-rw-r-----  1 mysql         adm                20 Nis  6 15:51 mysql.log.1.gz
-rw-r-----  1 mysql         adm                20 Nis  5 13:58 mysql.log.2.gz
-rw-r-----  1 mysql         adm                20 Nis  3 19:44 mysql.log.3.gz
-rw-r-----  1 mysql         adm                20 Nis  2 14:51 mysql.log.4.gz
-rw-r-----  1 mysql         adm                20 Nis  1 14:48 mysql.log.5.gz
-rw-r-----  1 mysql         adm                20 Mar 31 13:05 mysql.log.6.gz
-rw-r-----  1 mysql         adm                20 Mar 30 15:30 mysql.log.7.gz
drwxr-xr-x  2 root          root             4096 Nis 17  2013 news
drwxr-xr-x  2 ntp           ntp              4096 Eki  9 21:08 ntpstats
-rw-r-----  1 www-data      adm                 0 Ara  1 04:06 owncloud.log
-rw-r-----  1 www-data      adm               956 Kas 12 19:54 owncloud.log.1.gz
-rw-r-----  1 www-data      adm              2948 Eki 24 21:17 owncloud.log.2.gz
-rw-r--r--  1 root          root           124628 Nis  7 19:46 pm-powersave.log
-rw-r--r--  1 root          root           727086 Nis  1 14:29 pm-powersave.log.1
-rw-r--r--  1 root          root             5923 Mar  1 13:46 pm-powersave.log.2.gz
-rw-r--r--  1 root          root             7297 &#350;ub  4 15:08 pm-powersave.log.3.gz
-rw-r--r--  1 root          root             5337 Oca  1 17:26 pm-powersave.log.4.gz
-rw-r--r--  1 root          root           115841 Nis  7 19:46 pm-suspend.log
-rw-r--r--  1 root          root           647127 Nis  1 12:18 pm-suspend.log.1
-rw-r--r--  1 root          root            12438 Mar  1 13:46 pm-suspend.log.2.gz
-rw-r--r--  1 root          root            17803 &#350;ub  3 20:41 pm-suspend.log.3.gz
-rw-r--r--  1 root          root            14743 Oca  1 17:26 pm-suspend.log.4.gz
-rw-r--r--  1 root          root           153773 Nis  5 14:02 popularity-contest
-rw-r--r--  1 root          root           155146 Mar 28 14:39 popularity-contest.0
-rw-r--r--  1 root          root            38158 Mar 21 18:56 popularity-contest.1.gz
-rw-r--r--  1 root          root            38390 Mar 14 12:23 popularity-contest.2.gz
-rw-r--r--  1 root          root            36936 Mar  7 17:48 popularity-contest.3.gz
-rw-r--r--  1 root          root            36908 &#350;ub 28 14:28 popularity-contest.4.gz
-rw-r--r--  1 root          root            36721 &#350;ub 21 14:20 popularity-contest.5.gz
-rw-r--r--  1 root          root            36718 &#350;ub 14 18:10 popularity-contest.6.gz
drwxr-xr-x  3 root          root            12288 Nis  7 15:46 samba
-rw-r--r--  1 root          root              774 Oca 12 13:06 samsung-tools.log
-rw-r-----  1 syslog        adm            104810 Nis  7 19:50 syslog
-rw-r-----  1 syslog        adm            358887 Nis  7 15:48 syslog.1
-rw-r-----  1 syslog        adm             79334 Nis  6 15:51 syslog.2.gz
-rw-r-----  1 syslog        adm             44438 Nis  5 13:58 syslog.3.gz
-rw-r-----  1 syslog        adm             33187 Nis  3 19:44 syslog.4.gz
-rw-r-----  1 syslog        adm             64800 Nis  2 14:51 syslog.5.gz
-rw-r-----  1 syslog        adm             39647 Nis  1 14:48 syslog.6.gz
-rw-r-----  1 syslog        adm             92553 Mar 31 13:05 syslog.7.gz
drwxr-s---  2 debian-tor    adm              4096 Nis  7 15:48 tor
-rw-r--r--  1 root          root           330079 Nis  5 17:56 udev
-rw-r-----  1 syslog        adm                 0 Eki 22 17:35 ufw.log
-rw-r-----  1 syslog        adm              2290 Eki 21 20:29 ufw.log.1
drwxr-xr-x  2 root          root             4096 Nis 17  2013 unattended-upgrades
drwxr-xr-x  2 root          root            12288 Nis  7 15:48 upstart
drwxr-xr-x  2 root          root             4096 Nis  5 17:57 wicd
-rw-rw-r--  1 root          utmp            46848 Nis  7 19:51 wtmp
-rw-rw-r--  1 root          utmp           158976 Nis  1 02:24 wtmp.1
-rw-r--r--  1 root          root              485 Oca 11 15:12 wvdialconf.log
-rw-r--r--  1 root          root            23635 Nis  5 17:58 Xorg.0.log
-rw-r--r--  1 root          root            23637 Nis  1 22:08 Xorg.0.log.old
-rw-r--r--  1 root          root            22995 Mar 31 17:21 Xorg.1.log
-rw-r--r--  1 root          root            24536 Mar 31 17:20 Xorg.1.log.old
-rw-r--r--  1 root          root            24384 Kas 24 16:45 Xorg.2.log
-rw-r--r--  1 root          root            23917 Kas 24 15:20 Xorg.2.log.old
-rw-r--r--  1 root          bumblebee       14382 Kas 19 20:08 Xorg.8.log
-rw-r--r--  1 root          bumblebee       14501 Kas  1 21:47 Xorg.8.log.old



```

---

### Post by vgezer on 2014-04-07
> **grahammechanical said:**
> This is what that is

[http://en.wikipedia.org/wiki/Journaling_block_device](http://en.wikipedia.org/wiki/Journaling_block_device)

I have just installed iotop on my trusty tahr (14.04) and I do not see jdb2 running at all. There is more to your setup then a default install of Ubuntu 14.04 beta. Do you have sda6 - sda8 as an LVM and is there a lot of read and writes happening to those partitions that would cause the Journaling utilities of Ext4 to write to the disk so much?

Regards.

Not really. I don't even have sda8:

```
volkan@ubuntu:~$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
NAME   FSTYPE   SIZE MOUNTPOINT  LABEL
sda           465,8G             
&#9500;&#9472;sda1 ntfs     100M             SYSTEM
&#9500;&#9472;sda2 ntfs     178G /media/sda6 
&#9500;&#9472;sda3            1K             
&#9500;&#9472;sda4 ntfs    21,6G             SAMSUNG_REC
&#9500;&#9472;sda5 ntfs   215,7G /media/sda5 
&#9500;&#9472;sda6 ext4    48,4G /           
&#9492;&#9472;sda7 swap       2G [SWAP]      swap
sr0            1024M             
zram0  swap   241,7M [SWAP]      
zram1  swap   241,7M [SWAP]      
zram2  swap   241,7M [SWAP]      
zram3  swap   241,7M [SWAP]      
zram4  swap   241,7M [SWAP]      
zram5  swap   241,7M [SWAP]      
zram6  swap   241,7M [SWAP]      
zram7  swap   241,7M [SWAP]      



```

---

### Post by vgezer on 2014-04-08
Up!

---

