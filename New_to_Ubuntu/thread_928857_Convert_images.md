---
title: "Convert images"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by szaqlon on 2008-09-24
How would I go about converting .ppm images to .jpg? I have 356 images and I would like to be able to do them all without manually doing them one by one.

---

### Post by vishzilla on 2008-09-24
if you have imagemagick installed use the **convert** keyword

EDIT: ```
convert *.ppm image%d.jpg
``` where %d increments from 0 to 355 in your case

---

### Post by NewJack on 2008-09-24
You should also be able to convert images in GIMP

---

### Post by vishzilla on 2008-09-24
> **NewJack said:**
> You should also be able to convert images in GIMP
thats a pain. convert is easy and powerful. all you need is to enter one line as I have given before

---

### Post by NewJack on 2008-09-24
I just wanted to give another option :)

---

### Post by lovinglinux on 2008-09-24
Phatch is a very nice batch converter. It's in the repos.

---

### Post by szaqlon on 2008-09-24
convert is perfect, thank you.

---

