---
title: "[SOLVED] cant get 2 gb usb key to work"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-01
when i plug in the usb key iget this message cannot mount volume invalid mount option when attempting to mount the volume.its a toshiba 2gb
memory stick (usb) i am running ubuntu 8.04 with all the updates
up to date im running ubuntu on a acer aspire 5315 w/intel celeron 550
2 ghz 533mghz fsb 1 mb l2 cache 252mb intel graphics accelerator x3100
2gb ddr2 memory please help me to solve this problem.
thanx rixtr66:confused:

---

### Post by unutbu on 2008-07-01
Hi. We'll need a bit more info to help you.

Please post:
(1)
```
sudo fdisk -l
```

(2) the command you used to mount the USB key.

---

### Post by rixtr66 on 2008-07-01
ick@rick-laptop:~$ sudo fdisk -l
[sudo] password for rick: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d8a1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 1999 MB, 1999634432 bytes
16 heads, 32 sectors/track, 7628 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              16        7628     1948736    e  W95 FAT16 (LBA)
rick@rick-laptop:~$ sudo fdisk -lsudo fdisk -l

---

### Post by rixtr66 on 2008-07-01
what command do you use to mount the usb key?

---

### Post by unutbu on 2008-07-01
When you stick the usb key into a usb port, the machine should mount the key automatically. We can work on that later, but first let's see if we can mount the key from the command line:

Try 
```

sudo mkdir /media/key
sudo mount /dev/sdb1 /media/key
```

---

### Post by rixtr66 on 2008-07-01
ok  that opened it up,will it open all the time or do i have to type in thatcode,thanx for getting me this far is there anything else i should know?
rixtr66:guitar:

---

### Post by rixtr66 on 2008-07-01
now i cant do anything withit i get permission denied errors,ugh
please help meeeeeeeeeeeeeeeeeee:confused:
rixtr

---

### Post by unutbu on 2008-07-01
First, a warning: Do not unplug your flash key without unmounting first:
Either right-click on the icon of the key on your desktop and select "Unmount", or run
```

sudo umount /media/key
```

If you don't do this, the filesystem on the key could get corrupted, and you could lose files. 

In the future, to mount the key manually (from the terminal),
you will only need run the second command:
```

sudo mount /dev/sdb1 /media/key
```

