---
title: "I can't get access to my second hard drive"
date: 2013-08-02
forum: New to Ubuntu
---

### Post by sacha98 on 2013-08-02
Hi, I'm using ubuntu 12.04 and I'm using two sessions.
On the main one, I can get access to my main hard drive and to the second one.
While on my second session, I can only see the main hard drive, the one on which ubuntu is installed.

I tried to run the command "sudo nautilus" which allowed me to see the second hard drive from my second session. From there, I went into the settings of that hard drive and tried to change the permissions. But every time I change something it swaps back to how it was. I really don't know what to do.

Thanks for your help :)

---

### Post by Bashing-om on 2013-08-02
sacha98; Hi ! ,,,...

I'll start this ball rolling.
Show us what we are working with; post the output of terminal codes:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f
cat /etc/fstab
mount

```
which relate your disk(s) partitioning, the related info and what is mounted and how.

[INDENT][INDENT]a tale in the telling
[/INDENT][/INDENT]

---

### Post by sacha98 on 2013-08-03
> **Bashing-om said:**
> sacha98; Hi ! ,,,...

I'll start this ball rolling.
Show us what we are working with; post the output of terminal codes:

There is only one problem I didn't thin of, my computer is in french so if you need me to translate something, just ask

sudo fdisk -lu

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes255 têtes, 63 secteurs/piste, 60801 cylindres, total 976773168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0xc8fd6d74


Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *        2048   488386559   244192256    7  HPFS/NTFS/exFAT
/dev/sda2       488388606   976771071   244191233    5  Étendue
/dev/sda5       972582912   976771071     2094080   82  partition d'échange Linux / Solaris
/dev/sda6       488388608   972582911   242097152   83  Linux


Les entrées de la table de partitions ne sont pas dans l'ordre du disque


Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 têtes, 63 secteurs/piste, 38913 cylindres, total 625142448 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0xfcdbb1bc


Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sdb1   *          63   625136592   312568265    7  HPFS/NTFS/exFAT



```

sudo parted -l

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes255 têtes, 63 secteurs/piste, 60801 cylindres, total 976773168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0xc8fd6d74


Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *        2048   488386559   244192256    7  HPFS/NTFS/exFAT
/dev/sda2       488388606   976771071   244191233    5  Étendue
/dev/sda5       972582912   976771071     2094080   82  partition d'échange Linux / Solaris
/dev/sda6       488388608   972582911   242097152   83  Linux


Les entrées de la table de partitions ne sont pas dans l'ordre du disque


Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 têtes, 63 secteurs/piste, 38913 cylindres, total 625142448 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0xfcdbb1bc


Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sdb1   *          63   625136592   312568265    7  HPFS/NTFS/exFAT
sacha@dieryck:~$ sudo parted -l
Modèle: ATA ST3500320AS (scsi)
Disque /dev/sda : 500GB
Taille des secteurs (logiques/physiques): 512B/512B
Table de partitions : msdos


Numéro  Début   Fin    Taille  Type      Système de fichiers  Fanions
 1      1049kB  250GB  250GB   primary   ntfs                 démarrage
 2      250GB   500GB  250GB   extended
 6      250GB   498GB  248GB   logical   ext4
 5      498GB   500GB  2144MB  logical   linux-swap(v1)




Modèle: ATA WDC WD3200BEVT-2 (scsi)
Disque /dev/sdb : 320GB
Taille des secteurs (logiques/physiques): 512B/512B
Table de partitions : msdos


Numéro  Début   Fin    Taille  Type     Système de fichiers  Fanions
 1      32,3kB  320GB  320GB   primary  ntfs                 démarrage




Avertissement: Impossible d'ouvrir /dev/sr0 en lecture-écriture (Système de
fichiers accessible en lecture seulement). /dev/sr0 a été ouvert en lecture
seule.
Erreur: Impossible d'ouvrir /dev/sr0 - étiquette de disque non reconnue.  
```
sudo parted /dev/sda unit s print
(It says error, unable to open /dev/sr0 in read write mode, only accessible in read mode)
(And then Error unable to open /dev/sr0 - disk label (not sure about that translation) not recognized 


lsblk -f

```
NAME   FSTYPE LABEL      MOUNTPOINTsda                      
&#9500;&#9472;sda1                   
&#9500;&#9472;sda2                   
&#9500;&#9472;sda5                   [SWAP]
&#9492;&#9472;sda6                   /
sdb                      
&#9492;&#9472;sdb1                   /media/BOOT
sr0    udf    UDF Volume /media/UDF Volume



