---
title: "Cannot delete or move files from or to my removable device."
date: 2008-09-02
forum: New to Ubuntu
---

### Post by bigge on 2008-09-02
Hi! I have tried to search down any similar threads but the ones I've found doesn't address this particular problem, so I'll try to create a new thread and hope that someone can help me with this.

I have a Maxtor III OneTouch removable harddrive connected to my laptop and I can't seem to figure out how to copy files to it, or how to delete files on it. Even when I use Thunar with sudo I can't delete or copy files on or to it.

All the folders and file-icons have a little padlock on them and when I right-click and choose properties it says that the owner of the device is root and that root has both read and write access to the device. 

I know that I probably could move files to the drive with "sudo mv" command but I really hope that there is some easier way to do this.

So if anyone could help me I would be really grateful :)!

---

### Post by aloshbennett on 2008-09-02
While mounting a device, if you specify "nouser" as an option, the device would be owned by the root.

But if you mount the device with "user" as an option, the current user would be the owner of the device.

I wouldnt know how to do it when the device is automounted.

---

### Post by Dedoimedo on 2008-09-02
Hello,

There could be several problems:

1. You have used the drive previously on Windows and did not unmount it properly. Try to connect it to Windows again and unplug it safely.

2. The drive is formatted as NTFS (Windows file format) and you do not have the right drivers to support this file system. We can solve this relatively easy. Tell me if this is the case.

3. You do not have the right permissions to access the files.

Let's try the good old Linux command line approach.

- Open terminal.

- Type sudo fdisk -l.

This will give you a list of all drives you have. Can you read the Linux notation? If not, tell me, I'll explain.

Once you have identified the external drive partition - let's sat sdb1 - let's try to mount it.

- Create a mount point for it: (sudo) mkdir /mnt/external

- Mount the drive: sudo mount /dev/sdb1 /mnt/external

- See if this works. If not, write the exact error here. Now, try to access the drive either via the GUI or copy some files manually.

Example: cp file1 /mnt/external or cp /mnt/externa/some-file.txt ~/home

Write if there are any errors. If so, you might need the ntfs-3g driver, which can be very easily installed to support a NTFS type drive / partition.

Dedoimedo

---

### Post by bigge on 2008-09-02
> 2. The drive is formatted as NTFS (Windows file format) and you do not have the right drivers to support this file system. We can solve this relatively easy. Tell me if this is the case.


Hi! This seems to be the case, I have a unit called /dev/sdb1 which have the system HPFS/NTFS. 

I have installed ntfs-config, but all I get when I start it is a dialog-box where I can enable NTFS-support for external units.

Is there some easy way to solve this problem? My external drive automounts btw and last time I had it plugged in to a Windows system I unmounted it properly.

Oh by the way, I am running xubuntu 8.04 just so you know.

---

### Post by nothingspecial on 2008-09-02
If your drive is ntfs, 

```
sudo apt-get install ntfsprogs
```

Then

```
sudo ntfsfix /dev/where your drive is
```

You can check where your drive is using

```
sudo fdisk -l
```

---

### Post by nothingspecial on 2008-09-02
Sorry, should have read your post properly. The 2nd command is exactly

```
sudo ntfsfix /dev/sdb1
```

---

### Post by Dedoimedo on 2008-09-02
Hello,

The dialog box is ok! Choose the partition you want to enable and give it a mount point, select its type (internal, external) and finish the mounting process.

Now, navigate to the mount point - /mnt/something and browse your files, try to copy & paste ...

Dedoimedo

---

### Post by bigge on 2008-09-02
Okay, I installed the ntfsprogs and used the sudo ntfsfix /dev/sdb1 command.

First it said that the volume was corrupted and that I had to run chkdsk on it, so I plugged it in on my other laptop which runs Windows XP and ran chkdsk on the external drive. Then plugged it back into my Linux-laptop and tried to execute the sudo ntfsfix command again and now it only gives me this response:

```
$ sudo ntfsfix /dev/sdb1
Refusing to operate on read-write mounted device /dev/sdb1.
```

I have a feeling that this problem is solved any minute now.. But then again, I am a complete newbie to the whole Linux-thing so what do I know :P.

But as always, any help is greatly appreciated! And thanks to those who have answered already :)

---

### Post by bigge on 2008-09-02
> **Dedoimedo said:**
> Hello

The dialog box is ok! Choose the partition you want to enable and give it a mount point, select its type (internal, external) and finish the mounting process.

Now, navigate to the mount point - /mnt/something and browse your files, try to copy & paste ...

Dedoimedo

Thanks for the fast replies! 

How do I choose which partition I want to enable? The dialog box closes after i press the OK-button.

Edit #1:

Oh and by the way this also happens:
```
$ sudo mount /dev/sdb1/mnt/external
mount: cannot locate /dev/sdb1/mnt/external in /etc/fstab or /etc/mtab

```

(I had to alter the text a bit, my xubuntu is in swedish)

Edit #2:

I saw my mistake, I wrote: ```
$ sudo mount /dev/sdb1/mnt/external
```

when it should have been: ```
$ sudo mount /dev/sdb1 /mnt/external
```

It works like a charm now :D! Thank you so very much for the help!

Will the drive automount like this all the time now or do I have to repeat the mounting-process every time I plug it in?

---

### Post by Dedoimedo on 2008-09-02
Hello,

First, good news!

Once you are fully satisfied with the answers, mark the thread as SOLVED. Second, if you want to thank anyone, use the the thank you button.

Now ...

This will work only for the duration of the session. To make the mount points permanent, you can use the ntfs-config tool to mount the drives, this will automount them every time you boot into Xubuntu.

Alternatively, you can manually add an entry to your /etc/fstab file. This file is the list of all mounts.

Be careful when editing, make a backup first!

sudo cp /etc/fstab /etc/fstab-backup

Now, add an entry. How to do this? Well, please read this part of my article - Highly useful Linux commands & configurations:

[http://www.dedoimedo.com/computers/linux_commands.html#mounting_drives](http://www.dedoimedo.com/computers/linux_commands.html#mounting_drives)

Cheers,
Dedoimedo

---

