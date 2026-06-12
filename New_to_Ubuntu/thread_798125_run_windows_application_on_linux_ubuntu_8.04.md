---
title: "run windows application on linux ubuntu 8.04"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by PeterSek on 2008-05-17
I recently lost my windows xp hdd and would like to give xp a flick all together. I loaded ubuntu 8.04 into RAM, installed skype, msn ect in seconds. Linux Ubuntu rocks!, bit ghank you to the creators
However I need for the moment to be able to run one (or two) win applications (one of these is MYOB Accounting program)

Is there an easy way to install some kind of Windows interpreter?

thanks
Peter

---

### Post by bjschuma on 2008-05-17
You could try WINE

sudo apt-get install wine

---

### Post by Oldsoldier2003 on 2008-05-17
> **PeterSek said:**
> I recently lost my windows xp hdd and would like to give xp a flick all together. I loaded ubuntu 8.04 into RAM, installed skype, msn ect in seconds. Linux Ubuntu rocks!, bit ghank you to the creators
However I need for the moment to be able to run one (or two) win applications (one of these is MYOB Accounting program)

Is there an easy way to install some kind of Windows interpreter?

thanks
Peter

```
sudo apt-get install wine
``` will install Wine. You may or may not be able to suffice with wine, some programs dont do well under wine and its forks- in those cases you would be better off running Windows inside a VM such as VirtualBox or VMWare

---

