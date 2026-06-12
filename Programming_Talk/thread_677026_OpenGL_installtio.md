---
title: "OpenGL installtio"
date: 2008-01-24
forum: Programming Talk
---

### Post by voltron035 on 2008-01-24
I apologize if this is in the wrong area but I am an older student who has just discovered Linux. I would like to force myself to learn and gain a better understanding of Linux by developing Linux. I am taking a class right now using OpenGL. I have tried search for tutorials on preparation and installation but nothing that is "simple stupid". Any suggestions?

---

### Post by hod139 on 2008-01-26
What are you trying to install?  The opengl development files?

```

sudo apt-get install libgl1-mesa-dev
```

You'll probably also want the glu development files:
```

libglu1-mesa-dev

```

If you need glut
```

sudo apt-get install freeglut3-dev

```

I hope I understood your question.

---

### Post by voltron035 on 2008-02-18
I tried those commands and they didn't work. I got errors stating that the package didn't exist.

---

### Post by Strike&gt;&gt; on 2008-02-18
Just try to search them on synaptic package manger, it will give you similar results so typos wouldn't be a problem.

---

