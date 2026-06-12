---
title: "Fstab Accidentally Renamed! PLEASE HELP!!!"
date: 2013-08-17
forum: New to Ubuntu
---

### Post by steamer360 on 2013-08-17
I was tinkering around with my machine (Acer C7 Chromebook), and renamed my fstab file to fstabBACKUP. When I tried to reboot, I just got a black screen. So, I pressed CTRL ALT F2 and it took me to a shell that said 
```
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.
root@JackBook:~#
```
Then, I tried to rename the file using the mv command:
```
mv /etc/fstabBACKUP /etc/fstab
```
That didn't work and I got this outcome:
```
mv: cannot move '/etc/fstabBACKUP' to '/etc/fstab': Read-only file system
```
My computer can't be accessed at the moment, and I can't really boot into recovery (because I'm on a Chromebook) without having to reinstall my software again, which would be a MAJOR pain.
Can somebody PLEASE help me with this?

---

### Post by carl4926 on 2013-08-17
Use a live CD and chroot in to your system
Or Parted Magic [http://sourceforge.net/projects/partedmagic/](http://sourceforge.net/projects/partedmagic/)
Can mount partitions and edit with full permissions, might be easier for you

---

### Post by steeldriver on 2013-08-17
From the recovery shell, you can remount the root filesystem with read-write permissions using

```
mount -o remount,rw /
```

Make sure you type it exactly (no space between 'remount' and 'rw' - just a comma) - after that try again with the mv command

---

### Post by ajgreeny on 2013-08-17
> **steeldriver said:**
> From the recovery shell, you can remount the root filesystem with read-write permissions using

```
mount -o remount,rw /
```

Make sure you type it exactly (no space between 'remount' and 'rw' - just a comma) - after that try again with the mv command

Surely with no fstab file the OP will not be able to get to recovery mode.  Or perhaps I have misunderstood the problem.
EDIT:
Sorry, ignore this.  I mistook recovery shell for recovery mode.

---

### Post by steamer360 on 2013-08-17
I can't boot from a live cd because I am using a Chromebook, and the remount command leads me to this error:
```
warning: can't open /etc/fstab: No such file or directory
```

Is there any sort of solution to this problem?

---

### Post by steamer360 on 2013-08-17
Also, if I could just rename the file, that should do the trick.

---

### Post by steeldriver on 2013-08-17
Oops my bad - of course ajgreeny was right, if you can't mount / then of course you can't **re**mount it either (I guess I was thrown off by the mv command apparently being found)
Do either of these commands work?

```

fdisk -l

blkid

```

If so then I guess you may be able to figure out which is your root partition and mount it manually, and then fix the /etc/fstab file?

---

### Post by Bashing-om on 2013-08-17
Manually boot the system from the grub menu ???
see:
[http://askubuntu.com/questions/21342/how-can-i-load-ubuntu-when-all-i-have-is-grub](http://askubuntu.com/questions/21342/how-can-i-load-ubuntu-when-all-i-have-is-grub)

I have seen other docs, this one looked simple and easily implemented.

[INDENT][INDENT]hey it's a thought
[/INDENT][/INDENT]

---

### Post by steamer360 on 2013-08-17
Those commands do work, SteelDriver. How would I go about mounting the partitions manually?

---

### Post by steamer360 on 2013-08-17
FANTASTIC!!! I finally found a way to rename it! First I opened the nano text editor in the shell:
```
sudo nano /etc/fstabBACKUP
```
Then, I typed in CTRL o to do a writeover, and renamed the file as fstab. Finally, I exited out of the nano editor using CTRL X and saved the file. Then when I rebooted, it worked like normal. Thanks for all the suggestions!

---

