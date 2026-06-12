---
title: "Comparing Two image files."
date: 2008-04-06
forum: Programming Talk
---

### Post by sheffrem on 2008-04-06
Hi guys, is there any way to compare two images. Actually my goal is to login by using my webcam to take a picture at login prompt then compare it with the picture in my profile. if it matche then i want to be granted access to the pc. Is there an easy way to do so ?

---

### Post by LaRoza on 2008-04-06
> **sheffrem said:**
> Hi guys, is there any way to compare two images. Actually my goal is to login by using my webcam to take a picture at login prompt then compare it with the picture in my profile. if it matche then i want to be granted access to the pc. Is there an easy way to do so ?

You can compare two files easily. 

Face recognition isn't easy, and certainly not something one could do alone. Biometrics is quite complex, and even now difficult to use.

---

### Post by sheffrem on 2008-04-06
Hi, after googling around i found those guys doing this but its a little confusing, can you guys help get what language they are using.

---

### Post by sheffrem on 2008-04-06
Hi, after googling around i found those guys doing this but its a little confusing, can you guys help get what language they are using.

[http://www.imagemagick.org/Usage/compare/#compare](http://www.imagemagick.org/Usage/compare/#compare)

---

### Post by LaRoza on 2008-04-06
> **sheffrem said:**
> Hi, after googling around i found those guys doing this but its a little confusing, can you guys help get what language they are using.

[http://www.imagemagick.org/Usage/compare/#compare](http://www.imagemagick.org/Usage/compare/#compare)

Most likely C or C++.

---

### Post by Nion on 2008-04-06
Im not trying to be rude here, but give up and pick an easier project! :-P
Comparing faces is not in any way an easy task, its one of these things that even experts have trouble with.
The article you link to - while beeing quite advanced - is nowhere advanced enough for comparing faces. Using that method the lightning conditions are way more important than the face in the picture. 
If your profile picture is taken at dalight conditions, you will never be able to log in at night. A stranger in dalight will however have much better chances.

---

### Post by stroyan on 2008-04-06
That imagemagick compare is written in C.
You can look at the source yourself with the 'apt-get source' command.
```

$ mkdir imagemagick_source; cd imagemagick_source
$ apt-get source imagemagick
$ find . | grep compare
...
$ gedit \
imagemagick-6.2.4.5.dfsg1/utilities/compare.c \
imagemagick-6.2.4.5.dfsg1/magick/compare.h \
imagemagick-6.2.4.5.dfsg1/magick/compare.c

```

  If you want to pursue more research on face recognition you may want
to start by learning about the computer vision software that is part of
ubuntu.  The commands below led to the 'OpenCV (Open Computer Vision)'
library.  That has C and python language bindings in ubuntu.

```

$ apt-cache search recognition
...
$ apt-cache show libcv1
...
$ apt-cache rdepends libcv1
...
$ apt-cache show python-opencv

```

This idea is in the brainstorm list at [http://brainstorm.ubuntu.com/idea/1817/](http://brainstorm.ubuntu.com/idea/1817/)
There is pointer to someone who says they have an implementation in C++ and java.
But they provide only a binary and no source code. :(

---

