---
title: "How do I edit /etc/default/acpi-support"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by kwc01 on 2008-08-25
I know this is a very basic question... but can someone help me figure out how to edit the /etc/default/acpi-support file?

Using "edit" or "gedit" lets me view the contents, but tells me I don't have "the permissions necessary to save the file."

I'm using edubuntu 8.04.

Thank you,
kwc

---

### Post by tuxulin on 2008-08-25
try
sudo gedit /etc/default/acpi-support

Tuxulin

---

### Post by dizee on 2008-08-25
> **tuxulin said:**
> try
sudo gedit /etc/default/acpi-support

Tuxulin
actually you should use gksudo instead of sudo for graphical apps.
```
gksudo gedit /etc/default/acpi-support
```

---

### Post by damis648 on 2008-08-25
> **dizee said:**
> actually you should use gksudo instead of sudo for graphical apps.
```
gksudo gedit /etc/default/acpi-support
```

+1, good advice.

---

### Post by tuxulin on 2008-08-26
deleted

---

