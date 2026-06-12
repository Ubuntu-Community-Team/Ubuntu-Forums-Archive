---
title: "How to install Apache on 16.04 lts desktop"
date: 2016-10-18
forum: New to Ubuntu
---

### Post by swb_mct on 2016-10-18
I just installed Ubuntu 16.04 LTS desktop.  There is a VERY short list of Software available to install from the Software menu.  In an earlier version with Cinnamon, there were 1000's of available apps.  I want to install Apache web server and VNC for example.

---

### Post by TheFu on 2016-10-18
"Software Center" is a dumbed down package manager meant for normal end-users. It hides developer packages and libraries. Don't know why apache server wouldn't be in the list. Perhaps it is a desktop thing?  I dunno. Haven't used software-center ... er ... ever.

You can use any package manager you like (apt, apt-get, aptitude, synaptic, whatever). If you are planning to run "servers" then forget the GUI.  Don't forget that program titles don't always match package names or program names.

**sudo apt install apache2** will install apache.

Best to ask 1 question per thread. Power management is **very** different from how to install apache. It is also very dependent on the specific hardware.

---

### Post by SeijiSensei on 2016-10-18
I recommend installing the full "[LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP")" package with
```
sudo apt-get update
sudo apt-get install lamp-server^
```
Make sure to include the circumflex ("^") at the end.  This will install Apache, PHP, and MySQL, and all the packages that link them together, in one fell swoop.

---

### Post by swb_mct on 2016-10-18
Thanks to both of you for your help.

---

