---
title: "update error"
date: 2008-09-17
forum: Philippine Team
---

### Post by dareymon on 2008-09-17
when im trying to update ubuntu, an error message pops out

here's the message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

how to fix this?

tnx;)

---

### Post by loell on 2008-09-17
what's the output when you execute

```
sudo dpkg --configure -a
```

---

### Post by dareymon on 2008-09-18
here's the output.


Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
dpkg: subprocess post-installation script returned error exit status 1


regards

---

### Post by loell on 2008-09-18
oh boy, you have no space left :(

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=889368]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=889368")

probably deleting other older kernels in your boot directory might work, but not advisable.

---

### Post by dodimar on 2008-09-18
> **loell said:**
> oh boy, you have no space left :(

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=889368]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=889368")

probably deleting other older kernels in your boot directory might work, but not advisable.

does this mean that whenever we update Ubuntu, it gets bloated?

---

### Post by pendletone on 2008-09-18
i don't think *bloated* is the correct term for this. when something is bloated (in software) it means that it uses more system resources than necessary.

but yes, it does get *larger* in time. just like windows does when it updates.

---

### Post by loell on 2008-09-18
> **dodimar said:**
> does this mean that whenever we update Ubuntu, it gets bloated?

these are past kernels where you can choose later if you encounter something that doesn't work in that particular kernel update, ubuntu doesn't carelessly delete this, if you meant bloated in disk space? yes, does it get sluggish? nope ;) only the last updated kernel is loaded at startup.

---

### Post by dodimar on 2008-09-18
At least, it's just the drive space that gets occupied. Unlike in windows that every upgrade makes your system slower.

---

