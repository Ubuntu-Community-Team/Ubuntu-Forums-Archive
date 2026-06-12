---
title: "Could anyone run the command &quot;groups&quot; and post the result for me? I am using hardy."
date: 2008-07-03
forum: New to Ubuntu
---

### Post by xueminfeng on 2008-07-03
I accidentally put myself out of all groups by following command
/usr/sbin/usermod -Gvboxusers testuser

I only belongs to the vboxusers, then I reboot the computer with cdrom. changed the /etc/sudoers, I have gained my root back.
But I need to put myself to the old groups, which I do not know.

Could anyone run the command "groups", and post the result for me? I am using hardy.

Thanks a lot

---

### Post by kestrel1 on 2008-07-03
Try this:
```
kestrel adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin vboxusers usbusers
```

---

### Post by wolfen69 on 2008-07-03
```

ed adm dialout cdrom floppy audio dip video plugdev fuse mythtv admin lpadmin


```

---

### Post by sisco311 on 2008-07-03
```
sudo usermod **-a** -G adm,dialout,cdrom,floppy,audio,dip,video,plugdev,fuse,lpadmin,admin,*username username*
```
-a = append

---

### Post by Mark_in_Hollywood on 2008-07-03
mark@Lexington-19:~$ groups
mark adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin

---

### Post by bhadotia on 2008-07-03
```
abhishek@ubuntu:~$ groups
abhishek adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin vboxusers mythtv mysql postgres
```

---

### Post by xueminfeng on 2008-07-03
Thanks a lot guys

---

