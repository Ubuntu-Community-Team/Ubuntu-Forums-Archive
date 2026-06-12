---
title: "XChat Opens and Suddenly Closes"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by LinkManDX on 2008-08-01
I just installed XChat and tried to run it. When it opened, it immediately closed. I ran it in terminal, and after it immediately closed, I get the error 'Segmentation Fault', and nothing else.

Can you help me?

---

### Post by tuxxy on 2008-08-01
xchat is included with the install I thought, should be located in applications > internet

---

### Post by superbenny on 2008-08-01
Try this:
```
sudo apt-get purge xchat
sudo apt-get install xchat-gnome
```

---

### Post by LinkManDX on 2008-08-01
I get the same error with XChat-GNOME, Segmentation fault.

---

### Post by dicecca112 on 2008-08-01
type in a terminal xchat and post what is output that may give you a hint as to what is going on

---

### Post by LinkManDX on 2008-08-01
Segmentation fault is the output, that's where I got the error from.

> steve@steve-laptop:~$ /usr/bin/xchat
Segmentation fault
steve@steve-laptop:~$

---

### Post by LinkManDX on 2008-08-04
This also started happening with the Pidgin Instant Messenger.

Any help?

---

### Post by dicecca112 on 2008-08-04
try deleting the .xchat# and .purple folder

---