```
cat /etc/fstab

```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=081814b7-0048-48d1-8a0f-f8d9d6e0a8c4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a3fbf792-83d0-4d7e-99d5-1fa455c2705d none            swap    sw              0       0



```

mount

```
/dev/sda6 on / type ext4 (rw,errors=remount-ro)proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dieryck/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dieryck)
/dev/sr0 on /media/UDF Volume type udf (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks)
/dev/sdb1 on /media/BOOT type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
gvfs-fuse-daemon on /home/sacha/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sacha)



```

---

### Post by Bashing-om on 2013-08-03
sacha98; Hi !

No problem understanding that output ... all is as expected...
Here is what I see:
Booting up with the 1st hard drive sda ... and sda contains Windows and Ubuntu....
There is currently no means to see that 2nd (sdb) drive. That can be changed, depending on what is contained on the sdb drive and how you want to access it.
 
ok ... you want to access the 2nd hard drive sdb - which is dedicated to Windows'..->
question: is there another operating system installed onto the 2nd hard drive (sdb) or is that hard drive only for data storage ?
next question ... in the event that 2nd hard drive (sdb) is only for data ... do you desire that that hard drive (sdb) be accessable as automount and available upon starting your system ... or accessable as -on-demand- ???

I am an advocate of only mounting my data partitions only as needed/wanted ... but one MUST remember to (un-)mount those partitions manually prior to shutting the system down.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by sacha98 on 2013-08-03
You got it :)
So there is only data on that second hard drive.
The thing is that I can access it on my other session but not on this one. It is automatically mounted on ther other session and I like that.
What's the point of making it accessable on demand ? What problem do you get if you forget to unmount it ? Because I wouldn't mind it but it is my family's computer and they aren't very good with computers so it will probably be easier for them to mount it automatically :)

---

### Post by Bashing-om on 2013-08-03
sacha98; Hey,

I nan not relate with "session" "other session"; I have no point of reference.
How about this,
I am able to access my Windows' data hard drive from my Windows' installation, 
but I can not access the windows data hard drive from the ubuntu installation.

The drawback to mounting the data partitions (drive) manually as on-demand, is that in the event you forget to (un-)mount that partition then file system corruption - at some level - will result ... maybe of little impact maybe catastrophic just depends on what the system is doing, and what the system was accessing when the system was shut down.
On that note, it is not considered a good idea to ever mount the Windows Install as automounted .. much too easy for file system corruption to occur on your Windows' install. 
Another thing to keep in mind ... ubuntu is versatile in it's little world .. and is able to read and write to other file systems; Windows in it's big world could care less about other operating systems and can not even see ubuntu.
ubuntu can read and write to Windows; Windows can not read or write to ubuntu. 

As I understand it .. you want to access the Windows' data disk from ubuntu ?
See:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
for the documentation and full explanation .

[INDENT][INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT][/INDENT]

---

### Post by sacha98 on 2013-08-05
Oops, sorry for session, I meant user.
So, I have a data HDD with no OS on it, only files.
I have two user sessions on ubuntu. The first one I created when I installed ubuntu (thus I suppose the main one) can see the HDD and read/write in it. The second user (the one I created after the installation) one can't even see the HDD, except when I use sudo nautilus. How can I make it so that the two users have the same right over it ?[COLOR=#000000]

[/COLOR]

---

### Post by Morbius1 on 2013-08-05
I'm confused.

Is this the partition you want the second user ( session ? ) to be able to access:
> /dev/sdb1   *          63   625136592   312568265    7  HPFS/NTFS/exFAT
sdb                      
&#9492;&#9472;sdb1                   /media/BOOT
The label on that partition is "BOOT" so is this another operating system or the boot partition of a Windows OS or is this actually a Data partition?

---

### Post by sacha98 on 2013-08-05
Yes this is the partition and it is a data partition. Sorry about the name confusion, that is the name it was automatically set to, I don't know why ...

---

### Post by Morbius1 on 2013-08-05
Here is my suggestion: Add an entry into /etc/fstab so that this partition mounts automatically and mounts so all users can access the partition:

[1] Unmount the partition if it is currently mounted:
```
sudo umount /media/BOOT
```
[2] Create a new mount point:
```
sudo mkdir /media/Data
```
[3] Add the following line to the end of /etc/fstab:
```
UUID=DA9056C19056A3B3 /media/Data ntfs defaults,nls=utf8,umask=000,windows_names 0 0
```
*[COLOR=#0000cd]**NOTE**: You need to replace the UUID number above with the correct value for your partition. To find that value run the following command:[/COLOR]*
```
sudo blkid -c /dev/null
```
[4] Then run the following command which tests for syntax errors in fstab and if there are none silently mounts the partition with it's new mount point:
```
sudo mount -a
```
Make sure that you can now access /media/Data with your current login then log into the other user and see if things work for that user.

---

### Post by Bashing-om on 2013-08-05
+1

---

### Post by Tom 6 on 2013-08-05
Hi :)
I have never had any troubles with shutting down a machine that had loads of other partitions mounted.  I thought part of the shut-down process was to shut-down processes and unmount partitions in some sensible order.  I could just have been lucky so far though.  
Regards from 
Tom :)

---

### Post by Bashing-om on 2013-08-05
@Tom 6. Hi !

If I may offer some guidance, so you see for yourself.
Any partition mounted via "fstab" the system will take care of in the (un-)mount process ... or any device that is "automounted".
Do this experiment to see for yourself:
Manually mount a partition ( unmount one if mounted in fstab, and re mount maually)
back out of the desk top to a terminal:
close the DE down:
```

