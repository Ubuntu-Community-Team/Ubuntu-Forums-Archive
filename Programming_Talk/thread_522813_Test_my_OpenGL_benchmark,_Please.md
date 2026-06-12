---
title: "Test my OpenGL benchmark, Please"
date: 2007-08-11
forum: Programming Talk
---

### Post by bsmith on 2007-08-11
Hi all,
  I've not been able to find a decent 3D benchmark thing for Linux, I was looking for something like 3DMark, and the best I could find needed Doom3 to be installed. Anyway I was playing today trying to make my own, so far it sucks, but I was interested to know what sort of frames you other guys get and your hardware.

The scene that tests your computer sucks big time, I don't know how I did it, but there are some dancing, texture mapped, lit crates on your screen, and all of the code is based on nehe's.

Oh, I have a X1600XT, but it is only running in software and I'm getting about 1200fps at 800x600x24

To compile you will need the development library's for SDL and OpenGL, then just extract the tarball, and type make.

Thanks for any comments, and don't be too critical of my code, its normally much better :)

EDIT:
I have just created a sourceforge project for the new glmark.

[https://sourceforge.net/projects/glmark/]("https://sourceforge.net/projects/glmark/")

The download should be up. :)

---

### Post by apetresc on 2007-08-11
Nice! It compiled and ran great for me after I installed the needed libraries:
```
adrian@rootbeer:~/glmark$ ./glmark

We have a software surface
Our screen mode is 800x600x24

Evaluation:
        Total time:     10.545000 seconds
        Total frames:   10000
        Average fps:    948.316711

```
Moreover, I've been wanting to learn the basics of graphics programming for a few months. It looks like your code is fairly neat and readable, and what's more important (for me, anyway), the build environment is laid out nicely.

So thanks!

---

### Post by bsmith on 2007-08-11
Great to be of help, I don't know how neat my code is, but I'll take your word for it. Most of the window initialization is from nehe.gamedev.net.

What I need now is for some good looking scenes that use a few fancy effects to really test out our machines.

The idea is for the program to run through a few different scenes, all testing different OpenGL extensions, and somehow compute a single rating of your system.

---

### Post by avik on 2007-08-11
Running at the same time as Compiz Fusion, with some music playing in the background, OpenOffice.org running, etc.  I'm sure I get better frame rates than this, since I'm using an AMD64 dual core computer with an NVIDIA GeForce 6150SE.  I'll test it again tomorrow when I boot up for the first time.

```

$ ./glmark 

We have a software surface
Our screen mode is 800x600x24

Evaluation:
        Total time:     25.814001 seconds
        Total frames:   10000
        Average fps:    387.386688

```

EDIT: By the way, here's a one-liner that replaces your Makefile:

```
gcc *.c -o glmark -lGL -lGLU -lSDL
```

No temporary .o files, and it's all in one line/step.  Just so you know.

EDIT 2: Here's the results without Compiz Fusion running, etc.

```

$ ./glmark 

We have a software surface
Our screen mode is 800x600x24

Evaluation:
        Total time:     19.923000 seconds
        Total frames:   10000
        Average fps:    501.932434

```

Still not as good as I'd hoped.  But I can run Compiz Fusion just fine, as well as run Enemy Territory and o ther FPS games without any problem.  I know I have the NVIDIA driver (nvidia-glx-new) installed, enabled, and running.  And yes, direct rendering is enabled.  Strange.

Great test, though.  I like the effect.

---

### Post by kostkon on 2007-08-11
> **bsmith said:**
> Hi all,
  I've not been able to find a decent 3D benchmark thing for Linux, I was looking for something like 3DMark, and the best I could find needed Doom3 to be installed. Anyway I was playing today trying to make my own, so far it sucks, but I was interested to know what sort of frames you other guys get and your hardware.

The scene that tests your computer sucks big time, I don't know how I did it, but there are some dancing, texture mapped, lit crates on your screen, and all of the code is based on nehe's.

Oh, I have a X1600XT, but it is only running in software and I'm getting about 1200fps at 800x600x24

To compile you will need the development library's for SDL and OpenGL, then just extract the tarball, and type make.

[http://au.geocities.com/bsmith1987/glmark.tar.gz]("http://au.geocities.com/bsmith1987/glmark.tar.gz")

Thanks for any comments, and don't be too critical of my code, its normally much better :)

I think you found a good project for yourself here!! 

Why not expand it and start a project for the first full featured 3D benchmark application for Linux. It is about time I think!!

I believe many people would be glad to help. A good starting point for project hosting and other services is [Launchpad]("https://launchpad.net/") of course!

---

### Post by bsmith on 2007-08-11
avik, I'm not sure why it would be getting such low frames, It seems it be running on a software surface and not hardware accelerated. Do you have the correct drivers for your video card installed?

Mine is also and AMD64 3700+

---

### Post by bsmith on 2007-08-11
kostkon, Thanks for the encouragement, I would love to create something that other people actually use and appreciate.

I've never been part of any community driven project, well actually no one has ever seen any of my code before, but I would love to give it a try.

I'll look into launchpad and see what happens.

---

### Post by slavik on 2007-08-11
you may want to look at glexcess

also, do you have a testing methodology?

---

### Post by moma on 2007-08-11
Great test.  It seems to work very well here.
Here are the results of Moma's machine.

$ [COLOR="SeaGreen"]./glmark [/COLOR]
We have a software surface
Our screen mode is 800x600x24

Evaluation:
        Total time:     5.152000 seconds
        Total frames:   10000
        Average fps:    1940.993896

$ [COLOR="SeaGreen"]./glmark [/COLOR]
We have a software surface
Our screen mode is 800x600x24

Evaluation:
        Total time:     4.312000 seconds
        Total frames:   10000
        Average fps:    2319.109619
-------------------------------------------------------
This machine has Nvidia's GeForce 6800 GPU and a proper driver that gives hardware accelerated graphics (direct rendering = Yes).
$ [COLOR="SeaGreen"]lspci | grep -i  vga[/COLOR]
01:00.0 VGA compatible controller: nVidia Corporation NV40.2 [GeForce 6800 LE] (rev a1)

$[COLOR="SeaGreen"] glxgears -info[/COLOR]
GL_RENDERER   = GeForce 6800 LE/AGP/SSE2/3DNOW!     <------- if you see "Mesa" here then it renders on software (= slow).
GL_VERSION    = 2.1.0 NVIDIA 96.31
GL_VENDOR     = NVIDIA Corporation
....
....
37238 frames in 5.0 seconds = 7447.519 FPS
38788 frames in 5.0 seconds = 7757.583 FPS
60379 frames in 5.0 seconds = 12075.699 FPS
63457 frames in 5.0 seconds = 12691.243 FPS
--------------------------------------------------------
$ [COLOR="SeaGreen"]glxinfo | grep -i direct[/COLOR]
direct rendering: Yes

---

### Post by slavik on 2007-08-11
the reason it reports that it runs in software is because you are using opengl ... opengl stores everything in hardware.

---

### Post by Wybiral on 2007-08-11
OK, I gave it a run and got:
```

We have a software surface
Our screen mode is 800x600x24

Evaluation:
        Total time:     15.519000 seconds
        Total frames:   10000
        Average fps:    644.371399
```

My machine:
```

Intel Celeron D 340
512mb ram
GeForce FX 5200
```

---

### Post by bsmith on 2007-08-11
moma, thanks for all the stats

salvic, glexcess looks liks some great work, It would be awesome to have some great effects like them.

And for a testing methodology, I was thinking of doing something like on 3DMark, where it will run a few demos, each testing out a new OpenGL extension. And by using the average FPS and the weighting for each demo in some nifty algorithm to produce a score.
I know the results would be better if they also took into account min and max FPS and stuff, but that can come later :)

> the reason it reports that it runs in software is because you are using opengl ... opengl stores everything in hardware.
What exactly does this mean, is it using hardware acceleration to render the scene? I am defiantly no expert on SDL or OpenGL.
It seems that my program is telling everyone that they have a software surface.
There were other demos on nehe that use GLX instead of SDL, and the GLX one did report using a hardware surface.
I'm confused:confused:

moma, thanks for the results, sounds like you have a cranking machine, I've have an 8600XT on order at the moment.

Wybiral, thanks for testing my benchmark, the results sound true to your hardware, Its great to see so many people taking an interest.

---

### Post by AlexThomson_NZ on 2007-08-11
Hi when I ran I got:
```

We have a software surface
Our screen mode is 800x600x24

Evaluation:
        Total time:     6.906000 seconds
        Total frames:   10000
        Average fps:    1448.016113

```

The second time I tried (straight after):

```

We have a software surface
Our screen mode is 800x600x24

Evaluation:
        Total time:     6.660000 seconds
        Total frames:   10000
        Average fps:    1501.501465

```

So a bit of varience there.  My PC is a fairly recent Dell 9300 laptop with a GeForce 6800 GO (sorry, can't remember exact specs!).  I get around 5300 with glxgears.

It would be good to see this expanded out a bit more, including things like shader models, etc., as well as more variance in the meshes getting rendered (ie. very large textures, high-count polys, triangle fans, points, lines, etc.), maybe make it a bit more CPU limited too?

---

### Post by bsmith on 2007-08-11
> Hi when I ran I got:
Code:

We have a software surface
Our screen mode is 800x600x24

Evaluation:
        Total time:     6.906000 seconds
        Total frames:   10000
        Average fps:    1448.016113

The second time I tried (straight after):

Code:

We have a software surface
Our screen mode is 800x600x24

Evaluation:
        Total time:     6.660000 seconds
        Total frames:   10000
        Average fps:    1501.501465

So a bit of varience there. My PC is a fairly recent Dell 9300 laptop with a GeForce 6800 GO (sorry, can't remember exact specs!). I get around 5300 with glxgears.

It would be good to see this expanded out a bit more, including things like shader models, etc., as well as more variance in the meshes getting rendered (ie. very large textures, high-count polys, triangle fans, points, lines, etc.), maybe make it a bit more CPU limited too?

I also get a slight variance in average fps, I'm not too sure how to fix this, maybe if it ran for longer and was fullscreen.

My plan is to expand it alot more, I just need to learn more about opengl, and get more creative :)

---

### Post by Wybiral on 2007-08-11
> **bsmith said:**
> I also get a slight variance in average fps, I'm not too sure how to fix this, maybe if it ran for longer and was fullscreen.

My plan is to expand it alot more, I just need to learn more about opengl, and get more creative :)

Also, be sure to specialize every test. That demo primarily makes use of opengl's display list which often produces better results then manual rendering. It might be interesting to see the benchmarks without the display lists.

I too would like to see something like this expanded to cover various areas of OpenGL rendering like mipmapping, vertex arrays, display lists, lighting, fog... etc.

I could help with the GL part if you ever need any.

It might serve as an interesting resource to OpenGL programmer like me who can use it to decide which approach will provide the best performance, and on which machines.

---

### Post by bsmith on 2007-08-11
> Also, be sure to specialize every test. That demo primarily makes use of opengl's display list which often produces better results then manual rendering. It might be interesting to see the benchmarks without the display lists.

This is exactly what I was thinking.

Your help would be greatly appreciated, should I set up a project on launchpad?

---

### Post by bsmith on 2007-08-11
Wybiral, also, do you think what I have coded so far is worth keeping, or should it be started again from scratch. In C or C++ etc...

---

### Post by legatvs on 2007-08-15
> **bsmith said:**
> 
...Anyway I was playing today trying to make my own...


I think that's a good start. I rounded up some suggestions:

[LIST]
[*]Clean up the code a bit (e.g. Linux coding style, see the URL below)
[*]Add autotools support (-> ./configure && make)
[*]Option: XML output
[*]Add command line interface (e.g. resolution etc.)
[*]Extract graphic card details (card, opengl version, extensions etc.) glGetString provides you with this info
[*]Add graphical user interface (eventually, not a top priority)
[/LIST]

