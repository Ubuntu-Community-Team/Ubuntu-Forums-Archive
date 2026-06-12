---
title: "Looking for location of .desktop file"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by SNIFFER_dog on 2011-09-15
Hi Ubuntu community,

Version: 11.04 Natty Narwhal

When creating a new launcher via the desktop using right click and 'Create Launcher...' for say an application I want to created called 'TestApp'

Where would the .desktop file be located for the newly created app?

Kind regards,


SNIFFY

---

### Post by whatthefunk on 2011-09-15
Try /usr/share/applications

---

### Post by SNIFFER_dog on 2011-09-15
Is the .desktop file named differently too TestApp.desktop

As I don't see it listed there

Thanks for you help


SNIFFY

---

### Post by whatthefunk on 2011-09-15
Create the launcher then do the following in a terminal:
```
locate TestApp
```

---

### Post by SNIFFER_dog on 2011-09-15
Thanks you solved my problem.

---

