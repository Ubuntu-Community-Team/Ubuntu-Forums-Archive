---
title: "CMake can't find GLUT Xi or Xmu"
date: 2011-03-09
forum: Packaging and Compiling Programs
---

### Post by RobotGymnast on 2011-03-09
I'm trying to configure a project with CMake, and set it to find the GLUT package.

It finds the GLUT library fine, but gives me errors with regards to GLUT Xi and GLUT Xmu:

```

CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
GLUT_Xi_LIBRARY (ADVANCED)
    linked by target "WindowsTest" in directory /home/me/devl/c++/game/2DGame/src
GLUT_Xmu_LIBRARY (ADVANCED)
    linked by target "WindowsTest" in directory /home/me/devl/c++/game/2DGame/src

```

Can somebody shed some light on this?

---

### Post by RobotGymnast on 2011-03-10
Bamp.

---

### Post by EnCuKou on 2011-03-10
Just had the same problem, and solved it by installing the corresponding packages :)

```
sudo apt-get install libxmu-dev libxi-dev
```

Hope it helps!

---

### Post by RobotGymnast on 2011-03-10
Great, thanks!

---

### Post by legends2k on 2013-03-10
Helped me too, thanks!

---

### Post by peng6662001 on 2013-03-11
It worked.

---

### Post by tidy1995 on 2013-10-26
Work fine, thanks!

---

