---
title: "problem mounting/umounting external drive"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Old Jimma on 2008-09-07
Hi Ubuntu community:

This morning I plugged in my 250GB external drive. It mounts at /media/EXTERNAL automatically.

Then, I backed up my file systems using

cd /media/EXTERNAL
cp -a /home/myhomedirectory .

When the cp completed its work, I used the disk mounter icon, and unmounted the external drive, then turned it off and put it away.

SOMETHING WENT WRONG... their was an icon on my desktop that showed the external drive icon, although I had turned the drive off and put it away.

I plugged the external drive back in and it will not mount now.

How can I mount that drive???

I'm not sure how to mount it manually by creating the mount point and associating it with the device (because I'm not sure what device it its).

Thank you!
Phil Smith
Duluth, GA

---

### Post by Pro-reason on 2008-09-07
It sounds like it did not in fact unmount correctly, and therefore you damaged the drive by removing it.  Run *fsck* on it.

---

### Post by Old Jimma on 2008-09-08
Hi Proreason:

I did a man on fsck. I think I need to know the /dev of the external hard drive. 

How do I find out what that is?

Thank you!
Phil Smith
Duluth, GA

---

### Post by Pro-reason on 2008-09-08
> **Phil Smith said:**
> Hi Proreason:

I did a man on fsck. I think I need to know the /dev of the external hard drive. 

How do I find out what that is?

Thank you!
Phil Smith
Duluth, GA

You can run commands such as “sudo lshw -C disk“, “sudo fdisk -l” and “sudo blkid”.

---

### Post by Old Jimma on 2008-09-08
Hi Pro-reason:

Here is what I get:

philipsmith@philipsmith-desktop:~$ sudo lshw -C disk
[sudo] password for philipsmith: 
  *-cdrom                 
       description: DVD-RAM writer
       product: CD/DVDW SH-S162A
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: TS02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
  *-disk
       description: ATA Disk
       product: SAMSUNG SP2504C
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sda
       version: VT10
       serial: S09QJ1ML201910
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0009eeb8


philipsmith@philipsmith-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009eeb8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30026   241183813+  83  Linux
/dev/sda2           30027       30401     3012187+   5  Extended
/dev/sda5           30027       30401     3012156   82  Linux swap / Solaris
philipsmith@philipsmith-desktop:~$

---

### Post by Pro-reason on 2008-09-09
That's showing only your internal hard drive.  The other drive is not showing up at all.

Check the connections.  Try a different port.

Can you mount it on another computer?

---

### Post by Pro-reason on 2008-09-09
OK, I can see in your private message to me that you have been able to view the files on another computer.

It's best if you keep it all here on the forum, rather than sending PMs.  That way, everyone can benefit from the info.

---

### Post by Pro-reason on 2008-09-09
What filesystem is on the external drive?  If you can view it on Windows, it is presumably FAT or NTFS.

NTFS filesystems are a bit dodgy.  I don't trust them to run on Linux machines.  Run CHKDSK or similar utility on the drive on Windows.

---

### Post by Old Jimma on 2008-09-09
Pro-reason:

When I plugged the external drive into my son's windows machine, Win didn't want to read it.

After clicking on "e:" quite a few times, win eventually asked me to pick an application to read the drive with. Then win went through some sort of read operation, and I could see the contents of the drive.

When I've connected the drive to a win computer in the past there has never been any problem reading it.

Also, I used qtpared on my ubuntu machine to try to find the external drive... no luck.

I'm beginning to think that the drive is heading for the bone-yard.

What could I have done to kill it?

Phil

---

### Post by Pro-reason on 2008-09-09
[GParted]("http://gparted.sourceforge.net/") is better than [QTParted]("http://en.wikipedia.org/wiki/QtParted").

On Windows, don't try to access the drive from the graphical interface (that could lead to further damage).  Instead, run the [CHKDSK]("http://technet.microsoft.com/en-us/library/bb491051.aspx") command from the command prompt.  In fact, it's probably best to boot from a Windows XP installation CD and run [CHKDSK]("http://support.microsoft.com/kb/187941") from there.

You might also want to look up the &#8220;dd&#8221; Linux command, and use it to back up the drive before performing any [file-recovery techniques]("https://help.ubuntu.com/community/DataRecovery") on it.

---

### Post by Old Jimma on 2008-09-10
Hi Pro-reason:

I used gparted. It could not detect the external drive.

Is this drive dead, or what?  :-)

Thanks,
Phil

---

### Post by Old Jimma on 2008-09-10
Hi Pro-Reason:

I tried Gparted. It couldn't see the drive.

Is it dead, or what? 

:-)

Wish I knew how I killed it.

Thanks,
Phil

---

### Post by Pro-reason on 2008-09-11
It seems dead.

As I said, try using [CHKDSK]("http://support.microsoft.com/kb/315265") on it.

---

