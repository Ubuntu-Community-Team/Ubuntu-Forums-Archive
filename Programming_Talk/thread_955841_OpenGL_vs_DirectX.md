---
title: "OpenGL vs DirectX"
date: 2008-10-22
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-22
So I was just wondering, is OpenGL better than DirectX? 
Which can do the best graphics?

I tried google, and found this image:
[http://i35.photobucket.com/albums/d198/mike4realz/4lzugkk.jpg]("http://i35.photobucket.com/albums/d198/mike4realz/4lzugkk.jpg")

OpenGL's and DirectX's graphics look pretty equal for me.

---

### Post by jespdj on 2008-10-22
Most games are written for Windows using DirectX. Because of Microsoft's dominance, graphics card vendors usually put priority on supporting DirectX over supporting OpenGL. As far as I know DirectX supports more features than OpenGL, but the difference is really in the details.

---

### Post by snova on 2008-10-22
Choice of API has nothing to do with the results produced. A skilled programmer can do the same thing with each. They are merely different ways to accomplish accelerated graphics.

DirectX encompasses more than graphics, however. It also includes many other sub-libraries. OpenGL is more specific to its purpose- graphics.

Stay away from DirectX, though. It will never work on anything but Windows. OpenGL is an open standard in comparison.

I also think OpenGL is easier to use.

---

### Post by rnodal on 2008-10-22
Another thing about OpenGL is the fact that is a state machine so it very easy to create novel things with it :). If you are starting in graphics programing I would recommend  learning OpenGL first.

-r

---

### Post by snova on 2008-10-22
The fact that OpenGL is stateful is the reason I mentioned that I thought it was easy to use.

For example, drawing some triangles would comprise the following steps:

[LIST]
    [*] Tell OpenGL to begin drawing a triangle via "glBegin( GL_TRIANGLES )".
    [*] Give OpenGL the vertexes of the triangles you want to draw with "glVertex2f( Xpos, Ypos )". Repeat that call three times for each triangle.
    [*] Finish with "glEnd()".
[/LIST]

Lines work the same way. Just specify GL_LINES instead of GL_TRIANGLES and give it coordinates in groups of two instead of three. And so on.

When you want to move up into 3D, just replace calls of "glVertex2f( X, Y )" with "glVertex**3**f( X, Y**, Z** )".

It gets a lot more complicated, but OpenGL is quite pleasant to work with.

---

### Post by slavik on 2008-10-22
OpenGL and DirectX are different things. DirectX is not only a graphics library (Direct3D) but it is also a multimedia framework (DirectShow) and a Sound framework (not sure of the name, DirectSound?) and also an input framework (DirectInput).

To get a similar thing in Linux, you'd need OpenGL, ALSA, gstreamer and SDL.

as far as OpenGL and Direct3D, they are not very different as far as capabilities (Doom3 uses OpenGL).

