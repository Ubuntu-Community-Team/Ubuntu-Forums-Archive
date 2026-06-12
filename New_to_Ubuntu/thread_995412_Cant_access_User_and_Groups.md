---
title: "Cant access User and Groups"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by blue4paper on 2008-11-27
Simply put, i cant access my User and Groups anymore. I think i was messing around too much in the user and groups trying to allow myself root user priviledges and ended up clicking the wrong thing.

Anyways i've tried a visudo in the recovery console as root and added myself as root. Unfortunately user and groups is still locked.

Any ideas?

---

### Post by taurus on 2008-11-27
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
id
```

---

### Post by blue4paper on 2008-11-27
uid=1000(name) gid=1000(name) groups=1000(name)

where i wrote "name" is where my name is supposed to be.

---

### Post by taurus on 2008-11-27
Looks like you have managed to remove yourself from group admin.  Therefore, sudo won't work for you anymore.  You need to boot into recovery mode from GRUB menu and at the prompt, add yourself back to group admin again.

```
adduser **name** admin
shutdown -r now
```

Of course, you need to replace **name** with the actual name of your account.

---

### Post by sisco311 on 2008-11-27
Your user is not in the admin group.

Reboot the computer in recovery mode and type:
```
adduser *name* admin
```in the root shell.

then type:
```
exit
```and select the *resume normal boot* option.

---

