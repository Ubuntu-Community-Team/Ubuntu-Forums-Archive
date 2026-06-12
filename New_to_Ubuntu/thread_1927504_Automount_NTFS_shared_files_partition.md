---
title: "Automount NTFS shared files partition"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by iangarforth on 2012-02-18
Hi all,

I've put all my music and photos (too big to shove in the cloud) into an NTFS partition separate from everything else.

If I've got this right (and I only speak from having attended multiple classes at the University of Hard Knocks), Banshee copes ok if I forget to mount the drive.  Shotwell very very much doesn't.

So what I'd like to do is to get the partition to automount (would this be at log on or at start up..?), but I really need idiot-proof instructions.  It's something to do with fstab, right?

---

### Post by coffeecat on 2012-02-18
> **iangarforth said:**
> 
So what I'd like to do is to get the partition to automount (would this be at log on or at start up..?), but I really need idiot-proof instructions.  It's something to do with fstab, right?

It's at startup and, yes, it's to do with fstab.

First thing - **please** don't be tempted to install GUI apps such as pysdm or ntfs-config to "help" with this. They are unmaintained and can cause more problems than they solve. The same probably applies to mountmanager, although I'm not sure of this. The best way is to manually edit /etc/fstab yourself.

Post the output of the following terminal commands, and I or someone else can take you through this.

```
sudo fdisk -lu
sudo blkid
mount
```

If you know which is your NTFS data partition, please indicate which it is if this is not obvious from the output.

Also, please enclose the terminal output between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

### Post by iangarforth on 2012-02-18
Thank you.

sudo fdisk -lu
generates the following

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf61a6901

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    20973567    10485760   27  Hidden NTFS WinRE
/dev/sda2   *    20973568    21178367      102400   27  Hidden NTFS WinRE
/dev/sda3        21178368    86714367    32768000    7  HPFS/NTFS/exFAT
/dev/sda4        86714368   312580095   112932864    5  Extended
/dev/sda5        86716416    92860415     3072000   82  Linux swap / Solaris
/dev/sda6        92862464   144062463    25600000   83  Linux
/dev/sda7       144064512   312580095    84257792    7  HPFS/NTFS/exFAT

```

sudo blkid
generates

```

/dev/sda1: LABEL="BIOS_RVY" UUID="7E769E5B769E13CD" TYPE="ntfs" 
/dev/sda2: LABEL="System" UUID="DA28A10328A0E02D" TYPE="ntfs" 
/dev/sda3: LABEL="OS_Install" UUID="26CAA540CAA50CDD" TYPE="ntfs" 
/dev/sda5: UUID="9de90b8a-ebb8-498c-95e3-48a7dd4e60c5" TYPE="swap" 
/dev/sda6: UUID="c7bff0aa-bfef-4296-83b8-230dc5b1e688" TYPE="ext4" 
/dev/sda7: LABEL="Masterstore" UUID="06FB798658FCF4DF" TYPE="ntfs" 

```

and finally

mount
generates

```
/dev/sda6 on / type ext4 (rw,errors=remount-ro,user_xattr,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ian/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ian)
/dev/sda7 on /media/Masterstore type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```

The partition I want to mount is called Masterstore and is sda7.

Cheers

---

### Post by coffeecat on 2012-02-18
**EDIT**: just noticed something. You have Masterstore already mounted via the GUI. Unmount it before you proceed otherwise you will get the error when you do the mkdir command. **end-edit**

Preamble. The instructions below will mount your partition in a mountpoint in the /media folder. The advantage of this is that if you are running Ubuntu with Unity, an icon will appear in the Launcher which if you click on takes you straight to your "Masterstore" partition. If you are running classic gnome, you will get an icon on your desktop. Some people see this as a disadvantage and mount partitions in /mnt or in a custom mount folder. You would then get no desktop icon or launcher icon and would have to navigate from Filesystem. If a mountpoint in /media does not suit then post back and we'll take it from there.

Also - you will see some people saying very forcefully that you should **never** use /media because this is used by the system. All I can say is that I very respectfully and very strongly disagree, mainly because there are safeguards built into the automounting functioning of the desktop to prevent clashes with manually created mountpoints.

Pre-amble over. :)

One thing I forgot to get you to do is to run "ls -l /media" to see if there were already any mountpoints in /media which we need to avoid. So - first thing, open a terminal, and:

```
sudo mkdir /media/Masterstore
```

If you get an error saying that Masterstore already exists, choose another name and/or post back.

Now:

```
gksu gedit /etc/fstab
```

Now add this line to the end of the file. Make sure it is a newline and doesn't carry on from the current last line.

```
UUID=06FB798658FCF4DF     /media/Masterstore     ntfs-3g     defaults,nls=utf8,windows_names     0 0
```

Save and close. Now:

```
sudo mount -a
```

An icon should appear in your launcher or desktop depending on whether you run Unity or classic gnome. Test it out. Please try drag and drop copying of a file from your ext4 partition (from your home folder) to the ntfs partition and vice versa. There's a bug in ntfs-3g that causes the date/time to change to current on a copy with certain mount options. I'm 99% sure the above options will prevent this, but let's check anyway.

Last point, if you've had to create a mountpoint with a name other than "Masterstore", change the line that I gave you for /etc/fstab accordingly.

---

### Post by iangarforth on 2012-02-18
Thanks for that - that's very thorough.

Firstly, running

```
sudo mkdir /media/Masterstore
```

generates

```