OpenGL3 is supposed to be OO (I haven't looked at it), not a state machine like OGL <= 2.x.

From everyone that I know that has tried to learn both at the same time, they found OpenGL to be easier.

OpenGL also runs on many different platforms which is a kicker if you want to dosome GPGPU using pixel shaders.

---

### Post by kernelhaxor on 2008-10-22
I have heard DirectX is a much richer than OpenGL though OpenGL can do awesome stuff too .. DirectX is more widely used because of the widespread Windows platform ..

---

### Post by Ferrat on 2008-10-22
> **kernelhaxor said:**
> I have heard DirectX is a much richer than OpenGL though OpenGL can do awesome stuff too .. DirectX is more widely used because of the widespread Windows platform ..

Well for games DX3D is more widely used but over all OpenGL is the most common one, also DX being richer that's where I would think people compare OpenGL (a graphic API) to DirectX (which includes a Graphic API but also as stated above, sound API, input API, network API etc and a specialized development environment where you can more or less just drag and drop modules).

---

### Post by snova on 2008-10-22
DirectX is not a library by itself, but a collection of libraries comprising things from 3D graphics to input (including joysticks) to networking. OpenGL is *only* a graphics library. A direct comparison of the two is nonsensical, as they have essentially different purposes.

Either of the two can be used to produce beautiful 3D graphics. The biggest difference in my eyes is that DirectX is limited to Windows, whereas OpenGL will run on most any platform with 3D acceleration.

---

### Post by Shea7993 on 2009-07-19
Ive always seen openGL to look beter than DirectX... However thats back when DX6 and 7 was out, lol however, I have hope, we all should have hope and support OpenGL and devs working on it, support is whats going to reflect a positive future for gaming on OGL in the near future

---

### Post by C++buntu on 2009-07-19
> **kernelhaxor said:**
> I have heard DirectX is a much richer than OpenGL though OpenGL can do awesome stuff too .. DirectX is more widely used because of the widespread Windows platform ..

And if you want to be a game programmer, you should learn DirectX, because the vast majority of games are for Windows...

---

### Post by efikkan on 2009-07-19
> **C++buntu said:**
> And if you want to be a game programmer, you should learn DirectX, because the vast majority of games are for Windows... No, the best would be to learn OpenGL, since it's used in Windows, GNU/Linux, Mac OS X and more, and consoles like PlayStation 3(OpenGL ES + cg shaders) and Wii. DirectX is only supported by Windows and Xbox, and DirectX 10+ is only supported by Vista and upcoming windows versions. OpenGL would make the game available to larger markets.

Like someone mentioned, OpenGL is comparable to Direct3D, not the whole DirectX package. As of version 3.1, OpenGL is fully competable with Direct3D. OpenGL and Direct3D basically supports the same features, but implements these features in different ways. But both HLSL and GLSL are very similar, and shaders can be converted. Both AMD/ATI and nVidia add new OpenGL features in almost every new major driver release.

OpenGL is quite widely used. A lot of the most advanced game engines supports OpenGL, and uses it on PlayStation 3, as well as other platforms.

In addition to OpenGL, you got libraries like SDL, OpenAL, OpenCL etc. to use.

---

### Post by khelben1979 on 2009-07-19
I wonder if the graphics card needs to work harder to produce Direct 3D graphics than OpenGL. Any comments on this?

In the future I'm hoping to be able to play World of Warcraft on my Linux system for the first time. Haven't done this yet.

---

### Post by Can+~ on 2009-07-19
> **khelben1979 said:**
> In the future I'm hoping to be able to play World of Warcraft on my Linux system for the first time. Haven't done this yet.

Runs pretty good on Wine, even with my Lame ATI card it does run fine.

---

### Post by efikkan on 2009-07-19
> **khelben1979 said:**
> I wonder if the graphics card needs to work harder to produce Direct 3D graphics than OpenGL. Any comments on this? In my experience nVidia tends to get a little higher OpenGL performance, and sometimes AMD/ATI get higher Direct3D-performance. But these are minor differences, just a few percent.

What's far more important is optimizing the rendering, reducing the amount of calls etc. This affects both APIs.

> **khelben1979 said:**
> 
In the future I'm hoping to be able to play World of Warcraft on my Linux system for the first time. Haven't done this yet. All the games from Blizzard supports OpenGL rendering. You can choose this and get full performance on GNU/Linux.:)

---

### Post by C++buntu on 2009-07-19
> **efikkan said:**
> No, the best would be to learn OpenGL, since it's used in Windows, GNU/Linux, Mac OS X and more, and consoles like PlayStation 3(OpenGL ES + cg shaders) and Wii. DirectX is only supported by Windows and Xbox, and DirectX 10+ is only supported by Vista and upcoming windows versions. OpenGL would make the game available to larger markets.

Like someone mentioned, OpenGL is comparable to Direct3D, not the whole DirectX package. As of version 3.1, OpenGL is fully competable with Direct3D. OpenGL and Direct3D basically supports the same features, but implements these features in different ways. But both HLSL and GLSL are very similar, and shaders can be converted. Both AMD/ATI and nVidia add new OpenGL features in almost every new major driver release.

OpenGL is quite widely used. A lot of the most advanced game engines supports OpenGL, and uses it on PlayStation 3, as well as other platforms.

In addition to OpenGL, you got libraries like SDL, OpenAL, OpenCL etc. to use.

Arghh, i think you're right...

---

### Post by khelben1979 on 2009-07-20
I wonder if the latest generation of graphic cards fully utilize all the power which comes from the latest version of OpenGL. Any comments on this?

In the Windows world it feels that all they are talking about is Direct X when it comes to graphics. I'm not as sure as the previous posters if even the latest version of OpenGL really can compete, I'm looking for facts not assumptions. Any sources?

---

### Post by Sockerdrickan on 2009-07-20
> **khelben1979 said:**
> I wonder if the latest generation of graphic cards fully utilize all the power which comes from the latest version of OpenGL. Any comments on this?
core OpenGL 3.1 you could say is based on what GeForce 8 series can do
So no, not without extensions

---

