---
title: "[SOLVED] Editing boot menu problems"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Robotech47 on 2008-06-04
Well I am having a slight problem, nothing system critical but just really annoying. I am currently running Ubuntu 8.04 on a dual booting laptop with windows xp pro. The problem that I am having is that every time Ubuntu does a major update, it adds another version (sort of) to the boot menu list. It looks like this,

[B]Ubuntu 8.04, kernel 2.6.24-18-generic
Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-17-generic
Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-14-generic
Ubuntu 8.04, kernel 2.6.24-14-generic (recovery mode)
Ubuntu 8.04, memtest86*
Other operating systems:
Microsoft Windows XP Professional[/B]

I really just want my most current version of Ubuntu to show up boot list menu along with memtest and win XP. Any help on how to do this would be greatly appreciated.

---

### Post by cpetercarter on 2008-06-04
[This]("http://ubuntuforums.org/showthread.php?t=818177&highlight=kernel+2.6.24-18-generic") may help.

---

### Post by spiderbatdad on 2008-06-04
[http://ubuntuforums.org/showthread.php?t=818177&highlight=drs305](http://ubuntuforums.org/showthread.php?t=818177&highlight=drs305)

---

### Post by sayakb on 2008-06-04
Install startupmanager:
```
sudo apt-get install startupmanager
```
Now open startup manager from System->Admin.->Startup-Manager
Click on Advanced tab, **check** the Limit the number of kernels... checkbox and set the value as 1.

---

### Post by kk0sse54 on 2008-06-04
```
sudo gedit /boot/grub/menu.lst
```
Just go into the file and delete the kernel entries that you don't want anymore then save it and your done.

---

