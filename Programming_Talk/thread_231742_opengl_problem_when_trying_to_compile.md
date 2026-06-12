---
title: "opengl problem when trying to compile"
date: 2006-08-07
forum: Programming Talk
---

### Post by forrestcupp on 2006-08-07
I know I'm probably in the wrong forum, but I don't know where to ask this.  I'm trying to compile an adventure game called Loose Cannon.  I found out about the game on the Ubuntu native games page.  Its homepage is [http://loose-cannon.sourceforge.net/](http://loose-cannon.sourceforge.net/)   When I run ./configure everything goes well until the end where I get  
```
configure: error: *** OpenGL GL-library not found
```

I don't understand, because I have nvidia drivers installed, and all of my opengl games from the repos work great. It looks as if I have my libgl files in /usr/lib.  I have had this error with other things as well.  Does anyone have any ideas?

---

### Post by Engnome on 2006-08-07
When compiling you usually need the -dev versions of the libraries.

---

### Post by forrestcupp on 2006-08-07
> **Engnome said:**
> When compiling you usually need the -dev versions of the libraries.

Thank you.  I was just coming back to say that I figured it out.  I guess I just assumed I had the devs, and now I realize that you don't initially have any.  Everything worked when I got the devs.

---

### Post by themusicwave on 2006-08-08
Would you mind explaining to me how you installed the dev libraries?

I am a recent convert from windows and I have no idea how to setup for OpenGl Programmign in Ubuntu.

---

### Post by Engnome on 2006-08-08
> **themusicwave said:**
> Would you mind explaining to me how you installed the dev libraries?

I am a recent convert from windows and I have no idea how to setup for OpenGl Programmign in Ubuntu.

Open synaptic, search for the library. Pick the one that ends in -dev and mark to install. Click apply.

---

### Post by themusicwave on 2006-08-08
That sounds pretty easy.  I assumed it would be like windows where I had to copy dlls to directories and such.

Thanks!

---

