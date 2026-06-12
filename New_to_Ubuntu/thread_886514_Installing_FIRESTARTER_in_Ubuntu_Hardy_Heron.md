---
title: "Installing FIRESTARTER in Ubuntu Hardy Heron:"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Bee Wildered on 2008-08-11
Installing FIRESTARTER in Ubuntu Hardy Heron:

PLEASE HELP: I am trying to install and activate Firestarter Firewall in Ubuntu Hardy Heron and have followed the instructions at:
[http://www.fs-security.com/docs/installation.php](http://www.fs-security.com/docs/installation.php)

I have checked the enable “universe” box in Repositories > Settings > Synaptic Package Manager.
I have then typed  - apt-get install firestarter – in the terminal box and pressed enter but it does not work and I just get the following message in response:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)

E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


...any clues as to what I'm doing wrong?!

---

### Post by Theo148 on 2008-08-11
You need to give yourself root access to modify system files and such, so the command should be:

```
sudo apt-get install firestarter
```
You'll need to type in your password to authenticate, and then everything should go smoothly. :)

---

### Post by Oldsoldier2003 on 2008-08-11
Please do not start multiple threads on the same subject. This is the same as [http://ubuntuforums.org/showthread.php?t=886517](http://ubuntuforums.org/showthread.php?t=886517)

---

