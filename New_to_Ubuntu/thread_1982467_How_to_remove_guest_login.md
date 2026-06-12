---
title: "How to remove guest login"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by SolarGent on 2012-05-18
I find the idea of guest login crazy, and I want to remove it from my computer. How do I remove this guest log in please?

---

### Post by papibe on 2012-05-18
Hi SolarGent.

You can disable the guest account by editing a configuration file.

Run this:
```
gksudo gedit /etc/lightdm/lightdm.conf
```
Confirm your password, and then and a line at the end that says:
```
allow-guest=false
```
Save the file, and restart your computer.

Hope that helps, and tell us how it goes.
Regards.

---

### Post by SolarGent on 2012-05-19
Ok thanks papibe, will try  that.

---

