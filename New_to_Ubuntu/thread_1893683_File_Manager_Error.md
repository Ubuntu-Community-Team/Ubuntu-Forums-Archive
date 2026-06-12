---
title: "File Manager Error"
date: 2011-12-10
forum: New to Ubuntu
---

### Post by joshswain123 on 2011-12-10
I just recently installed Lubuntu 11.10, and when I open File Manager, I get the error in the attached screenshot. So far, it hasn't caused any noticeable problems, but I'm curious what it means.

---

### Post by nothingspecial on 2011-12-10
Are you using sshfs, fuse, samba etc?

---

### Post by joshswain123 on 2011-12-10
...translation? 0:]

I'm not entirely sure what those are.

---

### Post by nothingspecial on 2011-12-10
That would be a no then :)

It looks like your file manager is trying to mount a remote filesystem and failing.

Have you done anything out of the ordinary since installing ?

---

### Post by joshswain123 on 2011-12-10
Not that I know of; I installed a few packages for flash/java/dual-layer dvds, but other than that, nothing really unusual...

---

### Post by SteveDee on 2011-12-12
> **joshswain123 said:**
> ...So far, it hasn't caused any noticeable problems...

So are you saying its done this from day 1, and that after the message is cleared the file manager appears to work OK?

Do you get a complete set of items in the left pane (Desktop, Rubbish, Applications)? Maybe post a screen-shot after the message is cleared.

It may also be worth posting your /home/josh/.config/pcmanfm/lubuntu/pcmanfm.conf file, although I can't imagine a problem in this would cause such a error.

---

### Post by joshswain123 on 2011-12-12
This is File Manager, post error.

---

### Post by jtarin on 2011-12-12
> **joshswain123 said:**
> This is File Manager, post error.Are you using an external USB drive sometimes?

---

### Post by joshswain123 on 2011-12-12
Yes, one is plugged in normally as I use it to work between home and school.

---

### Post by ubername on 2011-12-13
Did you install when the USB drive was plugged in?

Do you get the message if you start the file manager with the USB drive plugged in?

---

### Post by joshswain123 on 2011-12-13
No to the first, and no to the second.

---

### Post by jtarin on 2011-12-13
Does the drive show in File manager when plugged in?
Copy and post here the contents of /etc/fstab here.

---

### Post by joshswain123 on 2011-12-14
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=90a81c9f-f771-4471-b845-1e92052b6aca /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
#UUID=8a780dcf-996f-446c-ade9-c0730cb6e267 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```

---

### Post by amjjawad on 2011-12-14
Hello there :)

Thanks for choosing and using Lubuntu :)

Do you still get that error? can you re-produce it? have you checked MD5SUM before creating the LiveCD or LiveUSB?

---

