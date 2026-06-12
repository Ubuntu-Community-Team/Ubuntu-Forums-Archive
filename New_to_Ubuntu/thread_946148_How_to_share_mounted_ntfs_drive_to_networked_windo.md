---
title: "How to share mounted ntfs drive to networked windows terminals"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by hatros on 2008-10-13
Hi,

I have a dual-boot system. Ubuntu 8.04 and XP-Pro.

When I ran XP exclusively, I used to drop files into a shared folder that my wife could easily open on her Vista laptop.

When I'm in Ubuntu, I still want to be able to drop files into a shared folder that she can easily open on her Vista box.

So.. I mounted my XP NTFS drive in /etc/fstab with:
/dev/sdc1 /mnt/xp ntfs nls=utf8,umask=0222 0 0

I can browse to a folder I want to share out, and then use  shares-admin to manually share it out, .. that seems to work ok; but I want the folder to share out on boot. How do I go about doing that?

Thanks for any help!

---

### Post by hatros on 2008-10-17
Nevermind. Figured it out.

---

