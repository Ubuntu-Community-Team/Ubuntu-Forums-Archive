---
title: "Kernel Panic - not syncing VFS"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by Jeffrey Kang on 2012-02-01
When I try to boot up my laptop, I get a black screen and error message that says: "0.9009321 Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"

I've googled the error message and all I'm getting is that people tried to update their system and booted and got the same error. I, on the other hand, did not update my system but somehow I'm getting this error.

I've downloaded a new liveCD, and I want to retain all my files on the laptop. What should I do?

Note: I'm a complete beginner so I'm afraid I don't really know my way around the terminal. All help is much appreciated.

---

### Post by xopher_mc on 2012-02-01
Could you load a live ubuntu cd?

You will then need to open the /etc/fstab on the system partition on your hard drive. You may need to type sudo nautilus to do this (be vary careful and do not save any changes). 

Also you will need to load terminal and type 

```
sudo fstab -l 
```

please copy and paste the output of both commands.

---

### Post by Jeffrey Kang on 2012-02-06
Ok. Here's what I did. I booted from liveCD, opened terminal, typed "sudo nautilus" and it opened the file browser. I navigated from "file system" > etc > fstab and here's what it says:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>  <type>          <options>         <dump>  <pass>
proc            /proc          proc            nodev,noexec,nosuid  0       0
/dev/sdal       /              ext4            errors=remount-ro 0         1
# swap was on /dev/sda5 during installation
UUID=551094e4-5b6e-42b6-ad04-6f2943eab09d      none               swap
sw              0          0


Then for the sudo fstab -1, it says:
command not found

---

### Post by Jeffrey Kang on 2012-02-20
Resolved. I just did a reinstall and deleted everything.

---

### Post by mastergkage on 2012-02-20
> **Jeffrey Kang said:**
> Resolved. I just did a reinstall and deleted everything.

Like!:lolflag:

---

