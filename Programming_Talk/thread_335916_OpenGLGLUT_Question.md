---
title: "OpenGL/GLUT Question"
date: 2007-01-10
forum: Programming Talk
---

### Post by davek20 on 2007-01-10
I just have a quick question about an aspect of OpenGL. I'm using Ubuntu edgy with P3 900, 512mb ram and nvidia 6600GT video card.

I was looking at Nehe's tutorials and ran a few of them, such as walking in a 3D world. It was incredibly slow, like I could see the "world" being drawn and getting horrible framerates. This was the code using GLUT. Then just the other day, I downloaded an OpenGL program from one of my course's websites, and it ran incredibly slow and it also used GLUT. This was a pong game and when I turned off textures it sped up a lot but still sluggish. 

I've written programs with GLUT for my classes before, but just basic things, such as no textures/lights. They ran really smooth, so I'm thinking it has to do something with the textures and GLUT not rendering them fast enough.

So is it just GLUT that is making these run slow? What are the other options then GLUT?

---

### Post by Wybiral on 2007-01-10
SDL is certainly an option... And it's a lot better than GLUT. From my experience SDL is a little faster and doesn't require you to hand everything over to it (whereas GLUT forces you to let it take control of the program flow).

NeHe has some SDL examples for linux too.

Your computer has better specs than mine and most of the SDL nehe tutorials run pretty smooth for me...

---

### Post by ansi on 2007-01-11
**davek20**

Do you have installed and enabled nvidia (proprietary ;)) drivers? The problem may be here, imho.

---

### Post by jblebrun on 2007-01-11
> **davek20 said:**
> I just have a quick question about an aspect of OpenGL. I'm using Ubuntu edgy with P3 900, 512mb ram and nvidia 6600GT video card.

I was looking at Nehe's tutorials and ran a few of them, such as walking in a 3D world. It was incredibly slow, like I could see the "world" being drawn and getting horrible framerates. This was the code using GLUT. Then just the other day, I downloaded an OpenGL program from one of my course's websites, and it ran incredibly slow and it also used GLUT. This was a pong game and when I turned off textures it sped up a lot but still sluggish. 

I've written programs with GLUT for my classes before, but just basic things, such as no textures/lights. They ran really smooth, so I'm thinking it has to do something with the textures and GLUT not rendering them fast enough.

So is it just GLUT that is making these run slow? What are the other options then GLUT?

Check to make sure you have 3D rendering enabled. On the command line:
```

glxinfo | grep render

```

---

### Post by skeeterbug on 2007-01-11
> **ansi said:**
> **davek20**

Do you have installed and enabled nvidia (proprietary ;)) drivers? The problem may be here, imho.

I agree.

---

### Post by slavik on 2007-01-11
OpenGL is for complex graphics.

GLUT was created to allow fast prototyping for OpenGL, the goal of GLUT was to get a window open as fast as possible to use OpenGL in it.

SDL is intented for game developers, especially with its addon modules for reading in any image file format you might ever need, sound mixing through ALSA, ability to render truetype fonts, and even wrappers for networking and threading.

I am not sure about quality of SDL as compared to other offerings (like Fmod, or OpenAL) but SDL+OpenGL combination can do everything you need concerning graphics applications. If you throw GTK into the mix (I think GTK allows creation of OpenGL contexts as surfaces), you can create pretty much any type of software you could ever need. :)

---

### Post by jblebrun on 2007-01-11
> **slavik said:**
> OpenGL is for complex graphics.

GLUT was created to allow fast prototyping for OpenGL, the goal of GLUT was to get a window open as fast as possible to use OpenGL in it.

SDL is intented for game developers, especially with its addon modules for reading in any image file format you might ever need, sound mixing through ALSA, ability to render truetype fonts, and even wrappers for networking and threading.

I am not sure about quality of SDL as compared to other offerings (like Fmod, or OpenAL) but SDL+OpenGL combination can do everything you need concerning graphics applications. If you throw GTK into the mix (I think GTK allows creation of OpenGL contexts as surfaces), you can create pretty much any type of software you could ever need. :)

Yes, slavik is correct. I should've also mentioned... GLUT is not "slow." It's just a toolkit to help with OpenGL programming. It has a few helper functions for window related thing, but nothing that it does will slow you down for basic OpenGL example programs.

I'm almost certain that you don't have GLX/DRI acceleration enabled.

---

### Post by davek20 on 2007-01-22
> **ansi said:**
> **davek20**

Do you have installed and enabled nvidia (proprietary ;)) drivers? The problem may be here, imho.

This may sound stupid but thats the driver off of the nVidia site right? I'm having trouble trying to install that driver. The error that I'm getting is to close out of X. I have no idea how to do that :confused: I read the README on the site to and it really didn't help out at all. I also checked out ubuntuguide and nothing caught my eye on how to do that.

Also, just a side note. I downloaded ActionCube and tried it out. I was getting horrible frames/sec (my guess would be about 1FPS :rolleyes: ).

Can some one help me?

---

### Post by lnostdal on 2007-01-23
> **davek20 said:**
> This may sound stupid but thats the driver off of the nVidia site right? I'm having trouble trying to install that driver. The error that I'm getting is to close out of X. I have no idea how to do that :confused: I read the README on the site to and it really didn't help out at all. I also checked out ubuntuguide and nothing caught my eye on how to do that.

Also, just a side note. I downloaded ActionCube and tried it out. I was getting horrible frames/sec (my guess would be about 1FPS :rolleyes: ).

Can some one help me?

Always check Ubuntu-documentation before trying the "generic way" -- being it installation of drivers or whatever.

Assuming you have a NVidia-card: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

So probably something like this:

```

sudo aptitude install nvidia-glx nvidia-glx-dev
sudo nvidia-xconfig

```

...then restart X. This:

```

glxinfo | grep render

```

..should now report "direct rendering:  Yes".

---

### Post by davek20 on 2007-01-23
> **lnostdal said:**
> Always check Ubuntu-documentation before trying the "generic way" -- being it installation of drivers or whatever.

Assuming you have a NVidia-card: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

So probably something like this:

```

sudo aptitude install nvidia-glx nvidia-glx-dev
sudo nvidia-xconfig

```

...then restart X. This:

```

glxinfo | grep render

```

..should now report "direct rendering:  Yes".

Thanks a lot, it works like a charm now :D

---

### Post by amo-ej1 on 2007-01-25
Now you know the difference between hardware rendering and software rendering :D

---

