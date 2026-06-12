---
title: "Can't delete songs, Rhythmbox, file permissions, fstab"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by snuffy on 2008-08-25
my hard drives wouldn't automount on startup, so i edited my fstab to add the bottom three lines:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=00a935f6-e0dc-472e-8435-baf164f295af /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=9365209b-fb6c-48fa-bee7-f8002d713467 /home           ext3    relatime        0       2
# /dev/sdb2
UUID=4567142f-63fe-4746-8502-0d4fe2e1c445 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/sdc1 /media/185F32 vfat defaults,umask=007,gid=46 0 0 
/dev/sda1 /media/drive1-37GBwin ntfs-3g defaults,umask=007,gid=46 0 0 
/dev/sda5 /media/drive1-37GB ntfs-3g defaults,umask=007,gid=46 0 0 
```

now my hard drives automount at startup, but the read/write permissions are wrong i think, because in rhythmbox for example i cannot now send songs to the trash. (my music is on the sdc1 by the way)

when i try to delete a file from these drives i get the error:
Cannot move file to the Deleted Items folder, do you want to delete permanently?

what have i done wrong?

---

### Post by Crafty Kisses on 2008-08-25
Do you get any errors?

Now if they are in your trashcan and you can't just empty it, try this:

-Do Alt+F2
-Type gksudo nautilus and enter your password
-You should now be in your root folder
-Navigate to your home folder and enter the hidden folder .Trash (To view hidden files and folders do Ctrl+H)
-Delete the files
-Go back to the Root folder
-There is a .Trash in there as well if it doesn't show try Ctrl+H again
-Now delete the files from there as well
-They should be gone for good at this point

Hope this helps...

---

### Post by snuffy on 2008-08-25
sorry, its not a problem of deleting the trash folder, that works ok, 

its when i right click a file in rhythmbox>move to deleted items, nothing happens.

also when i try to delete a file from these drives in nautilus i get the error:
Cannot move file to the Deleted Items folder, do you want to delete permanently?

it worked an hour ago before i set my drives to automount on startup, so it must be something i did wrong in the fstab file, only i don't know what.

---

### Post by regala on 2008-08-25
> **snuffy said:**
> sorry, its not a problem of deleting the trash folder, that works ok, 

its when i right click a file in rhythmbox>move to deleted items, nothing happens.

also when i try to delete a file from these drives in nautilus i get the error:
Cannot move file to the Deleted Items folder, do you want to delete permanently?

it worked an hour ago before i set my drives to automount on startup, so it must be something i did wrong in the fstab file, only i don't know what.

The problem is that you have no right to write on your disks, assuming you mount your disks acording the fstab file:
/dev/sdc1 /media/185F32 vfat defaults,umask=007,gid=46 0 0 
/dev/sda1 /media/drive1-37GBwin ntfs-3g defaults,umask=007,gid=46 0 0 
/dev/sda5 /media/drive1-37GB ntfs-3g defaults,umask=007,gid=46 0 0

these filesystems are win32 fs's and do not have any notion of owner or group owner; by default, root owns your FAT or NTFS filesystems.
Either the fs's contain a .Trash folder and *you* (not root) try and fail to write in them and on the disk, or you have no .Trash folder in it, and it fails to create it.

When you automount, this is on the account of *your* session and the system use *pmount* to mount and set the right *permissions*.

You have to add on each win32 filesystem line, uid=<your_user_login> with the other options.

By the way, switching to such a system is a regression, you wouldn't be able to "umount" it as a simple user (unless you specify user option again in fstab...) with the GUI... This is just my opinion :)

---

### Post by snuffy on 2008-08-25
thanks for your replies everyone, 

i changed my fstab lines to this...

```
/dev/sdc1 /media/185F32 vfat defaults,umask=007,gid=46 0 0 uid=snuffy
/dev/sda1 /media/drive1-37GBwin ntfs-3g defaults,umask=007,gid=46 0 0 uid=snuffy
/dev/sda5 /media/drive1-37GB ntfs-3g defaults,umask=007,gid=46 0 0 uid=snuffy
```

but it still doesn't work.

---

### Post by AGSzabo on 2008-10-18
what you do is this:
/dev/sdc1 /media/185F32 vfat defaults,umask=007,gid=46 0 0 uid=snuffy

what you need to do however is this:
/dev/sdc1 /media/185F32 vfat defaults,umask=007,gid=46,uid=snuffy 0 0

you got the difference?

i know what to do since i got the same problem with moving files to the trash. i've found this thread and did what really was to do correctly.

---

### Post by snuffy on 2008-10-18
thanks, i'll try it.



> **AGSzabo said:**
> what you do is this:
/dev/sdc1 /media/185F32 vfat defaults,umask=007,gid=46 0 0 uid=snuffy

what you need to do however is this:
/dev/sdc1 /media/185F32 vfat defaults,umask=007,gid=46,uid=snuffy 0 0

you got the difference?

i know what to do since i got the same problem with moving files to the trash. i've found this thread and did what really was to do correctly.

---

### Post by gerhard83 on 2009-09-17
Thank you AGSzabo, that helped me!

>what you need to do however is this:
>/dev/sdc1 /media/185F32 vfat defaults,umask=007,gid=46,uid=snuffy 0 0

---

### Post by v1nsai on 2009-09-21
THANK YOU SO MUCH for the info on using gid or uid to specify ownership of ntfs and fat systems.

I have gone through every music player I can find trying to find one that would let me change tags on my music so that I can organize them and NOTHING would work because I didn't have ownership of the drive, even though I thought I did.  I just thought I had angered repo gods that were sending me bad .debs or something.  I've been stumped for months.

So happy :guitar:

---

### Post by hic3456 on 2010-03-14
I have a similar issue, which I think is somehow related to how I mount an external USB drive, but can't quite figure out what am I doing wrong.

The actual HD is an external USB drive, connected to a Ubuntu server machine and ext3 formatted; I can happily access it and the various folders on the disk have the permissions I expect them to have.

The [FONT="Courier New"]/etc/fstab[/FONT] on my Ubuntu (Karmic) desktop looks as follows:

```
sshfs#marco@rohan:/media/data/shared/media    /media/multimedia  fuse     users,auto    0 0
```

(rohan is mapped in [FONT="Courier New"]/etc/hosts[/FONT] to map the server's local IP and all is sunshine and ponies).

However, the drive does not "automount" at boot, and I have to "manually" mount (the easiest is to just click on a shortcut on the desktop and I can then see it on the file browser etc. with no problems) or I can just 
```
mount /media/multimedia
```
(no sudo) and it all works fine again.

However, for some weird reason, Rhytmbox seems to be believe that I have no write permission on the music folder I point it to, and refuses to change any of the properties on any of the songs.

I have actually tried to change the prefs' to point to my local /home/marco/music folder, adding a few mp3s in that folder, and I can happily change the file's ID3 tags without any problem.

Hence, I *know* it's something to do with mounting remotely with sshfs, but can quite figure out what to change (given that permissions are just fine when I try to access the folder -- which is, incidentally, shared across several computers at home, including a few Macs, so I don't want to mess around with it too much).

Ideas?

I've filed a bug with Rhytmbox ([https://bugzilla.gnome.org/show_bug.cgi?id=612869](https://bugzilla.gnome.org/show_bug.cgi?id=612869)) as I think it should respect the file's permissions like every other app under Gnome.

---

### Post by Teh_Messiah on 2011-12-27
I am having a similar problem but don't know why I cant [Move to Trash] or [Remove] from Rhythmbox.

[LIST=1]
[*]I'm running Xubuntu 10.10 as a file server/web server.
[*]I manually installed Rhythmbox through Synaptec packet manager.
[*]I have 2x 2Tb Raid5 arrays storing files.
[*]I have another 2Tb drive which has all my music and some backups stored on it.
[/LIST]
These are all mounted in fstab as
```
# /dev/sda1: UUID="1188ccca-6bb7-4e26-bca7-aec168f214ac" TYPE="ext3"
UUID=1188ccca-6bb7-4e26-bca7-aec168f214ac       /home/share1    ext3    defaults        0       0
# /dev/sdb1: UUID="0b977015-e6de-4097-9013-023e70a6322d" TYPE="ext3"
UUID=0b977015-e6de-4097-9013-023e70a6322d       /home/share2    ext3    defaults        0       0
# /dev/sdc1: UUID="473c9a37-c34b-4b6e-bbdd-7b114edca4f1" TYPE="EXT3"
UUID=473c9a37-c34b-4b6e-bbdd-7b114edca4f1       /home/Downloads ext3    defaults        0       0

```
I can [Move to Trash] or [Remove] from Rhythmbox, however when I restart Rhythmbox it detects the songs again and plays them. I have to manually find the songs in their albums and delete them that way.
```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdd1              29G  5.1G   22G  19% /
none                  1.9G  264K  1.9G   1% /dev
none                  2.0G  4.8M  2.0G   1% /dev/shm
none                  2.0G  708K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
/dev/sdd2              42G   18G   22G  45% /home
/dev/sda1             1.8T  1.2T  549G  69% /home/share1
/dev/sdb1             1.8T  1.6T  145G  92% /home/share2
/dev/sdc1             1.8T  1.6T  183G  90% /home/Downloads
```
It's very frustrating trying to remove double ups of files or old copies of files and some songs I have more than 5 copies of yet can't remove them!
Help Please?

---

### Post by Teh_Messiah on 2012-03-02
Bump!

---