Linux coding style: [http://lxr.linux.no/source/Documentation/CodingStyle]("http://lxr.linux.no/source/Documentation/CodingStyle")

Now, the coding style is a matter of preference really, and the above is just one example of that. If I was to recommend any specifics, I'd say you cannot go wrong with 8-character indentations and < 75 character lines.

And as for C or C++ (or any other), that's another matter of preference. Which ever enables your productivity and creativity best and provides the means to achieve your goals. You cannot go wrong with either, C or C++.

_Side note:_ You may want to look into portability depending on your goals, it's much easier to do that now than later and end up re-writing nearly everything due to some bizarre moment of enlightenment in your mid-life crisis.

URL: [Mozilla: C++ portability guide]("http://www.mozilla.org/hacking/portable-cpp.html")
Includes some C specific info also.

URL: [Autools book (online)]("http://sourceware.org/autobook/autobook/autobook_toc.html#SEC_Contents")
Covers Autotools and adds a few tips about portable C.

As this thread has shown already there's interest and use for a program like this one. I can probably commit some code and I'm certain others will join/help with your project as they find out about.

Keep it up.

---

### Post by Wybiral on 2007-08-15
> **legatvs said:**
> Now, the coding style is a matter of preference really, and the above is just one example of that. If I was to recommend any specifics, I'd say you cannot go wrong with 8-character indentations and < 75 character lines.

The only time style really matters is when you're working in a team. When you're on your own, use what you are comfortable with.

8 space tabs? Why not 4?

Why 75 and not 79-80?

Preference...

There was a big post recently about coding style, you should look for it. Lots of different styles (especially when languages differ).

---

### Post by bsmith on 2007-08-16
legatvs, you've got some great ideas, portability is defiantly the way to go, and I do love good looking code so I'll neaten it up when I get time.

glGetString sounds like it would add a great feature to the program.

And the GUI can also wait

Thanks for the support

---

### Post by legatvs on 2007-08-16
Like you quoted me saying: it is a matter of preference.

> **Wybiral said:**
> The only time style really matters is when you're working in a team. When you're on your own, use what you are comfortable with.

However, the experience has taught that style often matters in the long run. This is especially true in open source projects as they are sometimes abandoned and taken over by someone else.

> "Because maintenance is so important and so expensive, write programs as if the most important communication they do is not to the computer that executes them but to the human beings who will read and maintain the source code in the future (including yourself)."

The above quote is from [Basics of the Unix Philosophy]("http://www.faqs.org/docs/artu/ch01s06.html") ([The Art of Unix Programming]("http://www.faqs.org/docs/artu")) which is a good read for anyone taking programming seriously.

There is actually a reason for the line length. Not everyone codes using a fancy IDE let alone X11. And even then one usually ends up having to scroll back and forth to see the rest of the lines if the screen settings (resolution, fonts etc.) vary, and they often do.

Regardless, I realize it's been discussed and it falls outside this topic.

> **bsmith said:**
> legatvs, you've got some great ideas, portability is defiantly the way to go, and I do love good looking code so I'll neaten it up when I get time.

Great, please keep us posted of any updates/changes and if you are accepting/needing any help.

---

### Post by legatvs on 2007-08-16
> **bsmith said:**
> glGetString sounds like it would add a great feature to the program.

You can use the `lspci' command, too, but I think it may require root access on some distros which is probably something you want to avoid.

e.g. lspci | grep -i 'vga compatible controller'

---

### Post by slavik on 2007-08-16
> **bsmith said:**
> moma, thanks for all the stats

salvic, glexcess looks liks some great work, It would be awesome to have some great effects like them.

And for a testing methodology, I was thinking of doing something like on 3DMark, where it will run a few demos, each testing out a new OpenGL extension. And by using the average FPS and the weighting for each demo in some nifty algorithm to produce a score.
I know the results would be better if they also took into account min and max FPS and stuff, but that can come later :)


What exactly does this mean, is it using hardware acceleration to render the scene? I am defiantly no expert on SDL or OpenGL.
It seems that my program is telling everyone that they have a software surface.
There were other demos on nehe that use GLX instead of SDL, and the GLX one did report using a hardware surface.
I'm confused:confused:

moma, thanks for the results, sounds like you have a cranking machine, I've have an 8600XT on order at the moment.

Wybiral, thanks for testing my benchmark, the results sound true to your hardware, Its great to see so many people taking an interest.
my understanding of sdl and open gl is that when you say HW_SURFACE, it tells SDL to use the video hardware, not opengl. opengl by itself does it in hardware. basically, most flags are useless when you use OpenGL ...

so, when you check which surface you have, SDL reports the truth, it's a software surfac, except you aren't using SDL to draw anything, try to create a surface without the opengl flag and I am sure you will get a hardware surface back.

also for relevance: [http://www.libsdl.org/cgi/docwiki.cgi/OpenGL_20Full_20Example](http://www.libsdl.org/cgi/docwiki.cgi/OpenGL_20Full_20Example)

notice how the example only has the opengl flag

from: [http://www.libsdl.org/cgi/docwiki.cgi/SDL_5fSetVideoMode](http://www.libsdl.org/cgi/docwiki.cgi/SDL_5fSetVideoMode)
> 
Need to be clarified. Some have found that enabling OpenGL attributes (like SDL_GL_STENCIL_SIZE, the Stencil Buffer Size) before the video mode has been set causes the application to simply ignore those attributes, while enabling attributes after the video mode has been set works fine. Hopefully this will be clarified soon. Maybe a bad flags parameter : for OpenGL mode, use only SDL_OPENGL (and SDL_FULLSCREEN if needed) nothing else.

---

### Post by foxylad on 2007-08-16
It would be neat to have a web site that allows people to compare their machine's performance with others with similar hardware. Maybe your app could have the option to query the hardware and then use web services to upload the hardware configuration and score to the website.

---

### Post by slavik on 2007-08-16
I hope you take the following as more constructive rather than offensive. but your benchmark so far sucks...

here's why: it does not test separate video subsystems (memory, integer calculations, floating point, etc.)

in certain cases you can expect a slower gpu with more memory being able to outperform a faster gpu with less memory.

sometimes, an app might use large textures, sometimes it might have lots of tiny triangles.

I think that you need to identify the separate types of apps that could appear and test the extreme cases for them (like memtest, cpuburn, etc)

this is the reason why I decided to not try to write an opengl benchmark, I don't know enough about opengl and video cards ...

---

### Post by pmasiar on 2007-08-17
> **legatvs said:**
> However, the experience has taught that style often matters in the long run. This is especially true in open source projects as they are sometimes abandoned and taken over by someone else.

Absolutely agree.

If following good standards is going to be "second nature", doing it "quick and dirty" outside throw-away 10-liners is wrong - should feel wrong and dirty.

---

### Post by AlexThomson_NZ on 2007-08-17
What I found interesting is that there seems to be a demand for a benchmark of this type.  I would love to have a crack at coding one (let's face it it's just a demo with flash graphics, who doesn't love coding those!)

Without trying to steal your idea or upstage you, I am interested to know what I should include, if I decide to do one.  I am thinking so far...

1. Multiple 3d objects consisting of small, medium and large # polys, using tris, quads and triangle stips.
2. A mix of no textures, small, medium and large textures
3. Multiple light sources
4. With and without fog effects and back-face culling
5. Both per-face and per-vertex normal shading
6. Alpha blending and bump-mapping

It should be pointed out I guess this would solely be a test of GFX card performance, and wouldn't really stress the CPU at all (unless you have a fast card and very slow CPU), and for consistancy should just run at a set resolution.

Any other thoughts?

---

### Post by bluehue on 2007-08-17
Nice little app :)

Results:
```

spiral@spiral-desktop:~/Desktop/glmark$ ./glmark

We have a software surface
Our screen mode is 800x600x24

Evaluation:
        Total time:     2.507000 seconds
        Total frames:   10000
        Average fps:    3988.831299
```

My machine:
```

Pentium IV 3.2 GHZ
1 GB RAM
Nvidia 6800 Ultra 256MB
```

---

### Post by kknd on 2007-08-17
We have a software surface
Our screen mode is 800x600x24

Evaluation:
        Total time:     5.568000 seconds
        Total frames:   10000
        Average fps:    1795.977063

On a 6600gt.

---

### Post by bsmith on 2007-08-17
You guys are all champs,
> but your benchmark so far sucks...
I love your honesty and I totally agree.:)
I'm slowly improving the program in between uni home work, I'm converting it all to c++, with classes for objects, vectors etc... , just a few bugs to sort out before I upload my next version.
And I have a little terrain demo with random camera movement, that makes me feel queesy, and 3ds support(now just for some decent models :))
And I still need to get my head around all that OpenGL/SDL stuff, thanks for the info

> (let's face it it's just a demo with flash graphics, who doesn't love coding those!)
I couldnt agree more, and your app sounds great, I cant wait to try it.

---

### Post by slavik on 2007-08-17
pixel and vertex shaders (if they are available) ...

---

### Post by AlexThomson_NZ on 2007-08-18
Hey, how are you going with the 3ds support?

I'm slaving away at the moment creating a loader for vrml models, just using blender to convert all the 3ds models to vrml format

---

### Post by slavik on 2007-08-18
I have some C++ code (single function) that can read wavefront obj files and another piece of code that can render the stuff from the reading function.

---

### Post by AlexThomson_NZ on 2007-08-18
Well I've come this far, so might as well finish up with the vrml stuff.

I'm quite proud of it, supports multiple meshes (tri and quad), multiple materials (diffuse, specular and transparency) and face normals so far.  Still need to implement texture (easy) and vertex normal (not so easy) support and I should be sorted!

---

### Post by sloggerkhan on 2007-08-18
I think you have a good project. Nice start. I think it's already a little more meaningful than glxgears.

---

### Post by slavik on 2007-08-18
> **sloggerkhan said:**
> I think you have a good project. Nice start. I think it's already a little more meaningful than glxgears.
glxgears is not even intended to be a benchmark (just to test opengl/direct rendering)

---

### Post by Wybiral on 2007-08-18
Be sure to keep in mind that this is to test OPENGL, and not C/C++.

Write small demos that lean HEAVILY on OpenGL and not C code.

The more C code in the render loop, the worse.

---

### Post by sloggerkhan on 2007-08-18
> **slavik said:**
> glxgears is not even intended to be a benchmark (just to test opengl/direct rendering)

Yeah, but these forums are full of "post your glxgears scores here" threads. By being even slightly meaningful, it has already surpassed them. My only point.

---

### Post by cmat on 2007-08-18
Here are my results...

We have a software surface
Our screen mode is 800x600x24

Evaluation:
        Total time:     16.435000 seconds
        Total frames:   10000
        Average fps:    608.457581

Very Impressive work!

---

### Post by bsmith on 2007-08-18
> Hey, how are you going with the 3ds support?

I'm slaving away at the moment creating a loader for vrml models, just using blender to convert all the 3ds models to vrml format
If you want 3ds support go to spacesimulator.net, they have an awesome tutorial, and source code that i modified for my data structure and got working in like 30mins
> 
Be sure to keep in mind that this is to test OPENGL, and not C/C++.

Write small demos that lean HEAVILY on OpenGL and not C code.

The more C code in the render loop, the worse.
I agree and I have to keep an eye on this.

Ive been playing with and without display lists and have noticed that without them im using 100% cpu, but with them on 50% or so.

---

### Post by bsmith on 2007-08-19
Ok, here is my next release, not too much excitement, but I think it is better, there are a few visual anomalies that need to be sorted out.

[http://au.geocities.com/bsmith1987/glmark.tar.gz]("http://au.geocities.com/bsmith1987/glmark.tar.gz")

To Compile, extract and...
```
$ cd glmark
$ make
$ ./glmark
```

```
OpenGL Information
GL_VENDOR:      ATI Technologies Inc.
GL_RENDERER:    Radeon X1600 Series
GL_VERSION:     2.0.6334 (8.34.8)

Scene 01, Monkey in Space :P
Tests display lists
Evaluation:
        Total time:     10.537000 seconds
        Total frames:   250
        Average fps:    23.725920

Scene 02, Terrain
Lots of polygons
Evaluation:
        Total time:     12.497000 seconds
        Total frames:   500
        Average fps:    40.009602

Scene 03, Monkey
Will show some fancy vertex shading or something
Evaluation:
        Total time:     4.705999 seconds
        Total frames:   6000
        Average fps:    1274.968262

Your GLMark07 score is 668 ^_^

```

I hope that this works better for you guys, and that you can see where I'm heading.

Bugs...
In the terrain, strange shading on a few polygons, probable something to do with my normal calculations.
I could not get my object class to work with large arrays of verticies and polygons, I think I was going about this the wrong way, so I'm just using a type for the objects instead of a class which I would have preferred.
The lights in general suck :)

Also, you might notice that there are monkey scattered over the landscape, these are meant to be trees, if anyone has a lowish poly model of a tree that I could use, It would be greatly appreciated.

---

### Post by Wybiral on 2007-08-19
Not bad, I got:

```

OpenGL Information
GL_VENDOR:      NVIDIA Corporation
GL_RENDERER:    GeForce FX 5200/PCI/SSE2
GL_VERSION:     2.1.0 NVIDIA 96.31

Scene 01, Monkey in Space :P
Tests display lists
Evaluation:
        Total time:     13.281000 seconds
        Total frames:   250
        Average fps:    18.823884

Scene 02, Terrain
Lots of polygons
Evaluation:
        Total time:     30.309999 seconds
        Total frames:   500
        Average fps:    16.496206

Scene 03, Monkey
Will show some fancy vertex shading or something
Evaluation:
        Total time:     9.147999 seconds
        Total frames:   6000
        Average fps:    655.881152

Your GLMark07 score is 344 ^_^

```

I see what you mean with the terrain lighting, I might check the code out later if I get some more free time.

I suggest adding a vertex array test, just load a complex model into a vertex array and render it, them load the same model with a display list and render it... Then render it raw. I would be interested to see just how different they end up.

EDIT:

Also, while all the camera movement and stuff makes it look cooler, it might be better to do the tests head-on to reduce any variation caused by culling or from the code used to move the camera (which I took a quick glance at and noticed the sin/cos calls which can be costly in tight loops). Camera motion should be done with GL's transformations since you're aiming at a GL test.

---

### Post by bsmith on 2007-08-19
> I suggest adding a vertex array test, just load a complex model into a vertex array and render it, them load the same model with a display list and render it... Then render it raw. I would be interested to see just how different they end up.
I'm not sure on how to do this, could you throw me some code if you have time, or a like to a tutorial.
I didn't even think the cos and sin for the camera transformations would alter the speed, but I guess it is in the main rendering loop, I'll work out how to get around it.
I would really appreciate it if you could have a look at the code some time, I'm not sure at all if I'm going the right way around it, most of the ideas have come from my software 0x13 rendering days :)

---

### Post by Wybiral on 2007-08-19
The effects of your camera code would be minimal considering the amount of rendering you're doing. I'm just reminding to keep the C side as minimal as possible.

If you can get away with moving the camera simply using the OpenGL transformation functions, that would be best, but like I said... It's not worth worrying about really.

Vertex arrays are really useful... I don't know of any good tutorials off the top of my head, but I bet google does. They allow you to render an array of vertex info without having to iterate and send each vertex (you can see how this would be a good test since it puts less weight on the C side).

The cool thing about vertex arrays is that the vertices's in them can change without needing to be rebuilt like a display list.

---

### Post by sloggerkhan on 2007-08-19
When I extract this, there is a binary that I can't run:
```
$ ./glmark
bash: ./glmark: cannot execute binary file

```
and make gives:
```
 $ make
make: `glmark' is up to date.

```
If I delete the binary, make gives:
```
$ make
gcc -O3 -Wall main.o nehe.o vector.o object.o camera.o 3dsloader.o scene01.o scene02.o scene03.o -o glmark -lGL -lGLU -lSDL
collect2: ld terminated with signal 11 [Segmentation fault], core dumped
/usr/bin/ld: warning: i386:x86-64 architecture of input file `main.o' is incompatible with i386 output
/usr/bin/ld: warning: i386:x86-64 architecture of input file `nehe.o' is incompatible with i386 output
/usr/bin/ld: warning: i386:x86-64 architecture of input file `vector.o' is incompatible with i386 output
/usr/bin/ld: warning: i386:x86-64 architecture of input file `object.o' is incompatible with i386 output
/usr/bin/ld: warning: i386:x86-64 architecture of input file `camera.o' is incompatible with i386 output
/usr/bin/ld: warning: i386:x86-64 architecture of input file `3dsloader.o' is incompatible with i386 output
/usr/bin/ld: warning: i386:x86-64 architecture of input file `scene01.o' is incompatible with i386 output
/usr/bin/ld: warning: i386:x86-64 architecture of input file `scene02.o' is incompatible with i386 output
/usr/bin/ld: warning: i386:x86-64 architecture of input file `scene03.o' is incompatible with i386 output
make: *** [glmark] Error 1

```

 Feisty Fawn, 32 bit. See sig for specs.

---

### Post by vadania on 2007-08-19
I got the archive (1.1MB) but the archiving tool tells me the file is incomplete. I suppose Yahoo webserver cut my download short. I'll retry downloading.

Your Yahoo hosting is no good. I get this: "The web site you are trying to access has exceeded its allocated data transfer. Access to this site will be restored within an hour. Please try again later."

Could you put up some mirrors? Of course I'll try mirroring it myself, if you allow

---

### Post by Lster on 2007-08-19
I can't run the program... I get the same problem as sloggerkhan.

---

### Post by Wybiral on 2007-08-19
For those who can't run it, you need to type:
```

make clean

```
Or delete the binary files (the executable AND the object files).

Then "make" it.

I believe it's because he has a 64 bit machine.

---

### Post by bsmith on 2007-08-19
Sorry about leaving all that crap in the zip. you will need to delete all the .o files and the executable and run make.

---

### Post by christhemonkey on 2007-08-19
God these resutls look awful!:
> OpenGL Information
GL_VENDOR:      NVIDIA Corporation
GL_RENDERER:    GeForce FX 5500/AGP/SSE/3DNOW!
GL_VERSION:     2.1.0 NVIDIA 97.55

Scene 01, Monkey in Space :P
Tests display lists
Evaluation:
        Total time:     13.186000 seconds
        Total frames:   250
        Average fps:    18.959503

Scene 02, Terrain
Lots of polygons
Evaluation:
        Total time:     29.660001 seconds
        Total frames:   500
        Average fps:    16.857721

Scene 03, Monkey
Will show some fancy vertex shading or something
Evaluation:
        Total time:     9.819000 seconds
        Total frames:   6000
        Average fps:    611.060174

Your GLMark07 score is 322 ^_^


Shuold i be worried? Or is 15/16 fps normal for my specs?!
(playing some music and have 3 firefox tabs open but thats it, no compiz running or anything, using nvidia-glx-new from repos)

---

### Post by bluehue on 2007-08-19
Once again, Pentium IV 3.2 GHZ with 1GB RAM

```

spiral@spiral-desktop:~/Desktop/glmark$ ./glmark

OpenGL Information
GL_VENDOR:      NVIDIA Corporation
GL_RENDERER:    GeForce 6800 Ultra/AGP/SSE2
GL_VERSION:     2.1.1 NVIDIA 100.14.11

Scene 01, Monkey in Space :P
Tests display lists
Evaluation:
        Total time:     1.075000 seconds
        Total frames:   250
        Average fps:    232.558155

Scene 02, Terrain
Lots of polygons
Evaluation:
        Total time:     2.377000 seconds
        Total frames:   500
        Average fps:    210.349171

Scene 03, Monkey
Will show some fancy vertex shading or something
Evaluation:
        Total time:     1.583000 seconds
        Total frames:   6000
        Average fps:    3790.271198

Your GLMark07 score is 2116 ^_^
```

---

### Post by Wybiral on 2007-08-19
> **christhemonkey said:**
> God these resutls look awful!:


Shuold i be worried? Or is 15/16 fps normal for my specs?!
(playing some music and have 3 firefox tabs open but thats it, no compiz running or anything, using nvidia-glx-new from repos)

Looks normal to me, look at my specs (you have a 5500 and I have a 5200, I also wasn't doing anything else when I ran it).

---

### Post by AntiRush on 2007-08-19
Athlon 64 x2 3800+, geforce 7950:

```

OpenGL Information
GL_VENDOR:      NVIDIA Corporation
GL_RENDERER:    GeForce 7950 GT/PCI/SSE2/3DNOW!
GL_VERSION:     2.1.1 NVIDIA 100.14.11

Scene 01, Monkey in Space :P
Tests display lists
Evaluation:
        Total time:     0.746000 seconds
        Total frames:   250
        Average fps:    335.120647

Scene 02, Terrain
Lots of polygons
Evaluation:
        Total time:     1.359000 seconds
        Total frames:   500
        Average fps:    367.917563

Scene 03, Monkey
Will show some fancy vertex shading or something
Evaluation:
        Total time:     1.132000 seconds
        Total frames:   6000
        Average fps:    5300.353500

Your GLMark07 score is 3000 ^_^

```

---

### Post by sloggerkhan on 2007-08-19
```
 $ ./glmark

OpenGL Information
GL_VENDOR:      ATI Technologies Inc.
GL_RENDERER:    MOBILITY RADEON X700
GL_VERSION:     2.0.6334 (8.34.8)

Scene 01, Monkey in Space :P
Tests display lists
Evaluation:
        Total time:     14.759000 seconds
        Total frames:   250
        Average fps:    16.938817

Scene 02, Terrain
Lots of polygons
Evaluation:
        Total time:     17.327001 seconds
        Total frames:   500
        Average fps:    28.856695

Scene 03, Monkey
Will show some fancy vertex shading or something
Evaluation:
        Total time:     6.820999 seconds
        Total frames:   6000
        Average fps:    879.636527

Your GLMark07 score is 461 ^_^


```

Thanks for the tip.
Those scenes seem to use a heavy load for what they look like (Admitted I had lots of stuff in background). I know that the fglrx driver is crap, but I can play most 3-D games decently and the FPS showing there didn't seem to reflect that. (On windows, Oblivion and FEAR were perfectly playable, though certainly not with high settings.)

---

### Post by Rhubarb on 2007-08-19
Core2Duo E6700, 3.2GB RAM, Ubuntu Feisty x86_64
```
OpenGL Information
GL_VENDOR:      NVIDIA Corporation
GL_RENDERER:    GeForce 7950 GT/PCI/SSE2
GL_VERSION:     2.1.1 NVIDIA 100.14.11

Scene 01, Monkey in Space :P
Tests display lists
Evaluation:
        Total time:     0.621000 seconds
        Total frames:   250
        Average fps:    402.576447

Scene 02, Terrain
Lots of polygons
Evaluation:
        Total time:     1.408000 seconds
        Total frames:   500
        Average fps:    355.113647

Scene 03, Monkey
Will show some fancy vertex shading or something
Evaluation:
        Total time:     1.185000 seconds
        Total frames:   6000
        Average fps:    5063.291504

Your GLMark07 score is 2909 ^_^
```

---

### Post by AlexThomson_NZ on 2007-08-20
Hey, love the new benchmark, here's my results, as you can see though, still a large varience:
```

athomson@athomson-laptop:~/Desktop/glmark$ ./glmark 

OpenGL Information
GL_VENDOR:      NVIDIA Corporation
GL_RENDERER:    GeForce Go 6800/PCI/SSE2
GL_VERSION:     2.1.0 NVIDIA 96.31

Scene 01, Monkey in Space :P
Tests display lists
Evaluation:
        Total time:     2.397000 seconds
        Total frames:   250
        Average fps:    104.297035

Scene 02, Terrain
Lots of polygons
Evaluation:
        Total time:     5.151000 seconds
        Total frames:   500
        Average fps:    97.068530

Scene 03, Monkey
Will show some fancy vertex shading or something
Evaluation:
        Total time:     4.720000 seconds
        Total frames:   6000
        Average fps:    1271.186369

Your GLMark07 score is 735 ^_^

athomson@athomson-laptop:~/Desktop/glmark$ ./glmark 

OpenGL Information
GL_VENDOR:      NVIDIA Corporation
GL_RENDERER:    GeForce Go 6800/PCI/SSE2
GL_VERSION:     2.1.0 NVIDIA 96.31

Scene 01, Monkey in Space :P
Tests display lists
Evaluation:
        Total time:     2.522000 seconds
        Total frames:   250
        Average fps:    99.127674

Scene 02, Terrain
Lots of polygons
Evaluation:
        Total time:     5.025000 seconds
        Total frames:   500
        Average fps:    99.502486

Scene 03, Monkey
Will show some fancy vertex shading or something
Evaluation:
        Total time:     3.849000 seconds
        Total frames:   6000
        Average fps:    1558.846463

Your GLMark07 score is 877 ^_^

```

---

### Post by bsmith on 2007-08-20
Hey, Its so great to see how many people are interested in this project, and I cant believe there isnt anything like it out yet?

I know the frames are looking miserable on some lower spec machines, and they are going through the roof on some beasts, but there are quite a few polygons being thrown at the screen each loop.

I'm right now trying to implement vertex arrays and vertex shading, which shold look good.

I might also make the tests longer for faster spec machines/or make them time bases not frame based. I was aiming at them all running for 10s on my machine, but it looks like not all machines are the same as mine :) my bad.

Anyway, thanks for all the feedback:rolleyes:

---

### Post by slavik on 2007-08-20
I would suggest doing something like a minute per test.

---

### Post by bites on 2007-08-21
Here are my results:

OpenGL Information
GL_VENDOR:      NVIDIA Corporation
GL_RENDERER:    GeForce Go 7400/PCI/SSE2
GL_VERSION:     2.1.0 NVIDIA 96.39

Scene 01, Monkey in Space :P
Tests display lists
Evaluation:
        Total time:     2.364000 seconds
        Total frames:   250
        Average fps:    105.752968

Scene 02, Terrain
Lots of polygons
Evaluation:
        Total time:     5.329000 seconds
        Total frames:   500
        Average fps:    93.826242

Scene 03, Monkey
Will show some fancy vertex shading or something
Evaluation:
        Total time:     8.700999 seconds
        Total frames:   6000
        Average fps:    689.575969

Your GLMark07 score is 442 ^_^

ignore this, was an incorrect symlink in /usr/lib.
-----------------------
Nice test!  But i'm wondering.. 

glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

glxinfo | grep vendor
server glx vendor string: NVIDIA Corporation
client glx vendor string: SGI
OpenGL vendor string: NVIDIA Corporation

glxgears -info
GL_RENDERER   = GeForce Go 7400/PCI/SSE2
GL_VERSION    = 1.4 (2.1.0 NVIDIA 96.39)
GL_VENDOR     = NVIDIA Corporation

How come glxinfo says I've got no direct rendering?  I've got about 2600 FPS in glxgears, so I thought I had direct rendering enabled.  But if it's disabled, perhaps I might get even more FPS?

---

### Post by bsmith on 2007-08-21
bites, im not sure what is wrong with your configuration, but I have just installed my new graphics card and followed the guide from the community documentation and this is what I got.

```
ben@ben-desktop:~$ glxinfo | grep direct
direct rendering: Yes
ben@ben-desktop:~$ glxinfo | grep vendor
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation
ben@ben-desktop:~$ glxgears -info
GL_RENDERER   = GeForce 8600 GT/PCI/SSE2
GL_VERSION    = 2.1.1 NVIDIA 100.14.11
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = ...
55118 frames in 5.0 seconds = 11023.497 FPS
55170 frames in 5.0 seconds = 11033.981 FPS
```

Good luck

---

### Post by nol1ght on 2007-09-14
AMD64 x2 4200+
```
 ./glmark 

OpenGL Information
GL_VENDOR:      NVIDIA Corporation
GL_RENDERER:    GeForce 7900 GS/PCI/SSE2
GL_VERSION:     2.1.0 NVIDIA 97.55

Scene 01, Monkey in Space :P
Tests display lists
Evaluation:
        Total time:     0.833000 seconds
        Total frames:   250
        Average fps:    300.120056

Scene 02, Terrain
Lots of polygons
Evaluation:
        Total time:     1.633000 seconds
        Total frames:   500
        Average fps:    306.184967

Scene 03, Monkey
Will show some fancy vertex shading or something
Evaluation:
        Total time:     1.321000 seconds
        Total frames:   6000
        Average fps:    4542.013184

Your GLMark07 score is 2574 ^_^


```

---

### Post by sloggerkhan on 2007-09-14
```
 

$ ./glmark 

OpenGL Information
GL_VENDOR:      ATI Technologies Inc.
GL_RENDERER:    ATI MOBILITY RADEON X700
GL_VERSION:     2.0.6849 Release

Scene 01, Monkey in Space :P
Tests display lists
Evaluation:
        Total time:     1.903000 seconds
        Total frames:   250
        Average fps:    131.371511

Scene 02, Terrain
Lots of polygons
Evaluation:
        Total time:     3.462000 seconds
        Total frames:   500
        Average fps:    144.425192

Scene 03, Monkey
Will show some fancy vertex shading or something
Evaluation:
        Total time:     5.171000 seconds
        Total frames:   6000
        Average fps:    1160.317152

Your GLMark07 score is 717 ^_^


```


I just reran with ATI fglrx driver 8.41.7. Huge improvement over the 8.3x.x shipped w/ Feisty.
Comparison: 

Old Test 1: 14.75 seconds, 16.94 FPS
Now T1: 1.90 seconds, 131.37 FPS

Old Test 2: 17.33 seconds, 28.86 FPS
NewT2: 3.46 seconds, 144.42 FPS

Old Test 3: 6.8 Seconds, 879.64 FPS
NewT3: 5.17 Seconds, 1160.32 FPS

Old Overall: 461
New Overall: 717

So, if next month's ATI driver improves from this month's and has stable AIGLX, things should be pretty nice.

---

### Post by etherealremnant on 2007-09-24
OpenGL Information
GL_VENDOR:      NVIDIA Corporation
GL_RENDERER:    GeForce 8800 GTS/PCI/SSE2
GL_VERSION:     2.1.1 NVIDIA 100.14.19

Scene 01, Monkey in Space :P
Tests display lists
Evaluation:
        Total time:     0.329000 seconds
        Total frames:   250
        Average fps:    759.878418

Scene 02, Terrain
Lots of polygons
Evaluation:
        Total time:     0.782000 seconds
        Total frames:   500
        Average fps:    639.386169

Scene 03, Monkey
Will show some fancy vertex shading or something
Evaluation:
        Total time:     0.931000 seconds
        Total frames:   6000
        Average fps:    6444.683105

Your GLMark07 score is 3920 ^_^


I hope work continues on this because I've been waiting for something like this for ages.

After closing out everything that was running:

OpenGL Information
GL_VENDOR:      NVIDIA Corporation
GL_RENDERER:    GeForce 8800 GTS/PCI/SSE2
GL_VERSION:     2.1.1 NVIDIA 100.14.19

Scene 01, Monkey in Space :P
Tests display lists
Evaluation:
        Total time:     0.301000 seconds
        Total frames:   250
        Average fps:    830.564758

Scene 02, Terrain
Lots of polygons
Evaluation:
        Total time:     0.705000 seconds
        Total frames:   500
        Average fps:    709.219788

Scene 03, Monkey
Will show some fancy vertex shading or something
Evaluation:
        Total time:     0.808000 seconds
        Total frames:   6000
        Average fps:    7425.742676

Your GLMark07 score is 4481 ^_^

---

### Post by Cuchaz on 2008-04-01
Hi there,

I had a little trouble getting glmark to compile. It looks like the new version of GCC has some regressions.

"As of version 4.2, GCC will no longer accept a typedef void as a function argument in C++."
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=383923](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=383923)

Basically, the bit in <GL/gl.h> that does this
typedef void GLvoid;
is no longer valid C++ when used as function arguments

To get the code to compile under GCC 4.2+, I had to replace all instances of GLvoid in the code with plain old void.

Other than my system not being set up correctly and rendering in software instead of hardware, the program looks cool. I've been having a bit of difficulty getting good a driver set for my intel X3100 in general. But I digress...  Keep up the good work!

If I can get it to work, I'll post some results later.

--Cuchaz

UPDATE: The results are in and my poor Intel X3100's performance is terrible at best.

```

OpenGL Information
GL_VENDOR:	Tungsten Graphics, Inc
GL_RENDERER:	Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
GL_VERSION:	1.4 Mesa 7.0.3-rc2

Scene 01, Monkey in Space :P
Tests display lists
Evaluation:
	Total time:	138.831996 seconds
	Total frames:	250
	Average fps:	1.800738

Scene 02, Terrain
Lots of polygons
Evaluation:
	Total time:	165.111010 seconds
	Total frames:	500
	Average fps:	3.028266

Scene 03, Monkey
Will show some fancy vertex shading or something
Evaluation:
	Total time:	18.166002 seconds
	Total frames:	6000
	Average fps:	330.287309

Your GLMark07 score is 166 ^_^

```

I very much hope that my system is misconfigured somehow. Also, I wonder if the image is rendering correctly. I looks like there might be texture issues. See the attached screenshot for details. Is it supposed to look like that?

---

### Post by Sockerdrickan on 2008-04-01
> OpenGL Information
GL_VENDOR:	NVIDIA Corporation
GL_RENDERER:	GeForce 8800 GTS/PCI/SSE2/3DNOW!
GL_VERSION:	2.1.2 NVIDIA 169.12

Scene 01, Monkey in Space :P
Tests display lists
Evaluation:
	Total time:	0.299000 seconds
	Total frames:	250
	Average fps:	836.120415

Scene 02, Terrain
Lots of polygons
Evaluation:
	Total time:	0.709000 seconds
	Total frames:	500
	Average fps:	705.218686

Scene 03, Monkey
Will show some fancy vertex shading or something
Evaluation:
	Total time:	0.824000 seconds
	Total frames:	6000
	Average fps:	7281.552863

Your GLMark07 score is 4410 ^_^
It quits after a few seconds, too quick!

---

### Post by Bushfire on 2008-04-01
```

OpenGL Information
GL_VENDOR:      Tungsten Graphics, Inc.
GL_RENDERER:    Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
GL_VERSION:     1.3 Mesa 7.0.1

Scene 01, Monkey in Space :P
Tests display lists
Evaluation:
        Total time:     91.719997 seconds
        Total frames:   250
        Average fps:    2.725687

Scene 02, Terrain
Lots of polygons
Evaluation:
        Total time:     58.325000 seconds
        Total frames:   500
        Average fps:    8.572653

Scene 03, Monkey
Will show some fancy vertex shading or something
Evaluation:
        Total time:     0.713004 seconds
        Total frames:   6000
        Average fps:    8415.098027

Your GLMark07 score is 4212 ^_^

```

Not that geocities isn't, err, *great* and all, a sourceforge page would be a step up. :D

Edit: Ah, Cuchaz, so it's a C++ thing is it? I just upgraded to 8.04 and came across the same problem. It seemed strange to me, because I whipped a small C program using the same declaration syntax and it had no troubles. Oh well, nothing a quick :%s/GLvoid/void can't fix.

---

### Post by Cuchaz on 2008-04-02
Yeah, it's a c++ thing. The weird typdef'd voids should still work in plain old c. Thankfully, the problem is easily fixable.

--Cuchaz

---

### Post by bsmith on 2008-04-07
Hey, all.

Sorry I haven't really touched this projects in like ages, but Ive been busy with uni and stuff, but I think I want to continue it again.

I would restructure the whole code and do it properly :D

And maybe I should learn some opengl :P

If anyone wants to help that would be great, and a sourceforge page could be set up.

I think it would be great if there was just a few scenes...
* One with lost of polys and tests the diffrences between just throwing them all at the GPU, and using the different lists, etc...
* One that tests different texture filters, and antialiaseing methods.
* One that tests all the different shaders (however they work)
* And a few fancy effect ones, like stencil shadows, radial blurs and stuff.

What else do I need, and what do you reckon.

---

### Post by sloggerkhan on 2008-04-08
[http://www.phoronix.com/scan.php?page=article&item=phoronix_pts_02&num=1](http://www.phoronix.com/scan.php?page=article&item=phoronix_pts_02&num=1)
might also be of interest to those who read this thread.

---

### Post by bsmith on 2008-04-09
I have just created a sourceforge project for the new glmark.:guitar:

[https://sourceforge.net/projects/glmark/]("https://sourceforge.net/projects/glmark/")

Check it out.

I think it is better structured, and has more potential, but there is still a lot of work to be done to make it respectable, mainly get an object with alot more detail to test the different methods of pre-compilation.

---

### Post by Zannax on 2008-04-10
I've just tested with my poor old Radeon RV100 QY [Radeon 7000/VE] (btw ATI doesn't ship any linux driver for it) and here's the result:

> OpenGL Information
GL_VENDOR:      Tungsten Graphics, Inc.
GL_RENDERER:    Mesa DRI Radeon 20061018 AGP 1x x86/MMX+/3DNow!+/SSE NO-TCL
GL_VERSION:     1.3 Mesa 6.5.2

Scene 01, Monkey in Space :P
Tests display lists
Evaluation:
        Total time:     66.003997 seconds
        Total frames:   250
        Average fps:    3.787649

Scene 02, Terrain
Lots of polygons
Evaluation:
        Total time:     101.905993 seconds
        Total frames:   500
        Average fps:    4.906483

Scene 03, Monkey
Will show some fancy vertex shading or something
Evaluation:
        Total time:     73.733002 seconds
        Total frames:   6000
        Average fps:    81.374688

Your GLMark07 score is 43 ^_^


DOH! :-)

btw, no vertex shaders or the like, everything was just grayscale...

---

### Post by stair314 on 2008-04-10
You might want to put the enclosing directory itself into the download so that it's easier to untar cleanly.
I don't know if this concerns you, but the window it displayed looked empty to me. Other than that it ran fine.

> 
======================================
GLMark
======================================
Screen mode: 800x600x20
OpenGL Information
GL_VENDOR:      NVIDIA Corporation
GL_RENDERER:    GeForce 8800 GT/PCI/SSE2
GL_VERSION:     2.1.2 NVIDIA 169.09
======================================
No precompilation
        Duration: 0.843000
        FPS: 5931.198242

Display Lists
        Duration: 0.788000
        FPS: 6345.177246

Vertex Arrays
        Duration: 0.786000
        FPS: 6361.324219

Nearest Filtered Texture
        Duration: 0.794000
        FPS: 6297.228027

Linear Filtered Texture
        Duration: 0.799000
        FPS: 6257.823730

MipMapped Texture
        Duration: 0.796000
        FPS: 6281.407227



---

### Post by Shuffle777 on 2008-04-11
> **stair314 said:**
> You might want to put the enclosing directory itself into the download so that it's easier to untar cleanly.
I totally agree. I felt like I would bite my keyboard when all files were extracted but not in a sub-directory!

> **stair314 said:**
> I don't know if this concerns you, but the window it displayed looked empty to me. Other than that it ran fine.
+1

With an older version, it runs just fine and I can see things. But it's also too quick.
As someone already said, you should run each scene for a longer time (like 1 minute or so).
But I add you should run them in realtime. I mean you have to get objects' positions, camera movement, etc using a timer based on system clock. SDL provides GetTicks().
I say this because I don't have time to see anything. There must be a difference between frame number and scene time, so that anyone can see the same thing (but with a framerate dependent on the software/hardware renderer).

I would really like to help you in this great project. Unfortunately, I won't have any time for it before the beginning of June (2008 of course). Tell me if you are interested anyway.

In any case, keep up that GREAT work!!!

BTW, here goes my mark :) :
(Note that I have many apps running, a [BOINC]("http://boinc.berkeley.edu/") client notably)

Host: AMD Phenom 9500 (stepping B2 :( ) + 4GB PC2-8500
[QUOTE=Old version (with visuals)]Downloaded it there: [http://au.geocities.com/bsmith1987/glmark.tar.gz]("http://au.geocities.com/bsmith1987/glmark.tar.gz")
```
OpenGL Information
GL_VENDOR:      NVIDIA Corporation
GL_RENDERER:    GeForce 8800 GT/PCI/SSE2
GL_VERSION:     2.1.2 NVIDIA 169.12

Scene 01, Monkey in Space :P
Tests display lists
Evaluation:
        Total time:     0.281000 seconds
        Total frames:   250
        Average fps:    889.679688

Scene 02, Terrain
Lots of polygons
Evaluation:
        Total time:     0.605000 seconds
        Total frames:   500
        Average fps:    826.446228

Scene 03, Monkey
Will show some fancy vertex shading or something
Evaluation:
        Total time:     0.918000 seconds
        Total frames:   6000
        Average fps:    6535.947266

Your GLMark07 score is 4124 ^_^
```[/QUOTE]
[QUOTE=Sourceforge version 0.1 (no visuals :-( )]```
======================================
GLMark
======================================
Screen mode: 800x600x20
OpenGL Information
GL_VENDOR:      NVIDIA Corporation
GL_RENDERER:    GeForce 8800 GT/PCI/SSE2
GL_VERSION:     2.1.2 NVIDIA 169.12
======================================
No precompilation
        Duration: 0.716000
        FPS: 6983.240234

Display Lists
        Duration: 0.700000
        FPS: 7142.857910

Vertex Arrays
        Duration: 0.711000
        FPS: 7032.349121

Nearest Filtered Texture
        Duration: 0.717000
        FPS: 6973.500488

Linear Filtered Texture
        Duration: 0.698000
        FPS: 7163.321777

MipMapped Texture
        Duration: 0.702000
        FPS: 7122.510742

```
Uh? No mark!? :confused: Is this really the latest version? And why is it plain old C while "older" version was C++?[/QUOTE]

---

### Post by BackwardsDown on 2008-04-11
The latest one from sourceforge doesn't give me a mark:confused:

---

### Post by closey on 2008-04-14
Just a hint for those people that are getting really low scores, make sure you have 'Sync to VBlank' turned off in your nvidia-settings (or whatever you use for ATI). My score went from 80 up to 1360 after I changed that ! :)

---

### Post by alaci on 2008-04-14
New Nvidia driver!

173.08

[http://www.nvidia.com/object/linux_display_ia32_173.08.html](http://www.nvidia.com/object/linux_display_ia32_173.08.html)

---

### Post by bsmith on 2008-04-18
Hi, I have uploaded a slightly altered version of the source to sourceforge that makes the scenes run for a minute each and gives a score at the end. It wont spew all over your current directory :D

Hope all goes well.

I rigged the scoring so that my computer gets a perfect 5000 :D

Also the model drastically needs improving as there is not difference between the different methods of precompilation as there is not enough polys/vertices's to make a difference.

---

### Post by Shuffle777 on 2008-04-18
Hi again. I have some bad news for you... :-(
[LIST=1]
[*]Woops: [http://www.majorgeeks.com/download179.html](http://www.majorgeeks.com/download179.html) !
Looks like GLmark is an already used name. I don't know how good it is, but it packs several megabytes... (of textures most likely). Anyway, it's rather old (2002). Plus it's a Windoze program !

[*]I think that line 17 of video.c has a mistake: the last x (just before \n) should be a d. (Why would you want a bpp value displayed in hexadecimal?)

[*]Your new score computation function sucks... (Sorry for saying it like this). Here is something I think better:
```
int calculate_score(int *results)
{
    double score = 0.0;
    score += (double)results[0] / 2268.0;
    score += (double)results[1] / 2260.0;
    score += (double)results[2] / 2266.0;
    score += (double)results[3] / 1045.0;
    score += (double)results[4] / 950.0;
    score += (double)results[5] / 2250.0;
    return (int)(score * 1000.0);
}
```
That way, people will get scores between multiples of 1000...my function will always give scores >= to yours because of integer truncation vs floating point.
Oh, and don't use floats: they suck at rounding, and FPU does all computations as IEEE 754 double-extended values (80bits, aka "long double") anyway. (Conversions to 64bits (doubles) or 32bits (floats) are made when reading from/writing to memory). And you're not up to 4 bytes of RAM, I believe. (For huge arrays, it would be different...)

[*]I still get no visuals. I think this is related to the way you set up the video buffer. But I don't have time to work on it for now... I just had a look in case it would be obvious, but I failed :lolflag: Maybe this is not where we should look anyway.
I also think this messes up the framerate: I get about 7050-7200 FPS to ALL tests. And the framerate does not seem related to the precompilation method or the filtering applied. I know that G92 is a perfect GPU, but still... ;-)
EDIT: sorry, i forgot to read that:
> **bsmith said:**
> 
Also the model drastically needs improving as there is not difference between the different methods of precompilation as there is not enough polys/vertices's to make a difference.

This may be a better explanation...[/LIST]

Anyway, here go my new marks: 25000 (your function) and 26877 (my function)
Note that I reduced the tests duration to 30 seconds, because 1 minute is soooooo long when you see nothing and have to stay idle...

Keep up the work anyway ! This project must NOT stop !

---

### Post by phoronix on 2008-04-18
bsmith,

The GLMark benchmark now has a test profile with the Phoronix Test Suite ([http://www.phoronix.com/vr.php?view=12237](http://www.phoronix.com/vr.php?view=12237)).

Though could you please add support for setting a resolution (other than 800 x 600) via a command-line argument? And a command-line argument for running just one of the tests instead of all of them?

Thanks.


Michael

---

### Post by bsmith on 2008-04-19
Hi,
Another update added, fixed the score, which did suck bad, thanks to Shuffle777.
Selectable res, color depth, and window mode.

But I have no idea why some people dont get anything on there screen, is it an ati thing?

And if we want to move the conversation to the sourceforge forum that would be cool, cause people might get annoyed with this post bumping to the top all the time :)

---

### Post by pingpongboss on 2008-04-19
Great program dude. Using the new 3.0 version.

E8400 oc'd to 3.6 ghz, GeForce 9600gt, 4 gig ram

With Compiz:
```
Screen mode: 800x600x32
OpenGL Information
GL_VENDOR:	NVIDIA Corporation
GL_RENDERER:	GeForce 9600 GT/PCI/SSE2
GL_VERSION:	2.1.2 NVIDIA 173.08
======================================
No precompilation
	Duration: 30.000999
	Frames: 148654
	FPS: 4954.968262

Display Lists
	Duration: 30.000002
	Frames: 147580
	FPS: 4919.333008

Vertex Arrays
	Duration: 30.000996
	Frames: 149623
	FPS: 4987.267578

Nearest Filtered Texture
	Duration: 30.000999
	Frames: 143416
	FPS: 4780.374023

Linear Filtered Texture
	Duration: 30.001007
	Frames: 143591
	FPS: 4786.206055

MipMapped Texture
	Duration: 30.000992
	Frames: 143102
	FPS: 4769.909180

Your GLMark08 score is 18293 ^_^

```

and without Compiz:
```
Screen mode: 800x600x32
OpenGL Information
GL_VENDOR:	NVIDIA Corporation
GL_RENDERER:	GeForce 9600 GT/PCI/SSE2
GL_VERSION:	2.1.2 NVIDIA 173.08
======================================
No precompilation
	Duration: 30.000999
	Frames: 183587
	FPS: 6119.362793

Display Lists
	Duration: 30.000002
	Frames: 184017
	FPS: 6133.899414

Vertex Arrays
	Duration: 30.000999
	Frames: 187961
	FPS: 6265.157715

Nearest Filtered Texture
	Duration: 30.000999
	Frames: 176257
	FPS: 5875.037598

Linear Filtered Texture
	Duration: 30.000999
	Frames: 176090
	FPS: 5869.471191

MipMapped Texture
	Duration: 30.001007
	Frames: 176189
	FPS: 5872.769531

Your GLMark08 score is 22586 ^_^

```

And like alot of other people, I only see a black screen, nothing being drawn on it.

Edit: I went on another computer with an Intel integrated GPU, and there are things being drawn on the screen. Maybe it's a problem with Nvidia's drivers? I'm using the latest beta which supports the newer 9xxx cards.
Edit2: Oh and i just noticed that even if I pick between 16/24/32 depth, Screen mode always says 800x600**x32**

---

### Post by sloggerkhan on 2008-04-19
tried latest version
AMD Athlon x2 2.1 ghz, 1 gig RAM, 8600gt 256 mb.
with compiz running.
First bench is for 1680x1050
Second is for 800x600
```

3$ ./glmark 

======================================
GLMark
======================================
What resolution would you like to use
4:3                 5:4             16:10
1: 640x480          7: 1280x1024    9:  1280x800
2: 800x600          8: 1600x1280    10: 1440x900
3: 1024x768                         11: 1680x1050
4: 1152x864
5: 1280x960
6: 1600x1280
11
What color depth would you like to use
1: 16               2: 24           3: 32
3
Would you like fullscreen
1: yes              2: no
1
Screen mode: 1680x1050x32
OpenGL Information
GL_VENDOR:      NVIDIA Corporation
GL_RENDERER:    GeForce 8600 GT/PCI/SSE2/3DNOW!
GL_VERSION:     2.1.2 NVIDIA 169.12
======================================
No precompilation
        Duration: 30.000000
        Frames: 45291
        FPS: 1509.700000

Display Lists
        Duration: 30.000000
        Frames: 45650
        FPS: 1521.666667

Vertex Arrays
        Duration: 30.000000
        Frames: 45379
        FPS: 1512.633333

Nearest Filtered Texture
        Duration: 30.000000
        Frames: 22070
        FPS: 735.666667

Linear Filtered Texture
        Duration: 30.000000
        Frames: 20972
        FPS: 699.066667

MipMapped Texture
        Duration: 30.000992
        Frames: 42501
        FPS: 1416.653164

Your GLMark08 score is 4074 ^_^
uname@comp$ ./glmark 

======================================
GLMark
======================================
What resolution would you like to use
4:3                 5:4             16:10
1: 640x480          7: 1280x1024    9:  1280x800
2: 800x600          8: 1600x1280    10: 1440x900
3: 1024x768                         11: 1680x1050
4: 1152x864
5: 1280x960
6: 1600x1280
2
What color depth would you like to use
1: 16               2: 24           3: 32
3
Would you like fullscreen
1: yes              2: no
2
Screen mode: 800x600x32
OpenGL Information
GL_VENDOR:      NVIDIA Corporation
GL_RENDERER:    GeForce 8600 GT/PCI/SSE2/3DNOW!
GL_VERSION:     2.1.2 NVIDIA 169.12
======================================
No precompilation
        Duration: 30.001001
        Frames: 64786
        FPS: 2159.461254

Display Lists
        Duration: 30.000998
        Frames: 63396
        FPS: 2113.129735

Vertex Arrays
        Duration: 30.000004
        Frames: 65143
        FPS: 2171.433057

Nearest Filtered Texture
        Duration: 30.000999
        Frames: 30051
        FPS: 1001.666629

Linear Filtered Texture
        Duration: 30.001999
        Frames: 27349
        FPS: 911.572595

MipMapped Texture
'/usr/share/applications/envy.desktop'  Duration: 30.001007
        Frames: 63788
        FPS: 2126.195292

Your GLMark08 score is 5706 ^_^

```

---

### Post by maddog39 on 2008-04-20
Here are my results
```

[maddog39@desktop GLMark-0.3]$ ./glmark

======================================
GLMark
======================================
What resolution would you like to use
4:3                 5:4             16:10
1: 640x480          7: 1280x1024    9:  1280x800
2: 800x600          8: 1600x1280    10: 1440x900
3: 1024x768                         11: 1680x1050
4: 1152x864
5: 1280x960
6: 1600x1280
10
What color depth would you like to use
1: 16               2: 24           3: 32
3
Would you like fullscreen
1: yes              2: no
1
Screen mode: 1440x900x32
OpenGL Information
GL_VENDOR:    NVIDIA Corporation
GL_RENDERER:    GeForce 8500 GT/PCI/SSE2
GL_VERSION:    2.1.2 NVIDIA 169.12
======================================
No precompilation
    Duration: 30.000999
    Frames: 14747
    FPS: 491.550291

Display Lists
    Duration: 30.000000
    Frames: 14824
    FPS: 494.133333

Vertex Arrays
    Duration: 30.000999
    Frames: 14839
    FPS: 494.616855

Nearest Filtered Texture
    Duration: 30.000000
    Frames: 9223
    FPS: 307.433333

Linear Filtered Texture
    Duration: 30.002007
    Frames: 8777
    FPS: 292.547100

MipMapped Texture
    Duration: 30.000992
    Frames: 13326
    FPS: 444.185315

Your GLMark08 score is 1451 ^_^

```
This was done on Arch Linux however, not Ubuntu, although shouldnt make a different. Also, you should add a Makefile for GLMark08, since there was not one included with the source tarball from sourceforge.net.

---

### Post by bsmith on 2008-04-26
Hi all,

I've just uploaded a new version on the benchmark and I think it has some better features including support for GLSL.
I would like to know if you are able to see anything on the screen, I can on both of my box's, but there were some problems before.
The whole benchmark should run for 100 seconds, which I think is plenty of time.
Shuffle777 said that the name GLMark was already taken, does this mean I need to change the name, what is the etiquette on these things?
I get a score of about 10,000 with an 8600GT.

Thanks for all the support.

---

### Post by pointfivezero on 2008-04-28
Hi there, before I post my results I must add that i needed to install **libsdl-ttf2.0-dev** in order to compile glmark -0.5.2...

righto, my test results

```

$ ./glmark
===================================================
    GLMark 08
===================================================
Enter screen width:  800
Enter screen height: 600
Enter screen bpp:    32
Enter '1' for fullscreen '0' for windowed: 0
===================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce 6600 GT/AGP/SSE2/3DNOW!
    GL_VERSION:    2.1.2 NVIDIA 171.06
===================================================
Precompilation
    No Precompilation             FPS: 403
    Build list                    FPS: 628
    Vertex array                  FPS: 675
    Vertex buffer object          FPS: 1083
Texture filtering
    Nearest                       FPS: 1247
    Linear                        FPS: 1098
    Mipmapped                     FPS: 1470
Shading
    Smooth shader model      FPS: 748
    GLSL per vertex lighting FPS: 751
    GLSL per pixel lighting  FPS: 767
===================================================
Your GLMark08 Score is 4877  ^_^
===================================================

```

Yes, everything looked to display correctly thoughout the entire test.

also

```

$ uname -r
2.6.24-16-generic
$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

```

system specs are:

CPU: AMD Athlon64 3200+
 CORE @ 2200MHz
RAM: 1024MB PC3200 DDR
GFX: NVIDIA 6600GT (AGP 8x)
 CPU @ 500MHz
 MEM @ 900MHz

...

Many thanks, :popcorn:!

---

### Post by pingpongboss on 2008-04-28
> **bsmith said:**
> Hi all,

I've just uploaded a new version on the benchmark and I think it has some better features including support for GLSL.
I would like to know if you are able to see anything on the screen, I can on both of my box's, but there were some problems before.
The whole benchmark should run for 100 seconds, which I think is plenty of time.
Shuffle777 said that the name GLMark was already taken, does this mean I need to change the name, what is the etiquette on these things?
I get a score of about 10,000 with an 8600GT.

Thanks for all the support.

What are the new dependencies? I'm getting errors from running make.

Edit: Additional libraries are: libsdl-ttf2.0-dev and libglew1.5-dev
I am now seeing the rendering instead of just a black screen! nice work.

---

### Post by bsmith on 2008-04-29
Thanks pointfivezero and pingpongboss for letting me know how you went.
Awesome that it works for you guys, I just need to learn how to actually write shaders and Ill try and make something cool for ya.
Have a nice day :)

---

### Post by bsmith on 2008-04-29
Sorry, I thought I got rid of the links to the sdl ttf lib, either install it of remove the line from oglsdl.h that includes the header file sdl_ttf.h.

Thanks

---

### Post by Mies on 2008-05-15
Really cool. Here are my results using GLMark-0.5.2 :


```
===================================================
    GLMark 08
===================================================
Enter screen width:  1440
Enter screen height: 900
Enter screen bpp:    32
Enter '1' for fullscreen '0' for windowed: 1
===================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce Go 7600/PCI/SSE2
    GL_VERSION:    2.1.2 NVIDIA 169.12
===================================================
Precompilation
    No Precompilation             FPS: 664
    Build list                    FPS: 960
    Vertex array                  FPS: 1127
    Vertex buffer object          FPS: 1118
Texture filtering
    Nearest                       FPS: 1156
    Linear                        FPS: 884
    Mipmapped                     FPS: 1260
Shading
    Smooth shader model      FPS: 839
    GLSL per vertex lighting FPS: 839
    GLSL per pixel lighting  FPS: 785
===================================================
Your GLMark08 Score is 5651  ^_^
===================================================
```


My Notebook details :

```

HP Pavilion dv9000 
Intel(R) Core(TM)2 CPU T5500 @ 1.66GHz
System Memory 2GiB
NVidia G70 [GeForce Go 7600]

$ uname -r
2.6.24-16-generic
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

```


Keep up the good work!

---

### Post by bluehue on 2008-05-20
Pentium IV 3.2 GHZ with 3GB RAM
```

spiral@spiral-desktop:~/Desktop/GLMark-0.5.2$ ./glmark
===================================================
    GLMark 08
===================================================
Enter screen width:  1600
Enter screen height: 1200
Enter screen bpp:    32
Enter '1' for fullscreen '0' for windowed: 1
===================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce 6800 Ultra/AGP/SSE2
    GL_VERSION:    2.1.2 NVIDIA 173.08
===================================================
Precompilation
    No Precompilation             FPS: 707
    Build list                    FPS: 1390
    Vertex array                  FPS: 1643
    Vertex buffer object          FPS: 1790
Texture filtering
    Nearest                       FPS: 2194
    Linear                        FPS: 1622
    Mipmapped                     FPS: 2290
Shading
    Smooth shader model      FPS: 1142
    GLSL per vertex lighting FPS: 1143
    GLSL per pixel lighting  FPS: 779
===================================================
Your GLMark08 Score is 8117  ^_^
===================================================
spiral@spiral-desktop:~/Desktop/GLMark-0.5.2$ 
```

---

### Post by kknd on 2008-05-20
Im receiving a segmentation fault here, with a Intel X3100.

[kknd@TuxDev GLMark-0.5.2]$ ./glmark 
===================================================
    GLMark 08
===================================================
Enter screen width:  1280
Enter screen height: 800
Enter screen bpp:    24
Enter '1' for fullscreen '0' for windowed: 1
===================================================
    OpenGL Information
    GL_VENDOR:     Tungsten Graphics, Inc
    GL_RENDERER:   Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
    GL_VERSION:    1.4 Mesa 7.0.3-rc2
===================================================
Falha de segmentação

---

### Post by pointfivezero on 2008-05-20
> **bsmith said:**
> Thanks pointfivezero and pingpongboss for letting me know how you went.
Awesome that it works for you guys, I just need to learn how to actually write shaders and Ill try and make something cool for ya.
Have a nice day :)

Your welcome, this is an awesome project. Thank you!

> **bsmith said:**
> Sorry, I thought I got rid of the links to the sdl ttf lib, either install it of remove the line from oglsdl.h that includes the header file sdl_ttf.h.

Thanks

Seems funny now I think about it... hmmm, oh well

> **kknd said:**
> Im receiving a segmentation fault here, with a Intel X3100.

[kknd@TuxDev GLMark-0.5.2]$ ./glmark 
===================================================
    GLMark 08
===================================================
Enter screen width:  1280
Enter screen height: 800
Enter screen bpp:    24
Enter '1' for fullscreen '0' for windowed: 1
===================================================
    OpenGL Information
    GL_VENDOR:     Tungsten Graphics, Inc
    GL_RENDERER:   Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
    GL_VERSION:    1.4 Mesa 7.0.3-rc2
===================================================
Falha de segmentação

I have the same problem now with a recent upgrade, ergo

```

===================================================
    GLMark 08
===================================================
Enter screen width:  800
Enter screen height: 600
Enter screen bpp:    32
Enter '1' for fullscreen '0' for windowed: 0
===================================================
    OpenGL Information
    GL_VENDOR:     DRI R300 Project
    GL_RENDERER:   Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 TCL
    GL_VERSION:    1.3 Mesa 7.0.3-rc2
===================================================
Segmentation fault

```


system specs are:

CPU: AMD Athlon64 X2 6400+
CORE 2x@ 3200MHz
RAM: 3096MB DDR2 800
GFX: ATI RADEON X300LE (PCI-E x16) - Temporary, since I can't afford a decent one :)
 CPU @ 350MHz
 MEM @ 200MHz

...

I don't propose to inflict solving the problem on to you, it did  take some time to get direct rendering working with ati drivers (can't wait for NVIDIA card!). I merely suggest that perhaps it is the kernel module / mesa / ati driver at fault, and not so much your code. I could be wrong.

---

### Post by BLTicklemonster on 2008-05-25
> **bsmith said:**
> 
To Compile, extract and...
```
$ cd glmark
$ make
$ ./glmark
```



I beg to differ:

> bill@bill-desktop:~$ cd glmark
bill@bill-desktop:~/glmark$ make
make: `glmark' is up to date.
bill@bill-desktop:~/glmark$ ./glmark
bash: ./glmark: cannot execute binary file


Now if there's some other stuff I need in order to make this work, could you please post what it is? Not all of us follow this thread as well as others, but would still like to benchmark their stuff.


make clean does no better, and removing the .o files and the glmark executable gives me this error:

bill@bill-desktop:~/glmark$ make
gcc -O3 -Wall -c main.cpp
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
make: *** [main.o] Error 1
bill@bill-desktop:~/glmark$ make clean
gcc -O3 -Wall -c main.cpp
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
make: *** [main.o] Error 1
bill@bill-desktop:~/glmark$

running make or make clean, and I'm on a 32 bit system.


Thank you.

---

### Post by BLTicklemonster on 2008-05-25
oO 

Okay, just downloaded the Phoronix Test Suite. 

And I'm lost. 

Went to their site and forums, and it appears as though I'm stuck in command line world and need more than just to download a deb and install it.

One quick question, is it me, or does the 21st century just not exist in Linux land?

---

### Post by bsmith on 2008-05-30
To install

```

sudo apt-get install build-essential

sudo apt-get install libsdl1.2-dev libgl1-mesa-dev libglu1-mesa-dev libglew1.5-dev

cd glmark

make

./glmark
```

Hope this helps

---

### Post by bsmith on 2008-05-30
Hey all, Sorry I haven't been around that much of late, but Ive been busy with exams and stuff.

I'm not sure whats happening with the segmentation fault, I guess Ive tried to access memory that I don't own, and I cant really fix it as I'm not getting the error myself.

Ive uploaded a new version, with a huge update, well actually one line has been changed, the one that requires the installation of the unused ttf library :)

