---
title: "Package manager Error"
date: 2012-12-05
forum: New to Ubuntu
---

### Post by snoylr on 2012-12-05
I have a red X on my top tool bar in Unbuntu.  The message when I click on the X is as follows:

An error occurred, please run package manager from the right-click menu or apt-get in a terminal to see what is wrong.  The error message was 'Error: BrokenCount >0.  This usually means that your installed packages have unmet dependencies.

The package with unmet dependencies; is 

google-earth-stable:i386: Depends: lsb-core (>= 3.2) but it is not installed

Another message also told me to run apt-get install -f

When I try to run that command I get the following message:

E: Invalid operation install-f
richard@richard-System-Product-Name:~$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

How can I clear the red X and install updates?

---

### Post by ubudog on 2012-12-05
You need to run apt-get install -f as root:
```
sudo apt-get install -f
```

Best,
ubudog

---

