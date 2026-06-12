---
title: "lightdm displays a black screen- with no logon"
date: 2011-10-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Andre-D on 2011-10-05
After updating my 11.11 beta today, and rebooting, there is no way to log on to GUI anymore.
The bug is reported here, also what I tried so far..  [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/868516](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/868516)

Please help me login to the desktop again.

---

### Post by Harry33 on 2011-10-05
> **Andre-D said:**
> After updating my 11.11 beta today, and rebooting, there is no way to log on to GUI anymore.
The bug is reported here, also what I tried so far..  [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/868516](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/868516)

Please help me login to the desktop again.

Try booting into recovery mode (choose from grub menu).
Then choose the option "drop down to shell with networking" or similar.
You can then login with the command:
login

---

### Post by Andre-D on 2011-10-05
recovery menu contains:
resume normal boot
fsck
remount
root (drop to root shel prompt)

so choosing the last, and then typing login, does only log me into the terminal, not GUI/desktop.

Terminal access is fine anyway on all tyy1-4 anyway. it's the GUI I miss.. :)

---

### Post by cariboo on 2011-10-05
What happens when you type:

```
startx
```

at the prompt?

---

### Post by Andre-D on 2011-10-05
nice, then I get to my desktop, kind of.. no window frames, no unity-menu, some no theme, but definitively my desktop :)
... no way to start any program or terminal .. or close the one that autostarted (ALT-F4) ..

---

### Post by Andre-D on 2011-10-06
when I try to start gdm og lightdm I get this message:

unable to connect to /var/run/dbus/system_bus_socket connection refused.

could that be the problem ?

---

### Post by Andre-D on 2011-10-06
my problem were solved by this: [https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441/comments/9](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441/comments/9)

- yes, it was a dbus problem

---

