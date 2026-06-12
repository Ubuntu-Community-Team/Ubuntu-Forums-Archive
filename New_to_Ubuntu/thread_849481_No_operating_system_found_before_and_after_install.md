---
title: "No operating system found before and after installation of Ubuntu"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by Bella2u on 2008-07-04
Have used HP formerly had Win XP now it has a different hard drive with No Operating System on it; next installed Ubuntu 8.04. Followed all installation steps from live CD. Everything appeared to be fine until the reboot after removing live CD.

Problem: does not boot up to Ubuntu; still have black screen with the message "No Operating System found". (tried re-installing ubuntu 3 times, received same message)
What do I do to resolved this glitch?  :popcorn:

---

### Post by ibuclaw on 2008-07-04
Try reformatting the hard-drive before the installation using the partition editor in the "System>Administration" menus.

Then when it comes to partitioning in the install setup, choose manual, and set the ext3 partition to mount on root "**/**" and leave the "format partition" box left unchecked.

If any warnings prompt up, just ignore them. As long as the drive is clean, you'll be alright.

If you still have persistant problems, it's most likely GRUB and your HD device map are wrong/not in sync.

[EDIT]
Also, check that your CD has no errors on it.

Regards
Iain

---

### Post by Bella2u on 2008-07-04
Will try out your info and let you know how it goes!

---

