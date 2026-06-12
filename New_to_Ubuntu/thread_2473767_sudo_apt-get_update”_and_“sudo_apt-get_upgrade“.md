---
title: "sudo apt-get update” and “sudo apt-get upgrade“?"
date: 2022-04-13
forum: New to Ubuntu
---

### Post by jmichaels29 on 2022-04-13
Question.  When "Software Updater" runs on its own, from time to time, does it automatically do these two commands?

Curious if a newbie would ever need to run either command.

---

### Post by &amp;KyT$0P# on 2022-04-13
Software Updater does equivalent of [FONT=Courier New]sudo apt-get update[/FONT], then when you click "Install Now" it does something similar to [FONT=Courier New]sudo apt-get dist-upgrade[/FONT] except for [phased updates]("https://wiki.ubuntu.com/PhasedUpdates").

So usually you don't need to run either command.  The exceptions would be if you encounter a problem or would like to get a specific phased update before it is phased enough to come through Software Updater.

---

### Post by jmichaels29 on 2022-04-13
Thanks so much!

---

### Post by grahammechanical on 2022-04-13
Software updater does a few other things. It will check for updates according to a time schedule. It will run autoremove to remove packages that are no longer required. When software updater installs a Linux kernel it will remove an older kernel. Software updater will also update any snap package apps installed.

All these things can be done through the command line but will require user effort to protect the operating system.

Regards

---

