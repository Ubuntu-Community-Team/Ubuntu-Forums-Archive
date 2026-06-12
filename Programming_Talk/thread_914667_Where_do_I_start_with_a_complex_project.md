---
title: "Where do I start with a complex project?"
date: 2008-09-09
forum: Programming Talk
---

### Post by booljayj on 2008-09-09
Okay, so here's the rundown:
I'm not a beginner to programming, and I've been able to make small projects with Bash, Python, C++, and a few others. These projects were simple, and usually only addressed a single need, so I found that online tutorials were plenty.

This time, however, I'm stepping it up a notch, and I find that my knowledge of programming, although adequate, has some gaping holes as far as complex projects go.

Here's my dilemma:
I'm trying to program a game. Not a huge one, but due to the nature of the project I need to interface with Ogre3d, SDL, and python scripts, all from a base of C++. Now, I know how to use all these tools separately, but I have no idea how to use them together.
For instance, I have Ogre1.4 installed on my system. There are no -dev packages, it's just ogre1.4. Whenever I try and use the tutorials from the ogre3d wiki, I find that g++ simply cannot find Ogre.h on my system. Most of the tutorials on the wiki use a file called ExampleApplication.h. I can find this file, but it requires a load of other ogre source files to work.
-How do I tell g++ where to look for the Ogre headers? And is there an easy way to make sure it will use the appropriate headers it finds on my system?

I have a partner in this venture. He is a CS major, but his forte is Java. As such, he doesn't really know much about constructing a project in C++.
-Can anyone give me a clear, concise explanation of how to create and use C++ Header files?

Overall, I think that we need the help of someone with experience. If you have some experience writing complex projects in C++, Python, Ogre3d, or SDL, here's a brief overview of the project:

"The idea is a Tactical, Turn-based Role-playing game in the style of Final Fantasy Tactics (the original), but expanding on the concept to create something truly unique and powerful. The project will take base concepts from Tactics such as a default Isometric view, a grid-structured battle arena, character classes, and leveling; and add features like real-time modifiable terrain, advanced class techniques, deep inter-class actions, and enhanced player interaction with the landscape. It will be written in C++ and Python with Ogre3d and SDL, and from the start will be designed to be cross-platform"

Interested? Any help is appreciated. Currently, we have 0 code and many ways of doing things. Please reply on here if you have any advice.

---

### Post by amo-ej1 on 2008-09-09
Have you installed libogre-dev ? 

```

edb@lapedb:~$ dpkg -L libogre-dev | grep Ogre.h
/usr/include/OGRE/Ogre.h

```

