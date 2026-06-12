---
title: "[SOLVED] External usb drive is sometimes sdb, sdc, sdd"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-10-22
I want to upgrade to Ibex. I should copy /home to an external usb 2.0. Everytime I boot with this usb device attached sudo fdisk -l shows the device with a different /dev name, for example, at the moment, (this session) it's 

mark@Lexington-19:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38536   309540388+  83  Linux
/dev/sda2           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cdf5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux

Is this a feature of the OS? Or is this disk acting screwy?

---

### Post by Vunutus on 2008-10-22
I'm not an expert on this by any means but my guess is that your problem has something to do with the order in which your drives are being mounted. 

Linux file systems follow this naming scheme: type(usually hd or sd) plus drive number (a-z, a is first drive, b is second, etc) plus partition number on that drive. So, hdc5 is the fifth partition on the third IDE drive.

Your external drive is probably getting a different name if it's not always mounted in the same order. I don't know enough to tell you how to fix it, however.

---

### Post by rustutzman on 2008-10-22
Make a backup copy of your /etc/fstab and then edit it using the UUID of the device. That way it will always mount using that info.

Russ

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sdb1
UUID=11150f74-2a63-49d5-83c8-374487ff05f5  /              ext3         defaults,errors=remount-ro  0  1  
#/dev/sdc1
UUID=34deebd6-86fb-4e80-95d8-7fe9e204ca3b  /home          ext3         nodev,nosuid                0  2  
# /dev/sda1
UUID=BA20315B20312035                      /media/sda1    ntfs         defaults,umask=007,gid=46   0  1  
# /dev/sdc1
UUID=48E4806FE4806154                      /media/sdg1    ntfs         defaults,umask=007,gid=46   0  1  
# /dev/sdc2
UUID=5EFA062FFA06044D                      /media/sdg2    ntfs         defaults,umask=007,gid=46   0  1  
# /dev/sdb5
UUID=a4a2ed89-4806-4c21-b632-35e7f6a8e19f  none           swap         sw                          0  0  
# /dev/sde1
UUID=74041752041716A8                      /media/sde1    ntfs         defaults                    0  1 

/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec            0  0  

```

---

### Post by Mark_in_Hollywood on 2008-10-22
> **rustutzman said:**
> Make a backup copy of your /etc/fstab and then edit it using the UUID of the device. That way it will always mount using that info.

Russ

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sdb1
UUID=11150f74-2a63-49d5-83c8-374487ff05f5  /              ext3         defaults,errors=remount-ro  0  1  
#/dev/sdc1
UUID=34deebd6-86fb-4e80-95d8-7fe9e204ca3b  /home          ext3         nodev,nosuid                0  2  


```

Here's the /etc/fstab file, this 80 gig drive isn't showing. Is there no other way to get the OS to "deal" with this? It's not I won't edit fstab, but I must know what to put into the file.

Your example is fine, but in no way reflects my computer parts.

---

### Post by rustutzman on 2008-10-22
With the device plugged in do.
```

sudo blkid

```
Use this info in the fstab then. 

edit: my file was for example only. Use the info from the command to edit your own fstab.

Russ

---

### Post by drs305 on 2008-10-22
Using UUIDs is one solution, using LABELS is another. Since these drives appear to be linux drives (ext2 or ext3), labeling is very easy. Replace XX with the device partition (sdb1, sde1, etc) determined by the 'sudo fdisk -l' command:
```
sudo tune2fs -L **labelname** /dev/sd**XX**
```
Example:  sudo tune2fs -L mydata /dev/sde1

You will have to create the mountpoint (choose a name and replace in the examples), and change ownership to yourself with the following commands:
```
sudo mkdir /media/**mountpoint**
sudo chown -R username:username /media/**mountpoint**
chmod 750 -R /media/**mountpoint**

```

Backup and edit fstab:
```
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```

The entry in fstab format would be:
```

# /dev/sdc1
LABEL=**mydata **/media/**mountpoint**  ext3   defaults,user   0  2  

```

If you would prefer UUIDs, insert the UUDI from the blkid command:
```

# /dev/sdc1
UUID=**3444-3454-3e4r** /media/**mountpoint**  ext3   defaults,user   0  2  

```

Then mount the drive. If it works, you will get no result and the drive will be mounted. If there is a problem, you will be able to read the error message to see what the problem is:
```
sudo mount /dev/sd**XX**
```

---

### Post by Mark_in_Hollywood on 2008-10-23
> **drs305 said:**
> Using UUIDs is one solution, using LABELS is another. Since these drives appear to be linux drives (ext2 or ext3), labeling is very easy. Replace XX with the device partition (sdb1, sde1, etc) determined by the 'sudo fdisk -l' command:
```
sudo tune2fs -L **labelname** /dev/sd**XX**
```
Example:  sudo tune2fs -L mydata /dev/sde1

You will have to create the mountpoint (choose a name and replace in the examples), and change ownership to yourself with the following commands:
```
sudo mkdir /media/**mountpoint**
sudo chown -R username:username /media/**mountpoint**
chmod 750 -R /media/**mountpoint**

```

Backup and edit fstab:
```
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```

The entry in fstab format would be:
```

# /dev/sdc1
LABEL=**mydata **/media/**mountpoint**  ext3   defaults,user   0  2  

```

If you would prefer UUIDs, insert the UUDI from the blkid command:
```

# /dev/sdc1
UUID=**3444-3454-3e4r** /media/**mountpoint**  ext3   defaults,user   0  2  

```

