---
title: "Apport report error"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by ssdt on 2012-07-12
I am facing this error every time I turn on the system:
[IMG]http://i.imgur.com/W8bZQ.jpg


How can I fix this? anyone please help.

---

### Post by NikTh on 2012-07-12
Hi , 
Hah.. This is apport's report for apport itself . 

_This is not a fix but a workaround. _

You can disable apport report info if you want.  

```
gksudo gedit /etc/default/apport
``` and chagne enabled=1 to enabled=0 . Save the document and on next reboot apport will be disabled (for ever) . 
Of course if you want to re-enable you can do it with same way , just change  enabled=0 to enabled=1 . 
Thanks.

---

### Post by lolpenguin on 2012-07-13
> **NikTh said:**
> Hi , 
Hah.. This is apport's report for apport itself . 

_This is not a fix but a workaround. _

You can disable apport report info if you want.  

```
gksudo gedit /etc/default/apport
``` and chagne enabled=1 to enabled=0 . Save the document and on next reboot apport will be disabled (for ever) . 
Of course if you want to re-enable you can do it with same way , just change  enabled=0 to enabled=1 . 
Thanks.

It's not something you can fix, and it is not a bug.
Apport is enabled in development releases, but usually disabled when the release occurs. However, in 12.04LTS, it seems it wasn't disabled, possibly because it's a LTS release.

---

### Post by NikTh on 2012-07-13
> **lolpenguin said:**
> It's not something you can fix, and it is not a bug.
Apport is enabled in development releases, but usually disabled when the release occurs. However, in 12.04LTS, it seems it wasn't disabled, possibly because it's a LTS release.
Hi,
Did you see the picture @lolpenguin ? 
I didn't say that apport its a bug. Apport report bugs and its very useful tool for Ubuntu development . As you say it is enabled by default at development releases (Alpha , beta) sometimes stays enabled more time.. i guess will stay enabled until 12.04.1 release. 

Sometimes apport reports itself , like ssdt's case . See picture he provided with link. 
In this situation a workaround is to disable apport , maybe until developers fix the problem.
Thanks

---

