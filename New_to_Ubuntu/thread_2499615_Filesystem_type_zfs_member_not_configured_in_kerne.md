---
title: "Filesystem type zfs_member not configured in kernel"
date: 2024-08-03
forum: New to Ubuntu
---

### Post by brijesh-d3v on 2024-08-03
Hello guys,

I installed Ubuntu 24.04 LTS as my primary operating system
I successfully done everything but now i m getting this Error while
opening the Other HDD location in my system

here is the error : 


Unable to access location
Error mounting /dev/sda4 at /media/brijesh/rpool:Filesystem type zfs_member not configured in kernel

[IMG]https://raw.githubusercontent.com/123Brijesh44aa/my-project-ubuntu3/main/Screenshot%20from%202024-08-03%2018-57-33.png?token=GHSAT0AAAAAACVU6ZLX5N44FBADKAKHKR3MZVO7UUA[/IMG]

---

### Post by euol on 2024-08-04
You are probably missing ZFS support (Ubuntu 24.04 LTS does not include ZFS support by default).

Try this:
sudo apt install zfsutils-linux
sudo modprobe zfs

---

