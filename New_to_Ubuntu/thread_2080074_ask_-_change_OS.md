---
title: "ask - change OS"
date: 2012-11-03
forum: New to Ubuntu
---

### Post by czgirb on 2012-11-03
Currently I used 12.04 and feel happy with it.
How can I change the current OS to Mint and make all installed software (incld. its Settings) stay the same. Is it possible?

---

### Post by zombifier25 on 2012-11-03
You can't just change an OS, you must do a full reinstall. To preserve the settings, backup your home folder.

In order to get a list of installed packages on your system run this command:
```
sudo dpkg --get-selections > ~/packages
```
Backup the text file. On your new system run this to reinstall all the packages:
```
sudo dpkg --set-selections < ~/packages && sudo apt-get -u dselect-upgrade
```



(but you do know you can install Mint packages on Ubuntu right? Since you did state you're happy with you current setup)

---

