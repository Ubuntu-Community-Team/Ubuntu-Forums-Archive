---
title: "I can't run my Ubuntu"
date: 2021-06-10
forum: New to Ubuntu
---

### Post by akstide2000 on 2021-06-10
Hi, I'm new using Ubuntu. And normally I can solve most issues but this Last one is getting me crazy.

After installed something, i turned off my laptop, in the night, I wanted to use it. Everything was running normally, but on the Ubuntu loading screen there is a message 
"An error has occurred mounting /home

Press S for don't mount or M for manual reparation" 

It's not exactly, because i translated to English

If I press S my laptop just show me the cursor

And if I press M it takes to a command line

---

### Post by mikewhatever on 2021-06-11
There might be a problem with the storage device - HHD, SSD or whatever you have. Boot from an Ubuntu Live USB, and theck the S.M.A.R.T. atributes.

---

### Post by ActionParsnip on 2021-06-11
Fsck from live CD / USB.

---

### Post by tea for one on 2021-06-11
> **akstide2000 said:**
> After installed something, i turned off my laptop

What did you install?
How did you install it?

---

### Post by TheFu on 2021-06-11
There's a problem.

It has something to do with the file system where your HOME directory is located.  Chances are that the automatic running of fsck on that file system failed - or there are errors that must be agreed to accept.  We are assuming that / and /home are different partitions.

At boot, in the grub menu, there's an "advanced" choice. Choose that.  When the TUI comes up, there should be a "Check all file systems" choice. Try that.

If it doesn't work, try the manual way. Boot like you've been doing, but choose M for the manual repair option. You'll need to know the device name where the file system is and manually run it. The fsck command looks like:
```
sudo fsck /dev/sd_Z3_
```
You'll need to figure out the correct device.  Also, if you use LVM, you'll need to figure out the device mapper name, not the partition device.  Same for ZFS OR BTRFS, but for the common EXT4 file systems, fsck is the command.  If NVMe storage is involved, the device name will be very different. Same for soldered on storage or a microSD card (usually seen on r-pi devices).

If everything works, run **sudo mount -a** to mount all the storage from the /etc/fstab.  If your HOME mounts clean, you are done. Reboot and a GUI login should be displayed.

If something is still wrong, I'd make a backup of any files you can't lose ASAP to other storage.  Then boot from a Try Ubuntu flash drive and use whatever tools you prefer to check on the health of the drive and file system for the storage device.  I'd use **smartctl**, but do it however you like.

---

