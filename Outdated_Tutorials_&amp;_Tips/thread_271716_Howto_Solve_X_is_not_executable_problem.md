---
title: "Howto: Solve X is not executable problem"
date: 2006-10-05
forum: Outdated Tutorials &amp; Tips
---

### Post by de4th on 2006-10-05
Sometimes after tests with xgl or aiglx your Xserver don't start or it saw you a message like "X is not executable". 
Follow these steps to solve it and have your graphical interface back.


**press alt+ctrl+F1**
login and replace xorg.conf and gdm.conf-custom files with their backups which your system was working well.
and type:
**sudo apt-get remove xserver-xorg-air-core**
**sudo apt-get --reinstall install xserver-xorg xserver-xorg-core ubuntu-desktop**
give "y" at the question and then type:
**killall gdm** and start it again, type:
**gdm**

Now you must see your graphical interface again but without aiglx!
Hope this help someone.

Have fun!

---

### Post by nomail on 2007-01-17
does anyone has a solution for offline installation. beacause im afraid these packages have a lot of depencies

---