Then mount the drive. If it works, you will get no result and the drive will be mounted. If there is a problem, you will be able to read the error message to see what the problem is:
```
sudo mount /dev/sd**XX**
```

I have used your "label" style. UUID's are too confusing. Attached a screenshot of fstab. Is this correct?

"Then mount the drive" -- At what step was it to be UNMOUNTED?

---

### Post by drs305 on 2008-10-23
> **Mark_in_Hollywood said:**
> I have used your "label" style. UUID's are too confusing. Attached a screenshot of fstab. Is this correct?

"Then mount the drive" -- At what step was it to be UNMOUNTED?

I assume it is /dev/sdb1 you want to mount. The fstab entry should be:
```

LABEL=marks80 /media/*mountpoint* ext3 defaults,user 0 2

```

Is your mountpoint really called 'mountpoint'? Normally users will make the mountpoint name something more descriptive, such as 'mymusic', 'data', etc. You can use 'mountpoint' if you wish...

For your education, any line in fstab (and many other files) which begin with a # symbol is treated as a comment. Nothing on that line will be acted upon. The # symbol is called a 'comment' symbol since it often preceeds comments placed within a file.

The device will not be mounted until you run the command to mount it or until you reboot. The command to mount everything listed in fstab follows. Of course some partitions such as root are already mounted:
```
sudo mount -a
```

If you wanted to unmount a device via the command line, you could unmount all devices allowed (you can't unmount your root partition or /home) or a specific partition:
```

sudo umount -a
or
sudo umount /dev/sdb1

```

---

### Post by Mark_in_Hollywood on 2008-10-23
mark@Lexington-19:/$ sudo mount -a
[mntent]: line 12 in /etc/fstab is bad

output of fstab is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=62e29314-59b3-4ead-95d0-92763420a111 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=755a36f6-c291-4ba2-b502-9304af3be671 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
**/dev/sdb1 marks80 /media/usbdrive  ext3   defaults,user   0  2**

I tried this and named it /media/usbdrive ... is that what I was supposed to do with "label"?

---

### Post by drs305 on 2008-10-23
This is what your fstab should look like:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=62e29314-59b3-4ead-95d0-92763420a111 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=755a36f6-c291-4ba2-b502-9304af3be671 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
**LABEL=marks80 /media/usbdrive  ext3   defaults,user   0  2**
```

For this to work, you have to have labeled /dev/sdb1 as **marks80**
You can check this with:
```
sudo blkid | grep dev/sdb1
```
It should contain:  **LABEL="marks80"**

You should also have a folder: /media/usbdrive
You should have run the following commands (assuming **mark** is your username):
```

sudo mkdir /media/usbdrive
sudo chown -R mark: /media/usbdrive
chmod 755 -R /media/usbdrive

```

Added:
The format for an fstab entry is:
device_name ( /dev/sdXX, label=, or UUID= ) mountpoint  format_type  options  disk_checking_options

---

### Post by drs305 on 2008-10-23
This is what your fstab should look like:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=62e29314-59b3-4ead-95d0-92763420a111 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=755a36f6-c291-4ba2-b502-9304af3be671 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
**LABEL=marks80 /media/usbdrive  ext3   defaults,user   0  2**
```

For this to work, you have to have labeled /dev/sdb1 as **marks80**
You can check this with:
```
sudo blkid | grep dev/sdb1
```
It should contain:  **LABEL="marks80"**

You should also have a folder: /media/usbdrive
You should have run the following commands:
```

sudo mkdir /media/usbdrive
sudo chown -R yourusername: /media/usbdrive
chmod 755 -R /media/usbdrive

```

Added:
An fstab entry includes the following:

device_id ( /dev/sdXX, LABEL= , or UUID= )
mountpoint
format_type
options
dump_option (usually 0)
fsck_option (1 for root - check; 2 for other ext2/3 - check with lower priority than root; 0 for non-ext2/3 partitions)

Here are a couple of references if you wish to learn more about fstab:
[Fstab]("https://help.ubuntu.com/community/Fstab")
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by Mark_in_Hollywood on 2008-10-23
A little weird. Output /media ls -la is:
[B]
drwxr-x---  2 mark mark  4096 2008-10-23 10:33 marks80[/B]
drwx------  3 mark root  4096 1969-12-31 16:00 PRESTON
drwx------  2 mark root 16384 1969-12-31 16:00 UDISK 28X
**drwxr-xr-x  2 mark mark  4096 2008-10-23 13:16 usbdrive**

please note marks80 and separate usbdrive with slightly differing permissions.

Is everything looking good, I want to re-boot, but am trying to be cautious.

---

### Post by drs305 on 2008-10-23
It looks like you made a folder named **marks80** as well as one called **usbdrive**. The last entry I gave you was mounting it to **usbdrive**

You don't have to reboot to check the fstab entry. You can run the following to just unmount and mount the usb drive:
```

sudo umount /dev/sdb1
sudo mount /dev/sdb1

```

If everything is ok, there won't be any messages. We can clean it up once we pass this step. I will do this via Private Message if you report success.

---

### Post by Mark_in_Hollywood on 2008-10-23
So I sudo'd the unmount and mount per the above post and then:


Oooppsss!

mark@Lexington-19:/media$ sudo mount /dev/sdb1
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

so 

dmesg | tail

[20804.267548] ext3: No journal on filesystem on sdb1

and relevant part:

mark@Lexington-19:/media$ sudo fdisk -l

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cdf5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux

---

### Post by drs305 on 2008-10-23
I've sent you a PM. Please check your mailbox.

Added: It appears the fstab line was not working as fstab was not reading a line break between the "# /dev/sdb1" and the next line.

---

