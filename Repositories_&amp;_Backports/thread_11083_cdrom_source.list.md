---
title: "cdrom source.list"
date: 2005-01-13
forum: Repositories &amp; Backports
---

### Post by lizardking on 2005-01-13
Someone can wirte me the value to insert to source.list for the cdrom. It is something like ** deb cdrom:[ etc etc.] ** to see the package in  the cdrom.

thanks

---

### Post by nemin on 2005-01-14
[QUOTE=lizardking]Someone can wirte me the value to insert to source.list for the cdrom. It is something like ** deb cdrom:[ etc etc.] ** to see the package in  the cdrom.[/QUOTE]
You mean this?
> deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted

---

### Post by az on 2005-01-14
type:
sudo apt-cdrom add

to add a cdrom to your list
It does all the rest for you.

---

