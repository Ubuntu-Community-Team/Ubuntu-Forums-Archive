---
title: "where is gl.h?"
date: 2006-06-05
forum: Programming Talk
---

### Post by fng on 2006-06-05
```

> *********************************************************
> * Building client
> *********************************************************
  > Compiling ref_gl/r_alias.c
In file included from ref_gl/r_local.h:58,
                 from ref_gl/r_alias.c:22:
ref_gl/qgl.h:30:19: error: GL/gl.h: No such file or directory

```

in what package can i find GL/gl.h ?

---

### Post by skeeterbug on 2006-06-05
gl.h is a header file for OpenGL.

---

### Post by hod139 on 2006-06-05
mesa-common-dev.  If you have an Nvidia card, you can grab nvidia's gl.h which will have their own extensions by installing nvidia-glx-dev.

---

### Post by fng on 2006-06-05
mesa-common-dev is installed.
locate can't find a GL/gl.h (yes is did a updatedb)

```
fng@butters:~$ dpkg -l | grep mesa-common
ii  mesa-common-dev                        6.4.1-0ubuntu8                        Developer documentation for Mesa
fng@butters:~$ locate gl.h
/usr/share/ubuntu-artwork/home/locales-ubuntu/index-gl.html
/usr/share/qt3/doc/html/opengl.html
/usr/share/qt3/doc/html/qaxserver-demo-opengl.html
/usr/share/qt3/doc/html/qaxserver-example-opengl.html
/usr/share/qt3/doc/html/qgl.html
/usr/include/FL/gl2opengl.h
/usr/include/FL/gl.h
fng@butters:~$
```

---

### Post by fng on 2006-06-05
it seems it a know bug if you upgrade from breezy to dapper: [https://launchpad.net/distros/ubuntu/+source/mesa/+bug/29435](https://launchpad.net/distros/ubuntu/+source/mesa/+bug/29435)

I solved it by : ```
apt-get install --reinstall mesa-common-dev
```

---

### Post by link6502 on 2006-06-17
I recently upgraded to dapper, and I think I'm experiencing the missing opengl headers bug. I tried installing nvidia-glx-dev, but when I tried to compile mplayer, it still couldn't find gl.h.

I looked for gl.h myself, and it looks like it was stuck in /usr/share/doc/nvidia-glx-dev/include/GL, which the compiler doesn't find.

I can try the reinstall of mesa-common-dev, but I was wondering if I'd be better off with nvidia's gl headers, since I have an nvidia card and use their driver. How do I install those so the compiler can use them?

---

### Post by hod139 on 2006-06-17
[quote=link6502]
I can try the reinstall of mesa-common-dev, but I was wondering if I'd be better off with nvidia's gl headers, since I have an nvidia card and use their driver. How do I install those so the compiler can use them?[/quote]

The choice truly is yours.  If you need any of nvidia's extensions in your program, then go with the their headers (of course, compatibility with ATI cards will become an issue).  If you want the generic gl headers that all openGL capable cards can use, then use mesa-common-dev.   If you want to use nvidia's gl.h, you have to manually copy it to /usr/include/GL (I believe there is a README file in /usr/share/doc/nvidia-glx-dev explaining all the details).

---

### Post by tenfishsticks on 2009-05-17
I'm having the same problem with Jaunty!  I'm installing VTK on a fresh Ubuntu install and having a time at it.  I didn't have this much trouble on Intrepid, but that machine had a nvidia card...

---

### Post by Sockerdrickan on 2009-05-17
> **hod139 said:**
> mesa-common-dev.  If you have an Nvidia card, you can grab nvidia's gl.h which will have their own extensions by installing nvidia-glx-dev.
^

---

