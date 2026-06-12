---
title: "Change OpenGL coordinate system?"
date: 2009-02-07
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-02-07
I don't like the retarded 3D coordinate system of OpenGL. I never get used to it.

I want to change it to like this:
[img]http://img294.imageshack.us/img294/7583/coordsystemtx4.png[/img]

In the picture, Z gets larger at near, and XY coords are similar to 2D, like in GIMP.

But I still want to keep 3d perspective and depth testing. How is this done?


And I also want to make the units smaller, like 50.0 matching ~50-60 pixels.

With default settings, 50.0 will be far outside screen.

---

### Post by hessiess on 2009-02-07
> **crazyfuturamanoob said:**
> I don't like the retarded 3D coordinate system of OpenGL. I never get used to it.

I want to change it to like this:
[img]http://img294.imageshack.us/img294/7583/coordsystemtx4.png[/img]

In the picture, Z gets larger at near, and XY coords are similar to 2D, like in GIMP.

But I still want to keep 3d perspective and depth testing. How is this done?


And I also want to make the units smaller, like 50.0 matching ~50-60 pixels.

With default settings, 50.0 will be far outside screen.

Invert the Y and Z acsiss of your coordinate system before passing to OpenGL.

It is not possible to make the coordinates equal to some pixel value unless you are using an orthographic projection, in which case you can:

```

	float proj_bot = 0 - (screen_res.Y / 2);
	float proj_top = 0 + (screen_res.Y / 2);
	float proj_lef = 0 - (screen_res.X / 2);
	float proj_rig = 0 + (screen_res.X / 2);

	glMatrixMode(GL_PROJECTION);
	glLoadIdentity();

	glOrtho(proj_lef, proj_rig, proj_bot, proj_top, 0.1, 200.0);

	glMatrixMode(GL_MODELVIEW);
	glLoadIdentity();

```

---

### Post by crazyfuturamanoob on 2009-02-07
> **hessiess said:**
> Invert the Y and Z acsiss of your coordinate system before passing to OpenGL.

Is it possible to inverse them with gl translate/rotate/scale functions or viewport/matrix/camera settings?

---

### Post by hessiess on 2009-02-07
> **crazyfuturamanoob said:**
> Is it possible to inverse them with gl translate/rotate/scale functions or viewport/matrix/camera settings?

You should be able to scale to -1 along the Y and Z assess. Though I was thinking more along the lines of calculating:

vertex. y = 0 - (vertex.y * 2)
vertex.z = 0 - (vertex.z * 2)

right before you pass the veracities to OpenGL, though both methods will also invert the face vertex order, so you may end up with all the polygon normals pointing the wrong way.

---

### Post by crazyfuturamanoob on 2009-02-07
I was messing up with projection code and found this working:
```
glRotatef( 180.0, 0, 1, 0 );
```
It does exactly what I want, with minimal work.

Edit: Doesn't seem to work correctly. :(
Edit2: Works with this:*```
glScalef( -1, 1, 1 );
```


And the scale of units can be changed by translating away:
```
glTranslatef( 0, 0, 125 );
```

---

