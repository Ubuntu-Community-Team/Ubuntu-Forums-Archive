---
title: "Either OpenGL is not found by the IDE or is not up-to-date (c++)"
date: 2016-04-27
forum: Programming Talk
---

### Post by Oinos on 2016-04-27
System specs:
ubuntu 14.04 lts
intel 945gm x86/mmx/sse2
2GiB RAM
[full specs]("http://i.imgur.com/x5RpHQ8.png")

1. I tried to include <GL/glew.h> in my project, but I got 'fatal error: GL/glew.h: No such file or directory'

2. Tried to update opengl as suggested [here]("http://askubuntu.com/questions/703761/how-do-i-upgrade-opengl-intel"), but using the appropriate version (.../14.04/.../intel-linux-graphics-installer_1.2.1-0intel1_i386.deb). After restart still got the same error, *glxinfo | grep "version"* gives ```
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL version string: 1.4 Mesa 10.5.9
``` and there is still no GL folder in /usr/include/. I have no idea what to do now.

3. Because my GPU is less than HD4000 I only want and should upgrade to openGL 2.1. I'm using code::blocks 13.12 as IDE for c++.

Could anyone help me out of this maze?

---

### Post by spjackson on 2016-04-27
How did you install libglew, was it from the Ubuntu repository or from the deb you mentioned in point 2? If you are using the repository one, then you need to install the libglew-dev package for the headers.

---

### Post by Oinos on 2016-04-27
> **spjackson said:**
> How did you install libglew, was it from the Ubuntu repository or from the deb you mentioned in point 2? If you are using the repository one, then you need to install the libglew-dev package for the headers.

Thank you. Now that I intalled libglew-dev everything complied.

---

