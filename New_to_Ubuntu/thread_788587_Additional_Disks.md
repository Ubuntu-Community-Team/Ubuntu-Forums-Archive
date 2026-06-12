---
title: "Additional Disks"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by fballem on 2008-05-09
I have two disks in my computer. Ubuntu is installed on the first and is working fine. I would like to use the second disk for additional storage, such as projects and other large files. How do I set up the second disk?

Related question: I have an NAS server and would like to set it up so that it is accessible, instead of having to mount it each time I start my system. In this way, I can setup a backup to go there. I can't reformat the NAS. I have been able to mount it and access the shares and work with it, but I would like to have this always started up.

Thanks,
Flavelle

---

### Post by Xiong Chiamiov on 2008-05-09
Can you please post the output of
```

sudo fdisk -l

```

---

### Post by logos34 on 2008-05-09
> **fballem said:**
> I have two disks in my computer. Ubuntu is installed on the first and is working fine. I would like to use the second disk for additional storage, such as projects and other large files. How do I set up the second disk?

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by fballem on 2008-05-09
output as requested:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x043d50dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11c3fc61

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux

---

### Post by Xiong Chiamiov on 2008-05-09
The fstab (/etc/fstab) is the file that controls what get mounted automatically when your computer starts, so we're going to have to add a line to that.

First, create a folder where you want the 2nd hard drive to be mounted.  For this example, I'll use /files, so I would run
```

sudo mkdir /files

```
You can check that everything's working right by running
```

sudo mount /dev/sdb1 /files

```
If you can now see your files in that folder, great!, let's continue.

You'll need to open your fstab as root to edit it:
```

gksudo gedit /etc/fstab

```
Gksudo is the same as sudo, but better when you're using graphical applications.
At the end of that file, add the line
```

/dev/sdb1    /files    ext3    defaults    0    2

```
To check it, we can first unmount the drive that we mounted just a minute ago
```

sudo umount /files

```
then mount everything listed in the fstab
```

sudo mount -a

```
Check /files again, and you should see your stuff.

The process is similar for the NAS.  If you can mount it manually, you can add it into the fstab.

---

### Post by fballem on 2008-05-10
Sorry - is there a GUI tool that I can use to manage all of this stuff. Working in terminal mode is not exactly the most comfortable place to be. I realise that I might need to get there, but if there is a GUI tool, then that would be better (and probably safer) for me.

The GUI tool should allow me to mount/unmount devices and set up these devices so that they can be mounted and accessible at startup.

---

### Post by logos34 on 2008-05-10
> **fballem said:**
> Sorry - is there a GUI tool that I can use to manage all of this stuff. Working in terminal mode is not exactly the most comfortable place to be. I realise that I might need to get there, but if there is a GUI tool, then that would be better (and probably safer) for me.

The GUI tool should allow me to mount/unmount devices and set up these devices so that they can be mounted and accessible at startup.

There's this tool:

PySDM - Graphical Storage Device Manager

info:
apt-cache show pysdm

But if you follow the link I gave you in my last post or Xiong's post above you should be fine with the terminal

---

### Post by fballem on 2008-05-10
> **Xiong Chiamiov said:**
> The fstab (/etc/fstab) is the file that controls what get mounted automatically when your computer starts, so we're going to have to add a line to that.

First, create a folder where you want the 2nd hard drive to be mounted.  For this example, I'll use /files, so I would run
```

sudo mkdir /files

```
You can check that everything's working right by running
```

sudo mount /dev/sdb1 /files

```
If you can now see your files in that folder, great!, let's continue.

You'll need to open your fstab as root to edit it:
```

gksudo gedit /etc/fstab

```
Gksudo is the same as sudo, but better when you're using graphical applications.
At the end of that file, add the line
```

/dev/sdb1    /files    ext3    defaults    0    2

```
To check it, we can first unmount the drive that we mounted just a minute ago
```

sudo umount /files

```
then mount everything listed in the fstab
```

sudo mount -a

```
Check /files again, and you should see your stuff.

