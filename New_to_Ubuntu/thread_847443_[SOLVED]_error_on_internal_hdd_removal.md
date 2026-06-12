---
title: "[SOLVED] error on internal hdd removal"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by melrokz on 2008-07-02
:confused:

This error popped up on ubuntu 7.10 recovery mode:

```
mount:special device /dev/disk/by-uuid/2854-46EF does not exist
```

It seems that ubuntu is trying to mount a internal hdd that i had removed from the pc recently.
Anything that i need 2 do, plz?

---

### Post by Victormd on 2008-07-02
Check your fstab to see if the drive is listed, and if so, remove the corresponding entry.
Open a terminal and type the following to edit your fstab file
```
sudo gedit /etc/fstab
```

---

