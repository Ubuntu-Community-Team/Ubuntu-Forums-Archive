---
title: "Process started in initramfs: How to access root filesystem?"
date: 2008-11-15
forum: Programming Talk
---

### Post by volanin on 2008-11-15
Ok, this one is tricky.
The boot process of the kernel, simplified, is something like this:

1. Boot the kernel vmlinuz image
2. Mount the initramfs image as /
3. Execute /init from initramfs image
4. Mount the real root filesystem as /root
5. Free memory by deleting all files of the initramfs in memory
6. Swap the real root filesystem from /root to /
7. Execute /sbin/init in the root filesystem

Then boot proceeds as normal.
My question is:

If I start a background process in phase 3, by calling it inside /init,
it will survive through the next steps and through normal boot until
it is killed. One common example of this in Ubuntu is usplash.

Is there a way for this process to access a file in the real root filesystem
after step 6? I have tried many times, but it seems that after step 6
it can't read neither from the initramfs files, nor from the root filesystem.

If somebody know anything about this, please help me!
Thank you a lot.
:)

---

