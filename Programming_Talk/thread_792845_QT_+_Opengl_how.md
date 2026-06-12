---
title: "QT + Opengl: how?"
date: 2008-05-13
forum: Programming Talk
---

### Post by piratenaapje on 2008-05-13
I'm trying to compile a qt4 program with opengl functions in c++. I installed freeglut3-dev, libqt4-opengl and libqt4-opengl. Still, there isn't a /usr/include/qt4/OpenGL dir, and I get the following errors:

error: QGLWidget: No such file or directory
error: qgl.h: No such file or directory

Any ideas on what packages I should install to fix this?

---

### Post by GeneralZod on 2008-05-13
Try libqt4-dev

---

### Post by piratenaapje on 2008-05-13
> **GeneralZod said:**
> Try libqt4-dev

Allready installed that :p

---

### Post by piratenaapje on 2008-05-13
I get this error:
E: /var/cache/apt/archives/libqt4-opengl-dev_4.4.0-1ubuntu3~hardy1_i386.deb: trying to overwrite `/usr/lib/pkgconfig/QtOpenGL.pc', which is also in package libqt4-dev

when trying to install libqt4-opengl-dev

---

### Post by piratenaapje on 2008-05-13
Fixed it in a evil way: downloaded the deb, unpacked it, unpacked the data.tar.gz, and copied it to the needed locations :p

---

