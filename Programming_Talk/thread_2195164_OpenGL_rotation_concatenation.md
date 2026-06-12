---
title: "OpenGL rotation concatenation"
date: 2013-12-22
forum: Programming Talk
---

### Post by kangaba on 2013-12-22
Hi,
I got an IcoSphere at the center of the canvas, it rotates "down" (-Y) when dragging with the mouse down, "up" when dragging up, and left and right respectively -X and X.
Soon after playing with it (dragging in random directions) it starts rotating in the opposite direction ("up" when I drag it "down") it's supposed to.

Any idea what this issue is called or how to fix it?

I'm using 4x4 matrices for X and Y rotations which I multiply into the final rotation:

```

    about_x += mgl::Rad() * state_->mouse_motion()->delta_y * kAccel;
    about_y += mgl::Rad() * state_->mouse_motion()->delta_x * kAccel;
    
    mat_mv.i(); // i() = set to identity
    mat_rot.i();
    mat_rot.rot_y(about_y); // Rotation about Y
    mat_mv *= mat_rot;
    
    mat_rot.i();
    mat_rot.rot_x(about_x); // Rotation about X
    mat_mv *= mat_rot; // concatenate both rotations
    
    mat_mv3 = mat_mv.to_mat3();

    mat_transl.transl(0.0f, 0.0f, frame->zn - 12.0f);
    mat_mv *= mat_transl;
    
    mat_mvp = frame->mat_persp * mat_mv;
   // send "map_mvp" to the shader

```

---

### Post by DaviesX on 2013-12-25
May I ask what is the Rad function in your code?

---

### Post by kangaba on 2013-12-25
It returns a number which when multiplied by degrees yields radians.
```

inline float
Rad() { return mgl::kPi / 180.0f; }

```

It looks like making an object rotate only vertically and horizontally no matter how much rotated it already is - is a difficult task.

---

### Post by DaviesX on 2013-12-27
how about 
state_->mouse_motion()->delta_y ?

I guess if delta_y is the distance a mouse moved, then it should be radian already.

---

### Post by kangaba on 2013-12-28
The movement is in points (Qt5 mouse move event) so treating them  directly as radians would yield too quick rotations, but the speed of  rotation isn't the problem.
The problem is about the direction of the  rotation. For example, in Google Earth the Earth is rotated  vertically/horizontally (about the x/y axes) compared to you (the  viewer), but my code rotates the object vertically/horizontally compared  it its own objects space (which is to be expected), that's why in my  code after rotating the object about some of its x/y axis the rotations  don't correspond any longer to the x/y axes of the world  (user/watcher/me) view.


Here's a youtube demonstration, first 3 mouse drags rotate the object properly (around viewer's X/Y axes).
[http://www.youtube.com/watch?v=cPYqOgLP4Vc]("http://www.youtube.com/watch?v=cPYqOgLP4Vc&feature=youtu.be")

---

