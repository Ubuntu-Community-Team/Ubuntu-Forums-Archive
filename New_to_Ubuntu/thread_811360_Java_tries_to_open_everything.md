---
title: "Java tries to open everything"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by canthus13 on 2008-05-29
I've managed to kludge everything together to make Xubuntu Hardy do everything I need, including accessing SMB shares reliably... But it always wants to open files using java. Any idea how to make it behave normally? i.e. ask if it doesn't know what program to use.

--Me

---

### Post by kpkeerthi on 2008-05-29
Try changing the settings under Preferred Applications
[IMG]http://www.xfce.org/images/about/tour/xfce44-preferences-applications.png[/IMG]

If it does not work, you may want to remove (or rename) the xfce folder under ~/.config/ and reboot. This should reset all XFCE setting back to defaults.

---

### Post by canthus13 on 2008-05-30
Unfortunately, there's no setting for file associations there.  I have similar issues when hitting some .php pages, on the Xubuntu machine and my Ubuntu machine.

--Me

---

