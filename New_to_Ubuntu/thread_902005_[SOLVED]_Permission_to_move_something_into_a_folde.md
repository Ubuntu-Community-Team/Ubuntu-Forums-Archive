---
title: "[SOLVED] Permission to move something into a folder"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by adobrakic on 2008-08-26
I'm trying to move a winamp skin from my desktop to the skins folder of audacious, but when I try to it says i dont have the permission to. Any help?

---

### Post by iaculallad on 2008-08-26
> **adobrakic said:**
> I'm trying to move a winamp skin from my desktop to the skins folder of audacious, but when I try to it says i dont have the permission to. Any help?

```
sudo mv /mountpoint/location_of_skin_folder /mountpoint/location_of_audacious_folder

```
Or, simply:

```
gksudo nautilus
```

Then you're free to just copy and paste the skin folder.

---

### Post by linuxguymarshall on 2008-08-26
```
sudo mv <file location and name> <where to move it to>
```

and if you are an ex-windows user this method is frowned upon but more graphical. Open up a terminal and type :
```
gksudo nautilus
```

---

### Post by adobrakic on 2008-08-26
i like the gksudo nautilus method better :P!
thanks guys

---

### Post by mrsteveman1 on 2008-08-27
I still don't get why nautilus can't just ask you to authenticate if you want to move something to a dir you don't have permissions for, every other OS does it already.

---

