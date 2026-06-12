---
title: "Setting up Ubuntu for OpenGL C++ development"
date: 2007-06-07
forum: Programming Talk
---

### Post by psublue on 2007-06-07
I've been using Ubuntu off and on for about a year now, and I'd like to be able to use Ubuntu for OpenGL development in C++. I'm currently a software engineering intern for a software company in State College, PA, where I do a lot of GUI and OpenGL work...but only in Windows.

As far as Linux goes, I'll probably be using Anjuta or KDevelop as my IDE. However, I have absolutely no idea how to go about getting all the required libraries, headers, etc., and it's been tough to find a good tutorial that starts from scratch. Could someone please outline the steps I need to take to get everything set up? Thanks - I really appreciate it.

Here's all the important stuff:

Ubuntu 7.04 - Feisty Fawn (x86_64)
AMD Athlon 64 3700+ (mobile)
ATI Mobility Radeon 9700 ('radeon' driver)
1 GB RAM

---

### Post by snoop on 2007-06-07
Not sure if you have seen this post or not, but I suppose its a good start as any. [http://ubuntuforums.org/showthread.php?t=375425](http://ubuntuforums.org/showthread.php?t=375425)

if you want to check out sdl along with opengl, check out the nehe opengl tutorials and/or lazy foo's tutorials.
[http://nehe.gamedev.net/](http://nehe.gamedev.net/) 
[http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php)

Edit: also dont forget to install the linux headers and build-essential (needed to compile stuff on ubuntu).

---

### Post by psublue on 2007-06-07
I guess my question is really more about how to set up the IDE with the proper includes, libraries, etc. If i just use g++ from the command line, everything compiles and runs flawlessly. However, coming from a Windows background and using (sadly) Visual Studio 2005, I am much more used to using an IDE and less accustomed to command-line compiling. Any help with setting up Anjuta (or any other IDE) would be appreciated. Thanks!

---

### Post by snoop on 2007-06-07
> **psublue said:**
> I guess my question is really more about how to set up the IDE with the proper includes, libraries, etc. If i just use g++ from the command line, everything compiles and runs flawlessly. However, coming from a Windows background and using (sadly) Visual Studio 2005, I am much more used to using an IDE and less accustomed to command-line compiling. Any help with setting up Anjuta (or any other IDE) would be appreciated. Thanks!


Aah...ok, i understand you now. I realize that this is for sdl, but it should be very similar to the opengl setup [http://lazyfoo.net/SDL_tutorials/lesson01/linux/index.php](http://lazyfoo.net/SDL_tutorials/lesson01/linux/index.php)

Also, the second post in this post seems to make it look easy [http://ubuntuforums.org/showthread.php?t=207061](http://ubuntuforums.org/showthread.php?t=207061)

good luck!

---

### Post by the_darkside_986 on 2007-06-07
To add libraries to link with in Anjuta, you go to the menu item "Settings" > "Compiler and linker options" > then the "libraries" tab. In the small text box, simply type the name of the library to link to, like "SDL", and press the button "Click Here" and it will automatically add -l<name of library> as a compile flag. For opengl and glu, you enter "GL" and "GLU" in that section.

OR, in Anjuta you can just go to the Options tab in that same dialog, and add options to "linker flags" like -lSDL -lGL etc.

---

### Post by rksk16it on 2007-06-08
If you are pretty comfortable with IDEs, i think you should give Code::Blocks a try. The website is [http://www.codeblocks.org]("http://www.codeblocks.org"). That IDE has some special features (out of many) that will greatly help :-

1. You can download dev-packages for openGL. Even if dev-packages are old and u have downloaded more recent headers and libraries then it is very easy to configure code::blocks to use that.

2. They come with preset templates for OpenGL, SDL and ogre3d, so that will get you started quickly.

PS:- Check out ogre3D graphics library, it is a great graphics library and can be easily made to either use openGL or directX backend, [http://www.ogre3D.org]("http://www.ogre3D.org"), the Code::Blocks is excellently supported by ogre3D wiki (though i haven't visited that site recently - but about 1 month ago).

Good luck. :)

---

### Post by danhm on 2007-06-08
Yeah, as rksk16it mentioned, Code::Blocks has a template for OpenGL.

---

### Post by fatalGlory on 2007-08-26
I can understand the attraction of IDE's (having felt it myself), but I found that once I just sat and learned how makefiles work, they really are a brilliant solution.

Sure there are 'newer' ways to do what make does but I am used to make and have bunch of makefiles already lying around.  Try it, I found that there are few faster and cleaner ways to write code than gedit with syntax highlighting and a terminal where all i have to type is "make".

---

### Post by Jem Masters on 2009-05-29
I downloaded Anjuta (I'm new in this)  and copy paste an example of OpenGL, I also right click my >>source file, left click >>properties, left click >> Advance and added under Libraries case -> "GLUT" "GL", but when I execute the code nothing happen.  

Does anyone have the same problem?

---

### Post by NielsBhor on 2009-05-29
I'm also doing some work using GLUT and OPENGL. There's a video tutorial of how to use many of the GL functions. I highly recommend seeing this video. An important part of openGL is knowing how rendering works inside the graphics card.

Link: [Video Tutorial]("http://www.videotutorialsrock.com/")

OpenGL is very easy for you after you watch this. I'm a Computer and Electrical Engineer. So, a software specialist like you will get the hang of it quickly!

---

