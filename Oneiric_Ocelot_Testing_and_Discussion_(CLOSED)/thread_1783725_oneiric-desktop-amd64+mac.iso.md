---
title: "oneiric-desktop-amd64+mac.iso"
date: 2011-06-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2011-06-16
It looks like something changed on the [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) website. I did not remember the amd64 being with mac but am zsyncing a new iso to test.

Bill

---

### Post by sparker256 on 2011-06-16
> **sparker256 said:**
> It looks like something changed on the [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) website. I did not remember the amd64 being with mac but am zsyncing a new iso to test.

Bill
I see a few rough edges but the daily live is looking very good. I have unity3d on nouveau. There are some missing icons and a crash or two but all in all very good progress so far. I am typing this from my daily live usb 061611. 

Bill

```

ubuntu@ubuntu:~$ date && lsb_release -sd || cat /etc/*release &&  uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p
Thu Jun 16 07:17:49 EDT 2011
Ubuntu oneiric (development branch)
Linux 3.0-0-generic
unity 3.8.14
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV92
OpenGL version string:  2.1 Mesa 7.10.3

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
ubuntu@ubuntu:~$ Wed Jun 15 03:02:07 MST 2011


```

---

