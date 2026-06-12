---
title: "Navigating to my NTFS partition"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by vulturesrow on 2008-04-28
How do I navigate to my NTFS partition. I would like to import all the music in my xp partition to amarok. My linux knowledge is very rusty, as I know I used to know how to do this. Thanks.

EDIT: This is in Hardy Heron.

---

### Post by daimaru on 2008-04-28
its in /media/something (maybe sda1 or hda1) . normally it should also show up on your desktop or under Places->Computer. 
Some times the windows partition is not mounted because you did not shutdown windows in a clean way e.g.  you had a system freeze and rebooted by hitting reset button. If you did that just boot into windows again and shutdown properly after that your windows partition should show up under ubuntu.
If this is not the case post your /etc/fstab contents. if your windows partition is listed there you can try a ```
sudo mount -a 
```to mount all the stuff in fstab

---

