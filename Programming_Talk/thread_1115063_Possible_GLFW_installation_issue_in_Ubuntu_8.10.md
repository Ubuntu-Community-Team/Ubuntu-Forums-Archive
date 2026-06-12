---
title: "Possible GLFW installation issue in Ubuntu 8.10"
date: 2009-04-03
forum: Programming Talk
---

### Post by dim-fish on 2009-04-03
Hi to boards, I'm a month new to Ubuntu and this is my first post.

I'm trying to configure an OpenGL with GLFW development environment in Ubuntu 8.10.  I installed GLFW via apt-get (aptitude?) and was not able to link a sample, tiny program.  There were many undefined references to 'XRRsomethingSomething' for one.

I manually installed libxrandr-dev that comes with some x11-proto-*stuff* and am able to compile by adding -lXrandr to the link line.  However, GLFW in windowed mode has no window title or other visible window borders, but I can render a single triangle no problem.

So, questions:

1.  Does the GLFW package for Ubuntu have missing dependency information?

2.  If so, have I managed to install dependencies but incompatible versions?

3.  Is there another way for me to set up an OpenGL + GLFW environment in Ubuntu?

4.  Is GLFW broken as I've configured it, or do I need to do something actively to get a window to render?

---