sudo service lightdm stop

``` assuming you are using unity ... gnome -> use gdm or other for other DE
now issue the terminal command:
```

lsof /dev/sda5 

``` substitute "sda5" for the partition you mounted.
now copy some trivial file to the some location in "sda5" ....
run the lsof command again ...see that file you copied is still listed as open ????
Because it is !... linux utilizes file system caching for efficiency and the cache is not flushed out to the device until it is (un-)mounted.
In this instance, linux expects you to know what you are doing ... and as you opened that device, linux expects you to -when you are done doing - to close it out... thus the "umount" command. When you then shut down with out (un)mounting, this data may not have been written out, and the file system is left in a dirty state.

Now when you do inappropriately shut the system down ... any devices left open are marked as dirty, and when you restart the system, "clean up" may or may not get done correctly as the system now has no way to recover the missing data.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]
see:
```

man lsof

``` for full disclosure.

---

### Post by Morbius1 on 2013-08-06
This seems to be a divergence from the original topic but a shutdown invokes a umount of all mounted partitions using /etc/init.d/umountfs.

If it's listed in /proc/mounts then it should safely unmount it on it's own. Mind you, I religiously unmount all usb / external devices anyway because I'm neurotic ;)

---

### Post by Tom 6 on 2013-08-06
Hi :)
Ok, so that's the side-issue resolved imo.  

Since i have never umounted partitions and not had problems it's largely just been my good luck but it's likely the other users of the o.p.s (=original poster, right?) machine will also be lucky too.  The system is very robust, much more so than Windows, but even so it is worth keeping back-ups if at all possible even if it's only of the most critical files on Ubuntu One or something like that.  

Long term and more experienced users often worry about things that are so incredibly unlikely that people just moving away from Windows wouldn't really notice even if they did get walloped by it.  

So, i think the op doesn;t really need to worry about this side issue too much, especialy wrt the other users of the machine.  I will make more effort to umount before shutting down and my ugess is that the op will too, when they have a chance.  

In the meantime we need to focus back on the original problem as the others have been doing.  

Btw thanks Morbius1 and Bashing-om for raising the side-issue and for showing how to deal with it.   
Thanks and regards from 
Tom :)

---

