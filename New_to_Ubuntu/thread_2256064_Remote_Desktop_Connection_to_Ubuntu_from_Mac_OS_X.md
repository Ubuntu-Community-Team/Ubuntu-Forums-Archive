---
title: "Remote Desktop Connection to Ubuntu from Mac OS X"
date: 2014-12-09
forum: New to Ubuntu
---

### Post by Jesimio on 2014-12-09
Hello,

I created Ubuntu server on DigitalOcean and would like to connect to Ubuntu desktop over Remote Desktop Protocol from Macbook Pro to watch movies and listen to music.

I tried VNC server and clients and they work flawlessly except they do not transfer sound of Ubuntu Desktop over VNC session.

Is it possible to watch and listen of Ubuntu desktop for Remote Desktop? If so, how can I achieve this?

Regards,

Jessie

---

### Post by sandyd on 2014-12-10
> **Jesimio said:**
> Hello,

I created Ubuntu server on DigitalOcean and would like to connect to Ubuntu desktop over Remote Desktop Protocol from Macbook Pro to watch movies and listen to music.

I tried VNC server and clients and they work flawlessly except they do not transfer sound of Ubuntu Desktop over VNC session.

Is it possible to watch and listen of Ubuntu desktop for Remote Desktop? If so, how can I achieve this?

Regards,

Jessie

As far as I can remember, VNC (at least none of the RealVNC) does not include sound. Nor does X Forwarding. However, TeamViewer, NoMachine NX/FreeNX seem to have support.

---