Ive even gone to the trouble of making a youtube account to show the installation and running of the app for those who might be interested, but arnt sure if its worth the bother. Is this cool or not, what does the ubuntu community think of youtube.

[http://www.youtube.com/watch?v=IsBO-Kf2k2U](http://www.youtube.com/watch?v=IsBO-Kf2k2U)

And one more thing for BLTicklemonster, try to delete the glmark executable from the glmark directory and rerun make, might work.

> One quick question, is it me, or does the 21st century just not exist in Linux land? 

I have to disagree, don't know why, but I do. Things might take a little longer to get to work, but when they do Its totally worth it, and doesn't the experience count for anything?

---

### Post by Mickeysofine1972 on 2008-05-30
Here are my test results for my acer TravelMate 5625SWMi:

```
OpenGL Information
GL_VENDOR:    NVIDIA Corporation
GL_RENDERER:    GeForce Go 7300/PCI/SSE2
GL_VERSION:    2.1.2 NVIDIA 169.12

Scene 01, Monkey in Space :P
Tests display lists
Evaluation:
    Total time:    3.230000 seconds
    Total frames:    250
    Average fps:    77.399380

Scene 02, Terrain
Lots of polygons
Evaluation:
    Total time:    7.334000 seconds
    Total frames:    500
    Average fps:    68.175619

Scene 03, Monkey
Will show some fancy vertex shading or something
Evaluation:
    Total time:    12.922000 seconds
    Total frames:    6000
    Average fps:    464.324410

Your GLMark07 score is 304 ^_^

```

Mike

---

### Post by Lster on 2008-05-30
```
===================================================
    GLMark 08
===================================================
Enter screen width:  1280
Enter screen height: 800
Enter screen bpp:    32
Enter '1' for fullscreen '0' for windowed: 1
===================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce 8600M GS/PCI/SSE2
    GL_VERSION:    2.1.2 NVIDIA 169.12
===================================================
Precompilation
    No Precompilation             FPS: 586
    Build list                    FPS: 1217
    Vertex array                  FPS: 1483
    Vertex buffer object          FPS: 1525
Texture filtering
    Nearest                       FPS: 1282
    Linear                        FPS: 963
    Mipmapped                     FPS: 1373
Shading
    Smooth shader model      FPS: 1014
    GLSL per vertex lighting FPS: 1014
    GLSL per pixel lighting  FPS: 800
===================================================
Your GLMark08 Score is 6328  ^_^
===================================================

```

Good work. I would like to see this in the repositories. :)