mkdir: cannot create directory `/media/Masterstore': File exists

```

So I presume I need to choose another name other than Masterstore?  Does it matter what the name is?  Will the name show up anywhere else?

Secondly, before I kick into having a lash at it, can WI just check - randomly, and not driven by anything other than it seemed logical to me, on Masterstore, one of the three folders I use to store my stuff in is called 'media'.  

Now, I'm presuming the 'media' you're talking about is a different 'media', right?  Will this cause problems or not?

Cheers

---

### Post by iangarforth on 2012-02-18
Sorry.  Just seen your reply - will try that again...

**EDIT** - yup, unmounted, and it sudo'd away quite happily with no errors

---

### Post by HavarN on 2012-02-18
First you need to create the directory /media/Masterstore
```
sudo mkdir /media/Masterstore
```

Then you need to add this line to your /etc/fstab file.
```
/dev/sda7    /media/Masterstore    ntfs-3g    defaults    0    0
```
Edit your fstab file with gedit. ALT+F2, type and run:
```
gksu gedit /etc/fstab
```

You can add the line to fstab by issuing this command in a terminal. However be careful to use both > in >>, as using only one > will replace your fstab instead of adding a line to it.
```
sudo sh -c "echo /dev/sda7'\t'/media/Masterstore'\t'ntfs-3g'\t'defaults'\t'0'\t'0 >> /etc/fstab"
```

---

### Post by iangarforth on 2012-02-18
All done and working.  Thanks so much!

---

### Post by coffeecat on 2012-02-18
> **iangarforth said:**
> 
Secondly, before I kick into having a lash at it, can WI just check - randomly, and not driven by anything other than it seemed logical to me, on Masterstore, one of the three folders I use to store my stuff in is called 'media'.  

Now, I'm presuming the 'media' you're talking about is a different 'media', right?  Will this cause problems or not?

Cheers

The /media I was referring to is the media directory in the root of your Ubuntu filesystem. It's there primarily for creating mountpoints in for removable media, but you can also use it for creating mountpoints for other partitions. I've obliquely referred to a bit of controversy surrounding this latter in my earlier post.

The media folder in your sda7 partition won't interfere with anything. In fact you would be able to navigate to it via "Filesystem" in Nautilus and its path would be /media/Masterstore/media/ . There would be no problem.

---

### Post by coffeecat on 2012-02-18
> **iangarforth said:**
> All done and working.  Thanks so much!

Excellent. Good luck!

---

### Post by nothingspecial on 2012-02-18
You can mount your 3 folders in Masterstore to your home directory, so they appear there rather than accessing them through /media.

```
mkdir $HOME/media
```

Then open fstab again

```
gksudo gedit /etc/fstab
```

and put a line like this (assuming your name is ian)

```
/media/Masterstore/media  /home/ian/media  none  bind  0  0
``` 

Then ```
sudo mount -a
```

The contents of the media folder in Masterstore should now be in your home. You can do the same for the other 2 folders.

---

### Post by coffeecat on 2012-02-18
@nothingspecial, that's a nice way of doing it. I've previously used symlinks in my home to open folders in my data partition, but that is more elegant. Thanks.

---

