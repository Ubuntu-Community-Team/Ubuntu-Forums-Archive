---
title: "[SOLVED] gedit won't save"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by mike22 on 2008-09-13
I'm trying to save the configuration file in kismet, but I can't. It says I don't have permissions necessary to save the file. How do I get permission?


error:You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

---

### Post by celticbhoy on 2008-09-13
use sudo gedit

---

### Post by Rhubarb on 2008-09-13
You can't save changes because gedit does not have the necessary permissions to change a file owned by root.

To do this, press alt + f2, then enter in:
```
gksu gedit
```
Then in gedit go to File --> Open, and open up the file you need to open, make the necessary changes, then you're able to save.
This runs gedit as root, enabling you to change any files you like.

---

### Post by Zzl1xndd on 2008-09-13
As was mentioned using Sudo gedit will work, The problem is that if you are trying to save to a Folder other then your home you don't have permission to write there as you are not the owner of the folder.

---

### Post by northern lights on 2008-09-13
> **celticbhoy said:**
> use sudo geditPlease **never** run graphical applications with sudo. If a graphical app needs to be run as superuser, use gksu/gksudo/kdesu instead. See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for references.

---

### Post by nothingspecial on 2008-09-13
Actually use ```
gksudo gedit
```

It dosen`t actually effect gedit if you use sudo with it, but you should always use gksudo with guis because you can you mess permissions up if you only use sudo.

---

### Post by mike22 on 2008-09-13
thanks it works

---

