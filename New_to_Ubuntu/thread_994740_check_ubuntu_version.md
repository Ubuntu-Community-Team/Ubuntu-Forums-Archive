---
title: "check ubuntu version"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by bcbotha on 2008-11-27
how do i check what version of ubuntu im running?

---

### Post by Dedoimedo on 2008-11-27
Hello,

In terminal, type:

```
uname -r
```

Or

```
uname -a
```

See if this helps you ...
Dedoimedo

---

### Post by adult swim on 2008-11-27
to find your ubuntu version number you can run ```
lsb_release -a
``` from a terminal

---

### Post by HittingSmoke on 2008-11-27
> **bcbotha said:**
> how do i check what version of ubuntu im running?

For a more clear and detailed screen you can go to "System>Administration>System Monitor" and click on the "System" tab on the far left.

It will give you your release version, kernel version and your desktop environment version along with some basic hardware info.

---

### Post by ibutho on 2008-11-27
Enter the commands
```
cat /etc/issue
```
or
```
cat /etc/lsb-release
```
If you prefer using a GUI, I think if you click under System, there is an "About Ubuntu" entery. That should also show the version (I might be wrong on this one).

---

### Post by bcbotha on 2008-11-27
thanks guys

---

