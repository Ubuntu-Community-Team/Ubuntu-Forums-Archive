---
title: "Civilized way to detect if redhat or debian based system"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by peterlauri on 2008-07-15
Hi,

I have a software that is running on both debian and redhat based systems. I need to be able to detect what system it is, without having to configure it. What is the best way to do that? Currently I check if /etc/debian-version exist or if /etc/redhat-release exist...

Any other way to do this?

/Peter

---

### Post by bobnutfield on 2008-07-15
How did you install the software?  Red Hat versions end in .rpm and Debian ends in .deb.

Bob

---

### Post by scragar on 2008-07-15
debian uses apt(and deb's), redhat uses yum(and rpms). You could test those commands:
```
if which dpkg &> /dev/null; then
    # DEBIAN
else
    if which rpm &> /dev/null; then
         # RED HAT
    fi
fi
```

---

### Post by unutbu on 2008-07-15
Maybe 
```
% cat /proc/version_signature 
Ubuntu 2.6.22-14.52-generic

``` or

```
% cat /etc/lsb-release | head -n 1 | awk 'BEGIN {FS="="} {print $2}'
Ubuntu

```
Not sure what you'd get on redhat...

---

### Post by peterlauri on 2008-07-16
> **scragar said:**
> debian uses apt(and deb's), redhat uses yum(and rpms). You could test those commands:
```
if which dpkg &> /dev/null; then
    # DEBIAN
else
    if which rpm &> /dev/null; then
         # RED HAT
    fi
fi
```

But as I understood rpm could be installed and used on a customized debian for example. So this would not be bullet proof.?

---

### Post by peterlauri on 2008-07-16
> **unutbu said:**
> Maybe 
```
% cat /proc/version_signature 
Ubuntu 2.6.22-14.52-generic

```

On redhat /proc/version exist, and contains redhat in content. But /proc/version_signature on Ubuntu contains Ubuntu, and not redhat :)

---

