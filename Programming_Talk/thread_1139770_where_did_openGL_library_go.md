---
title: "where did openGL library go?"
date: 2009-04-27
forum: Programming Talk
---

### Post by tneva82 on 2009-04-27
Pretty weird thing. Reinstalled ubuntu from scratch to both home and work computers(different reasons but what the heck). Used same 9.04 desktop for both. In home computer I got development stuff installed no problemo and now I can compile my project without issues. In work computer however it gives "usr/bin/ld: cannot find -lGL" error message.

I thought openGL libraries came as standard and if they don't why could I compile in home computer? I certainly didn't install any openGL packages there(just build-essential, SDL and SDL_net).

Annoying enough that work computer doesn't seem to find any non-installed packages in synaptic packet manager(NONE. Only packages it shows is ones I have installed...) so had to install build-essential, SDL, SDL_net and ftgl manually but now what's the packet to install openGL libraries?

---

### Post by geirha on 2009-04-27
OpenGL libraries are installed by default, but not the development package containing header files and other stuff needed to compile and link against it.

In general, try searching for packages called libraryname<something>-dev. I.e.
```
aptitude search 'gl.*-dev'
``` Unfortunately alot of packages contain the letters gl, so you get a lot of hits on that one, but the one you want should be [libgl1-mesa-dev](apt:libgl1-mesa-dev).

EDIT:
> **tneva82 said:**
> Annoying enough that work computer doesn't seem to find any non-installed packages in synaptic packet manager(NONE. Only packages it shows is ones I have installed...) so had to install build-essential, SDL, SDL_net and ftgl manually but now what's the packet to install openGL libraries?

Go to System -> Administration -> Software Sources and make sure the repositories are enabled. They may be disabled if you didn't have internet access when you installed Ubuntu.

---

### Post by tneva82 on 2009-04-27
Atleast openGL got fixed(though not the packet issue. Ah well. Atleast add/remove program works). However now ftgl is causing issues. First it seems to go smootly except in the very end when doing sudo make there comes Done.: command not found and Error 127 & Error 1 error mesages. Since those came in docs and demos not sure if they affect anything. sudo make install gives similar errors. And then when I try to compile the program I get undefined reference to FTPixmapFront::yadda yadda. This with code that has worked long time so I guess I screwed up something in ftgl installation but what? procedure was:

./autogen.sh
./configure
sudo make
sudo make install

ARGH!

---

### Post by geirha on 2009-04-27
You'll need to provide the whole output of each of those commands. However, ftgl is in the repositories; [ftgl-dev](apt:ftgl-dev), or [libftgl-dev](apt:libftgl-dev) if you have Intrepid or newer. You'll save yourself the trouble by just installing that.

---

### Post by tneva82 on 2009-04-29
Urgh. Most DEFINETLY should not have "upgraded" to 9.04. Now it compiles but when I try to RUN it SDL_Init() gives me "Video initialization failed: No available video device." error. First part is written in code but No available video device comes from SDL.

What's up with this? Code ran just fine on 8.10 so why should it fail to work in 9.04? Anybody able to figure out how to fix it?.

Code where it fails is:

```

if(SDL_Init(SDL_INIT_VIDEO)<0) {
   fprintf(stderr, "Video Initialisation failed: %s\n", SDL_GetError());
   Quit(1);
}

```

So I suppose SDL doesn't recognise the graphic card but why not? Did before. Why not now? Only thing changed is ubuntu version. So is only hope to get it working reinstall ubuntu 8.10 back?

---

