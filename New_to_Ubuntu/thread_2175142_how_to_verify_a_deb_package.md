---
title: "how to verify a deb package?"
date: 2013-09-17
forum: New to Ubuntu
---

### Post by minsf on 2013-09-17
hi there,

i have deb package that i want to install with

```
dpkg -i foo.deb
```

but before i do this i want to verify the package's signature/checksum.

i know this is usually done automatically with apt-get, but i do not have internet connection from the box, so i had to download this (linux-image) package from ububtu's repositories on a usb (hopefully the network driver is fixed in this newer kernel, and then i'll have internet connection). so before installing, i thought it would be better to verify that it is signed with ubuntu's key and that the checksum match (i.e. that it was downloaded correctly).

perhaps another possible solution is to add a filesystem path to my sources.list somehow and let apt-get take it from there. but i'm not sure how to do that either.

thanks

---

### Post by ibjsb4 on 2013-09-17
An example.  Package glibc-doc

At the bottom of the page, click on your Architecture (in this example, it is [COLOR=#ff0000]all[/COLOR]).

[ATTACH=CONFIG]246317[/ATTACH]

---

