---
title: "sync with fat32/ntfs formatted nas"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by tramir on 2008-07-06
I am trying to find a solution to "backup" (better said, sync) my home partition with a NAS. The problem is that the partition in the NAS can only be formatted as FAT32 (rumors are it might work with NTFS too, but that wouldn't help too much anyway). What I'd like to have is something along the lines of Unison/rsync, but that would somehow allow me to preserve the permissions of the files. I've spent a couple of weeks already trying to figure out if there's any way to achieve this. Anybody has any idea?

One thing I thought of was to somehow get a list of all the files (their permissions and owners) in a file that would be saved on the NAS and could then be used to restore the permissions. But my knowledge of the utilities that could produce this file and then read it to restore the permissions are more than limited. Any ideas?

Thanks in advance for any help...

---

### Post by HalPomeranz on 2008-07-06
You could create a "file system within a file system".  Basically you would create a big file on the NAS device that you would then format as an ext file system.  This file can then be mounted on your Linux box via a loopback mount and you can write files into it just like a normal Unix file system, preserving the normal Unix file system ownerships, permissions, etc.

To create the file system:

```

cd /path/to/NAS/storage
dd if=/dev/zero of=linuxfilesystem bs=4096 count=10000000
sudo mkfs linuxfilesystem

```

This will create a file called "linuxfilesystem" that's roughly 40GB in size and build an ext file system in it.  If you want to make the file bigger or smaller, just change the value of the "count=" parameter (every 1,000,000 units is roughly 4GB).

Once you've created the file system, you can mount it with:

```

sudo mount -o loop /path/to/NAS/storage/linuxfilesystem /mnt

```

Once you do that, anything you write into the /mnt directory will actually end up getting written into your new file system.  When you're done writing data, you can unmount the file system with:

```

sudo umount /mnt

```

Note that if you want to protect your data more stringently, you could use Truecrypt to create an encrypted container (documentation available from [www.truecrypt.org/docs](www.truecrypt.org/docs)).

---

### Post by tramir on 2008-07-06
Wow, thanks, I was wondering if something like that was possible, just didn't know how to do it. That should work. Is there any way I could do this on a FAT32 partition as well (2GB file limit)? Just in case the NAS doesn't work with NTFS.

---

### Post by HalPomeranz on 2008-07-06
> **tramir said:**
> Is there any way I could do this on a FAT32 partition as well (2GB file limit)? Just in case the NAS doesn't work with NTFS.

Hmmm, there might be some trickery you could do with LVM to make a bunch of 2GB files look like a single combined file system, but I'm not certain how to do that off the top of my head.

One weird option would be to create a virtual machine using something like VMware and use the NAS storage as the location of the virtual disk drives (VMware has built-in support for splitting virtual disks into 2GB chunks).  You could run Ubuntu or some other distro inside the virtual machine and do your rsyncs to that.

---

### Post by tramir on 2008-07-06
Cool, I'll look into that to see if/how it could be done. I'll report back after I look into that, just in case anybody else is interested. Thanks for all your ideas, it helped a lot!

---

