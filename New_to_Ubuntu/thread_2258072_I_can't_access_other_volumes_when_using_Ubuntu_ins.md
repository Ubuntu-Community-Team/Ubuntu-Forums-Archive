---
title: "I can't access other volumes when using Ubuntu installed alongisde Windows8"
date: 2014-12-24
forum: New to Ubuntu
---

### Post by Arnold_O on 2014-12-24
Hello folks,
I am a computer (Ubuntu) dummy and I just installed Ubuntu 14.10 today alongside WIndows 8 that came with the laptop and while I was pretty excited to use something new, I can't access files on the other volumes (105 GB and 69 GB respectively) on which I stored files I use with WIndows. I'll like to know how to fix this. I get an error message which goes like this

"Error mounting /dev/sda3 at /media/binod/38ACB72CACB6E412: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda3" "/media/binod/38ACB72CACB6E412"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda3': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option."

I tried shutting down completely WIndows but no change as you can guess, that's why I am here. What am I to do in the cmd prompt Ubuntu equivalent to fix this?
Thanks for any help

---

### Post by Mark Phelps on 2014-12-24
Windows 8 introduced a new form of hibernation in which all Windows filesytem partitions that were open when Win8 was "shut down" remain mounted -- even when Win8 is not running!  This is due to the feature known as FastStartup.  You have to go back into Win8 and disable than and then, shutdown.  Then, when you reboot into Ubuntu, the other partitions will no longer remain mounted.

The tradeoff is that after than,Win8 will take a LOT longer to boot -- because you basically disabled hibernation.

---

### Post by Arnold_O on 2014-12-26
Thank you Mark!! I saw a video on youtube that teaches how to shut down "completely". A command in the "run" box that goes like this "shutdown /s /t 0" I hope it helps someone because I realised many Ubuntu new users experienced the same problem. Could you please outline the different ways to properly shut down? and how long is "a LOT longer to boot"? 
I have a 2.5GHz, 4GB RAM Toshiba

---

### Post by Mark Phelps on 2014-12-26
Details about how to shutdown in Win8 are better addressed in the Win8 forums -- eightforums.com.

As to a lot longer -- everyon'e boot time varies; thus, it's not possible for me to estimate yours.

---