---

### Post by BLTicklemonster on 2008-05-30
After build essential and the next install listed previously, and removing the executable, I now get this:

```
bill@bill-desktop:~$ cd glmark
bill@bill-desktop:~/glmark$ make
gcc -O3 -Wall -c main.cpp
In file included from main.cpp:1:
nehe.h:30: error: &#8216;<anonymous>&#8217; has incomplete type
nehe.h:30: error: invalid use of &#8216;GLvoid&#8217;
In file included from main.cpp:2:
scene.h:7: error: &#8216;<anonymous>&#8217; has incomplete type
scene.h:7: error: invalid use of &#8216;GLvoid&#8217;
scene.h:8: error: &#8216;<anonymous>&#8217; has incomplete type
scene.h:8: error: invalid use of &#8216;GLvoid&#8217;
scene.h:10: error: &#8216;<anonymous>&#8217; has incomplete type
scene.h:10: error: invalid use of &#8216;GLvoid&#8217;
scene.h:13: error: &#8216;<anonymous>&#8217; has incomplete type
scene.h:13: error: invalid use of &#8216;GLvoid&#8217;
scene.h:15: error: &#8216;<anonymous>&#8217; has incomplete type
scene.h:15: error: invalid use of &#8216;GLvoid&#8217;
scene.h: In function &#8216;int main(int, char**)&#8217;:
scene.h:7: error: too few arguments to function &#8216;int init_scene_01(<type error>)&#8217;
main.cpp:112: error: at this point in file
scene.h:8: error: too few arguments to function &#8216;int draw_scene_01(<type error>)&#8217;
main.cpp:117: error: at this point in file
scene.h:10: error: too few arguments to function &#8216;int init_scene_02(<type error>)&#8217;
main.cpp:123: error: at this point in file
scene.h:13: error: too few arguments to function &#8216;int init_scene_03(<type error>)&#8217;
main.cpp:134: error: at this point in file
make: *** [main.o] Error 1

```

