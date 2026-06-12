---
title: "chmod 777"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by pmohankumar on 2013-02-01
Hi,

How to execute chmod 777 command without sudo right?.
Is there possibility to add chmod command to sudoers file to execute without sudo rights, if possible, pls give the command to add in sudoers file.
Kindly help me.

Thanks,
Mohan
EMG

---

### Post by omeomi on 2013-02-01
It would be helpful if you could provide a bit more information on what you need to happen.

If your user owns the file/folder that you want to change the permissions for than you don't need sudo.

If you really want your user to use the chmod command w/o password you have to add this to the sudoers file as explained here: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by aromo on 2013-02-01
Without being clear about what you want, perhaps what you should do is change the default permissions for file creation (aka umask).

To set default file permissions to 777 edit [FONT="Courier New"]/etc/profile[/FONT] and append this line:
```
umask 000
```

---

