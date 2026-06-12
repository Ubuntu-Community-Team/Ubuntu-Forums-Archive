---
title: "A question about Snap Packages"
date: 2017-02-03
forum: New to Ubuntu
---

### Post by waltd on 2017-02-03
Hi all, 
    If I install a snap package, say VCL Player, will it automatically update when I run Software Updater or the updates tab in Software?  Basically I'm asking how does a program installed with snap automatically update?  Thanks.

---

### Post by howefield on 2017-02-03
I believe that

```
sudo snap refresh packagename
```

will update the named snap, in your case sudo snap refresh vlc and..

```
sudo snap refresh
```

will update all snaps on the system.

---

### Post by ian-weisser on 2017-02-03
Software Updater, and all other apt-based serves, don't talk snap and have no effect on snap packages.
That's precisely one purpose of snap packages - they do not rely upon apt services or infrastructure.

---

