---
title: "OpenGL lighting example?"
date: 2007-04-06
forum: Programming Talk
---

### Post by lawentzel on 2007-04-06
I've read several posts on here about OpenGL and SDL.  That is what I am currently playing with.  One person directed me to:

[http://ubuntu-gamedev.wikispaces.com/Intro+to+OpenGL+part+2]("http://ubuntu-gamedev.wikispaces.com/Intro+to+OpenGL+part+2")

I've played with that quite a bit, tweaked the fog settings, changed the colors, messed with the size of the cube.  Now I would like to see something that shows how to use lighting in OpenGL.  If anyone knows of any good examples, I would appreciated it.  Thank you in advance.

Lee

---

### Post by xtacocorex on 2007-04-06
When I get my 3D geometry render, that uses TecPlot files, fully working with better rotation and the addition lighting, I'll send you a link to the code.

Here is a tutorial on gpwiki:
[http://gpwiki.org/index.php/OpenGL_Tutorial_Framework:Light_and_Fog](http://gpwiki.org/index.php/OpenGL_Tutorial_Framework:Light_and_Fog)

nehe.gamedev.net has some good tutorials, they also have linux codes for them since they are mostly based in Windows.  Nehe is a good site.

---

### Post by Wybiral on 2007-04-06
Basically, for simple OpenGL lighting you have two options... Per-face lighting and per-vertex lighting. The per-face lighting doesn't really look good for shading things... It's mostly for glass/crystal looking lighting, it lights the face the same shade. The per-vert lighting (lol, I know...) lights the model at each vertex and interpolates the lighting over the face.

Basically, for per-face lighting, you need to calculate the normal for each face and use:
```

glNormal3f(nx, ny, nz);

```
Before rendering each face (but use the actual normal values :) )

You'll need a simple vector class to calculate the normals, basically it's just a normalized vector perpendicular to the face pointing outward (which is determined by the polygon winding). The function for this usually requires a vector cross product, btw.

For per-vert lighting you need to take those face normals and average them amongst the vertices's that make the faces (and normalize them).

Then you just flip the switch in OpenGL (glEnable(GL_LIGHTING) and glEnable(GL_LIGHT0) or 1... 2... 3... etc) and set some of the specifics (diffuse, specular, ambient, etc etc).

It's pretty easy once you obtain the normals.

EDIT:

Well, you don't NEED a vector class, but it will make the cross product easier.

---

### Post by lawentzel on 2007-04-07
Thanks for everyone's help.

---