Then you should call g++ with -I/usr/include/OGRE (if you entered #include <Ogre.h> ) this will make g++ search for header files in the directory '/usr/include/OGRE'

You should also link your final project with some Ogre libraries this can be done with passing -l<libraryname> 

```

edb@lapedb:/usr/lib$ ls /usr/lib/libOgr*
/usr/lib/libOgreMain.la  /usr/lib/libOgreMain.so.14
/usr/lib/libOgreMain.so  /usr/lib/libOgreMain.so.14.0.5

```

e.g. 

```

edb@lapedb:/tmp$ cat ogretest.cpp 
#include <Ogre.h>
using namespace Ogre;

int main(int argc, char **argv)
{
   Root *root = new Root();
   if(!root->showConfigDialog())
   {
      return 0;
   } 
}
edb@lapedb:/tmp$ g++ -Wall -I/usr/include/OGRE/ -lOgreMain ogretest.cpp -o testogre
edb@lapedb:/tmp$ ./testogre 
Creating resource group General
Creating resource group Internal
Creating resource group Autodetect
SceneManagerFactory for type 'DefaultSceneManager' registered.
Registering ResourceManager for type Material
Registering ResourceManager for type Mesh
Registering ResourceManager for type Skeleton
MovableObjectFactory for type 'ParticleSystem' registered.
OverlayElementFactory for type Panel registered.
OverlayElementFactory for type BorderPanel registered.
OverlayElementFactory for type TextArea registered.
Registering ResourceManager for type Font
ArchiveFactory for archive type FileSystem registered.
ArchiveFactory for archive type Zip registered.
FreeImage version: 3.9.3
This program uses FreeImage, a free, open source image library supporting all common bitmap formats. See http://freeimage.sourceforge.net for details
Supported formats: bmp,ico,jpg,jif,jpeg,jpe,jng,koa,iff,lbm,mng,pbm,pbm,pcd,pcx,pgm,pgm,png,ppm,ppm,ras,tga,targa,tif,tiff,wap,wbmp,wbm,psd,cut,xbm,xpm,gif,hdr,g3,sgi
DDS codec registering
Registering ResourceManager for type HighLevelGpuProgram
Registering ResourceManager for type Compositor
MovableObjectFactory for type 'Entity' registered.
MovableObjectFactory for type 'Light' registered.
MovableObjectFactory for type 'BillboardSet' registered.
MovableObjectFactory for type 'ManualObject' registered.
MovableObjectFactory for type 'BillboardChain' registered.
MovableObjectFactory for type 'RibbonTrail' registered.
plugins.cfg not found, automatic plugin loading disabled.
*-*-* OGRE Initialising
*-*-* Version 1.4.5 (Eihort)

```

That should get your ogre development starting 

And on the other questions, first THINK, split your project in modules, seperate the python and the C++ development, setup a proper build system ....

---

### Post by mujambee on 2008-09-09
Basic steps:

[LIST=1]
[*]**Lay out your objectives**. In this case, you should have a detailed set of features you want in your game, maybe two lists, MUSTs and COULDs.
[*]**Design architecture.** Define the basic architecture of your program and how are your modules to interact.
[*]**Detailed design.** Design each module to its lower detail, define data structures and try to identify possible traps.
[*]**Estimate times.** This is the trickiest and, for me, one of the most important parts of ANY project. Analyze each task at hand and try to advance how much time will it take. Be pessimistic and don be surprised if things start adding up, they always do. Add 25%, you'll use it.
[*]**Plan.** Once you have an estimate of the time every task will take, you can lay them out on a calendar. Leave room for problems, if a computer breaks down on Friday you may need to wait till Monday to fix it.
[*]**Start coding.** If you have reached this point, you can start coding your game.
[/LIST]
And a few extra advices:

[LIST]
[*]Stick to your schedule. If you don't strictly follow it, you'll never end it, that's for sure. One trick is having fixed and floating milestones. Fixed milestones cover full modules or big tasks and MUST be strictly met, floating milestones cover subtask in the fixed ones an can to bee loosely followed, but keep in mind that if you are late for a floating you must sprint to catch up on the next one. Ideally fixed milestones are set 8 weeks apart and floatings are a week apart.
[*]Include auxiliary tools in the plan. For a game, you'll need not only the engine, but also editors for maps, units, textures,... whatever data file you'll use, you will also need an editor o a converter.
[*]Plan on your art and level design. This will take far more time than your software.
[/LIST]

---

### Post by pmasiar on 2008-09-09
Extra advice: for a year, join existing project doing similar game, learn their workflow and tricks. This will let you:
- learn from their experience (instead from your own mistakes)
- gain skills in handling big projects you so obviously lack
- gain name recognition for your good work
- which would allow you to recruit people to help you with your own project: you will need it, your project might easily be 10 man-years.

so "wasting" a year will help you to avoid stupid design decisions, and might allow you to  recruit say 3 more developers, so you finish your game in 1+3 years total, instead of 10 years doing it alone.

Just a thought. See also FAQ in my sig.

---

### Post by rnodal on 2008-09-09
Have you posted your problems at ogre3d.org? Nothing wrong with posting here but you may get a quicker response there and probably in more detail since most people there deal with Ogre every day. Also consider downloading the source code of Ogre3D from their site instead of using the Ubuntu packages. I always found compiling the source better than using the Ubuntu packages. Also if remember well(I have not touched Ogre in a big while), integrating SDL+Ogre is not that trivial. Take care,

-r

---

### Post by booljayj on 2008-09-11
Very helpful, thank you all very much! This should get me going for a while.

---

