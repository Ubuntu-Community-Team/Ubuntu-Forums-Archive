---
title: "Real-time mesh animation with openGL"
date: 2009-05-10
forum: Programming Talk
---

### Post by Ultra Magnus on 2009-05-10
Hi, I have a question about openGL.

I'm writing some software to display a visualisation in the form of a 3D mesh (the mesh has 440x440 verts). I have to display this in real time (ie atleast 25 FPS).

My problem is that when I use glVertexPointer and glDrawElements, I can only get around 16 frames per second. I can subsample it to 220x220 and get ~64 FPS but I'm obviously losing detail by doing this.

Does anyone know the fastest most efficient way of displaying a mesh like this using openGL? I'm afraid this is my first foray into graphics so I'm not quite sure how to proceed.

Thanks for your time.

James

---

### Post by CptPicard on 2009-05-10
Provided that there is no inefficiencies on your side of the code, would display lists be an option?

---

### Post by Neheb on 2009-05-10
I think vertex arrays are the second fastest technique for drawing with opengl, the fastest being vertex buffer objects.

---

### Post by Sockerdrickan on 2009-05-10
Yes, use VBO's.

---

### Post by Ultra Magnus on 2009-05-11
Hi thanks for the response, I'll have a look into VBOs. Jim

---

