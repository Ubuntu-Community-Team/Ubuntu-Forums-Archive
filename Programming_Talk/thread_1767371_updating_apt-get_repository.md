---
title: "updating apt-get repository"
date: 2011-05-25
forum: Programming Talk
---

### Post by Blackbug on 2011-05-25
I am using ubuntu lucid..even after executing "sudo apt-get update" new packages of any application are not updated.

is there any other way to do so? for example if i am trying to install libgtk3.0-dev its doesnt show that and gives error..it supports only 2.0..

i have updated all packages in repository also..

---

### Post by Toz on 2011-05-25
'sudo apt-get update' only updates your index files to show what is currently available. Basically, the apt-get program compares what you have currently installed against whats available. To upgrade the packages, for which there is an upgrade available, type:```
sudo apt-get upgrade
```

As for libgtk3.0-dev, I'm not sure I understand. What does:```
apt-cache policy libgtk3.0-dev
``` return? What is the error?

---

### Post by SledgeHammer_999 on 2011-05-25
I don't think that gtk3 will be available in the official Lucid repositories. You better update to Natty or use some other distribution (eg Debian-sid)

---

