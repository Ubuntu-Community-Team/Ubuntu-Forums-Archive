---
title: "remote desktop from windows machine using xrdp"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by beard3dgeek on 2013-02-01
hi all,

Iv trying to connect to my ubuntu server using xrdp. however when I connect all i seem to get is the desktop without any icons or anything. When i connect my server to a monitor and log on it seems to work fine. I have installed gnome-shell by the way, if that makes any difference.

any ideas what might be goind wrong ?

---

### Post by steeldriver on 2013-02-01
As well as installing gnome-shell, you need to tell xrdp to use that for your session I think - for example I have a minimal ~/.xrdp/.xsession like

```
$ cat ~/.xrdp/.xsession
gnome-session --session=ubuntu-2d

```which seems to work (no guarantees this is the "right" way to do it though) - modify with the appropriate session name instead of ubuntu-2d of course

---

