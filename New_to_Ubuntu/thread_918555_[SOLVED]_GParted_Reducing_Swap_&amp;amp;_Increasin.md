---
title: "[SOLVED] GParted: Reducing Swap &amp;amp; Increasing ext3"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by epidemiks on 2008-09-13
Hi,
During this last install I made a silly mistake and made my Swap partition 10GB. After a bit of hunting, I've come to realise this is pretty much useless as I only run 1GB/RAM. 
So I want to resize my swap down to ~2GB and let ubuntu use the excess.

So, just to be sure I'm not overlooking anything, could I get a few pointers on using gparted from the livecd to make this a success.

One of my main concerns is keeping my XP safe. 
The documentation on [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php) only really talks about making changes to NTFS partitions, but I'm not going to be touching them.
If I'm not making any changes to the XP boot drive (different physical disk), should I worry about the MBR getting eaten etc?

Is gparted really just as simple as "partition:resize/move" to shrink the swap, then "partition:resize/move" to grow ubuntu into the new free space? And will increasing ubuntu's partition affect it booting Grub etc?

Also, I have a few questions about backing up data, but I'll have a bit more of a hunt around before making the *n*th "how do i backup?" thread

Thanks!

---

### Post by swoll1980 on 2008-09-13
It's pretty cut, and dry. Just shrink the swap partition then expand the ext3 to take up the extra space. Your xp partition is safe unless you delete it (which would be imposable to do unless you wanted too)

---

### Post by epidemiks on 2008-09-13
> **swoll1980 said:**
> It's pretty cut, and dry. Just shrink the swap partition then expand the ext3 to take up the extra space. Your xp partition is safe unless you delete it (which would be imposable to do unless you wanted too)

Thanks, I think all the ntfs references in the docs i'm reading are just freaking me out lol!

---

### Post by Elfy on 2008-09-13
One small point - you will need to resize the extended partition before you can resize the ext3, swap is inside the extended. You need the spare outside where your linux is.

---

### Post by cotcot on 2008-09-13
I suggest to use the [[COLOR="Blue"]Gparted LiveCD[/COLOR]]("http://gparted.sourceforge.net/livecd.php") for changing partitions and to let gparted finishing a job before ordering a new job. With this I have never had problems.
If you shrink the swap you will see an unallocated space between swap and your ntfs. After that you can move the ntfs. After that you can extend the ntfs or use the free space to install linux for experimenting. It is good to try out something before using it on your default OS.   

I also suggest to study a backup strategy (as you annonce) before changing partitions. That is safer anyway.

For backup I have a script to incremental backup my important directories to partitions on a second hard disk.
> # rsync.sh
#
# - this script will back up my 2 dirs that need to be synchronized with 
# (mirrored to) my external ext3 usb disk:
# 
# 
# 
# - can be executed by user (no need for sudo/root access)
# - other dirs (video, tgz, etc.) must be updated by hand
# 

echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo "(1) Backing up Documents"
echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"

ls /home/cotcot/Documents
rsync -vurt --progress --delete /home/cotcot/Documents/ /media/sdb7/Documents/
echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo "(2) Backing up Foto..."
echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"

ls /home/cotcot/Foto
rsync -vurt --progress --delete /home/cotcot/Foto/ /media/sdb7/Foto/

echo ""
echo "~*~*~*~*~*~*~*~*~*~*~*~*~*"
echo "All done!"

---

### Post by epidemiks on 2008-09-13
thanks everyone 

cotcot, does that just backup/sync files that have changed? thats pretty much what I'm looking for.

but fools rush in.. I'm in the hardy live cd now.

As for moving the extended partition, is it better to cut from the start or end of the swap?

---

### Post by Elfy on 2008-09-13
> As for moving the extended partition, is it better to cut from the start or end of the swap?It's a while since I used the partition tool on the buntu livecd as I use a seperate part editor.

What you need to do is resize the swap from the left to right so that the unallocated space is on the left, then shrink the extended, once that is done you can grow the ext3 from the right.