Being the ever diligent type, I went to your sourceforge site (um duh, right?) and downloaded the newest version, and it installed just fine.

I can live with this:

bill@bill-desktop:~/GLMark-0.5.2.1$ ./glmark
===================================================
    GLMark 08
===================================================
Enter screen width:  1280x1024
Enter screen height: Enter screen bpp:    Enter '1' for fullscreen '0' for windowed: ===================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce 8500 GT/PCI/SSE2
    GL_VERSION:    2.1.2 NVIDIA 169.12
===================================================
Precompilation
    No Precompilation             FPS: 543
    Build list                    FPS: 571
    Vertex array                  FPS: 639
    Vertex buffer object          FPS: 919
Texture filtering
    Nearest                       FPS: 853
    Linear                        FPS: 804
    Mipmapped                     FPS: 931
Shading
    Smooth shader model      FPS: 740
    GLSL per vertex lighting FPS: 741
    GLSL per pixel lighting  FPS: 709
===================================================
Your GLMark08 Score is 4423  ^_^
===================================================

---

### Post by bsmith on 2008-05-30
Glad to see that you got it working BLTicklemonster.

Im going to have to compile a nice list of all the results that you champs have been sending in.  Maybe I could make the program send an email or something, but I have no idea at all about how to accomplish this.

