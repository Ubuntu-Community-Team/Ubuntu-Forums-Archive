---
title: "how to restore session"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by biji on 2008-09-09
hi... im using gnome and accidently delete bluetooth from system -> pref -> Sessions
how to make it back?? coz my bluetooth dongle is now undetected thanks!

---

### Post by unutbu on 2008-09-09
Go to System>Pref>Sessions and click the "+ Add" button.

Enter
```

Name:  Bluetooth Manager
Command: bluetooth-applet
Comment: Bluetooth Manager applet
```

This is part of the "Startup Programs" tab, so the change won't take effect until you log out and log back in.

---

### Post by biji on 2008-09-09
thanks...

---

