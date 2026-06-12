---
title: "No Internet--Uninstalled Accidently Network Manager Gnome"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by sports fan Matt on 2008-05-05
I like a dummy uninstalled Network Manager Gnome--not I cant connect to the Internet.  When I try to do a sudo apt-get install Network-manager-gnome, it says "failed to fetch" .....

How easy is this to fix?

---

### Post by jimv on 2008-05-05
Are you using wireless or wired internet?

---

### Post by sports fan Matt on 2008-05-05
Wired ..the pc is a hp pavillion 7920 with 384 mb ram and an intel celleron processor

---

### Post by jimv on 2008-05-05
In a terminal, type:

```
sudo gedit /etc/network/interfaces
```

Add these lines

```
auto eth0
iface eth0 inet dhcp
```

Save and close the file.

In a terminal, type:
```

sudo /etc/init.d/networking restart
```

Try the internet now.  If it works, reinstall network manager.

---

### Post by sports fan Matt on 2008-05-05
Jim,

Thanks..took me a few to type in the commands exactly (I had forgotten to add spaces and such)

Thanks again

---