> Good work. I would like to see this in the repositories.

Now that would be cool, but how would I go about doing this, and doesn't a program have to be good to get in?

---

### Post by BLTicklemonster on 2008-05-30
BTW, you might request that we all give information on our system, or is the information in the test enough? I'm on an Emachine t3508 3.3 G Celeron, 2 Gigs DDR RAM, and a new Evga Nvidia 8500 GT 1Gig DDR Video card.

---

### Post by CTRLurself on 2008-06-01
I'm not a newby to ubuntu (used for about a year now)... but i've never really gotten into the nitty-gritty of things.

So when i tried to use GLMark to test my laptop, i simply couldn't get the first command to work.

My laptop has no internet connection on it, so i transfered over the archive, unzipped it to the desktop (for convenience) and now, no matter what directory i type it never finds the file. I may be missing something simple here, but any help would be appreciated.

i think I've tried just about every permutation to get the right file directory, but i guess i didn't know as much as i thought (which i know isn't a lot)

And i guess that would be a tip... simplify actually using it. I know it's just an alpha test, but that will be a biggy if this is gonna go truly public.

---

### Post by CTRLurself on 2008-06-02
Please dis-regard my last post, i sorted out my problem

---

### Post by rashaverak on 2008-06-27
make

g++ *.cpp -o glmark -Wall -lSDL -lGL -lGLU -lGLEW


sh glmark

glmark: 1: ELF: not found
glmark: 1: Syntax error: Unterminated quoted string


I am unable to install the nvidia drivers, could it be the problem ?

---

### Post by BLTicklemonster on 2008-06-28
How funny. New motherboard/processor. amd 64 bit forget which, but it's like not slow. ubuntu 64 bit, nvidia 8500 gt i gig card, restricted drivers, 2 gigs ram:

bill@bill-desktop:~/glmark$ ./glmark
===================================================
    GLMark 08
===================================================
Enter screen width:  1600X1200
Enter screen height: Enter screen bpp:    Enter '1' for fullscreen '0' for windowed: ===================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce 8500 GT/PCI/SSE2
    GL_VERSION:    2.1.2 NVIDIA 169.12
===================================================
Precompilation
    No Precompilation             FPS: 398
    Build list                    FPS: 622
    Vertex array                  FPS: 654
    Vertex buffer object          FPS: 786
Texture filtering
    Nearest                       FPS: 739
    Linear                        FPS: 676
    Mipmapped                     FPS: 794
Shading
    Smooth shader model      FPS: 660
    GLSL per vertex lighting FPS: 660
    GLSL per pixel lighting  FPS: 608
===================================================
Your GLMark08 Score is 3809  ^_^
===================================================
bill@bill-desktop:~/glmark$ 



and I get a lower score than I did before.

woot

(prolly cause I haven't tweaked anything, I hope)

---

### Post by svenbertil on 2008-07-20
To stress the card until the end of time, you could do:
```
 while [ 1 = 1 ]; do echo -e "800\n600\n24\n0\n" | ./glmark ; done
```

;)

Thank you for this program.

---

### Post by lamborghiniwang on 2008-07-22
Awesome code!

Here is the result on my Quadro FX 570M (128MB) card on a Thinkpad T61p with 4GB ram, Core 2 Duo T7300 and 64bit Hardy, Compiz and AWN are both running:
===================================================
    GLMark 08
===================================================
Enter screen width:  800
Enter screen height: 600
Enter screen bpp:    24
Enter '1' for fullscreen '0' for windowed: 0
===================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   Quadro FX 570M/PCI/SSE2
    GL_VERSION:    2.1.2 NVIDIA 173.14.09
===================================================
Precompilation
    No Precompilation             FPS: 1014
    Build list                    FPS: 961
    Vertex array                  FPS: 1048
    Vertex buffer object          FPS: 991
Texture filtering
    Nearest                       FPS: 750
    Linear                        FPS: 665
    Mipmapped                     FPS: 981
Shading
    Smooth shader model      FPS: 805
    GLSL per vertex lighting FPS: 805
    GLSL per pixel lighting  FPS: 794
===================================================
Your GLMark08 Score is 5771  ^_^
===================================================

PS: I noticed that in the first test, the horse is not moving at all during the entire test. I don't know if that's normal.
Another observation: if you stop the benchmark by Ctrl-C, your score will be astronomical (maybe need to initialize the variable?). :D

---

### Post by apetresc on 2008-07-22
I re-ran this benchmark on my Macbook Pro and got the following bizarre result:

> adrian@gauss:~/Desktop/GLMark-0.5.2.1$ ./glmark
===================================================
    GLMark 08
===================================================
Enter screen width:  800
Enter screen height: 600
Enter screen bpp:    32
Enter '1' for fullscreen '0' for windowed: 0
===================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   ATI Mobility Radeon X1600
    GL_VERSION:    2.1.7412 Release
===================================================
Precompilation
    No Precompilation             FPS: 548
    Build list                    FPS: 578
    Vertex array                  FPS: 633
===================================================
Your GLMark08 Score is 728040911  ^_^
===================================================

A score of 728,040,911 seems... rather high... several thousand times higher than any other score posted on this thread, I think.

Is there a bug in the benchmarker or is my Macbook Pro just the most insane OpenGL machine known to man? O_o;

---

### Post by lamborghiniwang on 2008-07-22
Not sure if it's normal, but it seems this benchmark doesn't work on the integrated Intel x3100 video card. Got a segmentation fault.

---

### Post by Norwal on 2008-09-06
This is an great project.  Thanks BSmith.:)

  GLMark 08
