---
title: "error: ELF header smaller than expected. grub rescue&gt;"
date: 2016-03-18
forum: New to Ubuntu
---

### Post by tc0nn on 2016-03-18
I found several other threads suggesting how to fix this, which none were easy in my case. 

It turns out, the server was in the middle of a apt-get dist-upgrade when someone rebooted it. So after a lot of digging around, I was able to
1) boot the Ubuntu Desktop DVD in "try" mode
2) switch to a text console
3) mount the root and boot partitions
4) found /boot/grub/ was very badly corrupted (all *.mod files were 0 size) - this was causing the error " error: ELF header smaller than expected. grub rescue> " when insmod normal would attempt to run.
5) brought up eth0, restored /boot/grub from a like server.
6) reboot, initramfs, oops... Forgot to fix the grub-config. Since the partitions are referenced by UUID, you need to create links to the real partitions that match the UUID. I did this manually, but then ran:
7) update-grub
8) reboot

Hope this helps someone else get to bed early...

---

