---
title: "2D OpenGL"
date: 2007-08-17
forum: Programming Talk
---

### Post by Lster on 2007-08-17
Hi all

This is an OpenGL problem related to layering textures over each other. Anyhow, I have set up OpenGL like this:

...

Now when I draw, everything appears on top of what was previously drawn. However I want it so that I can choose what is behind or in front. I can see, perhaps a couple of ways of doing this.

...

Can you advise me on either of these methods? Are they possible? Anything else I could consider?

Thank you lots,
Lster

---

### Post by moshy on 2007-08-17
I reckon, using OpenGL, you could render in 3D, with no transformation, so you're looking directly down the z-axis, and set the perspective to orthogonal-perspective, so things stay the same size even if they are further away. Then you would have to set arbitrary z-coordinates for each object, and of course enable depth testing.

---

### Post by Lster on 2007-08-17
> I reckon, using OpenGL, you could render in 3D, with no transformation, so you're looking directly down the z-axis, and set the perspective to orthogonal-perspective, so things stay the same size even if they are further away. Then you would have to set arbitrary z-coordinates for each object, and of course enable depth testing.

Great! This would rock! I have no idea how to do this, however. What should my ortho be? And how do I enable orthogonal-perspective?

After that, would I render things like this:

```
...
```

instead of:

```
...
```

Thank you lots,
Lster

---

### Post by Lster on 2007-08-17
*Bump* :)

---

### Post by Mirrorball on 2007-08-17
I'm new to OpenGL, but I have the red book 5th edition and it doesn't say anything about orthogonal perpective, but it has a whole section on ortographic projection. Are they the same thing? If it is, the relevant functions are glOrtho and gluOrtho2D.

---

### Post by Wybiral on 2007-08-17
> And how do I enable orthogonal-perspective?

You have your near/far planes set up for a lack of depth (-1 to 1). I've never used ortho with depth, so I can't suggest a better range, I guess just experiment.


>I'm new to OpenGL, but I have the red book 5th edition and it doesn't say anything about orthogonal perpective, but it has a whole section on ortographic projection. Are they the same thing? If it is, the relevant functions are glOrtho and gluOrtho2D.

Perspective projection is when there is size distortion with object further away, orthogonal has no distance based distortion. I assume ortho perspective is just another way to say ortho projection (albeit confusing). glOrtho and gluOrtho2d are basically the same thing except glOther allows you to specify the near/far clipping planes and gluOrtho2d sets them to (-1, 1).

---

### Post by moshy on 2007-08-18
yeah, sorry about the confusion with perspective/projection

---

### Post by Lster on 2007-08-18
> You have your near/far planes set up for a lack of depth (-1 to 1). I've never used ortho with depth, so I can't suggest a better range, I guess just experiment.

EDIT: I did eventually get all this working! :)

---

### Post by Wybiral on 2007-08-18
Have you tried "glEnable(GL_DEPTH_TEST);" by chance?

Also, you will need to clear your depth buffer when you clear the color buffer if you plan to use it.

---

### Post by mikesofty on 2008-04-18

[SIZE="3"]Hi everyone..
I want to configure opengl  or glut in ubuntu..
Is opengl and glut are same.?
I got all the header files ..
But how to link the library functions ..?
Which IDE can i use for opengl..

[/SIZE]

---

### Post by Larrxi on 2008-04-18
GLUT handles the window and stuff like that.

You link with -lGL.

Anjuta, Eclipse and Kdevelop are possible IDE:s, i prefer to use the console :)

---

