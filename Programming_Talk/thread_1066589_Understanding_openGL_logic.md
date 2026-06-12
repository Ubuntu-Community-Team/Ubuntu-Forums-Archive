---
title: "Understanding openGL logic"
date: 2009-02-11
forum: Programming Talk
---

### Post by tneva82 on 2009-02-11
As I can now load and draw object(and rotate it and even animate it) from own 3d-object file it's time to look for what to do next. Figured camera might be good idea.

However I'm bit baffled by the openGL's logic(too used for ease-of-use darkGDK which wraps technical sides a lot :D). So if I have bunch of objects defined as vertexes around imaginary point 0,0,0. I also have X, Y and Z co-ordinates of where I want them to appear(plus angle it's supposed to be). In addition I have X, Y, Z and angles of where I want camera to be. Now how one goes around drawing scene so that I could move camera around, rotate it and at the same time moving and rotating objects independently?

What's the order I should be doing this? Set camera position, rotate camera, rotate object X, draw object X with vertex co-ordinates being x+difference_between_cameraX_and_objectPositionX with Y and Z similary calculated? Then rotate things for next object and draw it then? That's how I think I should do it but not quite sure.

Any help appreciated.

---

### Post by Gordon Bennett on 2009-02-11
Well, 3d objects and cameras all depend on multiplying the respective matrices together to give the final 'looking at' effect.

However, you can use gluLookAt to simplify the process for you.

---

### Post by Victor Liu on 2009-02-11
As per the OpenGL FAQ:

[http://www.opengl.org/resources/faq/technical/viewing.htm]("http://www.opengl.org/resources/faq/technical/viewing.htm")

There is no camera; that is simply an abstraction. OpenGL is only concerned with rendering primitives at certain specified locations, although the GLU library contains gluLookAt() which provides very basic camera functionality.

There are varying degrees of camera functionality that you may want. In the unlikely event that you simply want to render a static scene, then you would compute the 4x4 matrix transformation to take the "camera" from its default position/orientation at the origin to the target point, and then apply its inverse to all primitives that you're rendering. If you want to decompose this into translations and rotations, you would more naturally think of rotating the camera to its final direction, then translating it to the location you want it to be at. The inverse would be to first translate all your objects in the opposite direction and then apply the opposite rotation. You would do all this with a call to glTranslate() and glRotate() at the beginning of your scene rendering function. Alternatively you could just set the matrix directly:

```

glMatrixMode(GL_MODELVIEW);
glLoadIdentity();
glMultMatrixf(camera_transformation);

```

Most likely, you want to be able to drag the scene around and move about. For this, computing the translation and rotations manually will be far too tedious. Most people use Arcball rotations since the user experience is quite intuitive. The mathematics behind are handled with quaternions. Quaternions are simply convenient objects that can represent transformations that preserve vector length (you only want to move/rotate your camera basis vectors without scaling them). There are plenty of websites covering these topics.

Just starting out programming a camera model can be frustrating since very often you will see nothing on screen! I suggest you try playing with the translation and rotation functions by applying very small changes (like rotating by 1 degree or translating a small distance) to get a feel for what you are doing.

---

### Post by tneva82 on 2009-02-11
Hum hum. Still not quite sure I got it. However my original idea seems to be mostly working. Only problem is it messes up rotation of the object in question(center of rotation goes haywire. Basicly I move back and rather than turning in spot it becomes simulation of moon's orbit :D).

Ah well. Going to find some tutorials on the subject. Atleast I can move around and as long as I don't rotate the object I can move around it, sort of. Still bit of a buggy but atleast I'm getting somewhere.

---

### Post by tneva82 on 2009-02-11
Heureka! Got it working. Thank you Nehe Productions! THANK YOU!

Now I need to make damned sure I actually UNDERSTAND why it works :D And see if I can get object moving working as well as "camera" moving.

Edit: Screw that. Object moving NOT working. Still need to figure that one out then. The damn object goes satelite syndrom appeared when I put object moving around. Hum hum. But atleast camera moving is working.

Edit: Me hates openGL. Still no luck getting that stupid cube object moving(as in object moving, not camera moving) without screwing up rotations.

Edit: Oh my god. Did I actually succeed in this? Atleast it SEEMS to be working. Bizare thing is I could swear it's what it used to be but I'll look closer what I did that worked. I HAVE tried quite a bit of things.

Edit: Still not QUITE perfect. Found out that more than 1 object and second+ objects go satelite again. Found out solution(reset view and set up camera again) but that feels resource waste(ie FPS reducer). What should I try to do to remove that? Tried to reverse translations and rotations in reverse order but though I thought it should do it didn't do it afterall.

---

### Post by Gordon Bennett on 2009-02-11
OpenGL is pretty sweet.  You have to look at it from a hierarchical point of view - matrix operations affect the 'next' matrix operations.

Hence why in OpenGL, if you want your object unaffected by other matrix operations, the usual is this:


<other stuff with camera/objects>

glPushMatrix();    <--- This prevents the previous matrix from being nuked.

<your object gets rotated etc here>

glPopMatrix();    <--- Restores the matrix.

The reason why this is so is that it allows for hierarchical rotations - for example, the joints in an arm: with forearm rotating relative to the elbow (in which case both rotation operations would be in between the push/pop).

The push and pop matrix operations are there to preserve any matrices outside of the push/pop, which is how multiple objects preserve their parameters.

Edit:  Oh, and I just remembered to mention something that will help you understand OpenGL even more - it's a state-machine, meaning that values and parameters remain the same unless you change them (a bit like 'static' variables in C).

---

### Post by Wybiral on 2009-02-11
Be careful with the order you tranform things in. For instance, if you rotate, then translate, the rotation will affect the translation (its axis orientation).

---

### Post by tneva82 on 2009-02-11
> **Wybiral said:**
> Be careful with the order you tranform things in. For instance, if you rotate, then translate, the rotation will affect the translation (its axis orientation).

I think I got that one ;-) Good old trial by error :D

And speaking of which I learned out(again) something very valuable: ALWAYS ALWAYS ALWAYS initialise your goddamit variables! I turned code I had into class to wrap things around and make it's use more automatic. Goody good. Except it lost texture. Bummer! Oh well let's see if altering objects creation moment helps(had crazy theory). Hups! Now it started throwing bad_allocs.

Well some debugging later found out that polygoncount value in object creation was pretty crazy(something like -123052346 or something like that). No wonder it crashed! So I set it(and other variables) to zero and works(and texture appeared). Goddamit.

---

### Post by Johann von Gunten on 2009-02-11
> **tneva82 said:**
> I think I got that one ;-) Good old trial by error :D





Also the position of your objects centre makes the big difference in the rotation, you can rotate around the objects own axis or the world space axis.

Rotations around points other than the origin are not linear transformations.

If you don't expect to rotate around the world axis and want to rotate around the objects centre just translate the centre of the object to the origin first, rotate, and then translate back to the original spot.

It'll look something like this;

glTranslatef(pointOfRotationX, pointOfRotationY, 0);
glRotatef(angle, 0, 0, 1);
glTranslatef(-pointOfRotationX, -pointOfRotationY, 0);

---

### Post by tneva82 on 2009-02-11
More questions.

Assuming I have Object X which is created by subobjects which can have subobjects of their own. Let's say for example torso, upper arm, lower arm and hand. I could do something like this right if I want them all turn around so that the angle would be bit different for each of them(like torso turning right while pulling arm to his chest for example)?

rotatef(torso)
pushstack
rotatef(upperarm)
pushstack(lowerarm)
rotatef(hand)

In recursive loop 'till all the subchildrens have gone through popping stack when I return(so for example if hand would have fingers it would go push stack, rotatef(finger 1), pop stack, rotatef(finger 2), pop stack etc.

Would this basicly be how to model skeleton based animation? Or have I went somewhere very wrong(since I figured this on my head I very well could be very astray in the implementation theory).

---

### Post by tneva82 on 2009-02-12
No help here? Anyway yet another question about calculating normals for polygons. I think I have got the formula for calculating normal for plane with 3 vertex which is, I think:

normal->x = (a.y * b.z) - (a.z * b.y);
normal->y = (a.z * b.x) - (a.x * b.z);
normal->z = (a.x * b.y) - (a.y * b.x);

However haven't found anywhere suggestions how to approach 4-vertex planes which is how I have built my box. And I do assume I need to change normals when z co-ordinates of 4 vertex in box(out of 8 vertex total) changes in animation. Figuring out normals when they are in nice 90 degree angles is easy but animation has 19 frames where the 2 sides of box are somewhat tilted(front face and backface). Tried to first calculate them with above formulas but started to get funny results which is from it being 3 vertex formula rather than 4.

Then realised calculating them by hands is major pain so figured I better create function to do that automaticly.

Anyway anybody could point me toward good tutorial which would send me forward with this?

---

### Post by Gordon Bennett on 2009-02-12
> **tneva82 said:**
> More questions.

Assuming I have Object X which is created by subobjects which can have subobjects of their own. Let's say for example torso, upper arm, lower arm and hand. I could do something like this right if I want them all turn around so that the angle would be bit different for each of them(like torso turning right while pulling arm to his chest for example)?

rotatef(torso)
pushstack
rotatef(upperarm)
pushstack(lowerarm)
rotatef(hand)

In recursive loop 'till all the subchildrens have gone through popping stack when I return(so for example if hand would have fingers it would go push stack, rotatef(finger 1), pop stack, rotatef(finger 2), pop stack etc.

Would this basicly be how to model skeleton based animation? Or have I went somewhere very wrong(since I figured this on my head I very well could be very astray in the implementation theory).

It's best if you visualise your skeleton as lines on a piece of paper.  E.g. 3 lines, arm, forearm, hand.
Or even stretch out your arm and wave your hand up and down - you'll notice that it has its own (local) rotation about the axis where it links to the forearm.  Then, add to that the rotation of your forearm, which has its own local rotation and so on...

---

### Post by Gordon Bennett on 2009-02-12
> **tneva82 said:**
> No help here? Anyway yet another question about calculating normals for polygons. I think I have got the formula for calculating normal for plane with 3 vertex which is, I think:

normal->x = (a.y * b.z) - (a.z * b.y);
normal->y = (a.z * b.x) - (a.x * b.z);
normal->z = (a.x * b.y) - (a.y * b.x);

However haven't found anywhere suggestions how to approach 4-vertex planes which is how I have built my box. And I do assume I need to change normals when z co-ordinates of 4 vertex in box(out of 8 vertex total) changes in animation. Figuring out normals when they are in nice 90 degree angles is easy but animation has 19 frames where the 2 sides of box are somewhat tilted(front face and backface). Tried to first calculate them with above formulas but started to get funny results which is from it being 3 vertex formula rather than 4.

Then realised calculating them by hands is major pain so figured I better create function to do that automaticly.

Anyway anybody could point me toward good tutorial which would send me forward with this?

First of all, I suggest you stay off using 4-vertex polygons/planes - they don't play nicely with deformation operations and the plane equation for a 4-point plane will become invalid if any of the points defining that plane is deformed away from the plane :P

With 3-vertex planes it is impossible to invalidate the plane equation by their very geometric nature.

Also, if you are using the formula to determine front or back face culling you can use OpenGL's own accelerated routines for that.

P.S.  The formula you pasted is correct - you will be needing that if you delve into lighting...

---

### Post by tneva82 on 2009-02-12
> **Gordon Bennett said:**
> It's best if you visualise your skeleton as lines on a piece of paper.  E.g. 3 lines, arm, forearm, hand.
Or even stretch out your arm and wave your hand up and down - you'll notice that it has its own (local) rotation about the axis where it links to the forearm.  Then, add to that the rotation of your forearm, which has its own local rotation and so on...

So my basic idea was totally off?

And lightning solved and yes I moved to 3-vertex models though how I ensure blender creates them is another thing(assuming I can figure out how to use blender files :D If not whole process is pretty moot as I wont' be able to get any half-complex models anyway ;-).

---

### Post by Gordon Bennett on 2009-02-12
> **tneva82 said:**
> So my basic idea was totally off?

And lightning solved and yes I moved to 3-vertex models though how I ensure blender creates them is another thing(assuming I can figure out how to use blender files :D If not whole process is pretty moot as I wont' be able to get any half-complex models anyway ;-).

Don't worry if your initial idea was a bit off, it takes practice to get the hang of the process.  Start off simple (two objects linked to each other for skeletal animation for example), then build upon what you have discovered.

Almost every 3d program outputs in 3-vertex polygon format.  Some file formats are a pain to work with, others not so :)

One that is used a lot (and it is human readable) is Wavefront .OBJ - Blender exports it - you need to make sure you choose the option to decompose quads into triangles :)

There are also libraries that will import various well-known binary formats for you.

Not that some formats use left or right-handed coordinate systems - if you find that your polygons aren't being displayed after backface culling, then you need to reverse the coordinate system of the imported data.

---

### Post by tneva82 on 2009-02-12
Thanks for the OBJ tip. I'll look into that. Would be blessing to be able to use blender to design models rather than by hands ;-) Cube I can work with. Trying to create spaceship by hand would be tricky!

And I'll also try to work with that skeleton thing though requires reworking engine a bit but that's something I would be interested to get my hands on.

Edit: Blooty hell! That OBJ is very, very, VERY similar to what my fileformat is :D Bit of differences but shouldn't be impossible to create converter ;-)

Edit: Why the Blender doesn't export anything of semblance to UV data? I have added texture, it even shows in rendering but no UV data in obj file...

Here's quick cube in OBJ:

# Blender3D v246 OBJ File: 
# [www.blender3d.org](www.blender3d.org)
mtllib test.mtl
o Cube
v 1.000000 -1.000000 -1.000000
v 1.000000 -1.000000 1.000000
v -1.000000 -1.000000 1.000000
v -1.000000 -1.000000 -1.000000
v 1.000000 1.000000 -1.000000
v 0.999999 1.000000 1.000001
v -1.000000 1.000000 1.000000
v -1.000000 1.000000 -1.000000
usemtl Material
s off
f 5 1 8
f 1 4 8
f 3 7 8
f 3 8 4
f 2 6 3
f 6 7 3
f 1 5 2
f 5 6 2
f 5 8 7
f 5 7 6
f 1 2 3
f 1 3 4

And here's my cube(without animation data):

#front face 
p 3 0 3 1 0.0 0.0 1.0 0.0 0.0 1.0
p 3 3 2 1 1.0 0.0 1.0 1.0 0.0 1.0
#bottom face
p 3 4 7 3 0.0 0.0 1.0 0.0 1.0 1.0
p 3 3 0 4 1.0 1.0 0.0 1.0 0.0 0.0
#left face
p 3 4 0 1 0.0 0.0 1.0 0.0 1.0 1.0
p 3 1 5 4 1.0 1.0 0.0 1.0 0.0 0.0
# top face
p 3 1 2 6 0.0 0.0 1.0 0.0 1.0 1.0
p 3 6 5 1 1.0 1.0 0.0 1.0 0.0 0.0
# right face
p 3 3 7 6 0.0 0.0 1.0 0.0 1.0 1.0
p 3 6 2 3 1.0 1.0 0.0 1.0 0.0 0.0
# rear face
p 3 7 4 5 0.0 0.0 1.0 0.0 1.0 1.0
p 3 5 6 7 1.0 1.0 0.0 1.0 0.0 0.0
f
# Front-Bottom-Left
v -1.00000000 -1.00000000 1.00000000
#Front-Top-Left
v -1.00000000 1.00000000 1.00000000
#Front-Top-Right
v 1.00000000 1.00000000 1.00000000
#Front-Bottom-Right
v 1.00000000 -1.00000000 1.00000000
#Rear-Bottom-Left
v -1.00000000 -1.00000000 -1.00000000
#Rear-Top-Left
v -1.00000000 1.00000000 -1.00000000
#Rear-Top-Right
v 1.00000000 1.00000000 -1.00000000
#Rear-Bottom-Right
v 1.00000000 -1.00000000 -1.00000000

As can be seen...VERY similar. Groovy. (and if you wonder what's the extra numbers after vertexes. Those would be UV numbers).

---

### Post by Gordon Bennett on 2009-02-12
> **tneva82 said:**
> 
Edit: Why the Blender doesn't export anything of semblance to UV data? I have added texture, it even shows in rendering but no UV data in obj file...


Some formats do not include UV data as that can be inferred/calculated at run-time from vertex data (saves on disk space too :P).

---

### Post by tneva82 on 2009-02-12
> **Gordon Bennett said:**
> Some formats do not include UV data as that can be inferred/calculated at run-time from vertex data (saves on disk space too :P).

There's method to calculate UV data run-time? Anywhere good tutorial on how to do that?

Edit: Haa! I think I found a way to get UV data to the OBJ file. Huzah!

Now I need to create .OBJ reader but that shouldn't be too hard.

---

