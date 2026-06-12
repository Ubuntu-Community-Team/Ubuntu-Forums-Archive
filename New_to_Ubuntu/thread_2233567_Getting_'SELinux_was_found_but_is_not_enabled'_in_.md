---
title: "Getting 'SELinux was found but is not enabled' in Terminal"
date: 2014-07-09
forum: New to Ubuntu
---

### Post by nomnomnomomnom on 2014-07-09
I've just started using Ubuntu yesterday and while I've used 'gnome-system-monitor' command a few times, today, after using it, Terminal put out '** (gnome-system-monitor:4398): WARNING **: SELinux was found but is not enabled.' after pressing enter. System monitor still opened, but I'm wondering if that warning is anything I should worry about and how can I remove it. The only thing I tinkered with is my hostname, but I closely followed [this tutorial]("http://www.youtube.com/watch?v=v1Pke5CnbIE").

On another note, is there any application with which I can see my CPU load, temperatures and such?

Also, attaching screenshot:
[IMG]http://i.imgur.com/utrEaR8.jpg[/IMG]

---

### Post by slooksterpsv on 2014-07-10
IIRC Ubuntu doesn't use SELinux and only uses AppArmor, so the warning you can ignore. Some apps integrated quite a bit with SELinux, but the same protection is offered with AppArmor.

---