You will need to do this in a livecd anyway so that partitions are unmounted. I use partedmagic [http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php) - it also includes some other useful tools and boots quicker than the full buntu livecd.

If you decide to use your buntu disc then you must turn off swap before you start ```
sudo swapoff -a
```

Further once you have completed the task, your swap will likely have a new UUID and you will need to edit fstab and the resume=  in  /etc/initramfs-tools/conf.d/resume

---

### Post by epidemiks on 2008-09-13
> **forestpixie said:**
> It's a while since I used the partition tool on the buntu livecd as I use a seperate part editor.

What you need to do is resize the swap from the left to right so that the unallocated space is on the left, then shrink the extended, once that is done you can grow the ext3 from the right.

ah, good. Thats how I've got it, finger on the trigger. 
gparted actually let me turn off the swap from a context menu.

> Further once you have completed the task, your swap will likely have a new UUID and you will need to edit fstab and the resume=  in  /etc/initramfs-tools/conf.d/resume

ok, how do I find what the new UUID once I've completed the process? And I assume I shouldn't reboot until I've updated these things?

---

### Post by Too Late on 2008-09-13
> **epidemiks said:**
> how do I find what the new UUID once I've completed the process?
```
sudo blkid
```

---

### Post by epidemiks on 2008-09-13
Ok, so all operations are done, and Swap has a new UUID, everything is mounted, but but fstab does not reference any UUID, and /etc/initramfs-tools/conf.d has no 'resume', nothing (I have disabled sleep/hibernate, is that why?) 
so do I need to update anything?

---

### Post by Elfy on 2008-09-13
Yea that would be why there is no RESUME=

Does fstab reference it as /dev/sdxy if so that's fine, just so long as it is there in one way or the other it should be ok.

---

### Post by epidemiks on 2008-09-13
> **forestpixie said:**
> Yea that would be why there is no RESUME=

Does fstab reference it as /dev/sdxy if so that's fine, just so long as it is there in one way or the other it should be ok.


fstab's swap line: /dev/sdb6 swap swap defaults 0 0

:)

now to reboot!

---

### Post by epidemiks on 2008-09-13
Worked a charm, except conky says I have no swap.
I'll tackle that tomorrow, got some drinking to do..

Thanks everyone, the cheques are in the mail!

---

### Post by Elfy on 2008-09-13
my fstab line reads

UUID=number none  swap sw 0 0

but as long as free -m reports it's there that's good :)

No drink for me it's 10am lol

---

### Post by epidemiks on 2008-09-13
erm, i've had several drinks, but free -m says

Swap:            0          0          0

everything seems to be operating as per normal, but conky still reports no swap.
I'm beginning to fear the worst.

---

### Post by Elfy on 2008-09-13
Unfortunately everything is not operating normally - at least swap isn't :)

Try ```
sudo swapon -a
```

Then free -m again, should be different.

Glad you've had a drink - I still haven't :(

---

### Post by epidemiks on 2008-09-13
oh, the drink was purely in preparation for this!
it's still giving me the old UUID when I sudo swapon -a

```
swapon: cannot canonicalize /dev/disk/by-uuid/1553f7e3-1410-469d-9207-c8914814739a: No such file or directory
swapon: cannot stat /dev/disk/by-uuid/1553f7e3-1410-469d-9207-c8914814739a: No such file or directory
```

ahhh, fstab actually does still reference the old UUID. 

"UUID=1553f7e3-1410-469d-9207-c8914814739a none swap sw 0 0"

I though that what I was looking at when in the livecd was the real fstab - clearly not..

"sudo gedit etc/fstab" + update with new UUID + "sudo swapon -a" = win!

Swap:         2062          0       2062


I think you deserve that drink forestpixie!! thanks again

---

### Post by cotcot on 2008-09-13
> **epidemiks said:**
> 

cotcot, does that just backup/sync files that have changed? thats pretty much what I'm looking for.



Yes, thats is through. That is what is called incremental backup.

---

### Post by elvis-nguyen on 2009-10-28
In my laptop, gparted disables Resize/Move functions. I don't how to enable them although the free space remains over 2GB.

---

