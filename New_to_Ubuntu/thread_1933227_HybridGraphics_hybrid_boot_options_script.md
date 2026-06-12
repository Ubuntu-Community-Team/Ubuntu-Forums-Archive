---
title: "HybridGraphics hybrid_boot_options script"
date: 2012-02-28
forum: New to Ubuntu
---

### Post by kmuels on 2012-02-28
This thread seems pretty much the same as [http://ubuntuforums.org/showthread.php?t=1856690](http://ubuntuforums.org/showthread.php?t=1856690), but unfortunately that thread has been closed with no answers.  

I followed the instructions to create a bootup script from [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics) in order to turn off my Discrete graphics card on bootup.  

The bootup script seems to be running fine, but I get the following errors because the vgaswitcheroo directory is not mounted yet.  Taken from /run/initramfs/initramfs.debug with the 'debug' flag set in the grub boot options:

```

...
Begin: Running /scripts/local-top ... + run_scripts /scripts/local-top
+ initdir=/scripts/local-top
+ [ ! -d /scripts/local-top ]
+ [ -f /scripts/local-top/ORDER ]
+ . /scripts/local-top/ORDER
+ /scripts/local-top/hybrid_boot_options
Switching hybrid graphics to ON
/scripts/local-top/hybrid_boot_options: line 62: can't create /sys/kernel/debug/vgaswitcheroo/switch: nonexistent directory
Switching hybrid graphics to IGD
/scripts/local-top/hybrid_boot_options: line 62: can't create /sys/kernel/debug/vgaswitcheroo/switch: nonexistent directory
Switching hybrid graphics to OFF
/scripts/local-top/hybrid_boot_options: line 62: can't create /sys/kernel/debug/vgaswitcheroo/switch: nonexistent directory
...

```I know that when I try to access this directory after boot in a terminal, I need to be root in order to even see it (not sure if this has anything to do with it).  

Attached is the actual bootup script I am using, taken from the Ubuntu HybridGraphics site above.

Any help would be appreciated, as it would be a pain to turn my Discrete card off every time I log on! 
Thanks!

---

### Post by kmuels on 2012-03-07
I am marking this thread as solved because I found a different solution.  I used a combination of [http://ubuntuforums.org/showthread.php?t=1873845]("http://ubuntuforums.org/showthread.php?t=1873845") and adding a sleep command at the top of /etc/rc.local. I added the sleep because sometimes the rc.local file would run earlier than I wanted, and the commands I needed would not complete.  I ended up inserting the following commands to into my /etc/rc.local file in order to shutdown my discrete card on bootup:

```

sleep 7
sudo chown -R <user>:<user> /sys/kernel/debug/
sudo echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

```

---

