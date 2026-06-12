---
title: "Hard disk partition not showing up under Devices in 12.04"
date: 2012-06-22
forum: New to Ubuntu
---

### Post by beruuu on 2012-06-22
I'm using Linux for the first time, dual-booting Ubuntu 12.04 with Windows 7.

Before installation, my hard disk had 2 partitions (/dev/sda1 [C: in Windows] which contains the Windows installation, and /dev/sda2 [D: in Windows] which I use for storing media), both NTFS formatted. I shrunk the media partition to make room for Ubuntu and created 2 partitions for it, one for the OS and one for swap space.

When I clicked 'Install Now', a message said that there was no mount point specified for /dev/sda2 and that it would be unusable if I continued. So I set its mount point to /windows and proceeded. It didn't ask for a mount point for /dev/sda1.

After installation, when I open the file manager (the default Home folder icon on the launcher), I can see the first partition (C:) under Devices on the left pane, but to access the second one (D:) I have to go to File System and then windows. 

Is there a way to make it appear alongside the first one for quick access?

---

### Post by blackbird34 on 2012-06-22
Well, you could make a bookmark for it in Nautilus (the file manager), and set it (i.e. D: ) to mount automatically.

---

### Post by beruuu on 2012-06-22
Yeah ok, I guess that will serve my purpose. Thanks a lot for the prompt reply.

---

