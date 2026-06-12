---
title: "Error Read-only file system"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by spiderman168 on 2013-02-10
Sorry don't want to hijack this thread but I got this error when trying to update the packages: 
 
sudo: unable to open /var/lib/sudo/administrator/0: Read-only file system
 
Could this be because I installed ISPConfig on it and it's change the status of the file system?

---

### Post by oldos2er on 2013-02-11
Post moved to its own thread.

---

### Post by SeijiSensei on 2013-02-11
Usually the file system is mounted read-only when it has errors that have not been repaired.  Fixing this requires a couple of steps that are usually easiest to accomplish at the console:

1)  Reboot into recovery mode.  If the GRUB menu doesn't appear at boot, hold down the shift key while booting.

2)  Run the command
```
mount -o remount,rw /
```
Note there is no space after the comma.

3)  Run the command
```
touch /forcefsck
```

4)  Reboot.

This will force a file system check when the system comes back up.

Another, perhaps easier, alternative is to run the command

```
sudo shutdown -rF now
```

---

