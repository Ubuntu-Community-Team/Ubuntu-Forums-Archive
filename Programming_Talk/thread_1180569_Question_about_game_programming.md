---
title: "Question about game programming"
date: 2009-06-07
forum: Programming Talk
---

### Post by feardotcom on 2009-06-07
I&#8217;m learning programming in college (working on an associate&#8217;s degree) and so far we have not got into much about game programming. Can someone explain to me the theory of game programming? How everything is integrated? OpenGL and all this talk about render engines. Is it 2 separate applications used separately or is it used together. 

Reason being is once i get my c++ classes (probably early 2010) I&#8217;m hoping to start an open source game project. I am already working on the graphics in blender.

---

### Post by Ferrat on 2009-06-07
Basics it this

You got an Game Loop
Within that loop you got the game that is constructed by different parts
Input
AI
GameUpdates
Graphics
Sound 
Network 
etc.

The loop itself is running very fast and usually you limit the different parts like rendering for ex. since you don't need to and often shouldn't try pushing out to much and you only need 30-60FPS for a good flow so the loop can put more effort to other stuff. 

In this game engine (the loop more or less) for ex. you can put rendering in if you want graphics, OpenGL is one way to do this, OpenGL is only a graphics API meaning it only handles just graphics and not input, sound etc, reason for the confusion is much due to Microsoft I think with DirectX, DirectX is a collection of APIs for input, sound, network, graphics etc, the graphics are Direct 3D but when game vendors puts it as requirements it's often listed under the graphics part because the card you use needs to be compatable with for ex. DirectX 9, same as it says OpenGL 2.1 or something the Direct X should really then say DirectX9 - Direct 3D or something but since DirectX in a package deal it doesn't matter.

It's all put together in different ways when you run a game you most often only have one main executable that handles all the different parts connecting them. 

hope that clears it up a little.

---

### Post by feardotcom on 2009-06-07
That clears up a fair amount. However, i am still alittle confused on whats the difference between a game engine and opengl/direct3d

---

### Post by simeon87 on 2009-06-07
> **feardotcom said:**
> That clears up a fair amount. However, i am still alittle confused on whats the difference between a game engine and opengl/direct3d

The game engine takes care of everything and rendering is just a part of that. Rendering on the screen can be done through OpenGL/Direct3D but the game engine also takes care of sound, user input, network connections, et cetera. So the game engine is the underlying software of a game and, as part of that duty, it takes care of the rendering.

---

### Post by feardotcom on 2009-06-07
Ok, i think i understand now.

So for example, companies that say they use the UT3 game engine. basically just saying the only thing they did to a game other than program the sequence was develope maps, characters, props and textures.

Would that be an acurate statement?

---

### Post by simeon87 on 2009-06-07
> **feardotcom said:**
> So for example, companies that say they use the UT3 game engine. basically just saying the only thing they did to a game other than program the sequence was develope maps, characters, props and textures.

Would that be an acurate statement?

Usually companies have a license to modify the engine to their needs, so they use the Unreal Engine and they build upon that. They develop all the content (like you say, maps, textures, ...) but they also add features to the engine that are needed for their game.

---

### Post by feardotcom on 2009-06-07
Im wondering how difficult it would be to develope a opengl state of the art game engine for a racing game.

---

### Post by simeon87 on 2009-06-07
> **feardotcom said:**
> Im wondering how difficult it would be to develope a opengl state of the art game engine for a racing game.

State of the art is always difficult, in particular without prior experience ;)

---

### Post by feardotcom on 2009-06-07
lol, yeah seriously. So i guess i know what i will be doing for the next 10 years of my life....lol

---

### Post by hessiess on 2009-06-07
> **feardotcom said:**
> Im wondering how difficult it would be to develope a opengl state of the art game engine for a racing game.

For a 3D game there isn't a whole lot of point developing a complete engine from scratch, as there are plenty of decent open source engines avalable and ready for use. Irrlicht, Crystal space and ogre for example. If you developed your own engine you would just end up re-inventing wheels a whole lot and never get the game made.

---

### Post by feardotcom on 2009-06-07
I didn't think the open source game engines were made for racing games?

---

### Post by simeon87 on 2009-06-07
> **feardotcom said:**
> I didn't think the open source game engines were made for racing games?

An engine is not a game, you still have to program the game using the engine. So you can take an open source 3D engine and then create a racing game. Most engines are general purpose engines so they deliver the underlying functionality of a game but they're not geared towards a specific genre, such as racing.

---

### Post by feardotcom on 2009-06-07
OHHH, ok, i thinnk got it now.

---

### Post by Falcon1002 on 2009-06-07
Hello! If your interested in developing a racing game you could start with an open source racing game like Torcs and change that to what you want. It would be easier then starting from scratch.

---

### Post by feardotcom on 2009-06-07
Interesting, im going to have to look into. It has good graphics, crappy models, but good graphics. 

My goal is to, hopefully, create a MMO racing game strictly for linux. Kind of think of NFS Most wanted meets the WoW servers. Im not sure if i want to do it open source or closed source, but still free.

---

### Post by kahootbot on 2009-06-07
About Falcon's comment. Just make sure you have somewhat of a hand on the openGL API and any other libraries you need before attempting anything to big.. Start small and work your way up, lest your current skill level make you give up and abandon the project.

I'm not trying to put it to high up for you, I'm just saying most programmers start out with to big of a project and never finish it. I did with an old allegro game. Just remember there is nothing wrong with remaking something as simple as space invaders. This would help you learn about OpenGL image surface blitting, sound output, AI logic, etc. 
You can do it, just don't overextend. Best wishes ;)

---

### Post by jimi_hendrix on 2009-06-07
i hope you have some artist friends that can help you...its a lot of work programing and doing the graphics yourself

---

### Post by feardotcom on 2009-06-07
Yeah, i thought aboutn that, and i decided, im just gonna do a small city in blender, and one car, and as a test run i was going to create a small scale city with people walking, have one car and be able to drive around the city, and eventually add in a race or 2. 

I have a good amount of time before i get to my c++ classes, so i have plenty of time to create every little detail in this small world. I'm probably going to write some how-to's and general info writings on creating graphics with blender for games. Afterall, there isn't much on the subject to begin to with, atleast not from what i can find.

---

### Post by soltanis on 2009-06-07
Games are the most involved programs you'll probably ever write, with the probable exception of OS kernels. They are very, very complex, and must be very structured; in particular, strict coding discipline must be used (especially if you're managing the memory yourself, which unless you are using Java, you will be doing) to prevent random crashes and memory consumption.

Above all, games integrate concepts from all over the fields of electronic entertainment, sound, video, 3D rendering and effects, logic, user interaction, and physics.

---

### Post by feardotcom on 2009-06-08
Yeah its going to be a learning curve, and a work in progress.

---

