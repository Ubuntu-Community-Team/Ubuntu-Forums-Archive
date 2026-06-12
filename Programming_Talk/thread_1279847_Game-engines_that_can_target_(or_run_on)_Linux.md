---
title: "Game-engines that can target (or run on) Linux?"
date: 2009-10-01
forum: Programming Talk
---

### Post by ucoder on 2009-10-01
Hi!

I'm not sure if this is really the correct forum, but I'll ask anyway :)

Are there any game-engines around that can target linux? Or better yet, run on linux and can target it?

I use Unity3D on windows, but that can't even target linux currently, although quite a lot of other platforms are supported. I've also been looking at Torque3D, but I guess the same applies to it.

---

### Post by hessiess on 2009-10-01
Irrlicht is pretty good, Ogre and crystal space are two more.

---

### Post by ucoder on 2009-10-01
Hey, thanks!

Do you have experience in using these? I mean, which one is considered the most advanced or "active" currently? 
I have no experience in any of these, just Unity3d currently.

And what about things like physics engines? COLLADA support? (this Irrlicht mentions to support it) Any differences there?

Thanks again!

---

### Post by hessiess on 2009-10-01
> **ucoder said:**
> Hey, thanks!

Do you have experience in using these? I mean, which one is considered the most advanced or "active" currently? 
I have no experience in any of these, just Unity3d currently.

And what about things like physics engines? COLLADA support? (this Irrlicht mentions to support it) Any differences there?

Thanks again!

Irrlicht is the only one I have used and is very easy to use (I was using Irrlicht *before* I learnt the details of C++:) ) and its active on the development side too. Physics engines are just external programs which can be linked into and used with a graphics engine, there are a number of tutorials for integrating irrlicht with different physics engines.

Regarding collada, support, can't say because I haven't used it.

---

### Post by ucoder on 2009-10-01
Alright, thanks again!

I will definitely check out Irrlicht - judging what's on their web site, it seems pretty cool :)
  
I guess ideally you could make your games independent of the Physics engine using whatever is available on the target platform. There's an abstraction layer for them, but I'm no expert in this stuff: [http://www.adrianboeing.com/pal/](http://www.adrianboeing.com/pal/)
  
COLLADA (a file format) is pretty much necessity for me because I model in XSI, which is usually not natively supported by "consumer" game-engines.

---

### Post by hessiess on 2009-10-01
> **ucoder said:**
> Alright, thanks again!

I will definitely check out Irrlicht - judging what's on their web site, it seems pretty cool :)
  
I guess ideally you could make your games independent of the Physics engine using whatever is available on the target platform. There's an abstraction layer for them, but I'm no expert in this stuff: [http://www.adrianboeing.com/pal/](http://www.adrianboeing.com/pal/)
  
COLLADA (a file format) is pretty much necessity for me because I model in XSI, which is usually not natively supported by "consumer" game-engines.

Regarding physics engines, both ODE and Bullet(Used in Blender) run on basically everything, you would only have a problem if you were using PhysX or any other platform dependent lib.

---

### Post by grayrainbow on 2009-10-01
Depending on how soon you want to work on your game I'll suggest to wait a while with physics, OpenCL is expected to be implemented(in real form) on most platforms, but after all you can just use it for AI :)

---

### Post by ucoder on 2009-10-01
Well, basically I want to start right away. Or rather, I want to migrate some of my ideas for Unity3D in the Windows/Mac world, to "linux-enabled" tools, targetting linux platform.

I'm also very interested to see if I can get something working on Maemo using these tools. After all, it's a linux as well, although as a mobile platform it "only" has OpenGL ES for 3d graphics, but that shouldn't be incompatible with full OpenGL, afaik.

Right now, it's not really important for me which physics engine I can use, but of course, the more advanced the better :)

Got to check out OpenCL also - I'm not really familiar with that either.

---

