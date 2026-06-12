---
title: "sync problem onedrive"
date: 2018-05-22
forum: New to Ubuntu
---

### Post by work-in-progress on 2018-05-22
Hi all,
I'm new of this forum and I hope that I'm in the right section.

Anyway, that's my problem:
root@mypc:~$ journalctl --user-unit onedrive -f
-- Logs begin at Wed 2018-05-16 22:16:26 CEST. --
mag 22 11:45:17 Sonic18 onedrive[1191]: 0x5598924f7ea3 ???
mag 22 11:45:17 Sonic18 onedrive[1191]:         ???:0
mag 22 11:45:17 Sonic18 onedrive[1191]: 0x7fe5158fdb96 __libc_start_main
mag 22 11:45:17 Sonic18 onedrive[1191]:         ???:0
mag 22 11:45:17 Sonic18 onedrive[1191]: 0x5598924efc99 ???
mag 22 11:45:17 Sonic18 onedrive[1191]:         ???:0
mag 22 11:45:17 Sonic18 onedrive[1191]: 0xffffffffffffffff ???
mag 22 11:45:17 Sonic18 onedrive[1191]:         ???:0
mag 22 11:45:17 Sonic18 systemd[1179]: onedrive.service: Main process exited, code=dumped, status=11/SEGV
mag 22 11:45:17 Sonic18 systemd[1179]: onedrive.service: Failed with result 'core-dump'.
^C

What I did? Just follow the instruction of the man page:
$ sudo apt-get install onedrive
$ onedrive
$ systemctl --user enable onedrive systemctl
$ systemctl --user enable onedrive

Thank you for the help

PS: Ubuntu 18.04

---

### Post by work-in-progress on 2018-05-29
up

---

