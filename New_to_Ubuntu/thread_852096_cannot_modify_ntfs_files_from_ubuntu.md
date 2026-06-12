---
title: "cannot modify ntfs files from ubuntu"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by santiagorf on 2008-07-07
Hi all,
I was using windows xp on a partition, and since my xp stopped working (showing the blue screen when it starts), I couldn't have access to the file of this partition from ubuntu.
I'm not very skilly with ubuntu, and so I tried solving the problem using "the storage device manager" which at least let me mount the NTFS partion to read the files. 
However, when I try to mount the NTFS partition using the same program but without using the option: "Mount file system in read-only mode", I cannot mount it
So far, the best I can do is to read the NTFS partition from ubuntu without being able to modify the files.

I tried solving the problem using NTFS configuration tool, with no positive result.

Any idea of how can I solve it?
Thanks in advance
Santiagorf

---

### Post by Darkspark on 2008-07-07
I have never had problems editing files with the LiveCD or the installed partion. Personally, the only thing I can think of is the copy all the imporant files off of XP onto another drive or your Xubuntu partion. Then to pop back in the Windows XP install or recovery disk and reformat that part of the partion. Reinstall it and then overwrite the MBR with whatever boot loader you use again, the Xubuntu LiveCD if you use Grub. Make sure you back up your important files first though.

---

### Post by kansasnoob on 2008-07-07
I'll assume you're using Hardy but I think this would also work in previous distros (shout if I'm wrong), anyway I'd start by installing 

> ntfs-config

from synaptic. This provides good ntfs read/write support.

The package > ntfsprogs which is also in synaptic provides more extensive ntfs support but it's a bit more fiddly:

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

---

### Post by santiagorf on 2008-07-07
solved it!

When I executed gksudo ntfs-config, and I chose "enable write support for internal device, I got the following message:


Mounting /media/hda1 failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/hda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/hda1 ntfs-3g force 0 0


and then I executed 
sudo mount -t ntfs-3g /dev/sda1 /media/hda1 -o force

thanks for your help!

---

