---
title: "Old server rollback"
date: 2019-08-13
forum: New to Ubuntu
---

### Post by it-lfbali on 2019-08-13
Hi,
I've just been given a new job to handle IT in a school. One of the server was setup for library Inventory using ubuntu 10.04. Nobody knows the authentication to enter the server machine. Foolishly I restarted the machine and entered the recovery mode, and now the library application stopped working.
My questions are : is it possible to rollback to the previous machine configuration? How can I change/reset the admin password of the server?

---

### Post by Impavidus on 2019-08-14
People must have neglected that computer for years. Ubuntu 10.04 server edition reached end of life in April 2015, over 4 years ago.

It is possible to reset the password. Use the grub menu to boot into recovery mode, drop to a root shell, remount the filesystem read-write and change the password: [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

If the library application doesn't start automatically, you may have to do it manually. Or configure the machine to start it automatically. I don't know your library application.

But really, that computer needs a fresh install.

---

