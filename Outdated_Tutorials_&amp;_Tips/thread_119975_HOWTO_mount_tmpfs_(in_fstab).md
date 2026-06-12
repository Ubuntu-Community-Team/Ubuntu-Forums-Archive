---
title: "HOWTO: mount tmpfs (in fstab)"
date: 2006-01-20
forum: Outdated Tutorials &amp; Tips
---

### Post by bartbes on 2006-01-20
do:
sudo gedit /etc/fstab
and add the line:
tmpfs		<dir> tmpfs rw 0 0
where dir is the directory you made for the tmpfs

---

