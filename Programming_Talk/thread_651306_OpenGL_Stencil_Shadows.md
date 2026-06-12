---
title: "OpenGL Stencil Shadows"
date: 2007-12-27
forum: Programming Talk
---

### Post by Lster on 2007-12-27
Hi everyone

I have gotten really far in the last months on my game engine. I have got to thank Wybiral for all his help a while ago with SDL and OpenGL in Linux - Thanks! :)

Right now I think I'm ready to program OpenGL shadows using the stencil buffer. NEHE has been a great help while learning OpenGL, but for once I can't understand the concepts or implementation in his Shadow Casting Tutorial (number 27).

I have tried searching Google but this still doesn't clarify me on the core concept. I understand the depth buffer and have read the Wikipedia page, Shadow Volumes.

Could anyone give a conceptual overview of stencil shadowing please?

Thanks and merry Christmas! :KS
Lster

---

### Post by Lster on 2007-12-27
*Bump*

I still haven't worked it out yet - but I'm determined! :)

---

### Post by CptPicard on 2007-12-27
Any particular question you have? I think the Wikipedia article looked pretty good... it's been some time since my computational geometry and computer graphics classes though. :p

Briefly: The central idea is that you compute actual geometry for the shadowed areas in 3D space. Then you render that geometry into your stencil buffer (and remember to choose appropriate faces of the shadow "blocks")... then you can use that stencil to render both lit and unlit versions of your scene, using the stencil to tell which areas of the screen to paint with the lit version and which with the unlit version...

---

### Post by Lster on 2007-12-27
You're right. I guess the bit really confusing me is step 3 in:

[QUOTE=Wikipedia]   1. Find all silhouette edges (edges which separate front-facing faces from back-facing faces)
   2. Extend all silhouette edges in the direction away from the light-source
   3. Add a front-cap and/or back-cap to each surface to form a closed volume (may not be necessary, depending on the implementation used)
[/QUOTE]

Could you elaborate on what Wikipedia say? What are the caps for?

---

### Post by CptPicard on 2007-12-27
"Implementation detail". :) I would suppose it's because dealing with objects stretching to infinity is not something your geometry system necessarily likes... I suppose you need to be actually building this stuff for yourself to know. Also, of course, capping your shadow volume makes it finite also in the sense that you aren't computing shadows for all eternity in a possibly big scene...

---

### Post by Lster on 2007-12-27
How do you work out from that where the shadows will be? I see there is a shadow where it meets the wall - infact for anything inside it.

---

### Post by CptPicard on 2007-12-27
Good question... actually on second reading I must admit that I'm not completely satified with my understanding of the method anymore either, but the basic idea anyway is that you count into the stencil buffer the amount of shadow surfaces in front and in back of the object, depth info of which you get from the z-buffer... if on both front and back of the object you have shadows both "opening" and "closing" then you're in light, if there is a shadow left "open" at the depth of your object, then you're inside the volume.

Grab a better resource for the details, I don't think Wikipedia quite has it as detailed as I'd like...

---

### Post by Lster on 2007-12-27
[QUOTE=CptPicard]Good question... actually on second reading I must admit that I'm not completely satified with my understanding of the method anymore either, but the basic idea anyway is that you count into the stencil buffer the amount of shadow surfaces in front and in back of the object, depth info of which you get from the z-buffer... if on both front and back of the object you have shadows both "opening" and "closing" then you're in light, if there is a shadow left "open" at the depth of your object, then you're inside the volume.[/QUOTE]

What do you mean by "in front" or "in back" - I think I get what you mean...?

I'll try another tutorial - I have found many! I think it's one of those strange things that you can't understand a bit of it until you understand the whole... ;)

---

### Post by CptPicard on 2007-12-27
```


Ok, This here is a shadow volume (two of them actually):

e      (    x       )     y    (       )

        ^front    ^back

e is eye, x is in shadow and y is in light. Light is somewhere else, casting the volumes (    ).

```

We know the depth of x and y from z-buffer. By painting ) and ( into the stencil buffer so that backface increments and front face decrements, we can count the amount of shadow at x and y: starting from the back, for y it is +1-1=0, for x it is +1-1+1=1. 

Now you just need to integrate the x and y depth information into this, and I must admit I didn't get it from the Wikipedia article :) Good luck -- I'm off to bed.

EDIT: OH YES... note that the z-buffer is ON when you render the shadow volumes. So you don't actually do the stencil-buffer incrementing or decrementing when you're rendering something *behind* either x or y. So you just do the sum from x or y onwards towards the eye! Which gives you either 0 for light or 1 for shadow. Got it?

---

### Post by Lster on 2007-12-28
Thanks for the help - I am beginning to get it. And it is partially working from code that has been hacked from tutorials. I have found a tutorial that looks good; I will post here if I can't understand anything else.

---

### Post by Lster on 2007-12-28
Woohoo! Have a look at this image attached!

---

### Post by CptPicard on 2007-12-28
Cool, congrats... was the shadow volume geometry computation difficult in practice? It's always been all theory to me, never even tried getting my hands actually dirty with OpenGL...

---

### Post by cellerit on 2007-12-28
Hello! I'm trying to learn OpenGL /SDL myself right now. I wondered if you knew some good tutorial(s) and ressource(s) for that? I already did some SDL and started a small RTS game ( that was on windows tho ). Now i want to do 3D. 

For example i have problems with the rendering not working in another thread but i need a thread for the game logic and a thread for the rendering ( at least ).

That looks awesome btw :).

---

### Post by Lster on 2007-12-28
[QUOTE=CptPicard]Cool, congrats... was the shadow volume geometry computation difficult in practice? It's always been all theory to me, never even tried getting my hands actually dirty with OpenGL...[/QUOTE]

I am still learning it as I don't actually understand the code fully yet! With your help and a little further reading I do understand the outline of what should happen in stencil shadow volumes. Now to see how it is approached in the code!

[QUOTE=cellerit]Hello! I'm trying to learn OpenGL /SDL myself right now. I wondered if you knew some good tutorial(s) and ressource(s) for that? I already did some SDL and started a small RTS game ( that was on windows tho ). Now i want to do 3D.[/QUOTE]

Well I have got to say: NeHe! And a couple of other sites...

[http://nehe.gamedev.net/](http://nehe.gamedev.net/) - NeHe
[http://www.gamedev.net/reference/list.asp?categoryid=31](http://www.gamedev.net/reference/list.asp?categoryid=31) - GameDev.net
[http://www.opengl.org/code/](http://www.opengl.org/code/) - And, of course, OpenGL's homepage

All of which I have found useful in the past!

[QUOTE=cellerit]For example i have problems with the rendering not working in another thread but i need a thread for the game logic and a thread for the rendering ( at least ).
[/QUOTE]

I will soon be attempting to add multi-thread support to my game - I plan to design my game engine to allow an arbitrary number of threads (by default the same number as the number of CPUs). I haven't crossed that bridge yet!

---

### Post by cellerit on 2007-12-28
Thanks alot for the links :)

---

