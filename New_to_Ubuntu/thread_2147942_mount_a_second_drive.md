---
title: "mount a second drive"
date: 2013-05-23
forum: New to Ubuntu
---

### Post by autotron on 2013-05-23
I have a remote server with ubuntu 12.04LTS installed and comes with 2*1TB drives, I would like to mount the second drive to /home/files/ so I have access to 2TB read/write but am really confused by all the different posts I have read.
this is the output of fdisk -l

```
Welcome to Ubuntu 12.04.2 LTS (GNU/Linux 3.8.13-xxxx-grs-ipv6-64 x86_64)


  System information as of Wed May 22 21:00:53 CEST 2013

  System load:    0.09                Processes:           142
  Usage of /home: 10.1% of 896.59GB   Users logged in:     1
  Memory usage:   57%                 IP address for eth0: **.**.**.**
  Swap usage:     0%

 
4 packages can be updated.
0 updates are security updates.


root@server:~# fdisk -l

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00030e86

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        4096    41947135    20971520   fd  Linux raid autodetect
/dev/sdb2        41947136  1952468991   955260928   fd  Linux raid autodetect
/dev/sdb3      1952468992  1953519615      525312   82  Linux swap / Solaris

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0005b3dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        4096    41947135    20971520   fd  Linux raid autodetect
/dev/sda2        41947136  1952468991   955260928   fd  Linux raid autodetect
/dev/sda3      1952468992  1953519615      525312   82  Linux swap / Solaris

Disk /dev/md2: 978.2 GB, 978187124736 bytes
2 heads, 4 sectors/track, 238815216 cylinders, total 1910521728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md1: 21.5 GB, 21474770944 bytes
2 heads, 4 sectors/track, 5242864 cylinders, total 41942912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table
```

and if i do sudo lshw -C disk

get this output

```
root@server:~# sudo lshw -C disk
  *-disk
       description: ATA Disk
       product: TOSHIBA DT01ACA1
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: MS2O
       serial: 13EJ81XPS
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0005b3dd
  *-disk
       description: ATA Disk
       product: TOSHIBA DT01ACA1
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: MS2O
       serial: 13OX3TKPS
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00030e86


```

the contents of /etc/fstab are

```
/dev/md1    /    ext4    errors=remount-ro,relatime    0    1
/dev/md2    /home    ext4    defaults,relatime    0    2
/dev/sda3    none    swap    defaults    0    0
/dev/sdb3    none    swap    defaults    0    0
proc        /proc    proc    defaults        0    0
sysfs        /sys    sysfs    defaults        0    0
devtmpfs    /dev    devtmpfs    rw    0    0


```

could some one please tell me how to do this?

---

### Post by dino99 on 2013-05-23
[http://askubuntu.com/questions/164926/how-to-make-hdds-mount-at-startup-in-ubuntu-12-04](http://askubuntu.com/questions/164926/how-to-make-hdds-mount-at-startup-in-ubuntu-12-04)

---

### Post by Albury_Boy on 2013-05-23
The official documentation from Canonical is really good. It walks you through everything step-by-step. Also, drives (other than your boot drive) are usually mounted in /media. 
You can set up what is called a 'RAID' which treats multiple drives as if there were one, but in your case you are better off following the instructions below. RAID's usually consists of more than two drives.[URL="https://help.ubuntu.com/community/InstallingANewHardDrive"]

https://help.ubuntu.com/community/InstallingANewHardDrive[/URL]

---

### Post by arpanaut on 2013-05-23
I'm no expert on this but it looks to me that you have a mirrored raid set up.
that is ... sda and sdb are exact copies if each other and done for the sake of redundancy.
If one drive fails the data is safe on the other.
How did you set up your drives when you installed?

---

### Post by Albury_Boy on 2013-05-23
The official documentation from Canonical is really good. It walks you through everything step-by-step. Also, drives (other than your boot drive) are usually mounted in /media. 
You can set up what is called a 'RAID' which treats multiple drives as if there were one, but in your case you are better off following the instructions below. RAID's usually consists of more than two drives.[URL="https://help.ubuntu.com/community/InstallingANewHardDrive"]

https://help.ubuntu.com/community/InstallingANewHardDrive[/URL]

Once you have formatted, partitioned and mounted a drive, the last thing to do is take ownership of it.

```
cd /media/[name of drive]
sudo chown [username]:[usergroup] *

```

This will give you a whole drive to fill up :-)
I also make a 'bookmark' in the file manager to make it easy to find in a GUI.

Be warned. You need to very very careful using chown. Don't make any typo's or it could wreck your whole day.

---

### Post by Bucky Ball on 2013-05-23
@ Albury_Boy: Nice to see another Australian! I have deleted your first post on this thread as it was exactly the same as the first half of your second post. Cheers. ;)

---

### Post by autotron on 2013-05-23
> **Albury_Boy said:**
> The official documentation from Canonical is really good. It walks you through everything step-by-step. Also, drives (other than your boot drive) are usually mounted in /media. 
You can set up what is called a 'RAID' which treats multiple drives as if there were one, but in your case you are better off following the instructions below. RAID's usually consists of more than two drives.[URL="https://help.ubuntu.com/community/InstallingANewHardDrive"]

https://help.ubuntu.com/community/InstallingANewHardDrive[/URL]

ya, read that one, and thats why I am confused lol, when it came to adding to fstab I looked at the contents of it and see

/dev/md1    /    ext4    errors=remount-ro,relatime    0    1 /dev/md2    /home    ext4    defaults,relatime    0    2 /dev/sda3    none    swap    defaults    0    0 /dev/sdb3    none    swap    defaults    0    0

so now not sure what to add here or where....I figured
/dev/sda3    none    swap    defaults    0    0
was first drives partition with useable space and 
/dev/sdb3    none    swap    defaults    0    0
was second drives partition with useable space...but where did md1 and md2 come from? 
every post i read just further confuses me.

---

### Post by Albury_Boy on 2013-05-24
[SIZE=2][FONT=arial]**[COLOR=#000000][arpanaut]("http://ubuntuforums.org/member.php?u=45953") [/COLOR]**said it better. It looks like you have a RAID set up. This is when you have two drives which act like one for the purpose of redundancy. If one fails, the other has a backup. 

What I suggest (if you want access to 2Tb's of data) is to format your second drive and start afresh. Run gparted from your desktop by pressing the 'super' key (aka the Windows key) and typing it in. See if you can determine which is the second drive. I've never used a RAID so I don't really know how it is displayed, but gparted is pretty smart and should show you.

You may need to format both drives and re-install Ubuntu on the 'primary' drive or what is usually called [FONT=courier new]sda[/FONT] by the system. If you have an external HDD, simply copy the contents of your home directory to it first. You can copy it back over when you are done.

Let me know how you go :-)[/FONT][/SIZE]

---

### Post by Albury_Boy on 2013-05-24
> **Bucky Ball said:**
> @ Albury_Boy: Nice to see another Australian! I have deleted your first post on this thread as it was exactly the same as the first half of your second post. Cheers. ;)

Thanks mate :). I was editing that post when someone else posted and it split up. I couldn't see a delete tool.

---

### Post by Bucky Ball on 2013-05-24
> **Albury_Boy said:**
>  I couldn't see a delete tool.

There isn't one for regular users, but if something screws up, feel free to use the 'Report Post' button on the post and explain. One of the staff will deal with it from there. Use the report for all oddities, not just sinister posts/users. ;)

---

