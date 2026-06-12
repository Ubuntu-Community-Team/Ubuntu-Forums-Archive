---
title: "Wine Install???"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by sonstar on 2008-11-30
Hello!!!!!!!!!!!!!

I'm trying to install Wine through the terminal and this is what I get.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.17) but 1.0.14-1ubuntu8 is to be installed
        Depends: libc6 (>= 2.7) but 2.6.1-1ubuntu10 is to be installed
        Depends: libldap-2.4-2 (>= 2.4.7) but it is not installable
        PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.14.5ubuntu16 is to be installed
E: Broken packages

What in the world does any of that mean?

---

### Post by taurus on 2008-11-30
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

