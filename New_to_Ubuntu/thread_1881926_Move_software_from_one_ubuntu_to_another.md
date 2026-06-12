---
title: "Move software from one ubuntu to another"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by LukaHr on 2011-11-16
If there any software to transfer programs from one installation to another. I got Ubuntu 11.10 on pc and I wonna same programs with their settings on laptop, so I don't have to work from home only. So I wonna save some time of installing all from begin and adjust setiings for programs!

---

### Post by abnordude on 2011-11-16
Why not try AptOnCD (Never actually tried it, but heard it's for the same reason)

---

### Post by oldfred on 2011-11-16
You can copy programs easily. Settings will be in /home.

I do this with each new install and to sync my desktop & laptop.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

Someone posted this as a newer way:
[http://stephen.rees-carter.net/2011/09/a-fantastic-new-feature-in-ubuntu-software-center-sync-between-computers/](http://stephen.rees-carter.net/2011/09/a-fantastic-new-feature-in-ubuntu-software-center-sync-between-computers/)
[http://www.addictivetips.com/ubuntu-linux-tips/how-to-synchronize-applications-between-multiple-ubuntu-computers/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-synchronize-applications-between-multiple-ubuntu-computers/)

You could copy all of /home over or find and copy the . (hidden) files & folders for settings for all the programs you want.

---

### Post by LukaHr on 2011-11-17
Thanks!

---

### Post by lolpenguin on 2011-11-17
Also in Ubuntu 11.10 [oneConf]("https://wiki.ubuntu.com/OneConf") is avaliable, and will synchronize your installed programs and settings in Ubuntu One.

---

### Post by LukaHr on 2011-11-17
> **lolpenguin said:**
> Also in Ubuntu 11.10 [oneConf]("https://wiki.ubuntu.com/OneConf") is avaliable, and will synchronize your installed programs and settings in Ubuntu One.


Going to try, thanks!

---

