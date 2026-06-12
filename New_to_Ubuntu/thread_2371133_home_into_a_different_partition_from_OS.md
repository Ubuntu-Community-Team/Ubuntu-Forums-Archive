---
title: "home into a different partition from OS"
date: 2017-09-11
forum: New to Ubuntu
---

### Post by pagno2 on 2017-09-11
As most users while installing ubuntu 16.04.3 I made two partitions, one for the OS and the other for the data. I did it during installation and modified with Gparted.
Now I am going to put all may data into the 'free space' space partition, that I called data.
To make it simple I'd like to click on 'documents' within 'home' e let the data file pop up.
I read many threads such as this one [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
However now with Gparted I can't mount home into the free space partition. See attachment.
Isn't there an easy way to do it?
Kind of changing the path and that's it?
GA

---

### Post by Impavidus on 2017-09-11
The guide you linked to ([https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)) explains exactly what you should do to create a /home partition. It's not very hard, probably the easiest and safest way to do it, but it's best if you understand what you're doing. So, could you tell us at which step you get stuck?

---

### Post by oldfred on 2017-09-11
As Impavidus suggests using /home is probably better for newer users. Very new users can just use the /home that is inside / (root). 
Bit more advanced then is a separate /home partition.
It is a separate partition, automatically mounted in fstab, givers user correct permissions and ownership all automatically if done during install.

But if more advanced or want to learn you can use a separate data partition. 
You have to create a mount point like /mnt/data. It will default mount with /media/$USER/data if data is your label or by UUID, but that will not auto mount when you reboot. And that will break links.
And then edit fstab with that mount point /mnt/data.
You have to give yourself ownership & permissions for all files & folders in the data partition.
First time you have to create all the folders you need or want in your data partition, like Music, Documents, etc.
Then you can link all your folders into /home so they look and work just like the folders in /home but data is really in another partition, often even on another drive.

Details:
Mounting & fstab:
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. 
Linking, I call it a shared data partition as I have multiple installs and link same data into all of them:
      
 [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by pagno2 on 2017-09-11
OK thanks. With a bit of commitment I'll do it.
I got stuck at an early stage.
1. after the 'Find the uuid of the Partition' in terminal I got few lines, basically the informations I get from Gparted plus a bulk of numbers I don't really know what to do with. Have I got what I already knew from Gparted, which is that my data are at /dev/sda4, or will I use the long numbers when doing the 'Setup Fstab'?
2. I don't understand the 'sudo cp /etc/fstab /etc/fstab.$(date +%Y-%m-%d)' command, what numbers/text I'm supposed to put instead of '$(date +%Y-%m-%d)' ?
3. further on I'll have to understand what to write in place of ????????, what part of the uuid I got at point 1?
4. I am currently not able to see the partition, not even from the 'computer', I just see from 'files' what is in the OS partition; nor I'm able to see an external hard drive (I can see it in windows).
GA

---

### Post by deadflowr on 2017-09-11
> 2. I don't understand the 'sudo cp /etc/fstab /etc/fstab.$(date +%Y-%m-%d)' command, what numbers/text I'm supposed to put instead of '$(date +%Y-%m-%d)' ?
If you don't want to use the date just use .bak or .old
like
```
sudo cp /etc/fstab /etc/fstab.old
```
all you're doing is creating a backup copy of fstab, in case things go south.

Also...
don't use the suggested command to sudo gedit.
install gksu
```
sudo apt install gksu
``` 
and use that, or
use sudo with the -H option/flag
```
sudo -H gedit blahblahblah-some-filename
```

---

### Post by oldfred on 2017-09-11
Are you using partition as data partition or moving /home to the sda4 partition?

UUID is a unique identifier for a partition. Then if drive order changes which with many systems it seems to when a flash drive is plugged in, the mount does not change, so it keeps working correctly.

You use the entire UUID from the blkid command as the entry in fstab.
fstab must have specific fields in order, that is why templates are usually suggested and then just edit with your UUID, and mount or perhaps changed parameters. Example in move home link shows ext3 format, much better to use extg4 now, and then entry in fstab must be ext4, not ext3.
see also
man fstab.

---

### Post by pagno2 on 2017-09-11
OK thanks a lot
1. I got the first point and I duplicated [COLOR=#000000]fstab. Don't really know where it is, as in terminal nothing nothing happened, but I suppose it did it.
2. I had already installed gksu
3. I edited [/COLOR]sudo -H gedit /etc/fstab and this popped up
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=92bfc2f1-ea36-4bf4-a078-0e3ed2f53832 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=A03B-ACCF  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=48177c93-6a2e-42dd-9429-6e6d4d4f7807 none            swap    sw              0       0
```

---

### Post by pagno2 on 2017-09-11
sorry but I am an intense yet shallow user of the PC, either windows or ubuntu and this is the first time I go into the boot realm.
As for your answer I suppose I am just trying to move /home to the sda4 partition.
GA

> **oldfred said:**
> Are you using partition as data partition or moving /home to the sda4 partition?

UUID is a unique identifier for a partition. Then if drive order changes which with many systems it seems to when a flash drive is plugged in, the mount does not change, so it keeps working correctly.

You use the entire UUID from the blkid command as the entry in fstab.
fstab must have specific fields in order, that is why templates are usually suggested and then just edit with your UUID, and mount or perhaps changed parameters. Example in move home link shows ext3 format, much better to use extg4 now, and then entry in fstab must be ext4, not ext3.
see also
man fstab.

---

### Post by deadflowr on 2017-09-11
> 1. I got the first point and I duplicated fstab. Don't really know where it is, as in terminal nothing nothing happened, but I suppose it did it.
You'll have the dupe in /etc
```
ls /etc
```
should now list an fstab and fstab.whatever
They try to make it so it only outputs something when things go bad.
No news is good news.

---

### Post by pagno2 on 2017-09-11
Good
:)
catching up

1. applying 'ls /etc' something happened and I saw a lot of numbers in different colors.

2. Then I wrote 'sudo -H gedit /etc/fstab' and the fstab window popped up (see below). In my understanding it gives you the UUID for every partition.
I spot a creepy 'UUID=92bfc2f1-ea36-4bf4-a078-0e3ed2f53832 /               ext4    errors=remount-ro 0       1'
dunno what it means, but I don't like it.

3. I do not see the sda4, the very partition where I am supposed to relocate the home
GA

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=92bfc2f1-ea36-4bf4-a078-0e3ed2f53832 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=A03B-ACCF  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=48177c93-6a2e-42dd-9429-6e6d4d4f7807 none            swap    sw              0       0
```

---

### Post by deadflowr on 2017-09-11
> I spot a creepy 'UUID=92bfc2f1-ea36-4bf4-a078-0e3ed2f53832 / ext4 errors=remount-ro 0 1'
dunno what it means, but I don't like it.
Learn to like it, that's the main entry.
It's output is normal

the UUID is the device, partition.

the / is the mount point, showing that the UUID is to be mounted as the / directory; the  / is the top most level, aka root.

ext4 is the file system type, like fat or ntfs, but linux-centric.

the errors=remount-ro is the option settings, basically it's saying that if an error occurs when trying to mount the partition to the mount point, it'll then try to remount the system read-only so you can diagnose problems without fear of causing further damage.

the first 0 is the dump entry, unless you know anything about file system dumps, leave as is.

the last 1 is the file system checking settings.
1 means it'll be the first file system to be checked, any other should list as 0 ( no check) or 2.

---

### Post by oldfred on 2017-09-11
If you are moving /home then you need to follow the procedure in the link you posted in first post.
I think it does a temporarily setting in fstab so you can copy all your data without causing issues with current /home folder & mount.
Then after copying data, you edit fstab to change from temporary mount to the permanent mount of /home in fstab.

You need to follow procedure exactly, just changing UUIDs partitions or formats (ext3 to ext4 for example) to match your configuration.
If issue with any step post details.

---

### Post by pagno2 on 2017-09-11
Stuck at the very beginning.
Already when writing 'cmp /etc/fstab /etc/fstab.old' nothing happens. Then when comparing the two fstab files 'cmp /etc/fstab /etc/fstab.old' nothing happens either.
GA

---

### Post by oldfred on 2017-09-11
When I run cmp, I also get no output. That must mean they match as when I run it against an older fstab backup that is different.
```
fred@Asusz97:~$ sudo cmp /etc/fstab /etc/fstab.backup
/etc/fstab /etc/fstab.backup differ: byte 431, line 9

```

You can also just look at file
 cat /etc/fstab.$(date +%Y-%m-%d)

Or confirm file is there:
```
fred@Asusz97:~$ sudo ls -l /etc/fstab*
-rw-r--r-- 1 root root 1013 Nov 22  2016 /etc/fstab
-rw-r--r-- 1 root root 1013 Sep 11 17:08 /etc/fstab.2017-09-11
-rw-r--r-- 1 root root  845 Apr 17  2016 /etc/fstab.backup


```

---

### Post by pagno2 on 2017-09-11
Trying to keep up.
Should I save the fstab as follows?
Not that sure.
GA
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=92bfc2f1-ea36-4bf4-a078-0e3ed2f53832 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=A03B-ACCF  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=48177c93-6a2e-42dd-9429-6e6d4d4f7807 none            swap    sw              0       0
# /home was on /dev/sda4 during installation / ext4 (some settings) 
UUID=4fa2612b-5e28-4852-8121-56a0cc837c89   /media/home    ext3          defaults       0       2

```

---

### Post by QIII on 2017-09-11
Please use code tags.

---

### Post by pagno2 on 2017-09-11
not that sure

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
# / was on /dev/sda2 during installation
UUID=92bfc2f1-ea36-4bf4-a078-0e3ed2f53832 / ext4 errors=remount-ro 0 1
# /boot/efi was on /dev/sda1 during installation
UUID=A03B-ACCF /boot/efi vfat umask=0077 0 1
# swap was on /dev/sda3 during installation
UUID=48177c93-6a2e-42dd-9429-6e6d4d4f7807 none swap sw 0 0
# /home was on /dev/sda4 during installation / ext4 (some settings) 
UUID=4fa2612b-5e28-4852-8121-56a0cc837c89 /media/home ext3 defaults 0 2
```

---

### Post by pagno2 on 2017-09-11
Moreover in terminal I get this message
```

pagno@pagno:~$ sudo -H gedit /etc/fstab

(gedit:3742): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (gedit:3742): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported

```

---

### Post by oldfred on 2017-09-11
Code tags are easy to add with Forum's advanced editor and # icon.
 How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168) 

Is not your sda4 formatted with ext4 not ext3? You have to modify examples with your actual format & UUID.
And this mount is so you can copy files in /home (that is inside / currently) to new partition which will be new /home? As final mount would be just /home.
Did you make the mount point /media/home as that now is not a default. Defaults have added the user to the auto mount. Like /media/$USER/[UUID] or label. Where $USER is you. to see that:
echo $USER

---

### Post by pagno2 on 2017-09-12
Thanks
1. OK for the code tags, I'll do it and I modified it in the last post.
2. From what I see in Gparted it is ext4. Should/need/can I change it?
3. >  And this mount is so you can copy files in /home (that is inside / currently) to new partition which will be new /home? As final mount would be just /home. 

Did not understand the question, nor the suggestion. E.g. what is '/currently'?
echo $USER gives out the proper user name.
4. >  Did you make the mount point /media/home as that now is not a default. Defaults have added the user to the auto mount. Like /media/$USER/[UUID] or label. Where $USER is you. to see that:
echo $USER 
Didn't understand. Sorry. Below is the last part of the code I am supposed to change in fstab. I followed the instructions in the dedicated post but I guessed most of the entries and I don't quite think it is right. Pretty sure current location of home is sda2 (OS partition) and I need to relocate it to sda4 (free space partition). Both partitions are ext4. At least this is what I see in Gparted.
Don' know: (identifier) (some settings) and global accuracy of the script. I don't even know if I have to leave the brakets.

```
# (identifier)  (location, sda4)   (format, ext4)      (some settings) 
UUID=4fa2612b-5e28-4852-8121-56a0cc837c89   /media/home    ext4          defaults       0       2 
```

---

### Post by oldfred on 2017-09-12
Anytime you edit fstab, you should run this:
sudo mount -a

If it just returns then your edits are ok, but if an error you must fix it before rebooting or you will have issues.

Post this, just so we can confirm UUIDs:
       sudo blkid -c /dev/null -o list 

I was asking what step you were at. And wanted to make sure you did not think that was the final  mount of your /home.
Ubuntu used to automatically mount (unmounted) partitions when clicked on at /media/UUID or label so that was a default mount. But they changed to use /media/$USER/UUID or label. 
Had not reviewed instructions & now see that you run a command to mkdir /media/home so it is ok and not expecting a default mount location.

Have you copied data yet?

---

### Post by pagno2 on 2017-09-12
1. I neither copied data nor saved the fstab.

2. '[COLOR=#000000]sudo mount -a'
just returns, so I assume it is ok[/COLOR]

3. '[COLOR=#000000]sudo blkid -c /dev/null -o list'
as below[/COLOR]

```
pagno@pagno:~$ sudo blkid -c /dev/null -o listdevice     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  vfat             /boot/efi      A03B-ACCF
/dev/sda2  ext4             /              92bfc2f1-ea36-4bf4-a078-0e3ed2f53832
/dev/sda3  swap             [SWAP]         48177c93-6a2e-42dd-9429-6e6d4d4f7807
/dev/sda4  ext4             (not mounted)  4fa2612b-5e28-4852-8121-56a0cc837c89



```

---

### Post by oldfred on 2017-09-12
Then mount is ok and UUIDs match.

---

### Post by pagno2 on 2017-09-13
Ok
indeed I now see the free data partition.
Now I have to relocate home to that partition, don't I?
Is the following code the one I'm supposed to add to the last line of fastb?
```

# (identifier)  (location, sda4)   (format, ext4)      (some settings) 
UUID=4fa2612b-5e28-4852-8121-56a0cc837c89   /media/home    ext4          defaults       0       2

```

---

### Post by oldfred on 2017-09-13
I thought you already added that to fstab.
That is why the check to confirm it was ok with sudo mount -a command.

Once mounted then you can copy data.

---

### Post by pagno2 on 2017-09-13
Not working
code added must e wrong, this is what happens after [COLOR=#000000][FONT=&quot]sudo -H gedit /etc/fstab[/FONT][/COLOR]

```
pagno@pagno:~$ sudo -H gedit /etc/fstab[sudo] password for pagno: 


(gedit:4523): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


** (gedit:4523): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-enabled not supported


** (gedit:4523): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported



```

---

### Post by oldfred on 2017-09-13
I also get various error messages but it works.
If not able to update using sudo -H gedit, try this.
sudo nano /etc/fstab

That requires you to use arrow keys to move to where you want to edit. 
Terminal type paste with control, shift, v all at once works to paste.

---

### Post by pagno2 on 2017-09-13
I did it. Not working.
Home is still where it was as when checking properties of documents in home it shows the capacity of the OS partition and not the 900 and some GA of the free space partition.
Are you sure the code I added to fstab (last two lines) is good? It doesn't look like good to me
GA
```

# (identifier)  (location, sda4)   (format, ext4)      (some settings) 
UUID=4fa2612b-5e28-4852-8121-56a0cc837c89   /media/home    ext4          defaults       0       2

```

---

### Post by oldfred on 2017-09-13
That is not yet your /home, it is the partition you copy data from /home that is currently inside your / Partiiton.
Does this not show any errors?
sudo mount -a

You still are at the beginning of the copy to new /home process, go back to link and look at all the steps again.

---

### Post by pagno2 on 2017-09-14
[COLOR=#000000]1. things went south when I followed the last step, that is deleting old home.
[/COLOR][COLOR=#000000]2. 'sudo mount -a' never showed any error but ...
Now I have no access to the PC after PW login.
Suppose I have to reinstall OS in the dedicated partition an go back to the start.
GA[/COLOR]

---

### Post by oldfred on 2017-09-14
You just about always can fix Ubuntu unless hardware failure, but many times it is quicker to reinstall and restore data from your backups. You do have backups?

And if you want a separate /home partition, you have to use the Something Else install option. And if /home has data you still choose it (change button) but DO NOT check the format box or else it is erased.

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing) 

 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

---

### Post by pagno2 on 2017-09-20
Reinstalled everything without any data partition. Bought a cloud space back up for data storage. I do not think I'll try again to put up a partition.
Everything works fine this way.
GA

---

