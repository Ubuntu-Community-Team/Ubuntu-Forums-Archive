---
title: "What is the difference in installing qmail server on ubuntu desktop vs ubuntu server"
date: 2014-12-14
forum: New to Ubuntu
---

### Post by satya3 on 2014-12-14
What is the difference in installing qmail server on ubuntu desktop vs ubuntu server

---

### Post by satya3 on 2014-12-14
any help pls

---

### Post by schragge on 2014-12-14
I wonder why there should be any difference? qmail doesn't depend on any graphical features. Besides, citing [uhelp]community/ServerFaq#line-162[/uhelp] > Since 12.04, there is no difference in kernel between Ubuntu Desktop and Ubuntu Server since **linux-image-server** is merged into **linux-image-generic**.

---

### Post by DuckHook on 2014-12-14
The issue is not the kernel. Both are "capable" of running it. The issue is the surface area exposed to attack and the unneeded complexity. Almost all Linux sysadmins shudder at running a GUI on their servers because not only does the unnecessary bloat of a GUI mean more security risk, but more updates, more resources and more points of failure. The difference in memory footprint between a lean CLI scrubbed down to the essentials and a GUI-heavy 3D DE like Ubuntu can be over 10x. Yikes!

There are also many tuning differences like swappiness, etc, but these can be manually reconfigured. The main issues are still security, bloat, and complexity.

---

