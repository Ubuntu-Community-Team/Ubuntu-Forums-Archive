---
title: "openGL question..."
date: 2005-11-29
forum: Programming Talk
---

### Post by grim918 on 2005-11-29
how do i install the openGL library to use with the g++ compiler. im new to linux and could really use some help

---

### Post by Lux Perpetua on 2005-11-29
I think you need to install *xlibmesa-gl*, *xlibmesa-gl-dev*, *xlibmesa-glu*, *xlibmesa-glu-dev* via apt-get or synaptic.

---

### Post by fct on 2005-11-30
Most OpenGL tutorials use the GLUT library that provides additions like window managing and input processing. For that, you only need to *apt-get install libglut3-dev* and compile with the flag -lglut.

---

