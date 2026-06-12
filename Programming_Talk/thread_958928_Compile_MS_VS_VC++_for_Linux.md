---
title: "Compile MS VS VC++ for Linux"
date: 2008-10-25
forum: Programming Talk
---

### Post by Sir-Rogers on 2008-10-25
Hello everybody,

as the topic indicates this is about compiling vc++ code that will run under Linux. I'm planning to create a 3D game which will run on MacOS X, Linux/UNIX and Windows platforms.

Now I need to know how to do that, basically :-)
I will not make use of any win api's and I will be using ogre3d as an engine, which is supported on all of those platforms.

Is it at all possible to do this with the Visual Studio 2008 Edition, using VC++? Or would I have to resort to C++ ANSI standards in order for it to be usable on platforms other than Windows?

Any help on this is greatly appreciated. If it is not possible with the VS Compiler, could anyone please guide me on what compiler/IDE to use?

Thanks in advance.

---

### Post by LaRoza on 2008-10-25
> **Sir-Rogers said:**
> 
Is it at all possible to do this with the Visual Studio 2008 Edition, using VC++? Or would I have to resort to C++ ANSI standards in order for it to be usable on platforms other than Windows?

That pretty much says it all...

Use the standards. Follow them. Worship them. 

> 
Any help on this is greatly appreciated. If it is not possible with the VS Compiler, could anyone please guide me on what compiler/IDE to use?


Use gcc (g++, for C++), and any editor or IDE you wish. See the stickies on how to use g++ and an overview of the IDE situation.

---

### Post by Sir-Rogers on 2008-10-25
> **LaRoza said:**
> 
Use gcc (g++, for C++), and any editor or IDE you wish. See the stickies on how to use g++ and an overview of the IDE situation.

The stickies only mention gcc for Linux?

My OS is Windows XP. Could you help me please on how to use gcc for c++ under Windows XP?

---

### Post by LaRoza on 2008-10-25
> **Sir-Rogers said:**
> The stickies only mention gcc for Linux?

My OS is Windows XP. Could you help me please on how to use gcc for c++ under Windows XP?

See my wiki.

You can use Dev-CPP which is pretty good and uses gcc and g++ for compiling. My wiki has information on them under C++. [http://laroza77.wikidot.com/cpp](http://laroza77.wikidot.com/cpp)

---

### Post by NovaAesa on 2008-10-25
You can use Cygwin to run gcc/g++ under Windows.

---

### Post by Sir-Rogers on 2008-10-25
Ok that looks awesome.

Well let me put it straight, I've been coding for quite a while and I've changed languages quite a bit. From C to VB to Java to C# and now to C++ ... My goal is it to make my own game. I've got the firm ideas in my head and I made a nice server already in C#, which I am intending to keep.

Now my problem is getting the client done, and I did a lot of research, but it's not an easy field to experiment around in for a newbie. I know if I want to go cross-platform OpenGL is my best bet; could you recommend any book or website with tutorials for programming games in OpenGL with C++?

That would be everything for now :-)
I've done a lot in DX9 and some DX10 but nothing with OpenGL yet, and I've been told that they're very different ...

---

### Post by LaRoza on 2008-10-26
> **Sir-Rogers said:**
> 

Now my problem is getting the client done, and I did a lot of research, but it's not an easy field to experiment around in for a newbie. I know if I want to go cross-platform OpenGL is my best bet; could you recommend any book or website with tutorials for programming games in OpenGL with C++?

That would be everything for now :-)
I've done a lot in DX9 and some DX10 but nothing with OpenGL yet, and I've been told that they're very different ...

It isn't much, but it should get you started: [http://laroza77.wikidot.com/opengl](http://laroza77.wikidot.com/opengl)

---

### Post by Sir-Rogers on 2008-10-26
Ok if you don't mind me asking another question, there's one thing that I haven't figured out yet.

Let's say I make an OpenGL application in my Dev-C++ IDE. How can I now compile the release version for MacOS X and Linux? So that I only copy the files onto a machine running MacOS X/Linux and then I can start the application? (provided the machine has the dependencies installed on it)

