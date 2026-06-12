---
title: "Can't see data on FAT32 drive"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by fruitman on 2008-11-24
I,ve just installed Ubuntu 7.1 dual booted with XP and created a FAT32 partition for data to be shared between the two systems. I've copied a selection of files onto it as I realise there are unsupported file types, I've included open office docs, mp3's, JPEG, bitmap etc. Booting into Ubuntu I can see the shared drive but all I can see on it are loads of folders which mare not of my creation. Can anyone tell me What I'm doing wrong?

---

### Post by Titan8990 on 2008-11-24
First off, you can use a NTFS drive to share files between both OSs. 

In regards your issue, my only guess is your looking at the wrong drive.

---

### Post by fruitman on 2008-11-24
thanks Titan, but it shows the correct volume label, so I can't see how it's the wrong drive. I can't see anything on the NTFS drives, and it wouldn't let me install NTFSconfig, message says list of applications is out date, and I haven't got my internet connection sorted out on this system yet.

---

### Post by taurus on 2008-11-24
Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Titan8990 on 2008-11-24
Go to Applications -> Accessories -> Terminal


type the following:


sudo fdisk -l

Then do this command:


mount


Copy and paste the outcomes here.

---

### Post by fruitman on 2008-11-24
Sorry, can you remind me how I access the terminal?

---

### Post by Titan8990 on 2008-11-24
Instructions are in my last post:

> Go to Applications -> Accessories -> Terminal

---

### Post by fruitman on 2008-11-24
too much to type in and copy paste isn't working well as I'm on two separate systems. Tried to use a stick for transfer but Ubuntu didn't recognise it. If the issue is one of mounting, I am right in thinking there's a way of doing this without the commans line?

---

### Post by fruitman on 2008-11-24
by the way, when using terminal do you hit return between each line like in DOS?

---

### Post by taurus on 2008-11-24
Yes, one line at a time.

---

### Post by Titan8990 on 2008-11-24
> too much to type in and copy paste isn't working well as I'm on two separate systems.


You typed way more in this post then you have to input into the terminal....

---

### Post by fruitman on 2008-11-24
after "sudo fdisk -1"it comes back with "[sudo]password for (my name)" but won't let me type in password or any further entries

---

### Post by taurus on 2008-11-24
That should be lower case letter L, not number 1.

```
sudo fdisk -**l**
```

---

### Post by Titan8990 on 2008-11-24
That is should be a lowercase "L" and not a one. You type in your password, it does not display what you are typing for security reasons but it is working. Just press enter after you have put in your pasword.

---

### Post by fruitman on 2008-11-24
sorry I didn't mean too much to type into the terminal, but it comes up with lines and lines of stuff which would take ages to type in a reply, copy and paste isn't really an option until I can sort out a way to transfer text files quickly between the two systems.

---

### Post by taurus on 2008-11-24
Just take pictures with your digital camera or cell phone.

---

### Post by Titan8990 on 2008-11-24
Ah, I understand that.

This has been my workaround:


Insert a thumb drive and wait for the icon to appear on your desktop. The name of that desktop icon will be important.

As an example I will assume that icon gets named "disk". In the terminal you would do:

cd /media/disk

disk will be whatever your desktop icon says.


Then you direct the output to a text file instead of it being displayed in a terminal:

sudo fdisk -l > fdisk.txt

mount > mount.txt


Then both text files should be on your thumb drive. Don't forget to right click on the desktop item and select "unmount" before removing the thumb drive.


edit: taurus is ahead of me everytime.... His suggestion will also work.

---

### Post by fruitman on 2008-11-24
If anyone's still out there;
this is the output from the simpler of the two sets of commands:


andy@saturn:~$ sudo fdisk -l 

Disk /dev/hda: 40.0 GB, 40020664320 bytes 
255 heads, 63 sectors/track, 4865 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x49c049bf 

   Device Boot      Start         End      Blocks   Id  System 
