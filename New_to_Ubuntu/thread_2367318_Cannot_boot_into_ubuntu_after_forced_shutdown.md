---
title: "Cannot boot into ubuntu after forced shutdown"
date: 2017-07-28
forum: New to Ubuntu
---

### Post by oliviabaq on 2017-07-28
Hello, all!
I have owned a System76 laptop for about four years, but have never had a troubleshoot a problem of this kind before, so I dropped in this forum...
Last night, one of my siblings Hibernated the laptop (I forget how I activated that feature, but it never worked correctly so I avoided it) and on starting it up this morning, it was acting up. I attempted to shut it down, but it wouldn't--not even from Terminal, so when it froze on logging out of my account, I held the power button to shut it off. 

On turning it on again, it gave a "Unexpected Inconsistency run fsck MANUALLY" so I booted to a Ubuntu 16.04 livecd and did that. On finishing, the fsck said the drive (dev/sda2) was not entirely fixed. I ran it again, and it gave this error:
e2fsck 1.42.13 (17-May-2015)
fsck.ext4: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?

I restarted the computer, and it couldn't boot and gave this error:
failure reading sector 0x1008 from hd0 
and went into grub rescue. 

I do not know what to do. When I google the fsck problem, everything that comes up mentions a bad superblock, but none of the fsck checks I have done say that there is a bad superblock, just that the "attempt to read block from filesystem resulted in a short read".
Googling the grub rescue issue brings up advice to run a boot repair, but boot repair suggests backing up my files first and I don't know how to do that given the current situation. 

What should I do?

---

### Post by Autodave on 2017-07-28
To back up your files, boot from a live USB or DVD. From that you can then mount the HD and copy anything you may need to a USB stick or external HD.

As to fixing what is wrong, sorry, but no ideas here.

---

### Post by Geoffrey_Arndt on 2017-07-29
To me, my data is the most important thing on the PC.   If that is copied & saved to an external device, then  . . . I'd opt for a **_full reinstall_** as that takes the least time and restores your system to a pristine state.    Then, don't enable any services or install any apps if you're not 100% sure what they do.

On most machines, there is really no good reason for hibernation anymore (so don't enable it).

---

### Post by cariboo on 2017-07-29
Try starting in recovery mode, select root from the menu, at the prompt type:

```
fsck /dev/sda1
```

assuming your / directory is on /dev/sda1.

---

### Post by oliviabaq on 2017-07-29
Thanks to all for your suggestions. 
It seems that the superblock was the problem after all. After running the fix that people suggest for that (using the backup copies in order to run e2fsck on the drive) I was able to access the drive again.

---

### Post by desimzatube on 2017-07-30
I was looking for this answer, I have got the answer here, thanks

---