The process is similar for the NAS.  If you can mount it manually, you can add it into the fstab.

For the second drive, I have followed the directions exactly. In /files, I have a file called 'Lost & Found' which I'm assuming is something put in by the system.

Are there any access issues?

If I create a folder in /files, do I need to do anything to make it available to other Users on my system?

Also, if I am able to setup the NAS, can I mount it in /files, or do I need a different place to mount it?

Thanks

---

### Post by vanadium on 2008-05-10
You can only mount one file system in one mount point, i.e. only the last file system you mount there will be visible.

In fact, I would rather mount under /mnt/files instead of /files. You could then mount your nas under /mnt/nas.

---

### Post by fballem on 2008-05-10
Oh, oh, I think I'm getting this!

In Windows, we have become used to seeing separate devices. For example, if I have two disk drives (which I do), then I would see Drive C and Drive D. There is no concept of 'mounting'. As a general principle, if I have multiple Userids on my computer, then all of the Userids would be able to see both drives automatically. There may be access restrictions that would prevent this, and also to prevent access to specific portions within one drive or another, but the drives do not have to be mounted and access is assumed, unless otherwise denied.

In Linux, access to devices is not automatic. If I'm right, then each user has a different /etc/fstab file. If you aren't careful, it would be theoretically possible that a user would have no access to anything (if there were no mount entries in their /etc/fstab file).

Once mounted, the devices are found in the filesystem at the mountpoints specified in the /etc/fstab file. This is is probably in the realm of 'a little knowledge is a dangerous thing', but this is starting to come together for me.

A question - on my NAS sources, I have coded the passwords in the /etc/fstab file. Instead, is there a way to code the file so that it asks for the UserID and Password, then uses those values to access the NAS source?

Also, if this is done, is there a mechanism for handling errors?

Thanks!

---

### Post by fballem on 2008-05-10
I've taken the suggestion of putting the additional mount points under /mnt. I have a mount point for the second drive, several from the NAS, including backup and media.

Looks like I'm good to go - although I wouldn't mind if I could get my mount points to show up as distinct 'Places' as opposed to having to go into the File System to find them. Still, that's small.

Many thanks!!

---

### Post by fballem on 2008-05-11
I found a link that describes a method to provide a little security to the permanent mounting for the NAS device

[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

Haven't tested it yet, but I will in a few moments.

Flavelle

---

### Post by fballem on 2008-05-11
> **fballem said:**
> I found a link that describes a method to provide a little security to the permanent mounting for the NAS device

[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

Haven't tested it yet, but I will in a few moments.

Flavelle

Testing is done and it works. I also made a couple of other changes. The resulting lines in /etc/fstab are:

```
//nasserver/media /mnt/media cifs credentials=/home/myuid/.smbpassword,uid=myuid,iocharset=utf8 0 0
//nasserver/linuxbackup /mnt/backup cifs credentials=/home/myuid/.smbpassword,uid=myuid,iocharset=utf8 0 0
//nasserver/fbprivate /mnt/private cifs credentials=/home/myuid/.smbpassword,uid=myuid,iocharset=utf8 0 0

```

where nasserver is the name or IP address of the actual NAS server and myuid is the userid for my desktop.
On my NAS, I have media, linuxbackup, and fbprivate defined as shares. I am using the utf8 characterset because I have accented names in some of my files, particularly the music files.
I am also using cifs instead of smbfs, since I read that cifs is the 'preferred' method.

In the .smbpassword file, which is located in /home/myuid/, I have three lines:

```
userid=nasuserid
password=naspassword

```

where nasuserid is my userid on the NAS, naspassword is my password, and myuid is the userid for my desktop.

The NAS is a LaCie Ethernet Disk mini (site: [http://www.lacie.com/ca/products/product.htm?pid=10843](http://www.lacie.com/ca/products/product.htm?pid=10843)) and it does seem to be working correctly.

Thanks to all!

---

