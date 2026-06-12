---
title: "C++ Application Title and Icon"
date: 2013-02-12
forum: Programming Talk
---

### Post by ProvenDantheman on 2013-02-12
Hello, I'm new here :)

     I run Ubuntu 12.10 with the Gnome 3 shell. I program in C++ using Code::Blocks. The libraries I use are OpenGL and GLUT. 
     My issue is that the OpenGL window has a name, but in the Activities bar, where for example one would see Firefox, my application says Unknown, and there is no icon.
     I attached an image. Any help would be appreciated.

---

### Post by Zugzwang on 2013-02-12
The following link is the first one that comes up when searching for "GLUT Window Title" on google:

[http://www.opengl.org/resources/libraries/glut/spec3/node27.html](http://www.opengl.org/resources/libraries/glut/spec3/node27.html)

It should already solve one or both of your problems.

---

### Post by ProvenDantheman on 2013-02-13
> **Zugzwang said:**
> The following link is the first one that comes up when searching for "GLUT Window Title" on google:

[http://www.opengl.org/resources/libraries/glut/spec3/node27.html](http://www.opengl.org/resources/libraries/glut/spec3/node27.html)

It should already solve one or both of your problems.
I tried it and it does not work. My problem isn't the name of the actual OpenGL window, but the title displayed in the activities bar. In my picture, on the top of the screen, my application is displayed as unknown.

---

### Post by r-senior on 2013-02-13
What if you create a .desktop file in ~/.local/share/applications?

Here are the docs, but it's usually easier to copy one from /usr/share/applications and edit it. Tools also exist, I believe.

[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)

---

### Post by ProvenDantheman on 2013-02-13
> **r-senior said:**
> What if you create a .desktop file in ~/.local/share/applications?

Here are the docs, but it's usually easier to copy one from /usr/share/applications and edit it. Tools also exist, I believe.

[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)
It sadly did not work. The .desktop file launched the application, but the title in the Activities bar was still unknown.

---

