---
title: "update manager crash"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by eurekamole on 2008-07-07
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '“deb' is not known on line 77 in source list /etc/apt/sources.list, E:The list of sources could not be read.'


I was trying to install zsnes yesterday from terminal using instructions from some random site, and something in my gut tells me that's the problem. May I please get some advice on how to fix this? I'm actively learning about the usage of linux, but I'm still very inexperienced when it comes to troubleshooting it.

---

### Post by iaculallad on 2008-07-07
Try to post your sources.list file:

```
cat /etc/apt/sources.list
```

---

