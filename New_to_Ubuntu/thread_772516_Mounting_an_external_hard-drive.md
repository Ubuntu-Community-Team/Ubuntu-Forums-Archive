---
title: "Mounting an external hard-drive"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Stochastics on 2008-04-28
Hi, 

I have an external USB hard drive and i want that Ubuntu 8.04 recognize it when i plug it...I haven't any problems with 7.10...someone can help me plz ?

Stochastics

---

### Post by bribri124 on 2008-04-28
I guess it depends on what problems you are having.  So allow me to ask you a few questions and we shall determine what the problem is.

[LIST=1]
[*]Is your drive listed in fstab?
[*]What file system does your drive use?
[*]Do you keep your drive plugged in all the time?
[*]What error(s) did you get when you tried to plug it in?
[/LIST]

I keep my ext drive plugged in at all times, and I had no problems after upgrading.  So let's get some specifics on your issue and resolve it.

---

### Post by Stochastics on 2008-04-28
Hi, 

Thanks for your fast answer.

1. Where is located fstab ?
2. I use Ubuntu 8.04 with ext3 file system
3. I don't let my external hard drive always plug in.

Stochastics

---

### Post by Stochastics on 2008-04-28
and..

4. In Ubuntu 7.10, when i plugged in my external hard-drive, i have a pop-up icon on my desktop that allowed me to browse the folders in it...with Ubuntu 8.04, i don't see anything.

---

### Post by bribri124 on 2008-04-28
Here is how to access fstab:
```
sudo gedit /etc/fstab
```
Additionally, I meant the file system that's on your ext drive.  Have you used this drive with any Windows systems?  In order for you to determine that, enter:
```
sudo fdisk -l
```
What happens when you do plug the drive in?

---

### Post by bribri124 on 2008-04-28
Thanks for that answer!  Not quite sure why Hardy is acting like this.  Here is what you can do:
```
sudo fdisk -l
```
Determine which one is your ext drive, then we can mount it:
```
sudo mount /dev/your_drive /media/drive_destination
```
Let me know what happens.

---

### Post by Stochastics on 2008-04-28
Ok, when i type "sudo /etc/fstab", i obtain the following :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=d3020aa8-b3f5-4b0f-86e9-81e0d688e5f5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=94F87F7CF87F5B84 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=b6370922-3b79-4468-9821-ed5a1f5257f2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Now, my external hard-drive use a FAT32 file systems i think.

sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc4bbc4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       12161    66966952+   5  Extended
/dev/sda5            3825       11906    64918633+  83  Linux
/dev/sda6           11907       12161     2048256   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x32570eef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5168    39070048+   c  W95 FAT32 (LBA)

---

### Post by bribri124 on 2008-04-28
Sorry for the late reply, girlfriend forced me to get her coffee.  Since you don't keep your ext drive plugged in all the time, there's no need to add an entry to fstab.  Let's do this:
```
sudo mount /dev/sdb1 /media/drive_destination
```
Just mount your ext drive to the directory under /media and you should be connected.

Let me know what happens.

---

### Post by Stochastics on 2008-04-28
What i need to put in the place of /drive_destination ?

---

### Post by Bloch on 2008-04-28
Did you update online to Hardy 8.04?
Do you get the message: > Cannot mount volume.
Invalid mount option when attempting to mount the volume. ?

If so the solution below is required:

Open Applications > System Tools > Configuration Editor

Go to the key system > storage > default_options > vfat
Edit the mount_options key by removing the usefree option.

T> his bug was fixed in the package gnome-mount - 0.7-2ubuntu2

---------------
gnome-mount (0.7-2ubuntu2) hardy; urgency=low

* debian/patches/ubuntu-default-mount-options.patch: Drop VFAT option
'usefree', it's not necessary any more with the current Hardy kernel,
and incompatible with pre-gutsy kernels. (LP: #151025)

-- Martin Pitt <email address hidden> Mon, 03 Mar 2008 15:54:25 +0100

---

### Post by Stochastics on 2008-04-28
Hi,

Yes i have Ubuntu 8.04 but i don't have the menu Configuration Editor in the System Tools menu :(.

I did an online upgrade of 7.10 to 8.04.

---

### Post by bribri124 on 2008-04-28
It sounds like you don't have a directory under /media.  If that is the case, we shall create one.
```
sudo mkdir /media/directory_name
```
Replace 'directory_name' with whatever name you would like.  Now lets set permissions for your new directory.  These permissions are probably already set, but let's do it just to be safe.
```
sudo chmod 755 /media/directory_name
```
Now we shall mount your ext drive to your new directory.
```
sudo mount /dev/sdb1 /media/directory_name
```
If you would like to have full permissions for everything within your ext drive, i.e. add new directories, remove files/directories, without using **sudo**, these permissions will take care of that for you.
```
sudo chmod -R 777 /media/directory_name
```
Now if you are getting different error messages, we may have to try something else.  If your error is what Bloch stated, use his method.  You can start by doing this in your terminal:
```
gconf-editor
```

---

### Post by Stochastics on 2008-04-28
Ok, 

I created the folder named PHOTON (the label of my external hard-drive) in the /media folder with the allowed permissions as noted.

When I do the following code, I have the error :

steeve@steeve-laptop:/media$ sudo mount /dev/sdb1 /media/PHOTON
mount: you must specify the filesystem type

---

### Post by bribri124 on 2008-04-28
> steeve@steeve-laptop:/media$ sudo mount /dev/sdb1 /media/PHOTON
mount: you must specify the filesystem type
Use this command to specify the ext drive file system.
```
sudo mount -t vfat /dev/sdb1 /media/PHOTON
```

---

### Post by Stochastics on 2008-04-28
YES ! It works !
I need to do this all the time if i switch between plug/unplug ? Or the system will recognize the drive the next time ?

One more question, when i right-click the desktop icon of my external drive, and i choose the option of unmount it, i have an error :

Cannot unmount volume
Error org.freedesktop.DBus.Error.UnknownMethod

As usual, this thing worked great in Ubuntu 7.10!

---

### Post by bribri124 on 2008-04-28
Use this command to unmount your drive.
```
sudo umount /media/PHOTON
```
I would try unplugging your drive, then plugging back in once it has been unmounted.  I cannot say your system will automatically pick it up, since it didn't do that in the first place.  Since this is the case, I would continue using the same command.

I have a lot of shares on my desktop as well.  Thankfully your terminal will keep these commands so you don't have to retype them every time.

---

### Post by Stochastics on 2008-04-28
OK, thanks a lot for the help !

---

