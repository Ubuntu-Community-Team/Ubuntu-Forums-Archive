---
title: "need help with package manager"
date: 2011-09-29
forum: New to Ubuntu
---

### Post by mahir28 on 2011-09-29
whenever i boot up ubuntu this message shows up and now i cant install any software.

```
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
```

PLEASE HELP!!!:confused::confused:

---

### Post by sisco311 on 2011-09-29
Thread moved to **Absolute Beginner Talk**.

---

### Post by MG&amp;TL on 2011-09-29
Try opening a terminal and typing:

```
sudo apt-get update && sudo apt-get upgrade
```I guess it might be update-manager's frontend, not apt itself. Although tbh, I would suggest a reinstall with a different disk.

---

### Post by Krytarik on 2011-09-29
Remove the possibly corrupted package list/s:
```
sudo rm /var/lib/apt/lists/*
sudo rm /var/lib/apt/lists/partial/*
```Then try updating and upgrading again, for a start:
```
sudo apt-get update
sudo apt-get upgrade
```If you are still getting any error messages, post them (use the #-button in the editor to enclose them in code-tags).

Greetings.

---

### Post by MG&amp;TL on 2011-09-30
Actually, are you connected to the internet?

---

