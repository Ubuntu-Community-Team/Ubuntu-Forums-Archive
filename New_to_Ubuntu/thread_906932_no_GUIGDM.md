---
title: "no GUI/GDM"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Zopiac on 2008-08-31
instead of popping up a pretty login screen, it gives me a CLI Prompt to login, and continues with CLI until i input "startx". how to i change this?

---

### Post by kellemes on 2008-09-01
> **Zopiac said:**
> instead of popping up a pretty login screen, it gives me a CLI Prompt to login, and continues with CLI until i input "startx". how to i change this?

gdm is installed?
Anyway, maybe this works..
```
sudo dpkg-reconfigure gdm
```

---

### Post by Zopiac on 2008-09-01
OK I met a whole bunch of problems yesterday. "sudo dpkg-reconfigure gdm" tells me gdm is not my default login manager. i can't switch it with Login Window preferences because that is for GDM, which startx does log open. sudo dpkg-reconfigure kdm tells me that kdm is not installed (but i have installed xubuntu and kubuntu!) and when i try to reinstall gdm it gives me a dpkg --configure -a error. i try that, but it says:

```
zopiac@zopiac:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0031' near line 1:
 newline in field name `#padding'
```

/var/lib/dpkg/updates/0031 is just 149 lines saying "#padding", can anyone verify this?

---

### Post by modmadmike on 2008-09-02
Try making a script and telling it to launch at startup.

---

