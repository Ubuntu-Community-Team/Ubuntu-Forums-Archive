---
title: "Tpmfs /run 100% used"
date: 2019-08-08
forum: New to Ubuntu
---

### Post by royaletop on 2019-08-08
[COLOR=#242729][FONT=Arial]I have a VPS with Nginx for a wordpress blog and I have a problem I don't know for what reason.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Whenever tmpfs 99M 20M 79M 21% / run gets 100% of used my database drops and I need to reboot the server. I'm starting with servers and I don't know what is causing it.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Is there a configuration error?[/FONT][/COLOR]
Filesystem      Size  Used Avail Use% Mounted on
udev            465M     0  465M   0% /dev
tmpfs            99M   20M   79M  21% /run
/dev/sda1        19G   12G  6.6G  64% /
tmpfs           493M     0  493M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           493M     0  493M   0% /sys/fs/cgroup
tmpfs            99M     0   99M   0% /run/user/0
[COLOR=#242729][FONT=Arial]Dist: Ubuntu 18.04.1 LTS[/FONT][/COLOR]

---

