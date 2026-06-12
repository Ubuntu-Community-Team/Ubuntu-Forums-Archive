---
title: "Mount folder effecting the size of my &quot;Filesystem&quot;"
date: 2012-09-16
forum: New to Ubuntu
---

### Post by aas452 on 2012-09-16
Hi,

I am having a Low Disk error, saying my file system is low. I ran a Disk Usage Analazyer on the file system and it has pleaty of space in the primary directories. What is showing up in red is 2 of my three drive I have automatically mounting on boot. The mounted drives are 1 and 2 TB and are formatted to ntfs. My filesystem is only 250gb, and the space I have used in the mounted drive is about the same amount(200gb or so), this is leading me to believe the used space I have on the mounted drives are somehow adding together and subtracting from the filesystem. Has anyone had a simular issue or can point me in the right direction for a solution. Thanks.

---

### Post by mcduck on 2012-09-16
You really shouldn't sue the Disk USage Analyzer when trying to get information about used/available space on a certain partition, it's not intended for that purpose but simply for analyzing how much files and directories are using space. (in other words it's great for finding out *where* space is being used, not for how much is used or unused) So by default it will give you a total sum of all connected file systems (and of course the way how it displays usage as percentages relative to parent directory can also make it more confusing if you try to use it to check used/free disk space on a partition).

While it *is* possible to configure Disk Usage Analyzer to only analyze a certain partition and not access other mounted filesystems, that's usually more complicated approach than it would be to simly check the aused/available space using the *System Monitor* or running "*df -h*" in a terminal...

---

### Post by aas452 on 2012-09-16
Right, Disk Usage Analyzer isn't the only tool I am using to find information about the used/avaliable space. 

df -h


```

/dev/sda5             220G  196G   14G  94% /
none                  7.9G  348K  7.9G   1% /dev
none                  7.9G  1.4M  7.9G   1% /dev/shm
none                  7.9G  112K  7.9G   1% /var/run
none                  7.9G     0  7.9G   0% /var/lock
none                  7.9G     0  7.9G   0% /lib/init/rw
/dev/sdb1             932G  9.3G  923G   1% /media/sdb1
/dev/sdc1             1.9T   46G  1.8T   3% /media/sdc1
/dev/sdd1             150G  152M  149G   1% /media/sdd1

```

System Monitor:

[IMG]http://i.imgur.com/3AWG4.png[/IMG]

and now I am trying to figure out what is taking all the space up in the filesystem through the Disk Usage Analyzer tool

[IMG]http://i.imgur.com/OeHT4.png[/IMG]

The issue lies in, why the filesystem thinks it is almost full

---

### Post by Bashing-om on 2012-09-16
This is not making sense to me.
IRT sda5 (df -h) ...I expected sda5 to be an extended partition rather than mounted as / (root).

so my questions:
1. Is ubuntu the only operating system installed on the first hard drive (sda) ?
2. What methods did you employ to install ubuntu onto the sda5 partition vice sda1 ?

What is the terminal output of:
```
fdisk -l
```
(that is s lower case "L")
 Post the output and we will see what we are working with.

[INDENT]kind regards <==BDQ
[/INDENT]

---

### Post by mcduck on 2012-09-16
Based on those pictures, the space must be used in some directory/file that's not readable by your normal user account (which is why the disk usage analyzer is also not able to read it).

I recommend checking root's home directory first, especially root's trash directory, and if there's nothing then run "*sudo du -hs*" in / to check largest directories, then based on that move to the largest subdirectory and repeat the same, until you find where the problem is. (you can ignore /mount of course, as the drives mounted there would be on other disks/partitions).

---

### Post by aas452 on 2012-09-16
No Ubuntu isnt the only OS on this system, there is a partition for windows as well. Windows was installed first on the system then I used the live cd to install Ubuntu, the sda1 must have been given to the windows partition.

fdisk -l

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd6c9f877

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       30401   244089856    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           30401       60802   244191233    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5           30401       59565   234254336   83  Linux
/dev/sda6           59565       60802     9935872   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000403c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xf02ec792

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243202  1953512448    7  HPFS/NTFS

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xca25ca25

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       19458   156288000    7  HPFS/NTFS

```

Thanks

---

### Post by aas452 on 2012-09-16
**@mcduck** 

I checked root directory nothing seems to be in there which is taking up the space, only the basics

---

### Post by Bashing-om on 2012-09-17
aas452;

As all appears in order; take a look in /var/log/    Here are located the majority of the system log files // inspect them size wise ...anything large->see what is writing so much to the file. Another thing ...you may safely delete the files ending in .gz (old compressed log files)
```
ls -la /var/log/
```

[INDENT]hth <==BDQ
[/INDENT]

---

### Post by aas452 on 2012-09-17
So I ended removing all the .gz files form the /var/log directory, there seems to be a bunch of .old files, but nothing to huge, anything else you can think of. Really strange.

```


drwxr-xr-x 14 root              root    4096 2012-09-16 23:25 .
drwxr-xr-x 16 root              root    4096 2011-10-01 19:07 ..
drwxr-xr-x  2 root              root    4096 2011-01-20 09:40 apparmor
drwxr-xr-x  2 root              root    4096 2012-09-02 10:28 apt
-rw-r-----  1 syslog            adm    14085 2012-09-16 23:18 auth.log
-rw-r-----  1 syslog            adm    24643 2012-09-16 00:20 auth.log.1
-rw-r-----  1 root              adm       31 2011-07-19 05:04 boot
-rw-r--r--  1 root              root     628 2012-09-16 09:06 boot.log
-rw-r--r--  1 root              root   41715 2011-07-19 05:05 bootstrap.log
-rw-rw----  1 root              utmp       0 2012-09-02 10:28 btmp
drwxr-xr-x  2 root              root    4096 2012-09-02 10:28 ConsoleKit
drwxr-xr-x  2 root              root    4096 2012-09-16 00:28 cups
-rw-r-----  1 syslog            adm   227640 2012-09-16 23:20 daemon.log
-rw-r-----  1 syslog            adm   309090 2012-09-16 00:27 daemon.log.1
-rw-r-----  1 syslog            adm   243078 2012-09-16 17:16 debug
-rw-r-----  1 syslog            adm   182499 2012-09-16 00:20 debug.1
drwxr-xr-x  2 root              root    4096 2011-12-30 22:14 dist-upgrade
-rw-r-----  1 root              adm    60335 2012-09-16 09:06 dmesg
-rw-r-----  1 root              adm    60309 2012-09-16 02:13 dmesg.0
-rw-r--r--  1 root              root   75228 2012-09-16 02:11 dpkg.log
-rw-r--r--  1 root              root   98765 2012-08-22 11:23 dpkg.log.1
-rw-r--r--  1 root              root   32032 2011-08-04 04:28 faillog
-rw-r--r--  1 root              root  112640 2011-09-03 08:08 failsafeX-backup-110903080609.tar
-rw-r--r--  1 root              root    2480 2012-08-13 21:01 fontconfig.log
drwxr-xr-x  2 root              root    4096 2011-07-19 05:04 fsck
drwxrwx--T  2 root              gdm     4096 2012-09-16 11:40 gdm
drwxr-xr-x  2 root              root    4096 2011-08-04 04:29 installer
-rw-r--r--  1 root              root       0 2012-09-16 00:28 jockey.log
-rw-r--r--  1 root              root   32991 2012-09-16 00:28 jockey.log.1
-rw-r-----  1 syslog            adm   733107 2012-09-16 23:23 kern.log
-rw-r-----  1 syslog            adm   834144 2012-09-16 00:27 kern.log.1
-rw-rw-r--  1 root              utmp  292292 2011-11-16 12:09 lastlog
-rw-r-----  1 syslog            adm        0 2011-08-04 04:32 lpr.log
-rw-r-----  1 syslog            adm        0 2011-08-04 04:32 mail.err
-rw-r-----  1 syslog            adm        0 2011-08-04 04:32 mail.info
-rw-r-----  1 syslog            adm        0 2011-08-04 04:32 mail.log
-rw-r-----  1 syslog            adm        0 2011-08-04 04:32 mail.warn
-rw-r-----  1 syslog            adm   571717 2012-09-16 23:23 messages
-rw-r-----  1 syslog            adm   639619 2012-09-16 00:28 messages.1
drwxr-xr-x  2 root              root    4096 2011-08-04 04:32 news
-rw-r--r--  1 root              root   39395 2011-11-16 12:13 nvidia-installer.log
-rw-r--r--  1 root              root   13354 2012-09-16 09:06 pm-powersave.log
-rw-r--r--  1 root              root   12482 2012-09-02 10:12 pm-powersave.log.1
-rw-r--r--  1 root              root       0 2012-05-13 10:26 pm-suspend.log
-rw-r--r--  1 root              root    3759 2012-05-12 08:54 pm-suspend.log.1
-rw-r--r--  1 root              root       0 2011-07-19 05:05 pycentral.log
drwxr-xr-x  3 root              root    4096 2012-01-22 08:26 samba
drwxr-xr-x  2 speech-dispatcher root    4096 2010-04-15 09:29 speech-dispatcher
-rw-r-----  1 syslog            adm  1044431 2012-09-16 23:23 syslog
-rw-r-----  1 syslog            adm   402258 2012-09-16 00:27 syslog.1
-rw-r--r--  1 root              root  259555 2012-09-16 09:06 udev
-rw-r-----  1 syslog            adm        0 2011-08-04 04:32 ufw.log
drwxr-xr-x  2 root              root    4096 2011-01-14 16:48 unattended-upgrades
-rw-r-----  1 syslog            adm    71949 2012-09-16 09:15 user.log
-rw-r-----  1 syslog            adm     2814 2012-09-16 00:20 user.log.1
-rw-r--r--  1 root              root  105659 2012-08-19 10:15 vmware-installer
-rw-r--r--  1 root              root  902347 2012-09-16 09:06 vnetlib
-rw-rw-r--  1 root              utmp  104448 2012-09-16 23:13 wtmp
-rw-r--r--  1 root              root   84506 2012-09-16 23:05 Xorg.0.log
-rw-r--r--  1 root              root   52751 2012-09-16 02:18 Xorg.0.log.old
-rw-r--r--  1 root              root   56754 2012-09-16 11:39 Xorg.1.log
-rw-r--r--  1 root              root   43056 2012-05-22 08:26 Xorg.1.log.old
-rw-r--r--  1 root              root   34054 2012-09-16 11:40 Xorg.2.log
-rw-r--r--  1 root              root    6152 2012-05-22 08:25 Xorg.2.log.old
-rw-r--r--  1 root              root    6152 2012-05-22 08:25 Xorg.3.log
-rw-r--r--  1 root              root    6151 2012-04-14 21:35 Xorg.3.log.old
-rw-r--r--  1 root              root    6152 2012-05-22 08:25 Xorg.4.log
-rw-r--r--  1 root              root    6151 2012-04-14 21:35 Xorg.4.log.old
-rw-r--r--  1 root              root    6152 2012-05-22 08:25 Xorg.5.log
-rw-r--r--  1 root              root    6151 2012-04-14 21:35 Xorg.5.log.old
-rw-r--r--  1 root              root   42994 2012-05-22 08:26 Xorg.failsafe.log
-rw-r--r--  1 root              root   42993 2012-04-14 21:35 Xorg.failsafe.log.old


```

only about .1 GB restored to the disk, boggling...

---

### Post by aas452 on 2012-09-17
OK found it, I signed out of my user account and signed in as root, did a disk usage analysis on the root user. It found that the .local/share/Trash folder had over a hundred gigs in it........ ugh sorry about that, I use a program called Nuke where it save massive amounts of data to the tmp dir, this might have been spillover from a previous clean, and before I slated another drive just for this particular reason. Thank you for all your help!! Everything seems to add up now.

---

### Post by rybnik on 2012-09-17
Is the disk usage analyzer the same as the du command?

---

### Post by mcduck on 2012-09-17
> **rybnik said:**
> Is the disk usage analyzer the same as the du command?

No, Disk USage Analyzer (actually called Baobab) is Gnome's graphical tool for analyzing where disk space is being used.

aas452: THat was pretty much what I menat by chekcign root's hokme and trash directories... Anyway, great that you got the problem sorted out. :)

---

### Post by Bashing-om on 2012-09-17
Good to have solution. See, we are all in this together !

[INDENT]enjoy'n ubuntu 
[/INDENT]

---

### Post by varunendra on 2012-09-18
Although this thread is already solved, I couldn't help commenting because many new users may take the same route to solve their similar problem.
> **aas452 said:**
> I signed out of my user account and signed in as root
^^ Absolutely [COLOR=Red]**WRONG**[/COLOR] way of doing what you intended to do!! Logging in as root is against Ubuntu's security design and is absolutely discouraged to do so unless you are a real linux expert (which obviously you are not).

There is almost nothing which can't be done from a normal user's account. To access places as 'root' you can simply open nautilus (or whatever file manager you are using) as root by-
```
gksu nautilus
```

Similarly, you could run Disk Usage Analyzer as root (which in turn will open in 'root's home directory "/root") by-
```
gksu baobab
```

In short, you can run and access everything as root when and if required, if you are a user in 'sudo' user group (which the first user is by default). Last notes-

- For GUI applications, use 'gksu',
- For commandline apps, use sudo.
- For details on why to do so, see this article : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

