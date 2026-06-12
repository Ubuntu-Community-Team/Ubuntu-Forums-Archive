---
title: "sudo /etc/sudoers is mode 00, but should be 0440"
date: 2015-07-31
forum: New to Ubuntu
---

### Post by mahi6 on 2015-07-31
[COLOR=#333333][FONT=Arial]Hi i have been trying to edit file permissions and by mistake i typed in [/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]sudo chmod -r  / R /etc/foldername[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]Now its locked me out. I am unable to access or do anything 
sudo unable to initialize policy plugin ubuntu is the msg i get 

[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]I tried going into the recovery mode and typed **chmod 0440 /etc/sudoers**[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]Still unable to login . can someone help [/FONT][/COLOR]

---

### Post by TheFu on 2015-07-31
If all the files on the box have wrong permissions, it would be best to recover from the last backup.
No backups with file permissions? Reinstall.

I thought chmod -r meant nothing.  It is **chmod -R** - case sensitive. Yep - checked the manpage.  So ... looks like you just need to fix a few files/directories.
You want / to be **chmod 755 /**```

drwxr-xr-x  28 root root  4096 Jul 26 20:13 ./
```

Just boot off any liveCD/USB and fix the permissions, assuming the filesystem isn't encrypted.

---

