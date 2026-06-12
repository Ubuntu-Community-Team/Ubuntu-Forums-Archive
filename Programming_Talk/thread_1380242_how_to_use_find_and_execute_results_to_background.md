---
title: "how to use find and execute results to background"
date: 2010-01-13
forum: Programming Talk
---

### Post by denarced on 2010-01-13
So I'd like to do something like this:
```
find . -type f -name 'something*' -exec vlc '{}' & \;
```
but the &-part don't work so well

The basic idea is to launch the files to separate vlc-windows.
The files are action shot from different angles.

Much thanks to any and all help

---

### Post by denarced on 2010-01-13
this should be in the programming section
my bad

---

### Post by denarced on 2010-01-13
So I'd like to do something like this:
Code:

```
find . -type f -name 'something*' -exec vlc '{}' & \;
```

but the &-part don't work so well

The basic idea is to launch the files to separate vlc-windows.
The files are action shot from different angles.

Much thanks to any and all help

---

### Post by Elfy on 2010-01-13
Please use the report button in fture and ask for it to be moved instead of opening a duplicate.

---

### Post by Hellkeepa on 2010-01-13
HELLo!

Escape the ampersand just like you've escaped the semicolon.

Happy codin'!

---

### Post by denarced on 2010-01-13
> **Hellkeepa said:**
> HELLo!

Escape the ampersand just like you've escaped the semicolon.

Happy codin'!

this does not work(first thing I tried)
In this way it'll open one file and another file called '&'

---

