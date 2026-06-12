---
title: "Differences between Mono Linux and Mono Win"
date: 2007-05-20
forum: Programming Talk
---

### Post by b4silence on 2007-05-20
Hello all!
 
I'm porting a game from c++ to c# and i'm using mono 1.2.3.1 to build it. I also use the assemblies SDL.NET 6.0.0 and Tao 2.0.
 
In order to make sure it all will work well I ran some example programs. I got problems when I found that the textures were messed only on Linux's mono...
 
I tried it with mono 1.2.3.1 on both Linux and Windows and also tried with the .Net 2.0 framework.
 
This is what i got using mono and .net 2.0 on windows (seems right):
[http://cs-sdl.sourceforge.net/images/4/49/NeHe006.jpg](http://cs-sdl.sourceforge.net/images/4/49/NeHe006.jpg)
 
In linux with mono and the same assemblies I get this (doesn't seem right Undecided):
[http://www.dei.isep.ipp.pt/~i020612/nehe006.png](http://www.dei.isep.ipp.pt/~i020612/nehe006.png)
 
The code I used to test this feature was this:
[http://www.dei.isep.ipp.pt/~i020612/NeHe.tar.gz](http://www.dei.isep.ipp.pt/~i020612/NeHe.tar.gz)
 
The command I used to compile it was:
```
gmcs -r:SdlDotNet.dll -r:Tao.Sdl.dll -r:Tao.OpenGl.dll -r:System.Drawing NeHe001.cs NeHe006.cs
```
 
An ran it using:
Code:
```
mono NeHe001.exe
```
 
My graphics card is an ATI X1100 and i'm using the fgrlx proprietary driver, running games perfectly...
 
Any thoughts on this?
 
Thanks a lot!

---