===================================================
Enter screen width:  1440x900
Enter screen height: Enter screen bpp:    Enter '1' for fullscreen '0' for windowed: ===================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce 9600 GT/PCI/SSE2
    GL_VERSION:    2.1.2 NVIDIA 173.14.12
===================================================
Precompilation
    No Precompilation             FPS: 449
    Build list                    FPS: 2185
    Vertex array                  FPS: 2321
    Vertex buffer object          FPS: 3311
Texture filtering
    Nearest                       FPS: 3465
    Linear                        FPS: 3222
    Mipmapped                     FPS: 3781
Shading
    Smooth shader model      FPS: 2740
    GLSL per vertex lighting FPS: 2674
    GLSL per pixel lighting  FPS: 2681
===================================================
Your GLMark08 Score is 13808  ^_^

---

### Post by Norwal on 2008-09-06
My machine is:

Dual Core AMD Opteron(tm) Processor 180
1.5 KVR PC3200
ASUS A8N SLI SE

I re-ran LGMark in full screen mode. 

   GLMark 08
===================================================
Enter screen width:  1440
Enter screen height: 900
Enter screen bpp:    32
Enter '1' for fullscreen '0' for windowed: 1
===================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce 9600 GT/PCI/SSE2
    GL_VERSION:    2.1.2 NVIDIA 173.14.12
