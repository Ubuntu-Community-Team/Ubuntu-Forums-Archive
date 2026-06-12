---
title: "OpenGL And Water"
date: 2008-01-23
forum: Programming Talk
---

### Post by Lster on 2008-01-23
Hi everyone

I'm not satisfied with my water so far and after trying a couple of things that haven't really worked I have come to ask all your opinions!

At the moment I render my terrain and then draw water horizontally through it so that it intersects smoothly. This doesn't look very good though as where it intersects with the land looks like "a hard line".

So really I want to have the water opacity to be reduced for shallower depths or something to give that kind of effect. I can't really see an efficient way to manage this however. Any suggestions?

Thank you
Lster

---

### Post by Lster on 2008-01-23
Here is a current screenshot:

---

### Post by Wybiral on 2008-01-23
Do you have any examples of what a normal water edge should look like in a game? Maybe you can do some hunting to find a good example, then see if there are any articles on the techniques they used. Personally, I'm not too thrown off by the example you've just posted, but I probably have really low standards for video game effects (I still use 512mb ram with an nvidia card that's at least three generations old). However, the game [Cube 2]("http://cubeengine.com/") manages to pull off a pretty decent water without fixing the edge problem, theirs just has shader-language ripples that make the line look less smooth. But if you post some game titles that have the effect you're going for, we might be able to hunt down some article on it somewhere.

---

### Post by Lster on 2008-01-23
Maybe I'm a little over-picky but I like things to look perfect. :)

The image attached is an example of what I would like. I did some searching but I'm not really sure what for. I kind of want to do a depth test and depending on that alter the opacity.

Thanks for the reply,
Lster

EDIT: Also I often play Sauerbraten on Linux (it is a very good game) so I will try browsing the source for how they do water.

---

### Post by Wybiral on 2008-01-23
One possible way would be to find the depth of the water at each vertex (water Y - terrain Y) and adjust the opacity of that vertex to correlate to the depth. That feels like it would create the effect of the picture you posted. Naturally (as I'm sure you know) you would want to do this on-load. Also, I haven't invested too much research into [volumetric fog]("http://nehe.gamedev.net/data/lessons/lesson.asp?lesson=41"), but that's probably what you would have to do if you were going to allow the camera to witness the same effect when they go under.

---

### Post by stroyan on 2008-01-23
It is not clear from your image whether you are always looking straight down into the water.  If you are, then you can use the glFog setting for a quick water depth
effect.  Just render the original land with the fog setting such that you start to blend to water color at sea level.

If you have an OpenGL implementation with the GL_EXT_fog_coord extension,
you can set the fog coordinate of each vertex to match the depth of the vertex below sea level.  That would work from any above water camera position.

Another common method for applying a depth effect at varying camera angles is to draw a series of parallel planes with low alpha values.  The planes are drawn from lowest to highest level after the land is all drawn.  The deeper the land, the more water planes that blend their color into the pixel.  But there are detectable edges at the various planes.

Or, if you get multitexture working for you then you might use a one dimensional texture to blend in a water color in proportion to water depth as you render the land.

---

### Post by Lster on 2008-01-23
Thank Wybiral - I think you've nailed what I need. And with any luck it will be as easy as multitexturing to implement. As I said before, I really wasn't sure what I needed, but seeing that I know now... :o :)

---

### Post by Lster on 2008-01-23
[QUOTE=stroyan]It is not clear from your image whether you are always looking straight down into the water. If you are, then you can use the glFog setting for a quick water depth
effect. Just render the original land with the fog setting such that you start to blend to water color at sea level.

If you have an OpenGL implementation with the GL_EXT_fog_coord extension,
you can set the fog coordinate of each vertex to match the depth of the vertex below sea level. That would work from any above water camera position.

Another common method for applying a depth effect at varying camera angles is to draw a series of parallel planes with low alpha values. The planes are drawn from lowest to highest level after the land is all drawn. The deeper the land, the more water planes that blend their color into the pixel. But there are detectable edges at the various planes.

Or, if you get multitexture working for you then you might use a one dimensional texture to blend in a water color in proportion to water depth as you render the land.[/QUOTE]

I'm not always looking down...

That is probably the way I will head (or similar).

I did actually try the blending planes method but it didnt look right and was a little slow (when I used a lot of planes).

I'm not quite sure what you mean by your multitexture method as I have that all working great. I'm interested in it if you could explain again. :)

---

### Post by Lster on 2008-01-24
Well I'm trying the NeHe tutorial which is pretty good really and it makes it seem so easy! I tried to implement it myself but failed and getting the tutorial from the NeHe site I see that the Linux/SDL port of the code doesn't work for me either (just see plain orange color). Checking my program there are no OpenGL errors and I have checked my extensions and they include "GL_EXT_fog_coord".

When I use glFogCoordfEXT nothing changes at all - the quad I use it on looks like it would without glFogCoordfEXT. I've changed the values sent to functions all over the place but to no avail and I can't find anything by searching. Any ideas at all would be appreciated greatly!

Thank you
Lster

---

### Post by Lster on 2008-01-24
Bump!

---

### Post by stroyan on 2008-01-24
The NeHe tutorial lesson 41 has a problem with getting the function declaration of glFogCoordfEXT.
dding a define for GL_GLEXT_PROTOTYPES before the include of GL/gh.h in lesson41.c makes the example work for me.
```

#define GL_GLEXT_PROTOTYPES 1
#include <GL/gl.h>        
```

Your own attempts may have the same problem.
If the parameter to glFogCoordfEXT is not known to be a GLfloat then the function may see a random value instead of the one you attempt to pass in.

---

### Post by Lster on 2008-01-25
You rock! :popcorn: It is working fine now, but I am surprised this worked. Could you explain it to me as I never like not understanding things!

Thank You!
Lster

---

### Post by stroyan on 2008-01-25
[http://www.opengl.org/registry/ABI/](http://www.opengl.org/registry/ABI/) notes that GL_GLEXT_PROTOTYPES needs to be defined before including GL/gl.h in order to get function prototypes for extensions.  That is implemented with an ifdef in glext.h, which is included by gl.h.

---

### Post by Lster on 2008-01-25
Thanks for the link and everything! I think I can manage everything now!

:)

---

### Post by Lster on 2008-01-25
And just to show you all what that looks like (notice how the depths look different):

---

