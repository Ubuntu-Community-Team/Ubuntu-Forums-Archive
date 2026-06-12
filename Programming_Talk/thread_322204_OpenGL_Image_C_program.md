---
title: "OpenGL Image C program"
date: 2006-12-20
forum: Programming Talk
---

### Post by dlai on 2006-12-20
Hey everybody
I'm looking into creating a opengl image program. What I'm not really sure how to do is scanning a folder looking for images and thereafter loading the images into the program. I will probably do it by texture mapping. Do anybody know how to scan a folder for images, and load them much like a displaylist, so I won't have to rebuild everytime?? Hope you can help, or point to some guidance...

---

### Post by duff on 2006-12-20
> **dlai said:**
>  Do anybody know how to scan a folder for images, .

```
# man 3 glob
```will get you started.  (you need to have installed **manpages-dev**)

---

### Post by hod139 on 2006-12-20
Boost offers a more cross platform solution if that is a concern: [Boost Filesystem Library]("http://boost.org/libs/filesystem/doc/index.htm")

---

