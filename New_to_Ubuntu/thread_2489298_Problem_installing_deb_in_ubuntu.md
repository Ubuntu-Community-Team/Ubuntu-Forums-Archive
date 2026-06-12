---
title: "Problem installing deb in ubuntu"
date: 2023-07-25
forum: New to Ubuntu
---

### Post by jitx-12345 on 2023-07-25
```
(base) lenovo@lenovo-81WB:/media/lenovo/Volume E/AI and Prompt Engineering/Deep Learning$ /etc/apt/sources.list.d/the-board-team-dev-snapshots-natty.list
bash: /etc/apt/sources.list.d/the-board-team-dev-snapshots-natty.list: No such file or directory
(base) lenovo@lenovo-81WB:/media/lenovo/Volume E/AI and Prompt Engineering/Deep Learning$ sudo ppa-purge -purge the-board-team/dev-snapshots
[sudo] password for lenovo: 
sudo: ppa-purge: command not found
(base) lenovo@lenovo-81WB:/media/lenovo/Volume E/AI and Prompt Engineering/Deep Learning$ sudo ppa-purge -purge the-board-team/dev-snapshots
sudo: ppa-purge: command not found
(base) lenovo@lenovo-81WB:/media/lenovo/Volume E/AI and Prompt Engineering/Deep Learning$ sudo ppa-purge -purge the-board-team/dev-snapshots
sudo: ppa-purge: command not found
(base) lenovo@lenovo-81WB:/media/lenovo/Volume E/AI and Prompt Engineering/Deep Learning$ sudo rm /etc/apt/sources.list.d/some-ppa.list
rm: cannot remove '/etc/apt/sources.list.d/some-ppa.list': No such file or directory
(base) lenovo@lenovo-81WB:/media/lenovo/Volume E/AI and Prompt Engineering/Deep Learning$ gksudo gedit /etc/apt/sources.list
Command 'gksudo' not found, did you mean:
  command 'gfsudo' from deb gfarm-client (2.7.20+dfsg-1build1)
Try: sudo apt install <deb name>
(base) lenovo@lenovo-81WB:/media/lenovo/Volume E/AI and Prompt Engineering/Deep Learning$ gksudo gedit /etc/apt/sources.list
Command 'gksudo' not found, did you mean:
  command 'gfsudo' from deb gfarm-client (2.7.20+dfsg-1build1)
Try: sudo apt install <deb name>
(base) lenovo@lenovo-81WB:/media/lenovo/Volume E/AI and Prompt Engineering/Deep Learning$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-updates main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-updates multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-security main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-security universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-security multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-security multiverse
(base) lenovo@lenovo-81WB:/media/lenovo/Volume E/AI and Prompt Engineering/Deep Learning$ gksudo gedit /etc/apt/sources.list
Command 'gksudo' not found, did you mean:
  command 'gfsudo' from deb gfarm-client (2.7.20+dfsg-1build1)
Try: sudo apt install <deb name>
(base) lenovo@lenovo-81WB:/media/lenovo/Volume E/AI and Prompt Engineering/Deep Learning$ gksudo gedit /etc/apt/sources.list
Command 'gksudo' not found, did you mean:
  command 'gfsudo' from deb gfarm-client (2.7.20+dfsg-1build1)
Try: sudo apt install <deb name>
(base) lenovo@lenovo-81WB:/media/lenovo/Volume E/AI and Prompt Engineering/Deep Learning$ ^C
(base) lenovo@lenovo-81WB:/media/lenovo/Volume E/AI and Prompt Engineering/Deep Learning$

```

---

### Post by ajgreeny on 2023-07-25
I can not figure out exactly what you are trying to do from what you have said so far but as a start please open a terminal and run commands shown and show us what output you get from that using code tags.
See my signature below for a **Code-Tags** how-to
```
sudo apt update
sudo apt upgrade
```

---

### Post by Impavidus on 2023-07-25
I can't see what you're trying to do, so I can only explain the error messages.

1: You try to execute a .list file in the sources.list.d directory. This fails, as the file doesn't exist (and .list files shouldn't be executable anyway).
2: You try to execute ppa-purge with sudo. This fails, because ppa-purge isn't installed.
3: The same.
4: The same.
5: You try to remove some-ppa.list from the sources.list.d directory. This fails, because the file doesn't exist. It looks like you didn't substitute something for the placeholder.
6: You try to execute gedit as root, using gksudo. That used to be the proper way to execute GUI applications with root, but it no longer is. gksudo is no longer around. The clean way to edit a text file as root, is to use sudoedit:```
sudoedit some-file
```By default, it will open de file in the nano text editor, but if you set the EDITOR environment variable, you can change that to any text editor you like.
7: The same.
8: cat shows your sources.list file. The file looks perfectly normal for Ubuntu 23.04.
9: The same as 6.
10: The same.

---