(sudo mkdir /media/key created the directory /media/key; you won't have to do that again.)

Now that we know we can mount the key, the best solution would be to convince Hardy to automount  USB key for you. 

Can you post a screen shot of the error message> 
cannot mount volume invalid mount option when attempting to mount the volume

Also, in Hardy (which I don't have) do you have a menu item System>Preferences>Removable Drives and Media?

---

### Post by unutbu on 2008-07-01
Okay, so that you can write to the key as a normal user, run
```

sudo chown rixtr66:rixtr66 /media/key
```

---

### Post by mbsullivan on 2008-07-01
> now i cant do anything withit i get permission denied errors,ugh
please help meeeeeeeeeeeeeeeeeee
rixtr

For a slightly more robust (but less secure) solution, you can explicitly set the permissions of the mounted files to be globally editable in the following manner:

```
sudo mount -o rw,umask=000,dmask=000,fmask=000 /dev/sdb1 /media/key
```

I agree with unutbu that automount is a nicer option. Otherwise, you could declare a couple of aliases like the following in ~/.bashrc in order to simplify the process:

```
alias usb='sudo mount -o rw,umask=000,dmask=000,fmask=000 /dev/sdb1 /media/key'
alias uusb='sudo umount -f /media/key'
```

Mike

---

### Post by rixtr66 on 2008-07-01
i keep getting error messages,error while copying workthere was an error copying
files into the net;/// operation not supported on backend,also; while copying tool there was an error copying the file into/media/key
error opening file /media/key/tool permission denied.i also noticed
the properties of the key it says everything about the key,in permissions
it says the permissions of"key"are not determined more help is needed to
solve this thanx so far
rixtr

---

### Post by unutbu on 2008-07-01
rixtr66, backup anything you have on the USB key.
I think you should delete the partition and recreate it from scratch.


```
sudo umount /dev/sdb1
sudo fdisk -C 7628 -H 16 -S 32 /dev/sdb
```
at the fdisk prompt type:

```

d               # delete
1               # first partition
n               # create new partition
p               # primary partition
1               # partition #1
1               # first cylinder
7628            # last cylinder
p               # take a look at the table
t               # set partition type
e               # Hex code for W95 FAT16 (LBA)
w               # write partition table

```

Finally, reformat the partition.
```
sudo /sbin/mkdosfs /dev/sdb1

```
Remount the key, (thanks, mbsullivan):
```
sudo mount -o rw,umask=000,dmask=000,fmask=000 /dev/sdb1 /media/key
```

---

### Post by Bubba64 on 2008-07-01
Gparted will repartition the thumb drive easily.

---

### Post by unutbu on 2008-07-01
I'm trying to preserve his disk geometry. 
```
Disk /dev/sdb: 1999 MB, 1999634432 bytes
**16 heads, 32 sectors/track, 7628 cylinders**
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

Device Boot Start End Blocks Id System
/dev/sdb1 16 7628 1948736 e W95 FAT16 (LBA)
```

GParted can not do that.

---

### Post by rixtr66 on 2008-07-02
nothing has worked except i can mount the key i cant save anything to it.
i tried this sudo chown rick:rick /media/key but i get a message that says
operation not permitted.isnt there something ican download that will detect
the key when i plug it in and automount? please help
rick:confused:

---

### Post by rixtr66 on 2008-07-02
after going through all the above nothing was working but when i took
the key out and put it back in it automounted and i could access it
with no problems?now i have a program called usbview and when i open
it i immediatly get this message"usbview error cannot open the file
/proc/bus/usb/devices"it also says verify that you have usb compiled
into the kernel,have the usb core modules  loaded,and havetheusbdevfs
file system mounted.could this have something to do with the problem?
:confused: rick

---

### Post by unutbu on 2008-07-02
rixtr66, your problem is very foreign to me -- my experience has been USB keys just work automatically. I'm not sure I know how to fix the problem.

Here are some weak suggestions:


(1) Let's make sure that at least root can write to the key. If root can write, then at least we know we are dealing with a permission problem.

Mount the key at /media/key. Then run
```
cd /media/key
sudo touch "ICanCreateAFileAsRoot"
ls -l
```
Do you see this?
```
-rw-r--r-- 1 root   root      0 2008-07-02 14:45 ICanCreateAFileAsRoot
```

(2) More checking to make sure the permissions are set correctly on the directories:
Please post the output of 
```
ls -ld /media/key
ls -ld /media
```

(3) HAL (hardware abstraction layer) is the part of the system which manages devices such as the USB key. In Gutsy, System>Preferences>Removable drives and media
has a configuration screen that looks like 
this:

[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=76157&stc=1&thumb=1&d=1215025426[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=76157&stc=1&d=1215025428")

That's all you need to do to get a USB key automounted on a Gutsy machine. There should be something just a simple for Hardy; check the GNOME menus?

(4) To check that HAL at least sees your USB key, stick it in to the computer and then run
```
lshal | bzip2 > lshal.out.bz2

```
Post lshal.out.bz2 as an attachment. There should be a lot of junk and then stuff about your USB key buried in the middle...

(5) Finally, let's check that hald, the HAL daemon is running:
```

ls -l /etc/rc2.d/*hal*
ps auxw | grep hald
```
Post the output.

---

### Post by rixtr66 on 2008-07-03
ok first off in removable drives and media prefrences i am missing
the storage and multimedia tabs all i have is cameras pda's,printers and scanners,input devices thats it.as for the out puts you asked for the
first one (i dont have the funny z thing onmy keyboard so ill use z)
zs-zd /media/key the output was drwxr-xr-x 2 root root 4096 2008-07-03
09:24 /media/key.andthenext command was the same output but with a 13.
the restofthe outputs are as followsrick@rick-laptop:~$ lshal | bzip2 > lshal.out.bz2
bash: lshal.out.bz2: Permission denied
rick@rick-laptop:~$ ls -l /etc/rc2.d/*hal*
lrwxrwxrwx 1 root root 13 2008-06-26 19:53 /etc/rc2.d/S24hal -> ../init.d/hal
rick@rick-laptop:~$ ps auxw | grep hald
111       5194  0.0  0.2   6216  4276 ?        Ss   09:07   0:00 /usr/sbin/hald
root      5259  0.0  0.0   3352  1172 ?        S    09:07   0:00 hald-runner
root      5273  0.0  0.0   3416  1168 ?        S    09:07   0:00 hald-addon-input: Listening on /dev/input/event7 /dev/input/event8 /dev/input/event1 /dev/input/event3 /dev/input/event4 /dev/input/event5 /dev/input/event6
111       5288  0.0  0.0   2204   908 ?        S    09:07   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      5301  0.0  0.0   3420  1156 ?        S    09:07   0:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)
root      7292  0.0  0.0   3420  1152 ?        S    09:23   0:00 hald-addon-storage: polling /dev/sdb (every 2 sec)
rick      7523  0.0  0.0   3004   748 pts/0    R+   09:44   0:00 grep hald
rick@rick-laptop:~ thats all of it,ithink ineed to know how to get those 
2 missing tabs into removable drives and media preferences.
thanks for your help so far.
rick:confused:

---

### Post by unutbu on 2008-07-03
Try this: click on System>Administration>Users and Groups.
Click your username. Click Properties. Click the User Privileges Tab. (See attachment).

Make sure "Access external storage devices automatically" is enabled.

---

### Post by ChameleonDave on 2008-07-03
Please paste the output of

```
cat /etc/fstab
```

---

### Post by rixtr66 on 2008-07-03
the box in user settings is checked,chameleondave here  is the output:
root@rick-laptop:/home/rick# cat /etc/fstab


# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=9567b837-3d1e-4317-801e-1f969b9e40ed / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=465fae8c-e4f6-4bf0-8827-338b7a21dfe2 none swap sw 0 0
/dev/sdb1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
root@rick-laptop:/home/rick# 
rick:confused:

---

### Post by unutbu on 2008-07-03
Type
```
gksu gedit /etc/fstab
```
Remove this line:
> **rixtr66 said:**
> 
```
/dev/sdb1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

It is wrong because your usb key is device /dev/sdb1, not your cdrom. (It is not the mount point that is making this fail, it is the filetype: the usb key is not iso9660, it is W95 FAT16.

---

### Post by peakshysteria on 2008-07-03
Also, if it was mounted on a windows machine/OS earlier and not removed properly this might happen. (Been there myself a couple times). If so, insert the USB into a windows machine, wait for it to appear properly and then remove it safely by rightclicking safely remove hardware in systray. Then it should pop up again as usual in your Ubuntu.

Just mentioning this since there doesn't seem to be anybody else who have mentioned it.

---

### Post by rixtr66 on 2008-07-03
unutbu that worked let me restart and see if it still works.:guitar:
rick,many thanks

---

### Post by rixtr66 on 2008-07-03
yes this problem is finally solved many thanks to all of you that helped
thank you very much:lolflag:
rick

---

### Post by ChameleonDave on 2008-07-03
> **peakshysteria said:**
> Also, if it was mounted on a windows machine/OS earlier and not removed properly this might happen. 

That often happens with NTFS drives.  I haven't heard of it happening with FAT drives like this.

---

### Post by jmr257 on 2008-09-24
Hey, i had the same problem and it fixed perfectly with this. 
Just wanted to write my thanks for helping out that other and at the same also me :)

---

### Post by amj on 2008-09-27
I was having a similar problem.  I don't know if it was because I had installed Ubuntu 8.04.1 from a live usb, but once I commented out a line from my /etc/fstab, I could read all my usb keys.   Here's my fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=fbad05f6-5e91-4330-ab87-2e7e0a82ac26 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=8724e6dc-87a7-4f57-8c62-5a72d9aa41d6 /home           ext3    relatime        0       2
# /dev/sda6
UUID=3bbd225c-6c43-46b6-82af-b479307704ef none            swap    sw              0       0
# /dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

The line I commented out was the one starting with /dev/sdb1

Hope this helps

---

### Post by jmr257 on 2008-11-05
I guess this comes from installing Ubuntu from a memorystick. For me happened the same, now twice when i re-installed my ubuntu. Anyways, thanks for your help, it was a huge help for me also ):P

---

