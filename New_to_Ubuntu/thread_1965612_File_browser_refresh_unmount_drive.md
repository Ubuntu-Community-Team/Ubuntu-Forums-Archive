---
title: "File browser refresh unmount drive"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by Szoke on 2012-04-26
Hi Everyone,
I'm using a linutop 4 computer running Ubuntu 10.04 lucid and Gnome 2.30.2.
When I press multiple times the Refresh button in the File Browse toolbar, the folder content suddenly disappears, as the drive seems to be unmounted.
This happens only if an application is continuously writing to that folder.
How to reproduce:
- A 500 GB hard drive is mounted as "DD500", fstab line :
UUID=50895c3e-5a95-48a8-bfe9-ea688cedb0d4   /media/DD500  ext3   defaults                 0  0 
- VLC is running, streaming an IP camera and writing the video stream to some file into path DD500/Video
- Open a File Browser and browse DD500/Video. Click every second on the Refresh button

This problem happens also with USB keys.
executing sudo umount -a and mount-a "solves" the problem.
Any idea why a drive is unmounted when pressing the Refresh button during concurrent access ?

---

