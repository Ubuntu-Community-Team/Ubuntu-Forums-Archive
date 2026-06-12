---
title: "@ packages..."
date: 2011-09-17
forum: New to Ubuntu
---

### Post by CherokeeBeauty on 2011-09-17
why is it that every time I try to use a command for apt-get it comes back as:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by Rubi1200 on 2011-09-17
Hi and welcome to the forums :)

Do you have another package manager such as Synaptic or the Software Center open?

If yes, close all instances of package managers and then try again.

---

### Post by P05TMAN on 2011-09-17
> **CherokeeBeauty said:**
> why is it that every time I try to use a command for apt-get it comes back as:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

have you tried installing a package using the command 

```

sudo apt-get install

```

?

---

### Post by doppel.ganger on 2011-09-17
Right, you need to add the sudo:
```
sudo apt-get install package-name
```

---

### Post by 3rdalbum on 2011-09-17
> **CherokeeBeauty said:**
> why is it that every time I try to use a command for apt-get it comes back as:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

You are not running the command as root. Only root (administrator) can make system-level changes.

Put the word 'sudo' in front of the command to run it as root.

For example:

```
sudo apt-get install gimp
```

---

### Post by hakermania on 2011-09-17
Ok, I would simply like to add *why* you should use sudo.
'sudo' will prompt for password and you will type it (it won't show anything but it is typed (for security reasons)), and once you type your password then you'll have root access.
This is done so as to have a secure system and avoid easy 'hacks' from viruses which install programs on their own as on windows.
In ubuntu, everything important (OS dependent usually) needs password authentication for security reasons.

---

### Post by P05TMAN on 2011-09-17
> **hakermania said:**
> Ok, I would simply like to add *why* you should use sudo.
'sudo' will prompt for password and you will type it (it won't show anything but it is typed (for security reasons)), and once you type your password then you'll have root access.
This is done so as to have a secure system and avoid easy 'hacks' from viruses which install programs on their own as on windows.
In ubuntu, everything important (OS dependent usually) needs password authentication for security reasons.

Excellent, & +1 for adding the 'why'. I should have. Here is the Wiki on sudo though for more info: 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

