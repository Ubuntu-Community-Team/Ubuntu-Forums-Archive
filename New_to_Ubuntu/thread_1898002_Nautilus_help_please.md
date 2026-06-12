---
title: "Nautilus help please"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by Shenachie on 2011-12-20
nautilus-actions-config

Installed Nautilus ad when entering the above am getting no such command? I took it from thjis page what I was following: [http://www.ubuntu-unleashed.com/2008/01/securely-wipeerase-files-in-ubuntu.html](http://www.ubuntu-unleashed.com/2008/01/securely-wipeerase-files-in-ubuntu.html)

Help appreciated as I have files I need to erase.

Thanks in advance

Shenachie

---

### Post by sudodus on 2011-12-20
What version 10.04 ... 11.10 are you running?
And what flavour
'vanilla' Ubuntu
Kubuntu
Lubuntu
Xubuntu
...
Do you have Nautilus itself? Try from a terminal window
```
nautilus
```

---

### Post by Shenachie on 2011-12-20
11.10. Vanilla.

Nautilus icon shows in the apps window. When I click on it, left or right it vanishes. 

Shenachie

---

### Post by lechien73 on 2011-12-20
There's a bug report files about that here: [https://bugs.launchpad.net/ubuntu/+source/nautilus-actions/+bug/818987](https://bugs.launchpad.net/ubuntu/+source/nautilus-actions/+bug/818987)

Depending on how adventurous you feel, it apparently works ok if you compile it from source: [http://packages.debian.org/source/sid/nautilus-actions](http://packages.debian.org/source/sid/nautilus-actions) :roll:

---

### Post by Shenachie on 2011-12-20
Well that little lot is double Dutch to me so what do you suggest?

Actually what I want to do, and this is where the nautilus matter arose is to delete some files totally. 

Surely there must be a way of doing so with out all the terminal performance?

I have tried dragging the offending files to the waste bin but no permission denied as is the right click menu. 

TBH I am not that interested in the nuts and bolts of Ubuntu, I just wish things would work simply. 

Shenachie

---

### Post by sudodus on 2011-12-20
Usually you can delete files that are selected in Nautilus by pressing the 'Delete' key. If not, it may be because you are not allowed to do it (because it is owned by root (superuser) or is read-only).

If you still want to get rid of it you may need to do some terminal commands. You can drag and drop  the file [FONT=Courier New]/path/name[/FONT] from the icon in Nautilus to the terminal window for your convenience. rm (remove) is the command to delete a file (directly, no detour via the trashcan). So be very careful!

```
sudo rm -i /path/name
```Edit: Maybe you need to repair Nautilus
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get purge nautilus
sudo apt-get install nautilus

```Does this work or will you get errors?

---

### Post by lechien73 on 2011-12-20
If you want to delete the files through the GUI, then you could open a terminal window and type:

```
gksu nautilus
```

This will open a nautilus window with superuser privileges, so you should be able to delete without getting a permission denied error.

Exercise caution using nautilus with elevated privileges though, as someone's signature here on the forums says: "Linux assumes you know what you're doing" ;)

---

### Post by Shenachie on 2011-12-20
Nautilus could not create the required folder "/root/.config/nautilus".

Ho hum this not easy is it?

The software center says Nautilus is installed but is it actually working? When I click on the icon it just disappears, and for sure I have no real idea what I am doing. But I DO know I want to delete these files securely.

Sodocus? I entered in your code and got do you wish to continue Y/N, I entered Y then hit enter key and got abort???

The permissions tab on a file I want gone tells me that as I am not "root" I cannot delete yet I am logged in as admin??

Shenachie

---

### Post by sudodus on 2011-12-20
> **Shenachie said:**
> Nautilus could not create the required folder "/root/.config/nautilus".

Ho hum this not easy is it?

The software center says Nautilus is installed but is it actually working? When I click on the icon it just disappears, and for sure I have no real idea what I am doing. But I DO know I want to delete these files securely.

Sodocus? I entered in your code and got do you wish to continue Y/N, I entered Y then hit enter key and got abort???

The permissions tab on a file I want gone tells me that as I am not "root" I cannot delete yet I am logged in as admin??

Shenachie
There is something that I cannot see (yet). Maybe if you post the output of a few commands, it will be possible to pass over the threshold. It is in order to find out if it is the permission of the file or the file system or the file owner, that is the problem.
```
sudo fdisk -lu
df
``````
cat /etc/mtab
```and for the file(s) you want to delete:
```
ls -l /path/name
```

[I]Edit 1: There is probably something wrong with Nautilus. Did you try to purge and install it?
Edit 2: What exactly do you mean by 'delete these files securely'?[/I]

---

### Post by Shenachie on 2011-12-21
Exactly. I want to remove these files completely. They were on the HD under windows then I installed Ubuntu and as part of the reformat I thought them to be gone. On running CheckDisk I discovered they are still here and I want to ensure they are destroyed as they hold info I need wiped clean. 

sudo fdisk -lu dfDisk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00041974

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   774084607   387041280   83  Linux
/dev/sda2       774086654   781422591     3667969    5  Extended
/dev/sda5       774086656   781422591     3667968   82  Linux swap / Solaris
pete@pete-desktop:~$ 
/dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/pete/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=pete 0 0
ls -l /path/name
ls: cannot access /path/name: No such file or directory

I am guessing that this means that Nautilus is not installed?

Shenachie

---

### Post by sudodus on 2011-12-21
Hi again!

fdisk found
1. the boot partition /dev/sda1 mounted on /  (the system root in linux)
2. an extended partition
3. a swap partition filling the extended partition

/etc/mtab shows that /dev/sda1 is mounted. It would have been more interesting if there were several partitions.

But the following was an attempt to make you type in the actual directory path and the actual name of one of the files that you are searching for (and not finding with Nautilus).
```
ls -l /path/name
```I still think that Nautilus is not working.

But maybe we should get going with deleting the files. One way would be to overwrite the drive completely with random 01001111010.... You can wipe the partitions like that using [B]*shred.*
[/B]
If you want to reinstall linux anyway, this is a good option.

Are the old files visible in the linux file system, or is  it only the file content, that is still there on the hard drive?

If the files are there, you can delete them with ***shred***.

If only the file content is there, you can overwrite all empty space is the linux partition with dd:
```
 sudo dd if=/dev/zero of=/blank bs=4096
``` and after that delete the file /blank
```
sudo rm /blank
```Now all empty space is 000000000... on the linux partition but not on the swap partition. You can wipe that partition too, but I don't know if that means that you have to make a new swap partition (in the same place) which means a new UUID and that you have to make changes in a couple of configuration files. The swap partition is at the end of the drive. Do you think that the files you want to delete completely were there?

---

### Post by Shenachie on 2011-12-21
Hi back.

Thanks for all your help. 

I have checked the directories that the recovery program created and there is nothing there I need. 

I would like to utterly and totally wipe the HD then do a fresh install of Ubuntu. 

How do you suggest I do that please?

Shenachie

---

### Post by sudodus on 2011-12-22
> **Shenachie said:**
> Hi back.

Thanks for all your help. 

I have checked the directories that the recovery program created and there is nothing there I need. 

I would like to utterly and totally wipe the HD then do a fresh install of Ubuntu. 

How do you suggest I do that please?

Shenachie

*Edit: You must boot your computer from a live CD or USB drive (because you will overwrite the entire hard disk drive including system files, space for temporary files, swap area).*

Assuming that you still have only one hard drive in your computer:

```
sudo dd if=/dev/zero of=/dev/sda bs=4096
```Read ```
man dd
``` for details

*Edit: and wait, it takes hours ...*

---

### Post by sudodus on 2011-12-22
And you have to wait ... it takes hours. If it is hard to wait, check the progress of dd using [FONT=Courier New]kill -USR1 $pid[/FONT] from *another* terminal window.

example:
```
ps -au root | grep dd
...
 [COLOR=Red]9877[/COLOR] pts/0    00:03:02 dd
```use this [COLOR=Red]red[/COLOR] process id number (in your case some other number)
```
sudo kill -USR1 [COLOR=Red]9877[/COLOR]
```and dd will print three status lines, something like
```
38775841+0 posts in
38775840+0 posts out
158825840640 bytes (159 GB) copied, 15054.6 s, 10.6 MB/s
```This can be repeated when you get curious again:
```
sudo kill -USR1 [COLOR=Red]9877[/COLOR]
``` and you get three new status lines.

Good luck :smile:

---

### Post by Shenachie on 2011-12-22
sudo dd if=/dev/zero of=/dev/sda bs=4096
man dd

Entered above in terminal which is via a live cd and absolutely nothing is happening??? Nor did it ask for the p/word which is suspicious?

Ah things seem to be moving now so I am off.... thanks again.

Shen

---

### Post by sudodus on 2011-12-22
> **Shenachie said:**
> sudo dd if=/dev/zero of=/dev/sda bs=4096
man dd

Entered above in terminal which is via a live cd and absolutely nothing is happening??? Nor did it ask for the p/word which is suspicious?

Ah things seem to be moving now so I am off.... thanks again.

Shen
[FONT=Courier New]man dd[/FONT] is only to give you a look behind the curtain. And dd is working, not making noise. But you can push it to print those three status lines according to my 'extra post'. If you doubt that it is working, do that [FONT=Courier New]sudo kill -USR1 $pid[/FONT] pushing!

The live CD or USB systems usually demand no password at login or sudo, that is OK :-)

---

