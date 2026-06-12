---
title: "Beginer Ubuntu/Linux Wirless issues"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by MartyMcfly26 on 2012-05-25
Hello community.  New to using Ubuntu Linux.  I've figured out some things here and there but cannot seem to figure out how to get my wireless driver working.  Ive seen some posts about getting windows drivers ect... What is the best method period for me to get wireless working.  I saw in another forum to type the following to give you info IOT help me out.  Thanks in advance.

sudo lspci -v 

Attached is the output from this command.  Thanks in advance for the help.

-marty

---

### Post by jonedney on 2012-05-25
Hey Marty!

Welcome to the forums!

I may have overlooked this in your attachment, but what brand of Wireless adapter are you using?

---

### Post by wildmanne39 on 2012-05-25
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one at a time:
```
sudo apt-get install --reinstall bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
disconnect wired connection and reboot.
Thanks

---

