---
title: "Anjuta Projects ??"
date: 2005-08-14
forum: Programming Talk
---

### Post by grofaz on 2005-08-14
Can someone give me a quick run down on what the differences are between the various project types ?? I have a basic understanding of win 32 but I'm totally unfamiliar with anything else. I code with C++ mainly and use SDL and OpenGL. So which project type should I concentrate on using ? Advice appreciated as it will save me a hell of a lot of useless reading, there's so much material to cover. Thanks!

---

### Post by Fluffy, the jolly sheep on 2005-08-14
You should pick a generic/console project since there isn't a template specifically for SDL/OpenGL in Anjuta. Then you should enter the following in the Options tab of the compiler and linker settings dialog (under the settings menu):
in the C-FLAGS field:   `sdl-config --cflags`
the LD-FLAGS: `sdl-config --libs` -lGL -lGLU -lSDL_image -lSDL_mixer
This causes for the project to be linked against the sdl and opengl libraries.
Also, make sure you have the necessary header files installed of those libraries (libsdl-dev and others). For OpenGL, you'll need xlibmesa-gl(u)-dev packages or the nvidia-glx-dev package if you've installed the proprietary nvidia driver.

---

### Post by grofaz on 2005-08-14
Thanks! That helps a lot.

Regards...

---

