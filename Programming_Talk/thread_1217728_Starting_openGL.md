---
title: "Starting openGL"
date: 2009-07-19
forum: Programming Talk
---

### Post by C++buntu on 2009-07-19
Hi everyone,

I want to start using openGL for some graphics programming with C++ but i have no clue of what i need to download in order to be ready.
I have a NVIDIA Quadro NVS 120M with 512 Megs. I don't even know if my video card can support this API...Do i need to download the NVIDIA specific openGL kit or some other?

Thanks for advice

---

### Post by efikkan on 2009-07-19
Your gpu seems to be OpenGL 2.x/DirectX 9.0c/Shader Model 3 -class (comparable to the GeForce 7xxx-series), after a quick search. It would certainly support hardware acceleration of OpenGL if you got the proper drivers (I recommend the proprietary nVidia-drivers if you run GNU/Linux). This is not a high-end graphics card, but it will perform ok for testing purposes. 


I suggest you follow NeHe's OpenGL tutorials for learning OpenGL basics: [http://nehe.gamedev.net/](http://nehe.gamedev.net/)
These tutorials cover the basics of OpenGL and more, but not a lot of shading.

You'll quickly notice there are different ways of setting up a window with an OpenGL rendering context. You could do it the hard way (doing calls to xorg or win32, etc.) or use a library like SDL or GLUT, both platform independent. Since GLUT is both outdated, restricted and buggy, I would strongly recommend SDL for those learning OpenGL, since GLUT is unusable in most cases, and writing your own loader requires som experience. Choose SDL for now. A lot of tutorials tends to use GLUT or their own implementation. (I prefer my own implementation, but I like to do things my own way :) )


Both nVidia and AMD/ATI got OpenGL SDK with demos and documentation. In addition, nVidia got cg shading, their own shading language, wich can be converted to both GLSL and HLSL. (since AMD/ATI don't support cg) Both nVidia and AMD/ATI got tools for designing shaders. Most demos will run on both nVidia and ATI cards, except demos using cg and/or special extensions. A new driver might help.


Notice: this post is written in the middle of the night, so it might contain serious spelling errors. :)


Wich compiler do you use?

---

### Post by C++buntu on 2009-07-19
> **efikkan said:**
> Your gpu seems to be OpenGL 2.x/DirectX 9.0c/Shader Model 3 -class (comparable to the GeForce 7xxx-series), after a quick search. It would certainly support hardware acceleration of OpenGL if you got the proper drivers (I recommend the proprietary nVidia-drivers if you run GNU/Linux). This is not a high-end graphics card, but it will perform ok for testing purposes. 


I suggest you follow NeHe's OpenGL tutorials for learning OpenGL basics: [http://nehe.gamedev.net/](http://nehe.gamedev.net/)
These tutorials cover the basics of OpenGL and more, but not a lot of shading.

You'll quickly notice there are different ways of setting up a window with an OpenGL rendering context. You could do it the hard way (doing calls to xorg or win32, etc.) or use a library like SDL or GLUT, both platform independent. Since GLUT is both outdated, restricted and buggy, I would strongly recommend SDL for those learning OpenGL, since GLUT is unusable in most cases, and writing your own loader requires som experience. Choose SDL for now. A lot of tutorials tends to use GLUT or their own implementation. (I prefer my own implementation, but I like to do things my own way :) )


Both nVidia and AMD/ATI got OpenGL SDK with demos and documentation. In addition, nVidia got cg shading, their own shading language, wich can be converted to both GLSL and HLSL. (since AMD/ATI don't support cg) Both nVidia and AMD/ATI got tools for designing shaders. Most demos will run on both nVidia and ATI cards, except demos using cg and/or special extensions. A new driver might help.


Notice: this post is written in the middle of the night, so it might contain serious spelling errors. :)


Wich compiler do you use?

I'm using g++ on Linux but i would try openGL on Windows too, perhaps with Microsoft Visual Studio 2008 if i can...

