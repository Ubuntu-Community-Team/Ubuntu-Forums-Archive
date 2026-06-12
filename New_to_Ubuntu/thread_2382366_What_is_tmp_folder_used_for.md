---
title: "What is /tmp folder used for?"
date: 2018-01-12
forum: New to Ubuntu
---

### Post by mac187 on 2018-01-12
Hi, trying to learn Ubuntu, and have been exploring around file explorer, wondring what is /tmp folder, and is it safe to delete everything in here? Will it cause problems or issues ? Thanks :)

---

### Post by QIII on 2018-01-12
By convention, /tmp really is temporary -- its contents are not preserved between boots.  The convention is that the files in /var/temp may persist between boots, depending on how the application using them manages them.

I don't think that it would be safe, in general, to remove files from either indiscriminately.  /tmp, in particular, may be saving something an app or process will be looking for when it gets back around to it.

---

### Post by oldos2er on 2018-01-12
[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

As QIII said, leave /tmp contents alone when the system is up. It will be cleared on shutdown and reboot.

---