===================================================
Precompilation
    No Precompilation             FPS: 436
    Build list                    FPS: 1768
    Vertex array                  FPS: 1881
    Vertex buffer object          FPS: 2537
Texture filtering
    Nearest                       FPS: 2499
    Linear                        FPS: 2161
    Mipmapped                     FPS: 2518
Shading
    Smooth shader model      FPS: 2115
    GLSL per vertex lighting FPS: 2115
    GLSL per pixel lighting  FPS: 2031
===================================================
Your GLMark08 Score is 10493  ^_^

:lolflag:

---

### Post by happysmileman on 2008-09-06
```
===================================================
    GLMark 08
===================================================
Enter screen width:  800
Enter screen height: 600
Enter screen bpp:    24
Enter '1' for fullscreen '0' for windowed: 0
===================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce4 MX 440/AGP/SSE2
    GL_VERSION:    1.5.8 NVIDIA 96.43.05
===================================================
Segmentation fault
```

Happens with both 0.5.2 and 0.5.2.1 from sourceforge

---

### Post by Norwal on 2008-09-06
Happy,

Try entering 800X600 at the Width line. It will run the rest of the setting at default.

---

### Post by happysmileman on 2008-09-06
> **Norwal said:**
> Happy,

Try entering 800X600 at the Width line. It will run the rest of the setting at default.

Still same problem

---

### Post by nidomedia on 2008-11-16
nido@toad:~/Desktop/GLMark-0.5.2.1$ ./glmark 
===================================================
    GLMark 08
===================================================
Enter screen width:  800x600
Enter screen height: Enter screen bpp:    Enter '1' for fullscreen '0' for windowed: ===================================================
    OpenGL Information
    GL_VENDOR:     Tungsten Graphics, Inc
    GL_RENDERER:   Mesa DRI Intel(R) 965GM 20061102
    GL_VERSION:    1.4 Mesa 7.2
===================================================
Segmentation fault

sorry dude

---

### Post by zoubidoo on 2008-12-05
I reported the segfault on sourceforge back in July but got no reply from the developer.  [http://sourceforge.net/tracker/index.php?func=detail&aid=2022251&group_id=224203&atid=1061105](http://sourceforge.net/tracker/index.php?func=detail&aid=2022251&group_id=224203&atid=1061105)

Z.

---

### Post by marcthenarc on 2009-03-24
```

foo@foo:~/GLMark-0.5.2.1$ ./glmark
===================================================
    GLMark 08
===================================================
Enter screen width:  800
Enter screen height: 600
Enter screen bpp:    24
Enter '1' for fullscreen '0' for windowed: 1
===================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   ATI Radeon 9550 / X1050 Series
    GL_VERSION:    2.1.8395 Release
===================================================
Precompilation
    No Precompilation             FPS: 242
    Build list                    FPS: 337
    Vertex array                  FPS: 384
    Vertex buffer object          FPS: 517
Texture filtering
    Nearest                       FPS: 785
    Linear                        FPS: 618
    Mipmapped                     FPS: 1070
Shading
    Smooth shader model      FPS: 308
    GLSL per vertex lighting FPS: 307
    GLSL per pixel lighting  FPS: 308
===================================================
Your GLMark08 Score is 2673  ^_^
===================================================

```

Doesn't seem to be a high mark, does it ? ;)
My machine is a Pentium IV, 2.4mHz, running Ubuntu Hardy.


---

Marc St-Jacques

[http://geekchef.com](http://geekchef.com)
[http://nihongo.geekchef.com](http://nihongo.geekchef.com)

---

### Post by mifritscher on 2009-04-11
works fine for me with the x3100
./glmark 
===================================================
    GLMark 08
===================================================
Enter screen width:  800
Enter screen height: 600
Enter screen bpp:    24
Enter '1' for fullscreen '0' for windowed: 0
===================================================
    OpenGL Information
    GL_VENDOR:     Tungsten Graphics, Inc
    GL_RENDERER:   Mesa DRI Intel(R) 965GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
    GL_VERSION:    2.0 Mesa 7.4
===================================================
Precompilation
    No Precompilation             FPS: 68
    Build list                    FPS: 87
    Vertex array                  FPS: 103
    Vertex buffer object          FPS: 275
Texture filtering
    Nearest                       FPS: 298
    Linear                        FPS: 250
    Mipmapped                     FPS: 394
Shading
    Smooth shader model      FPS: 160
    GLSL per vertex lighting FPS: 160
    GLSL per pixel lighting  FPS: 160
===================================================
Your GLMark08 Score is 1030  ^_^
===================================================


./glmark 
===================================================
    GLMark 08
===================================================
Enter screen width:  1200
Enter screen height: 960
Enter screen bpp:    24
Enter '1' for fullscreen '0' for windowed: 0
===================================================
    OpenGL Information
    GL_VENDOR:     Tungsten Graphics, Inc
    GL_RENDERER:   Mesa DRI Intel(R) 965GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
    GL_VERSION:    2.0 Mesa 7.4
===================================================
Precompilation
    No Precompilation             FPS: 52
    Build list                    FPS: 44
    Vertex array                  FPS: 51
    Vertex buffer object          FPS: 146
Texture filtering
    Nearest                       FPS: 143
    Linear                        FPS: 117
    Mipmapped                     FPS: 151
Shading
    Smooth shader model      FPS: 103
    GLSL per vertex lighting FPS: 104
    GLSL per pixel lighting  FPS: 104
===================================================
Your GLMark08 Score is 563  ^_^
===================================================

---

### Post by tmtfx on 2009-04-13
the same error for S3 Chrome 20 series error on ubuntu 8.10:

===================================================
    GLMark 08
===================================================
Enter screen width:  800
Enter screen height: 600
Enter screen bpp:    24
Enter '1' for fullscreen '0' for windowed: 0
===================================================
    OpenGL Information
    GL_VENDOR:     S3 Graphics, Incorporated
    GL_RENDERER:   S3 Graphics Chrome20 Series
    GL_VERSION:    1.5 12.01.01
===================================================
Segmentation fault

it starts and appear a black window then it closes and segfault...

---

### Post by alexv75 on 2009-04-24
===================================================
    GLMark 08
===================================================
Enter screen width:  1920
Enter screen height: 1200
Enter screen bpp:    24
Enter '1' for fullscreen '0' for windowed: 1
===================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce 7950 GT/PCI/SSE2
    GL_VERSION:    2.1.2 NVIDIA 185.18.04
===================================================
Precompilation
    No Precompilation             FPS: 1038
    Build list                    FPS: 1545
    Vertex array                  FPS: 1769
    Vertex buffer object          FPS: 2744
Texture filtering
    Nearest                       FPS: 2432
    Linear                        FPS: 1861
    Mipmapped                     FPS: 2525
Shading
    Smooth shader model      FPS: 1734
    GLSL per vertex lighting FPS: 1737
    GLSL per pixel lighting  FPS: 1593
===================================================
Your GLMark08 Score is 10711  ^_^
===================================================

---

### Post by swietowid on 2009-08-11
===================================================
    GLMark 08
===================================================
Enter screen width:  1280
Enter screen height: 1024
Enter screen bpp:    24 
Enter '1' for fullscreen '0' for windowed: 1
===================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce 8400 GS/PCI/SSE2
    GL_VERSION:    3.2.0 NVIDIA 190.18.03
===================================================
Precompilation
    No Precompilation             FPS: 618
    Build list                    FPS: 544
    Vertex array                  FPS: 647
    Vertex buffer object          FPS: 616
Texture filtering
    Nearest                       FPS: 498
    Linear                        FPS: 378
    Mipmapped                     FPS: 531
Shading
    Smooth shader model      FPS: 432
    GLSL per vertex lighting FPS: 432
    GLSL per pixel lighting  FPS: 388
===================================================
Your GLMark08 Score is 3362  ^_^
===================================================

---

### Post by AaronD12 on 2009-09-24
I think it would be a good idea to display the CPU, RAM, OS 32/64-bit, etc., when displaying the results of the benchmark.

FWIW: This is from my new Core i7 860 (2.8GHz) with BFG nVidia 9800 GTX OC, 4GB RAM, and Gigabyte M55-D4 motherboard, running Jaunty Jackelope in 64-bit mode.


```
===================================================
    GLMark 08
===================================================
Enter screen width:  1024
Enter screen height: 768
Enter screen bpp:    24
Enter '1' for fullscreen '0' for windowed: 1
===================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce 9800 GTX/9800 GTX+/PCI/SSE2
    GL_VERSION:    3.0.0 NVIDIA 180.44
===================================================
Precompilation
    No Precompilation             FPS: 775
    Build list                    FPS: 4317
    Vertex array                  FPS: 5031
    Vertex buffer object          FPS: 6092
Texture filtering
    Nearest                       FPS: 6065
    Linear                        FPS: 5032
    Mipmapped                     FPS: 6163
Shading
    Smooth shader model      FPS: 4335
    GLSL per vertex lighting FPS: 4336
    GLSL per pixel lighting  FPS: 4334
===================================================
Your GLMark08 Score is 23877  ^_^
===================================================
```

---

### Post by Clancy_s on 2009-12-14
On a Toshiba Satellite A200 with a Mobility Radeon HD2600 and the ATI drivers from the Ubuntu 9.10 64 bit repository:

./glmark
===================================================
    GLMark 08
===================================================
Enter screen width:  640
Enter screen height: 480
Enter screen bpp:    32
Enter '1' for fullscreen '0' for windowed: 0
===================================================
    OpenGL Information
    GL_VENDOR:     ATI Technologies Inc.
    GL_RENDERER:   ATI Mobility Radeon HD 2600
    GL_VERSION:    2.1.9016
===================================================
Precompilation
    No Precompilation             FPS: 978
    Build list                    FPS: 860
    Vertex array                  FPS: 886
    Vertex buffer object          FPS: 549
Texture filtering
    Nearest                       FPS: 433
    Linear                        FPS: 407
    Mipmapped                     FPS: 497
Shading
    Smooth shader model      FPS: 400
    GLSL per vertex lighting FPS: 400
    GLSL per pixel lighting  FPS: 400
===================================================
Your GLMark08 Score is 4249  ^_^
===================================================

fwiw:

$ glxgears
7117 frames in 5.0 seconds
7519 frames in 5.0 seconds
7175 frames in 5.0 seconds
5974 frames in 5.0 seconds
6132 frames in 5.0 seconds
7143 frames in 5.0 seconds
7585 frames in 5.0 seconds

---