---

### Post by LaRoza on 2008-10-26
> **Sir-Rogers said:**
> 
Let's say I make an OpenGL application in my Dev-C++ IDE. How can I now compile the release version for MacOS X and Linux? So that I only copy the files onto a machine running MacOS X/Linux and then I can start the application? (provided the machine has the dependencies installed on it)

It is called "source distribution".

You could try to cross compile, but I don't know how to do that (on Windows) and having source archives with a makefile is the most portable way (for using something like C++).

---

### Post by Sir-Rogers on 2008-10-26
> **LaRoza said:**
> It is called "source distribution".

You could try to cross compile, but I don't know how to do that (on Windows) and having source archives with a makefile is the most portable way (for using something like C++).

I never got this whole makefile thing. Do I have to get a makefile, export it to a machine with the desired platform and then compile it on that machine?

So take the makefile from my Windows to a Linux and compile it on the Linux machine?

Is there any tutorial on this? I tried things with makefiles before and I couldn't get it to work, if that's what I need.

---

### Post by LaRoza on 2008-10-26
> **Sir-Rogers said:**
> I never got this whole makefile thing. Do I have to get a makefile, export it to a machine with the desired platform and then compile it on that machine?

So take the makefile from my Windows to a Linux and compile it on the Linux machine?

Is there any tutorial on this? I tried things with makefiles before and I couldn't get it to work, if that's what I need.

First, what OS are you going to be using primarily?

If you want to get into open source development using all free tools, I heavily recommend you use Linux.

It would depend on the complexity. You probably don't need a makefile, for just starting out.

You may want to check this out (warning, complex!): [http://www.gnu.org/prep/standards/standards.html](http://www.gnu.org/prep/standards/standards.html)

---

### Post by Sir-Rogers on 2008-10-26
Right now I am using Windows primarily, but that can change if you tell me that it is easier on Linux. The game should run equally well on any platform, if that is what you meant by primarily.

I don't know what you mean by the complexity, all I want is to code a game in C++ and then make it run on any other platform, but I have no idea how to do that. I would be using Ogre as a game engine, because I know that it runs on all major platforms.

Now I need to know how I can test that my code works, i.e. compile it for different platforms, but I have no idea how to do that. So that's all I would need to know really.

---

### Post by gnusci on 2008-10-26
I recommend you to give a look to **CMake**

[http://www.cmake.org](http://www.cmake.org)

Could be an interesting option for your purposes.

---

### Post by Sir-Rogers on 2008-10-26
> **gnusci said:**
> I recommend you to give a look to **CMake**

[http://www.cmake.org](http://www.cmake.org)

Could be an interesting option for your purposes.

As I stated in a post earlier, I installed cmake before, but had no idea how to make use of it. I'm really unexperienced in this field and all the tools are too complicated, they offer not enough documentation or at least I didn't find any of it to be understandable.

---

### Post by slavik on 2008-10-26
where have you tried looking for information on using the tools???

---

### Post by dribeas on 2008-10-26
> **Sir-Rogers said:**
> Hello everybody,

as the topic indicates this is about compiling vc++ code that will run under Linux. I'm planning to create a 3D game which will run on MacOS X, Linux/UNIX and Windows platforms.
[...]
Is it at all possible to do this with the Visual Studio 2008 Edition, using VC++? Or would I have to resort to C++ ANSI standards in order for it to be usable on platforms other than Windows?


My advice would be starting with a multiplatform build system (cmake is the one I use, never tried others). This help you build MSVS projects for windows as well as Makefiles for linux, XCode projects, Eclipse CDT projects, CodeBlocks... just choose your IDE.

Then limit yourself to multiplatform libraries, you can find multiplatform libs for anything you want to do.

When it comes to the language itself, you should code by the standards, and that will make your code portable, but even then there are a few tweaks you will have to make with each compiler system / version. Anyway, if you have bound yourself to multiplatform tools and libs most of the way is already paved.

---

