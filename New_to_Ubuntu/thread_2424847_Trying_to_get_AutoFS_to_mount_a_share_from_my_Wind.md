---
title: "Trying to get AutoFS to mount a share from my Windows desktop. Failing."
date: 2019-08-15
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2019-08-15
Trying to set up to pull backups from my Windows computer to my Ubuntu machine.


Autofs configs




```
root@megalith:~# tail -n 1 /etc/auto.master
/srv/familydesktop /etc/auto.family --timeout=30
```


```

root@megalith:~# tail -n 1 /etc/auto.family
jason -fstype=cifs,credentials=/etc/jason.creds ://family.mylan.home/jason
```


Error


```
Aug 15 10:49:58 megalith kernel: [3016410.975386] CIFS VFS: cifs_mount failed w/return code = -112
```


I was able to manually mount by specifying the vers=2.0 option on the command line however that option just causes an error -13 for the autofs cifs mount fail. This is on Windows 10 Home and Ubuntu Xenial LTS.


How can I get this to work, or force autofs to use version 2.0 of samba by default?

---

### Post by DuckHook on 2019-08-15
I'm of little help because I don't run Windows except in VMs (and I don't use cifs in any way, shape or form), but web searching found this: [https://unix.stackexchange.com/questions/124342/mount-error-13-permission-denied](https://unix.stackexchange.com/questions/124342/mount-error-13-permission-denied)

---

### Post by joris_donders2 on 2019-08-16
```
[COLOR=#333333][FONT=&quot]ntfsfix /dev/sdaX 
```

[/FONT][/COLOR][COLOR=#333333][FONT=&quot]maybe this solves the problem ? in Ubuntu to do of course[/FONT][/COLOR]

---