/dev/hda1   *           1        1483    11912166    7  HPFS/NTFS 
/dev/hda2            1484        3440    15719602+   5  Extended 
/dev/hda3            3441        4865    11446312+  83  Linux 
/dev/hda5            1484        2647     9349798+   7  HPFS/NTFS 
/dev/hda6            2648        3371     5815498+   b  W95 FAT32 
/dev/hda7            3372        3440      554211   82  Linux swap / Solaris 
andy@saturn:~$ mount 
/dev/hda3 on / type ext3 (rw,errors=remount-ro) 
proc on /proc type proc (rw,noexec,nosuid,nodev) 
/sys on /sys type sysfs (rw,noexec,nosuid,nodev) 
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755) 
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777) 
udev on /dev type tmpfs (rw,mode=0755) 
devshm on /dev/shm type tmpfs (rw) 
devpts on /dev/pts type devpts (rw,gid=5,mode=620) 
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw) 
securityfs on /sys/kernel/security type securityfs (rw) 
/dev/hdc on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=andy) 
andy@saturn:~$

---

### Post by taurus on 2008-11-24
So I assume you want to mount /dev/hda1, /dev/hda5, & /dev/hda6 then.  From a terminal, type

```
sudo mkdir /media/hda1 /media/hda5 /media/hda6
sudo mount -t ntfs-3g /dev/hda1 /media/hda1
sudo mount -t ntfs-3g /dev/hda5 /media/hda5
sudo mount -t vfat /dev/hda6 /media/hda6 -o umask=000
df -h
```

---

### Post by fruitman on 2008-11-25
After first line I get;

mkdir: cannot create directory '/': File exists
mkdir: cannot create directory 'media/hda6': No such file or directory

---

### Post by taurus on 2008-11-25
> **fruitman said:**
> After first line I get;

**[COLOR="Blue"]mkdir: cannot create directory '/': File exists[/COLOR]**
mkdir: cannot create directory 'media/hda6': No such file or directory

What exactly did you type to get that error message?  Remember, the command is

```
sudo mkdir /media/hda6
```
_not_
```
sudo mkdir / media/hda6
```

---

### Post by fruitman on 2008-11-25
yes I did have that extra space. correcting that I get;

mkdir: cannot create directory '/media/hda1': File exists
mkdir: cannot create directory '/media/hda5': File exists

I haven't used command lines since DOS!

---

### Post by taurus on 2008-11-25
The message just means that you already have /media/hda1 & /media/hda5 so just continue with mounting those three partitions now.

---

### Post by fruitman on 2008-11-25
after first sudo mount line I get;

fuse: failed to access mountpoint media/hda1: No such file or directory
FUSE mountpoint creation failed
Unmounting /dev/hda1 ()

---

### Post by taurus on 2008-11-25
You have to remember to put a / in front of the media.

```
sudo mount -t ntfs-3g /dev/hda1 **/**media/hda1
```

---

### Post by fruitman on 2008-11-25
this time I'm okay as far as;

sudo mount -t vfat /dev/hda6 /media/hda6 -o umask=000

