---
title: "Controlling mouse movements with c++"
date: 2010-10-08
forum: Programming Talk
---

### Post by a sandwhich on 2010-10-08
What library would I use to control cursor movements with c++ in ubuntu? I have found many ways to do it in VC++, but I need this to work in ubuntu. Any ideas? Also, what does the little arrow("->") mean? I have only seen it put to use in qt, but now I am beginning to see it elsewhere.

---

### Post by worksofcraft on 2010-10-08
You will need to use [X11 windows programming]("http://www.math.msu.su/~vvb/2course/Borisenko/CppProjects/GWindow/xintro.html"). There is a function to generate events. That can include mouse movement events as one might use in a macro playback. When I remember the name of the function I'll come back and edit this post but it's not coming to mind atm.

p.s.... nope I really can't remember but what I do remember is that you can get the source code of this [macro recorder/play back utility]("http://www.gnu.org/software/xnee/") and see exactly how they done it :)

oh and also the -> arrow is for identifying a field in a data structure that you have a pointer to e.g:
[php]
struct my_class {
    int MyInt;
    char *MyString;
    float MyFloat;
};

my_class *PointerToMyClassInstance = new my_class;

PointerToMyClassInstance->MyInt = 2010;
PointerToMyClassInstance->MyString = "Pie is yummy";
PointerToMyClassInstance->MyFloat = 3.1415;
[/php]

---

### Post by LinksPatrocinados on 2010-10-08
I heard something about X11 too, ill try find at my delicious and post here the link to the article.

---

### Post by a sandwhich on 2010-10-08
Ok thanks. I used to use x11 with my bsd partition. Didn't think it would work well with ubuntu.

---

### Post by a sandwhich on 2010-10-08
Um, how would I go about installing x11? On a completely different topic my installation of opencv is not working. Everytime I try to #include <cv> it says no file or directory found.

---

### Post by worksofcraft on 2010-10-08
x11 is the actual windows system that will be running your graphical desktop under Ubuntu so you already have it installed. All you need is the developer library header files.

Go to synaptic package manager from System Administration and search for libx11-dev. Mark that for installation and click "Apply". I think that's all you need :guitar:

p.s. Soz IDK anything about opencv... but perhaps some of those people whose posts were removed might contribute *positively* and they can help you?

---

### Post by a sandwhich on 2010-10-08
And what about the opencv problem?

---

### Post by CharlesA on 2010-10-08
Trolling posts removed.

---

### Post by spjackson on 2010-10-09
> **a sandwhich said:**
> Um, how would I go about installing x11? On a completely different topic my installation of opencv is not working. Everytime I try to #include <cv> it says no file or directory found.
Did you install libcv-dev from the repositories? This package has cv.h and cv.hpp but nothing for
```

#include <cv>

```Also, what command do you use to compile your program?

---

### Post by a sandwhich on 2010-10-09
Sorry, I meant #include <cv.h>. I used g++ -o file file.cpp

---

### Post by spjackson on 2010-10-09
> **a sandwhich said:**
> Sorry, I meant #include <cv.h>. I used g++ -o file file.cpp
Well, still assuming that you installed it from the libcv-dev package, then it will have installed the headers in /usr/include/opencv, in which case you need one of the following.
```

g++ -o file file.cpp -I/usr/include/opencv
g++ -o file file.cpp `pkg-config --cflags opencv`

```and for linking, 
```

pkg-config --libs opencv

```

---

