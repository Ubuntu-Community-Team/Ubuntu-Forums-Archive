---
title: "OpenGL again: oddly blended textures."
date: 2009-06-06
forum: Programming Talk
---

### Post by Bulletbeast on 2009-06-06
[http://img357.imageshack.us/img357/1649/sbb.png](http://img357.imageshack.us/img357/1649/sbb.png)
[http://img150.imageshack.us/img150/7073/sbc.png](http://img150.imageshack.us/img150/7073/sbc.png)

I have a bunch of these (view on black background), which I draw using the feedback buffer to define at what window coordinates a bunch of points (corresponding to the images' centres) end up. However, instead of being correctly blended, they are drawn like this:

[[IMG]http://img231.imageshack.us/img231/7158/localgroupblending.th.png[/IMG]](http://img231.imageshack.us/my.php?image=localgroupblending.png)

Any other texture put in their place renders in the same way, and those textures put elsewhere (i.e. "images mode", the mode which renders 3d billboards of the galaxies with colour images) render correctly. All of my textures are loaded with libSOIL ([http://lonesock.net/soil](http://lonesock.net/soil)). glColor3f makes a miniscule difference:

[img]http://img387.imageshack.us/img387/3328/minisculedifference.png[/img]
(zoom 4x)

It seems as if every galaxy symbol is drawn on top of itself several times. However, the loop seems to be correct, and the only thing that's making any difference between how the galaxies are drawn in "images mode" and "symbols mode" are the Begin2D()/End2D() functions:

```
void glBegin2D()
{
    glMatrixMode(GL_PROJECTION);
    glPushMatrix();
      glLoadIdentity();
      glOrtho(0.0, window_width, 0.0, window_height, -1.0, 1.0);
      glMatrixMode(GL_MODELVIEW);
        glPushMatrix();
        glLoadIdentity();
  return;
}

void glEnd2D()
{
        glPopMatrix();
      glMatrixMode(GL_PROJECTION);
      glPopMatrix();
    glMatrixMode(GL_MODELVIEW);
  return;
}
```

which get me into a 2D view. I draw my font between these, and it blends correctly... I think. When I look at it carefully, it's too small to tell whether it's blended right, either...

Anyone with whatever insights on the subject, please help...

---

### Post by Victor Liu on 2009-06-09
Hey there, it's me again. (I trawl through this forum every now and then looking for unanswered questions, and yours seem to turn up.)

So let me get this straight, you render your galaxies. Then on the next frame you enter feedback mode and render your billboards using an ortho projection? Why not just make your billboards little squares that face the viewer? (Yes, this requires some geometrical transformation, but you can do it in a single pass). If you use the feedback buffer, I'm not sure what happens to the alpha channel; the alpha values may end up getting squared, which may lead to the saturation effects you observe.

---

### Post by Bulletbeast on 2009-06-09
Well, it's more like this. I have two modes of operation: one which draws billboards, little squares in 3D which face the viewer. In the other one, points marking the locations of galaxies are drawn in feedback mode. Those are XYZ points that are transformed to XY window coordinates. Then I leave feedback mode and, centered at the XY coordinates, I draw those images.

---

### Post by Victor Liu on 2009-06-09
So why not just draw the galaxy icon on the billboards in 3D in the first mode of operation? Is it that you want to be able to draw the same thing in two different ways? If, as you say, the only difference between the two modes is the projection matrix setup, then there should be no difference.

---

### Post by Bulletbeast on 2009-06-09
One mode has real photos of galaxies, which should scale with perspective, and the other - icons which should be fixed-size, 2D.

---

### Post by hessiess on 2009-06-09
You are probably calling:

```

glAlphaFunc ( GL_GREATER, 0.1 ) ;
glEnable ( GL_ALPHA_TEST ) ;

```

somewhere in your application, which causes alpha values more than 0.1 to be clipped to 1, resulting in no alpha blending. You also have to make sure that you draw alpha blended polygons from the back of the scene to the front.

---

### Post by Bulletbeast on 2009-06-09
I think I don't have this, unless I've pasted it from somewhere.. I'll try playing around with it, though. And when I'm drawing in 2D, with all my polygons having the same Z coordinate, what do I do?

---

### Post by Victor Liu on 2009-06-09
Do you want your polygons at different z-depths in 2D? (what would be the point?) From the code you pasted, your orthogonal projection will clip z-values to [-1,1], so you can specify a z-value in that range. To do so you would need glVertex3 instead of glVertex2 (which defaults the z coordinate to zero).

---

### Post by Bulletbeast on 2009-06-09
No, I don't want my 2D polygons at different z-depths.

---

### Post by soltanis on 2009-06-09
Oh the magic of three dimensions.

I am 99% sure that like someone above said, you need to be drawing from back to front.

---

### Post by Bulletbeast on 2009-06-10
I don't understand why, or, for that matter, how. The polygons that are textured incorrectly (as opposed to those drawn correctly) all have the same Z coordinate and don't overlap most of the time.

---

### Post by Victor Liu on 2009-06-10
What if you disable rendering of everything else, does it still look wrong? Is there a way for you to count the number of times each billboard is rendered per frame? Have you tried rendering them so that they face away from the camera? I'm not suggesting these things will necessarily help, but it would be interesting to see what happens.

---

### Post by Bulletbeast on 2009-06-10
Oh, I would try, surely. But some minor code change somewhere now makes my app crash when I enter that mode. Always, except when I run it through a debugger.

---

### Post by hessiess on 2009-06-10
> **Bulletbeast said:**
> Oh, I would try, surely. But some minor code change somewhere now makes my app crash when I enter that mode. Always, except when I run it through a debugger.

That would be annoying... This is one of the reasons why version control is so useful in software development ;).

When you do get it working again, you could try offsetting all your polygons by a small amount in the z acsiss so they are not on exactly the same plain.

You could also look at how Quad-Ren draws 2D objects, the alpha blending is working perfectly. The drawing code is located in the qr_renderer class in the draw() function, PNG loading is done in qr_load_png.cpp and qr_sprite.cpp.

---

### Post by Bulletbeast on 2009-06-10
I still don't understand the purpose behind drawing them in any specific order, when they don't even overlap... By the way, I have GL_BLEND enabled...

---

### Post by NielsBhor on 2009-06-10
Hmm....Sounds very complex for me. This has been pondering in my mind, why use openGL programming versus using basic modeling software like Blender to help you with manipulating the geometries, applying textures, etc...? If anyone the have time, I'd like to know why one would need to literally used openGL programming versus running a 3D App that does everything. Thanks in advance!

---

### Post by Bulletbeast on 2009-06-10
You use 3D modelling if you're using 3D models, and I'm not using any texturing more complex than mapping the four corners of an image to the four corners of a quad. You'd use OpenGL to render those models, anyway. And there's things that (a) can't be modelled, and (b) need to be calculated at run-time, such as the perpendiculars to the plane.

---

