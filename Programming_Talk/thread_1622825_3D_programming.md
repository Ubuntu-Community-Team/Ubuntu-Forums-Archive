---
title: "3D programming"
date: 2010-11-15
forum: Programming Talk
---

### Post by denarced on 2010-11-15
3D is coming, it's already in the movies and pretty soon we'll have widespread use of monitors that support 3D.
But how about programming applications that support 3D ?
Maybe some educational programs for math or physics, or something..
Can you give me examples of some existing tools, libraries ? Possibly there are even open source ones?
Tutorials or anything really, I'm trying to get to know the state of the art right now.

All input is welcome.

---

### Post by s3MA00RRNY on 2010-11-16
Two 3D animation softwares that come to mind are Maya and Blender. Blender is FLOSS, Maya is not.

Pixar uses Renderman to render all of their movies. It is also not free (duh) and costs somewhere in the thousands.

As far as libraries, there is OpenGL and DirectX. DirectX is Microsoft's proprietary library. OpenGL is an open standard.

---

### Post by denarced on 2010-11-16
> **pcdude2143 said:**
> Two 3D animation softwares that come to mind are Maya and Blender. Blender is FLOSS, Maya is not.

Pixar uses Renderman to render all of their movies. It is also not free (duh) and costs somewhere in the thousands.

As far as libraries, there is OpenGL and DirectX. DirectX is Microsoft's proprietary library. OpenGL is an open standard.

Those are traditional 3D rendering softwares, meaning not really 3D but sort of. I'm sure someone knows the right words for the difference :D.
Or maybe you're saying there is no difference for the programmer ?
Whether you're making traditional 3D or the legit kind for the new 3D monitors, it doesn't matter for the programmer ??

---

### Post by KoRnholio on 2010-11-16
It sounds like you're referring to stereoscopic rendering. Yes, the programmer does have to program specifically for that. I've never done it, but here's a thread with two links that should further explain it...
[http://forums.epicgames.com/showthread.php?t=717107](http://forums.epicgames.com/showthread.php?t=717107)

---

### Post by unknownPoster on 2010-11-16
> **denarced said:**
> 3D is coming, it's already in the movies and pretty soon we'll have widespread use of monitors that support 3D.


Doubtful at best. 3D desktops have been tried before and failed so miserably that most people don't remember them.

Regardless, as for your question, there are quite a few research projects going on at my University in which full scale 3D simulations, most notably a hospital, are being created using Unity: [http://unity3d.com/](http://unity3d.com/)

---

### Post by denarced on 2010-11-16
> **unknownPoster said:**
> Doubtful at best. 3D desktops have been tried before and failed so miserably that most people don't remember them.

Regardless, as for your question, there are quite a few research projects going on at my University in which full scale 3D simulations, most notably a hospital, are being created using Unity: [http://unity3d.com/](http://unity3d.com/)

So unity supports stereoscopic rendering ?
And yes, they have failed. Miserably.
But how's this: it's included in standard monitors as an extra feature which in time will become a standard feature which does not hinder it's normal features in a significant way. Thus in time people will have the means to use stereoscopic 3D software if they so choose. I think that would lead to 3D having it's own slice of the software market. Maybe not that big but still significant. Something like 5%, maybe. Plausible ??

---

### Post by NovaAesa on 2010-11-16
Anaglpyhs can easily be done in OpenGL using the accumulation buffer. I would hazard a guess that it would be easy in DirectX as well. If you wanted 3D with polarized light... I would have no idea how to do that with OpenGL.

---

