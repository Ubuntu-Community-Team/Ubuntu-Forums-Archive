---
title: "Auto Mount at start"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by GBee on 2008-04-24
I've installed the RC, and my two Windows partitions don't auto mount at start up now, help, oh and thanks for the helps i'm sure to get. I can mount the partitions after start up, but that's a pain to do manually as i have Amarok pointing at a folder in Windows where i keep my music.

Cheers

---

### Post by aeiah on 2008-04-24
you need to add them to your fstab file (/etc/fstab)

ubuntu.com is dying right now due to the release of 8.04 so i cant search the wiki and help for you, but there is some info here as to what to put in your fstab, and strewn across google.

---

### Post by GBee on 2008-04-24
Thanks, that's a start, i'll keep hunting for a solution, you're right, nothing about the two partitions on fstab

---

### Post by enigmaniac23 on 2008-04-24
Here's my fstab line that mounts my windows drive at boot.

/dev/sda2	/media/disk	auto auto,users,uid=1000,gid=1000 0 0


Obviously you'd customize based on your disk and mount point.

---

### Post by GBee on 2008-04-24
any risk? i assume (possibly dangerously so) that i change sdaX and media/XXXXX to whatever mine are? just don't want to murder anything, i'm loving hardy

---

### Post by enigmaniac23 on 2008-04-24
That should do it.  You might also have to change the uid and gid, but probably not.  

The worst that "should" happen is if it's wrong it just doesn't mount properly, assuming you don't mess with the other stuff in there.

Check out this thread for a very detailed explanation of fstab.
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by FuturePilot on 2008-04-24
You can also use the ntfs-config tool which is in the repositories. The problem with adding them to fstab is that you won't be able to unmouont them if you want to without opening a terminal. If you configure them with ntfs-config you can right click it and unmount it that way.

---

### Post by GBee on 2008-04-24
enigmaniac23 Thanks, it worked a treat

FuturePilot, i tried ntfs-config, the only option the GUI gave me was to make external drive read/write or something to that effect, but you are right, i can't mount after unmount. Am i not using ntfs-config correctly?

---

### Post by GBee on 2008-04-24
Oh, and now, how do i remount the partition i unmounted? It's dead in the water now? Thanks for your patience!

---

