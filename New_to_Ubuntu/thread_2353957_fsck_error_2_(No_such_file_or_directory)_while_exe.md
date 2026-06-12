---
title: "fsck: error 2 (No such file or directory) while executing fsck.ext2 for /dev/sbd4"
date: 2017-02-26
forum: New to Ubuntu
---

### Post by gregcb on 2017-02-26
Firefox had stopped working and had closed my browser window and would not let me open a new one until I had closed the old one but I couldn't, so I restarted my computer. After selecting to boot Ubuntu, my screen showed the following:

/dev/sbd4 contains a file system with errors, check forced.
Inodes that were part of a corrupted orphan linked list found.

/dev/sbd4: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
             (i.e., without -a or -p options)
fsck exited with status code 4
done.
Failure: File system check of the root filesystem failed
The root filesystem on /dev/sbd4 requires a manual fsck

BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built in commands.

So, then I tried that and got this:

(initramfs) fsck /dev/sbd4
fsck from util-linux 2.27.1
fsck: error 2 (No such file or directory) while executing fsck.ext2 for /dev/sbd4

What do I do to fix this? I am able to see all of my partitions when I boot from usb to try Ubuntu.

---

### Post by Bashing-om on 2017-02-26
gregcb; Hellol

One must run a file system check from an external means - can not test/check/repair a file system while in use ( mounted )/
Further in grub .. grub will not understand a identifier such as sdb4 - that is not in grub speak .

So what we do is work from say a liveUSB from the try ubuntu terminal.
Make sure that the target remains identified as 'sdb' , Depending on when a device is recognized by the system is what the device name is given.
```

sudo parted -l

```
now "assuming" that the target remains as 'sdb4' then run:
Make sure swap is not in use:
```

sudo swapoff -a

```
```

sudo e2fsck -C0 -p -f -v /dev/sdb4

```
if errors: -y auto answers yes for fixes needing response see: man e2fsck
```

sudo e2fsck -f -y -v /dev/sdb4

```

[INDENT][INDENT]hope is that all is fixed right up
[/INDENT][/INDENT]

---

### Post by steeldriver on 2017-02-26
. . . are you sure it's not just a simple typo?

```

/dev/s[COLOR=#0000ff]db[/COLOR]4

```

rather than 

```

/dev/s[COLOR=#ff0000]bd[/COLOR]4

```

---

### Post by gregcb on 2017-02-26
Wow... thanks for pointing that out.

---

