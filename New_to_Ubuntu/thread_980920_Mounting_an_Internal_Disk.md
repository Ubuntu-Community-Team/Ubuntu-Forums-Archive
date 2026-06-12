---
title: "Mounting an Internal Disk"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by exicer on 2008-11-13
I recently reinstalled ubuntu on my eeepc (901). It contains 2 disks - 4gb (for the OS) and 16gb for files. Cleverly, I managed to put my home folder on the 4gb one. So, to try and change it I edited my fstab to say 

/dev/sdb1     /home/myname    /ext3   relatime,errors=remount-ro 0 1

Now, my home folder is still on the 4gb disk, and I get a message saying "You are not privileged to mount this volume" if I try and look at it.

Any help on how to fix this would be useful!

Thanks,

exicer

---

### Post by mapes12 on 2008-11-13
This might help: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Coreigh on 2008-11-13
Well first thing I see it a typo error:
> /dev/sdb1 /home/myname /ext3 relatime,errors=remount-ro 0 1
it say relatime, I think you mean realtime.


```
/dev/sdb1 /home/myname /ext3 rw,auto,user 0 1
```

Here is a how-to on an other forum thread:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by prshah on 2008-11-13
> **Coreigh said:**
> Well first thing I see it a typo error:
it say relatime, I think you mean realtime.

```
/dev/sdb1 /home/myname /ext3 rw,auto,user 0 1
```


1) Nope, "relatime" is correct.
2) The code attached is just plain wrong. A corrected version will read```
/dev/sdb1 /home/myname ext3 defaults,relatime 0 1
``` But that still won't solve the problem.

To the OP: You want to mount "/home", not "/home/username". So a possible correction will be ```
/dev/sdb1 /home ext3 defaults,relatime 0 1
```

A further point; I hope the files and directories belonging to "/home" already exist on sdb1.

And you should really use UUIDs, not device names. To find the UUID for /dev/sdb1, use the command [/code]sudo blkid /dev/sdb1[/code] and then further change the fstab to read```
#/dev/sdb1
UUID=[color=blue]xxxxxxxxxxx[/color] /home/myname ext3 defaults,relatime 0 1
```

Replace the part in blue with the UUID you get from the previous (blkid) command.

---

### Post by exicer on 2008-11-13
Ok, so I checked out the guides. Perhaps I am missing something, but basically they seem to suggest I just type sudo mount /dev/sdb1 , which I have tried before. I get an error saying "wrong fs type, bad option, bad superblock on /dev/sdb1 missing codepage or helper program, or other error"

I ran fsck, and there are no problems reported. If I boot with a live usb, I can access the 16gb disk with no problem.

---

### Post by mapes12 on 2008-11-13
> I recently reinstalled ubuntu on my eeepc

If you have nothing on there that would be an issue if you were to start gain then why not do that. Then, when you get to the "Partitioning" section of the install select "Manual" from the options and for each partition set the variables i.e. /(root) for the 4GB part and /home for the other partition. Not forgetting Swap of course but that should already be there. The installer will then assign correct permissions and mount points and you should be up and running again.

---

### Post by exicer on 2008-11-13
True, but it's frustrating that I don't know why it doesn't work!

---

### Post by mapes12 on 2008-11-13
> True, but it's frustrating that I don't know why it doesn't work!
Welcome to Linux!

But seriously, unlike some commercial OS's, and because Linux is so flexible, there are many many ways to resolve issues. Although a reinstall may take about 30 mins or so (or less sometimes) at least you know your configuration is fresh and ready to go:guitar:

Keep /home on a separate partition (see my sig below) and a system restore can take no time at all.

---

