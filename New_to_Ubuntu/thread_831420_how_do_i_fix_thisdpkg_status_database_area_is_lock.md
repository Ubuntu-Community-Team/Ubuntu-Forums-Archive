---
title: "how do i fix thisdpkg: status database area is locked by another process wht does thi"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by glb48 on 2008-06-16
dpkg: status database area is locked by another process
wht does this mean

---

### Post by iaculallad on 2008-06-16
> **glb48 said:**
> dpkg: status database area is locked by another process
wht does this mean

It means that other process are using your install/package managers. Try to close opened "Synaptics" window or kill "unterminated" apt/aptitude commands.

---

### Post by RomeReactor on 2008-06-16
Hi. It means another package administration program is running. If you have Synaptic or Add/Remove open, close them before running the terminal command again. If neither of those programs are open, it may be the update manager running in the background; just give it a few minutes and try again. Also, please be patient and don't start multiple threads; concentrate on one thread and one problem at a time and wait for others to reply.

---

