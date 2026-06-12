---
title: "[SOLVED] access denied when pasting files"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by UIIIU on 2008-06-26
im modifying my kubuntu theme and i need to paste .png files to this location /usr/share/apps/kicker/tiles but when i do this it says access denied

any help?

---

### Post by Dr Small on 2008-06-26
/usr/share/apps/kicker/tiles is apparently not owned by you.

---

### Post by Dutch70 on 2008-06-26
right click the file, select properties,> permissions tab, and change it to read and write. I believe that should work for you, if you do own it.:)


Dutch

---

### Post by hyper_ch on 2008-06-26
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by UIIIU on 2008-06-26
i dont get it how is it not owned by me?

---

### Post by bodhi.zazen on 2008-06-26
either copy them from a terminal with sudo

```
sudo cp xyz.png /usr/share/apps/kicker/tiles
```

Or ues a gui :

```
kdesu konqueror
```

Then drag & drop

---

### Post by bodhi.zazen on 2008-06-26
> **UIIIU said:**
> i dont get it how is it not owned by me?

Permissions

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[uhelp]community/FilePermissions[/uhelp]

---

### Post by UIIIU on 2008-06-26
thanks bodhi i got it figured out

---

### Post by Dutch70 on 2008-06-26
Wonderful!  :) Glad you got it figured out, but would you mind letting us know what exactly you got figured out. So that I and others that find this thread will know?

---

