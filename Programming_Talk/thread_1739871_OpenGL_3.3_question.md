---
title: "OpenGL 3.3 question"
date: 2011-04-26
forum: Programming Talk
---

### Post by t1497f35 on 2011-04-26
Hi,
I don't understand the attached example (from SuperBible5).
The uniform:
uniform samplerCube cubeMap
is never set to anything (the uniform from SkyBox_f.cpp, not from Reflection_f.cpp), yet the whole example works fine.

Anyone knows why it works fine despite never being set to anything?

The whole example is attached and it compiles & runs if you got GL3.3 & freeglut3-dev installed.

The 4 tga.zip files to be extracted to the dir with the Makefile which is at sample/Linux/Chapter07/MultiTexture.

---

### Post by Ferrat on 2011-04-26
It's the same in both, it's a uniform ident that are the same in both shaders, there for both shaders use the same data and it's already been used in Reflection so SkyBox just use the exact same, it's linked when the shader is compiled as both names and definitions are the exact same. 
I'm just learning shaders myself but at least that's what I think. 

So even if you had even more shaders using 
uniform samplerCube cubeMap
as long as they got compiled together with Reflection that variable is linked and works. 

You should double check your book and online and with others but I believe this is why it doesn't need to be explicitly set to anything, because it already is.

---

### Post by t1497f35 on 2011-04-26
Thanks a lot, what book (about shaders) are you learning from if not a secret?

---

### Post by Ferrat on 2011-04-26
Haha no it's not a secret, it's multiple books 
read so far 
Beginning OpenGL Game programming ,2nd Ed. : shows only basics about shaders
Addison Wesley OpenGL ES 2.0 Programming Guide : this one is really good at explaining shaders as ES 2.0 only uses a programmable pipeline

and just started reading 
OpenGL Shading Language 2nd Ed(Orange.Book)

Those are the books most bound to OpenGL and shaders :)

---

### Post by t1497f35 on 2011-04-26
Thanks a lot,
I also wanted to read the ES 2.0 programming guide since I read many people praising it, but I'm not sure whether to read it since I'm afraid I won't be able to test "GL ES 2.0" examples (if any) since the Nvidia binary driver probably doesn't ship with ES 2.0 support. I'm using GeForce 9600 gt.

---

### Post by Ferrat on 2011-04-26
There are emulators for ES 2.0 but you can do 90% of it at least in normal OpenGL without any changes afaik, ES is more or less just a streamline version of OpenGL, shaders and stuff works just the same except ES has a few more restrictions on how many variables of different types uniform in out etc a shader can use :)

---

### Post by t1497f35 on 2011-04-26
Thank you!

---

