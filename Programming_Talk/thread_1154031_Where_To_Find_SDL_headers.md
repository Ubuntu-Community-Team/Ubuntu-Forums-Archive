---
title: "Where To Find SDL headers?"
date: 2009-05-09
forum: Programming Talk
---

### Post by Mad Hacker on 2009-05-09
hello
i was just wondering what the path to the sdl headers is, i looked in /usr/include and didn't find it.

i checked, and it is installed

thanks :)

---

### Post by simeon87 on 2009-05-09
Open a terminal and type:

```

locate SDL.h

```

Common locations would be /usr/include/SDL/SDL.h or /usr/local/include/SDL/SDL.h but perhaps it's elsewhere.

---

### Post by Mad Hacker on 2009-05-09
i did that and it didn't find it.
(i actually thought of searching after i posted, sorry for not looking first)

i checked synaptic and the package name is *libsdl1.2debian-alsa*(this is installed)
the description being
> 
Simple DirectMedia Layer (with X11 and ALSA options)

SDL is a library that allows programs portable low level access to a video
framebuffer, audio output, mouse, and keyboard.

This version of SDL is compiled with X11 graphics and ALSA sound.


---

### Post by simeon87 on 2009-05-09
It looks like you didn't install the -dev package of SDL For example libsdl1.2-dev for SDL and the other -dev packages if you need them (for image, mixer, etc).

There's a difference between the library itself and the development files (such as the headers) that the compiler uses to build an SDL application.

Try installing at least libsdl1.2-dev and probably some others depending on your needs.

---

### Post by Mad Hacker on 2009-05-09
that did it, thanks! :)

---

