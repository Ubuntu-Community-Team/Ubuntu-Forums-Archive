---
title: "opengl question"
date: 2008-01-20
forum: Programming Talk
---

### Post by rightclickhere on 2008-01-20
i downloaded the latest tarball of the quesa 3d and ran configure but it failed with the following error "checking for OpenGL... yes configure: error: Fatal - can't find OpenGL Libraries - Stopping here." im not 100% sure but could this be because ubuntu uses mesa by default instead of opengl?

---

### Post by stroyan on 2008-01-20
You are probably missing some of the *-dev development packages for OpenGL.  Try adding these-

sudo apt-get install freeglut3 freeglut3-dbg freeglut3-dev libgl1-mesa-dev libgl1-mesa-dri libgl1-mesa-glx libglew1.4 libglew1.4-dev libglu1-mesa libglu1-mesa-dev x11proto-gl-dev

---

