---
title: "Touchpad not working in ubuntu 12.04 after updates"
date: 2012-08-13
forum: New to Ubuntu
---

### Post by ryka on 2012-08-13
touchpad not working in ubuntu 12.04 after updates installation in dell inspiron n5050 ..
pls help me out i am a new user of ubuntu
pls rply asap

---

### Post by NikTh on 2012-08-13
Hi , 
please open a terminal(ctrl+alt+t)  and apply this command 
```
synclient TouchpadOff=0
``` 

If touchpad works , we can make it permanent . 
Thanks

---

### Post by mpereira1 on 2012-08-19
This happened to me yesterday. I'm on an ASUS UX31A.

```

$ uname -a
Linux pluto 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```Relevant package history diff:

```

Start-Date: 2012-08-18  12:17:37
Commandline: aptdaemon role='role-commit-packages' sender=':1.170'
Upgrade: gcalctool:amd64 (6.4.1.1-0ubuntu2, 6.4.1.1-0ubuntu3), python-aptdaemon.pkcompat:amd64 (0.43+bzr805-0ubuntu2, 0.43+bzr805-0ubuntu4), compiz-plugins-default:amd64 (0.9.7.8-0ubuntu1.2, 0.9.7.8-0ubuntu1.4), libnux-2.0-common:amd64 (2.12.0-0ubuntu1, 2.14.0-0ubuntu1), dconf-gsettings-backend:amd64 (0.12.0-0ubuntu1, 0.12.0-0ubuntu1.1), gnome-settings-daemon:amd64 (3.4.2-0ubuntu0.2, 3.4.2-0ubuntu0.4), perl:amd64 (5.14.2-6ubuntu2, 5.14.2-6ubuntu2.1), libnux-2.0-0:amd64 (2.12.0-0ubuntu1, 2.14.0-0ubuntu1), libgl1-mesa-dri:amd64 (8.0.2-0ubuntu3.1, 8.0.3+8.0.2-0ubuntu3.2), libgl1-mesa-glx:amd64 (8.0.2-0ubuntu3.1, 8.0.3+8.0.2-0ubuntu3.2), perl-base:amd64 (5.14.2-6ubuntu2, 5.14.2-6ubuntu2.1), perl-modules:amd64 (5.14.2-6ubuntu2, 5.14.2-6ubuntu2.1), libglapi-mesa:amd64 (8.0.2-0ubuntu3.1, 8.0.3+8.0.2-0ubuntu3.2), libdconf-dbus-1-0:amd64 (0.12.0-0ubuntu1, 0.12.0-0ubuntu1.1), xserver-xorg-video-intel:amd64 (2.17.0-1ubuntu4, 2.17.0-1ubuntu4.1), python-aptdaemon:amd64 (0.43+bzr805-0ubuntu2, 0.43+bzr805-0ubuntu4), compiz-gnome:amd64 (0.9.7.8-0ubuntu1.2, 0.9.7.8-0ubuntu1.4), aptdaemon:amd64 (0.43+bzr805-0ubuntu2, 0.43+bzr805-0ubuntu4), libxatracker1:amd64 (8.0.2-0ubuntu3.1, 8.0.3+8.0.2-0ubuntu3.2), flashplugin-installer:amd64 (11.2.202.236ubuntu0.12.04.1, 11.2.202.238ubuntu0.12.04.1), libdconf0:amd64 (0.12.0-0ubuntu1, 0.12.0-0ubuntu1.1), libdecoration0:amd64 (0.9.7.8-0ubuntu1.2, 0.9.7.8-0ubuntu1.4), libperl5.14:amd64 (5.14.2-6ubuntu2, 5.14.2-6ubuntu2.1), libsqlite3-dev:amd64 (3.7.9-2ubuntu1, 3.7.9-2ubuntu1.1), aptdaemon-data:amd64 (0.43+bzr805-0ubuntu2, 0.43+bzr805-0ubuntu4), nux-tools:amd64 (2.12.0-0ubuntu1, 2.14.0-0ubuntu1), compiz:amd64 (0.9.7.8-0ubuntu1.2, 0.9.7.8-0ubuntu1.4), python-aptdaemon.gtk3widgets:amd64 (0.43+bzr805-0ubuntu2, 0.43+bzr805-0ubuntu4), libglu1-mesa:amd64 (8.0.2-0ubuntu3.1, 8.0.3+8.0.2-0ubuntu3.2), sqlite3:amd64 (3.7.9-2ubuntu1, 3.7.9-2ubuntu1.1), compiz-core:amd64 (0.9.7.8-0ubuntu1.2, 0.9.7.8-0ubuntu1.4), dconf-service:amd64 (0.12.0-0ubuntu1, 0.12.0-0ubuntu1.1), libsqlite3-0:amd64 (3.7.9-2ubuntu1, 3.7.9-2ubuntu1.1)
End-Date: 2012-08-18  12:18:29

Start-Date: 2012-08-18  12:48:33
Commandline: aptdaemon role='role-commit-packages' sender=':1.170'
Upgrade: ubuntuone-installer:amd64 (3.0.0-0ubuntu1, 3.0.2-0ubuntu1.1), libnspr4-0d:amd64 (4.8.9-1ubuntu2.1, 4.8.9-1ubuntu2.3), ubuntu-sso-client-gtk:amd64 (3.0.2-0ubuntu1, 3.0.2-0ubuntu2), tzdata-java:amd64 (2012b-1, 2012e-0ubuntu0.12.04), python-ubuntu-sso-client:amd64 (3.0.2-0ubuntu1, 3.0.2-0ubuntu2), libnspr4:amd64 (4.8.9-1ubuntu2.1, 4.8.9-1ubuntu2.3), ubuntu-sso-client:amd64 (3.0.2-0ubuntu1, 3.0.2-0ubuntu2), jockey-common:amd64 (0.9.7-0ubuntu7, 0.9.7-0ubuntu7.1), tzdata:amd64 (2012b-1, 2012e-0ubuntu0.12.04), libmission-control-plugins0:amd64 (5.12.0-0ubuntu2, 5.12.0-0ubuntu2.1), jockey-gtk:amd64 (0.9.7-0ubuntu7, 0.9.7-0ubuntu7.1), telepathy-mission-control-5:amd64 (5.12.0-0ubuntu2, 5.12.0-0ubuntu2.1)
End-Date 2012-08-18  12:48:45

```

---

