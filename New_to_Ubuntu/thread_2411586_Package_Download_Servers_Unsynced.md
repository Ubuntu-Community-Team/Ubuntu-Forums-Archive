---
title: "Package Download Servers Unsynced"
date: 2019-01-31
forum: New to Ubuntu
---

### Post by d.brotherston on 2019-01-31
When running apt upgrade today the following packages returned 404 on the Australian mirror but after switching to the main server I was able to get them.
Shouldn't the regional mirrors be synced with the main server?

```
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/main amd64 python3-gi-cairo amd64 3.26.1-2ubuntu1
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/main amd64 python3-gi amd64 3.26.1-2ubuntu1
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/main amd64 gir1.2-dbusmenu-glib-0.4 amd64 16.04.1+18.04.20171206-0ubuntu2
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/main amd64 libdbusmenu-glib4 amd64 16.04.1+18.04.20171206-0ubuntu2
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/main amd64 libcogl-common all 1.22.2-3ubuntu1
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/main amd64 libcogl20 amd64 1.22.2-3ubuntu1
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/main amd64 libcogl-pango20 amd64 1.22.2-3ubuntu1
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/main amd64 libcogl-path20 amd64 1.22.2-3ubuntu1
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/main amd64 libdbusmenu-gtk3-4 amd64 16.04.1+18.04.20171206-0ubuntu2
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/main amd64 libdbusmenu-gtk4 amd64 16.04.1+18.04.20171206-0ubuntu2
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/universe amd64 python-gi-cairo amd64 3.26.1-2ubuntu1
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/main amd64 python-gi amd64 3.26.1-2ubuntu1
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed/universe amd64 python-gobject all 3.26.1-2ubuntu1
```

---

### Post by wildmanne39 on 2019-01-31
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Irihapeti on 2019-01-31
For more information on the state of repository mirrors, see [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

Officially, they should probably all be in sync, but in practice, not all of them are.

---

### Post by d.brotherston on 2019-02-01
> **Irihapeti said:**
> For more information on the state of repository mirrors, see [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)
Thank you, This is a super useful site!

---