(I'm trying to check my syntax more carefully)
Output I get is many lines of info on mounting commands but it doesn't mean mush to me

---

### Post by taurus on 2008-11-25
Can you post the whole outputs after you run each command?  Need to see what they are so I would know what's wrong with the command.

---

### Post by fruitman on 2008-11-25
here's the last attempt.I put in the df -h line although it looks like it had already gone wrong by then

andy@saturn:~$  sudo mkdir /media/hda1 /media/hda5 /media/hda6 
[sudo] password for andy: 
mkdir: cannot create directory `/media/hda1': File exists 
mkdir: cannot create directory `/media/hda5': File exists 
mkdir: cannot create directory `/media/hda6': File exists 
andy@saturn:~$ sudo mount -t ntfs-3g /dev/hda1 /media/hda1 
andy@saturn:~$ sudo mount -t ntfs-3g /dev/hda5 /media/hda5 
andy@saturn:~$ sudo mount -t vfat /dev/hda6 /media/hda6 -o unmask =000 
Usage: mount -V                 : print version 
       mount -h                 : print this help 
       mount                    : list mounted filesystems 
       mount -l                 : idem, including volume labels 
So far the informational part. Next the mounting. 
The command is `mount [-t fstype] something somewhere'. 
Details found in /etc/fstab may be omitted. 
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab 
       mount device             : mount device at the known place 
       mount directory          : mount known device here 
       mount -t type dev dir    : ordinary mount command 
Note that one does not really mount a device, one mounts 
a filesystem (of the given type) found on the device. 
One can also mount an already visible directory tree elsewhere: 
       mount --bind olddir newdir 
or move a subtree: 
       mount --move olddir newdir 
One can change the type of mount containing the directory dir: 
       mount --make-shared dir 
       mount --make-slave dir 
       mount --make-private dir 
       mount --make-unbindable dir 
One can change the type of all the mounts in a mount subtree 
containing the directory dir: 
       mount --make-rshared dir 
       mount --make-rslave dir 
       mount --make-rprivate dir 
       mount --make-runbindable dir 
A device can be given by name, say /dev/hda1 or /dev/cdrom, 
or by label, using  -L label  or by uuid, using  -U uuid . 
Other options: [-nfFrsvw] [-o options] [-p passwdfd]. 
For many more details, say  man 8 mount . 
andy@saturn:~$ df -h 
Filesystem            Size  Used Avail Use% Mounted on 
/dev/hda3              11G  2.1G  8.2G  21% / 
varrun                125M   80K  125M   1% /var/run 
varlock               125M     0  125M   0% /var/lock 
udev                  125M   84K  125M   1% /dev 
devshm                125M     0  125M   0% /dev/shm 
lrm                   125M   34M   92M  28% /lib/modules/2.6.22-14-generic/volatile 
/dev/sda1             983M  104M  880M  11% /media/disk 
/dev/hdc              696M  696M     0 100% /media/cdrom0 
/dev/hda1              12G  3.8G  7.7G  33% /media/hda1 
/dev/hda5             9.0G  5.3G  3.7G  60% /media/hda5 
andy@saturn:~$

---

### Post by taurus on 2008-11-25
Try this one again.

```
sudo mount -t vfat /dev/hda6 /media/hda6 -o umask=000
```

---

### Post by djbushido on 2008-11-25
I think it should be:```
andy@saturn:~$ sudo mount -t vfat /dev/hda6 /media/hda6 -o unmask=000 
```

NOT:
```
andy@saturn:~$ sudo mount -t vfat /dev/hda6 /media/hda6 -o unmask =000 
```

There is an extra space on the "unmask =000", it should be "unmask=000"

And I could be wrong, but I am pretty sure it is umask, not unmask.

EDIT: sorry, taurus beat me to the post...

---

### Post by fruitman on 2008-11-25
Well done Taurus I seem to be getting somewhere! Tried to go through the whole thing again in a new terminalbut it said something about device busy so I simply added your corrected line to my first effort than the 
df -h line again and got this output:

andy@saturn:~$  sudo mount -t vfat /dev/hda6 /media/hda6 -o umask=000 
[sudo] password for andy: 
andy@saturn:~$  df -h 
Filesystem            Size  Used Avail Use% Mounted on 
/dev/hda3              11G  2.1G  8.2G  21% / 
varrun                125M   84K  125M   1% /var/run 
varlock               125M     0  125M   0% /var/lock 
udev                  125M   72K  125M   1% /dev 
devshm                125M     0  125M   0% /dev/shm 
lrm                   125M   34M   92M  28% /lib/modules/2.6.22-14-generic/volatile 
/dev/hdc              696M  696M     0 100% /media/cdrom0 
/dev/hda1              12G  3.8G  7.7G  33% /media/hda1 
/dev/hda5             9.0G  5.3G  3.7G  60% /media/hda5 
/dev/hda6             5.6G   73M  5.5G   2% /media/hda6 
andy@saturn:~$ 

Result; I can see my drives! Those are Windows, the NTFS data, the SHARED drive (FAT32), but not the Ubuntu system drive. At least I can get started. Do you always have to mount all the drives via the terminal?

---

### Post by fruitman on 2008-11-25
Also thanks to Titan 8990 for input yesterday. Does anyone know any good pages for an introduction to using the command line, helping to understand commands and syntax etc. ?

---

### Post by fruitman on 2008-11-25
One more thing; I'd put some shortcuts to the drives on my desktop, including the NTFS one labelled "shared". Suddenly I have two different icons labelled "shared", one which opens a window allowing me to see the drive contents, and the other is described in properties as a desktop configuration file, I'm wodering why I've got that for this drive and not the others.

---

### Post by djbushido on 2008-11-26
ubuntu automounts some drives and not others, so this could be why you see one drive as a configuration file, and the other as a folder.

---