If i download the latest openGL kit from NVIDIA, will my video card be ok or i should use the 2.x versions?

Thanks for your advice!

---

### Post by abhilashm86 on 2009-07-20
for opengl, u need to install freeglut libraries, type following in terminal,

```
sudo apt-get install freeglut3 freeglut3-dev
```

then,
use g++ compiler......

```
g++ -lGL -lglut test1.cpp -o test1
```

__________________

---

### Post by Sockerdrickan on 2009-07-20
Actually
```

g++ test1.cpp -o test1 -lGL -lglut

```makes more sense to me :P

---

### Post by nrs on 2009-07-20
> **abhilashm86 said:**
> for opengl, u need to install freeglut libraries, type following in terminal,

```
sudo apt-get install freeglut3 freeglut3-dev
```then,
use g++ compiler......

```
g++ -lGL -lglut test1.cpp -o test1
```__________________
Incorrect. He only needs to install the freeglut libraries if he intends to use freeglut. Your video driver will provide the library, libglu1-mesa-dev will provide all relevant headers.

build-essential if you don't already have it. 
Proprietary nVidia driver.
libglu1-mesa-dev. 

that's it.

---

### Post by C++buntu on 2009-07-20
A big thanks for all of us! It's good to know that there are helping people in the Linux community!

---

### Post by Sockerdrickan on 2009-07-20
> **nrs said:**
> Incorrect. He only needs to install the freeglut libraries if he intends to use freeglut. Your video driver will provide the library, libglu1-mesa-dev will provide all relevant headers.

build-essential if you don't already have it. 
Proprietary nVidia driver.
libglu1-mesa-dev. 

that's it.
The proprietary nvidia driver brings headers.

---

### Post by efikkan on 2009-07-20
> **C++buntu said:**
> If i download the latest openGL kit from NVIDIA, will my video card be ok or i should use the 2.x versions?

Thanks for your advice!

The latest SDK is [nVidia  OpenGL SDK 10.5]("http://developer.download.nvidia.com/SDK/10.5/opengl/samples.html").
As you can see, some of these demos require GeForce 8 (wich is OpenGL 3.x/DirectX 10.x class), but none of these demos require OpenGL 3.x, but some might require extensions wich your gpu does not support. Just test it out, some might work. If not, you'll get an error message displaying wich extensions your gpu lacks support for.

Check out the [9.5 SDK as well]("http://developer.download.nvidia.com/SDK/9.5/Samples/samples.html"), and the cool [nature scene demo]("http://developer.nvidia.com/object/nature_scene.html")

---

### Post by nrs on 2009-07-20
> **Tux0r said:**
> The proprietary nvidia driver brings headers.
Heh. You have to install nvidia-glx-WHICHEVERVERSION-dev separately. I knew the proper came with headers, always assumed Ubuntu just went with MESA's. Well, I'm wrong too then. Though you still can use MESA's. I doubt most people would notice unless using a lot of proprietary extensions.

---

### Post by abhilashm86 on 2009-07-20
> **nrs said:**
> Incorrect. He only needs to install the freeglut libraries if he intends to use freeglut. Your video driver will provide the library, libglu1-mesa-dev will provide all relevant headers.

build-essential if you don't already have it. 
Proprietary nVidia driver.
libglu1-mesa-dev. 

that's it.

we need not install drivers, if NVIDIA, my computer just asked about installing driver, i made it, note that this video drivers wont provide headers in default, we need to install.........

---

### Post by Sockerdrickan on 2009-07-21
> **nrs said:**
> Heh. You have to install nvidia-glx-WHICHEVERVERSION-dev separately. I knew the proper came with headers, always assumed Ubuntu just went with MESA's. Well, I'm wrong too then. Though you still can use MESA's. I doubt most people would notice unless using a lot of proprietary extensions.
I use OpenGL 3.1 so I have to fetch this either way [http://www.opengl.org/registry/api/gl3.h](http://www.opengl.org/registry/api/gl3.h) :popcorn:

---

