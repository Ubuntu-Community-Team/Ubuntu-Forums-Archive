---
title: "trying to open tagtool when connect usb drive"
date: 2011-08-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by grandtoubab on 2011-08-28
Hello all
When I connect a usb drive I got an error message saying it can't find /usr/bin/tagtool.
That is for sure as I uninstall tagtool.
But I don't understand why the process try to launch it. I guess it should be nautilus.
The usb drive is mounted and I can open it manually using nautilus.

So where are the libraries or rules to manage usb?

I try a
```
sudo grep -r tagtool /usr/lib
```

but it is very long
Do someone knows where I can find in which file the command tagtool is launched in the usb process?

---

