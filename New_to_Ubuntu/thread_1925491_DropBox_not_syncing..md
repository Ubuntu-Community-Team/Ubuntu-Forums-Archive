---
title: "DropBox not syncing."
date: 2012-02-14
forum: New to Ubuntu
---

### Post by Markg55 on 2012-02-14
I am currently runninig Lubuntu 11.10 and set up Drop Box (cloud type file storage). My drop box folder is in file manager. The files I have on Drop Box are there but hasn't re-synced (I have since uploaded a few pics from my droid phone). Vice-a - versa files I have created on this PC and copied to the Drop Box are not syncing to the cloud. Any suggestions would be appreciated.

---

### Post by LowSky on 2012-02-14
make sure dropbox is starting when the PC boots up. You should have a dropbox icon in the top panel next to the sound and internet icons (EDIT: in unity icon would be there, sorry I dont use lubuntu)

in the meantime the command to run dropbox is this:
```
/opt/dropbox/dropboxd
```

worse case uninstall and the reinstall

---

### Post by Markg55 on 2012-02-14
Lowsky gave it a shot and this is what pops up:

Failed to execute child process "/opt/dropbox/dropboxd" (No such file or directory)

Was I suppose to use the Run command or paste it in terminal?

---

### Post by Markg55 on 2012-02-14
Uninstalled and re-installed using gdebi. Everything is now up to snuff.
Thanks LowSky!

---

