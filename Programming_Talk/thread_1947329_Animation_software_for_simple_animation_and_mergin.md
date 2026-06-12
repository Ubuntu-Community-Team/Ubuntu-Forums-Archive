---
title: "Animation software for simple animation and merging existing videos?"
date: 2012-03-26
forum: Programming Talk
---

### Post by rpupa on 2012-03-26
I often wonder how the movies like shrek or avatar etc, are made. Is there any free software in ubuntu for merging or animating videos or inserting our photos in real time to an existing video running on background , or just adding our sound in real time in an existing video etc...........???

---

### Post by Vaphell on 2012-03-26
Shrek is all about rendering 3d scenes - you set up the scene, animate things according to the time scale, set the camera position/movement and then frame after frame you render the scene (take a 'photo' of that scene) and encode it in desired format. For that you got free blender3d.
Avatar is a much more complicated case. On top of bleeding edge 3d you got bluebox tech to mix real life stuff with cgi, no wonder it's cost was well north of $200M. Some simple effects probably can be achieved with relatively simple tools but i'm not too familiar with this particular area of gfx art.

---

### Post by rpupa on 2012-03-26
Thank you very much, Now i can imagine how complex it must be to produce such great piece of art, and why every one is not capable of producing such things.

---

### Post by alexfish on 2012-03-26
there are a couple of basic ones in the repos

Ktoon and Pencil

There is also a video Editor

Avidemux

For Transitions can have a look at imagination

---

### Post by avacado on 2012-04-11
You can acheive fast, very clunky two dimesnional results with KDENLIVE alone.  Basically you use the composite transition to 'slide' PNG images around over a backing video. see example [http://commons.wikimedia.org/wiki/File:Open_Educational_Resources_Video.ogg](http://commons.wikimedia.org/wiki/File:Open_Educational_Resources_Video.ogg)

---

