---
title: "Second IDE drive keeps disappearing"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by emperorming on 2008-05-23
I have a second IDE drive set as a slave, automounted at boot where I keep all my music. I've noticed that my desktop wallpaper vanished a few days ago & along with it, my desktop icon for the second drive. The directory folder for the drive is still listed in /media but that's about it. Dunno if some update caused this (I religiously update). Thinking that the drive might be duff, I put in another, but it's disappeared too.   Anybody any ideas? Ubuntu Gutsy.

---

### Post by sayakb on 2008-05-23
Try this:
Since most of the apps you use daily do not run as root, so mount the drive from CLI using:
```
sudo mount -t /dev/sda2 /media/disk
```
Replace /dev/sda2 with whatever applicable for you. So if any application is causing the drive to unmount, it might not work as the drive could be unmounted only by using CLI as root again.

---

