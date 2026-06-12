---
title: "Create rescue partition that can boot from an Ubuntu iso"
date: 2014-01-24
forum: New to Ubuntu
---

### Post by ptn107 on 2014-01-24
I can't find my original thread to this, so whatever.  I got the partition set up and the installer goes right into ubiquity.  I re-installed my system with it without problems. Here was the final solution.

I created a 2 GB partition that has just the ubuntu-13.10-desktop-amd64.iso file on it.
```
/dev/sda6       974675967   976773119     2097152   83  Linux
```

and here's the final grub custom menu entry
```
menuentry "Reinstall Ubuntu 13.10 64-bit" {
loopback loop (hd0,6)/ubuntu-13.10-desktop-amd64.iso
linux (loop)/casper/vmlinuz.efi file=/preseed/ubuntu.seed boot=casper only-ubiquity iso-scan/filename=/ubuntu-13.10-desktop-amd64.iso noeject noprompt toram quiet splash --
initrd (loop)/casper/initrd.lz
}
```

The error was fixed by adding one '/' before the iso name, to iso-scan/filename=**/**ubuntu-13.10-desktop-amd64.iso and I don't know why but all tutorials I read left it out.

---

### Post by oldfred on 2014-01-24
I used the examples in the example thread. They use a set isofile which has / in it.
set isofile="/iso/ubuntu-12.04-desktop-amd64.iso"

 This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

