---
title: "Getting started with OpenGL in Ubuntu for a Windows user"
date: 2006-01-16
forum: Programming Talk
---

### Post by megalomaniac on 2006-01-16
Hi,
I'm really new to Ubuntu and Linux in general so I hope these questions aren't too silly; I'm just trying it out at the moment. I really don't like the directions M$ seems to be heading with Vista so figured it was time to look for an alternative and I must admit Ubuntu is pretty good so far. Anyway; I've been programming in OpenGL and DirectX (in C/C++) on M$ Windows for a long time and want to get into OpenGL programming in Ubuntu however there seems to be a lot of confusing information out there and I'm struggling to get my head round it. So here come the questions:

1. As mentioned I've been coding in windows for a while now and so have rather a lot of OpenGL code written for windows, how would I go about converting this to run in Linux? Is it simply a case of stripping out the windows stuff (message handling, window setup etc.) and replacing it with a Linux equivalent?

2. As far as starting something new goes I notice everyone seems to use things like GLUT and SDL, why is this? In windows I always did everything myself, all the windowsy stuff all the OGL stuff everything. Is this possible under Linux (and if so how difficult is it compared to windows) or do you ***have*** to use something like SDL?

3. Everyone seems to have a different opinion about what IDE is best, but what would be easiest to get into for a long time Visual Studio user such as myself? Or would you recommend going through the effort of getting into something a bit different?

4.What sort of setting up is required to be able to compile and run OpenGL under Ubuntu?

5. I've done a lot of shader (GLSL) work in windows; would this compile and run ok on my NVIDIA GF6800 under Linux? If so is any special setup required?

Thanks in advance

---

### Post by mdh on 2006-01-16
Hi,

[QUOTE=megalomaniac]
4.What sort of setting up is required to be able to compile and run OpenGL under Ubuntu?
[/QUOTE]

I have a couple of questions along these lines

1. When I install a nvidia (or any)  graphics drivers, is that when the gl headers and gl libraries (libgl and libglu) get installed ?

2. Where does the actual gl headers and libraries reside ? On some other systems I have seen them in /usr/X11R6, but on my machine, inside /usr/X11R6, I don't find a include directory, I do have a lib directory which has some nvidia libs but I dont find any libGL or libGLU in there. 

3. When I do a "locate libGL", I get
[I]/usr/lib/libGLU.so.1.3.060302
/usr/lib/libGL.so.1.0.7667
/usr/lib/libGLU.so.1
/usr/lib/nvidia/libGL.so.1.2.xlibmesa
/usr/lib/libGLcore.so.1.0.7667
/usr/lib/libGLcore.so.1
/usr/lib/libGL.so.1
/usr/lib/libGL.a
/usr/lib/libGL.so
/usr/lib/libGLU.a
/usr/lib/libGLU.so
/usr/X11R6/lib/nvidia/libGLcore.a.xlibmesa
[/I]

Among these how do I know which library (.so .a difference aside) to link my apps with. Also if libGL and libGLU were installed during driver installation (??) why were the headers not installed.

Thanks for your time,
mdh

---

### Post by megalomaniac on 2006-01-17
Looks like I'm not the only one struggling with OpenGL in Linux, might help if there were tutorials on this stuff somewhere but all the examples I can find that actually have proper explanations attached (as oppose to just being code) are windows based :-(.

---

### Post by gord on 2006-01-17
opengl was designed from the ground up to be a specification not a piece of software, ie; the graphics card makers look at the opengl specification and make drives that work with it, so generally the processes that are involved are relitivly similar.

sdl is sometimes/often used to handle the opengl window because its got other great fetures such as event catching and sound stuff, but if you want to make your own thats fine, id still suggest using sdl for the window though, it might sound like another abstraction layer between you and what you want to do but in reality its very low level and transparent, the clue is in the name, **simple** directmedia layer ;)

[http://cone3d.gamedev.net/cgi-bin/index.pl?page=tutorials/ogladv/index](http://cone3d.gamedev.net/cgi-bin/index.pl?page=tutorials/ogladv/index) has some nice tutorials and so does [nehe](http://nehe.gamedev.net/), remeber to look for sdl ones if you want more linux orientated code.

---

### Post by gord on 2006-01-17
also, most include files are stored in /usr/include/ you should try looking there :) if not look for the correct <whatever>-dev files in synaptic

---

### Post by Viro on 2006-01-17
[QUOTE=mdh]
1. When I install a nvidia (or any)  graphics drivers, is that when the gl headers and gl libraries (libgl and libglu) get installed ?
[/quote]

No, when you install graphic drivers none of the headers are installed as it is assumed that you aren't doing any development so why install the headers? The headers are only installed when you install the development packages, stuff generally ending with the suffix -dev. For example, libglut3 is a package that contains glut3 end-user libraries while libglut3-dev contains the header files and development libraries.

For OpenGL development, you might want to install the mesa development headers.

The enduser libraries libGL and libGLU should always ship on any system that uses Xfree86 or Xorg. The only downside with these is that there isn't any hardware acceleration provided and everything is emulated. Installing the nVidia drivers will update libGL and libGLU with hardware accelerated versions.

[QUOTE=mdh]
2. Where does the actual gl headers and libraries reside ? On some other systems I have seen them in /usr/X11R6, but on my machine, inside /usr/X11R6, I don't find a include directory, I do have a lib directory which has some nvidia libs but I dont find any libGL or libGLU in there. 
[/quote]
The headers will reside in /usr/include/GL, and they will only be there once you install the development packages. 

[QUOTE=mdh]
Among these how do I know which library (.so .a difference aside) to link my apps with. Also if libGL and libGLU were installed during driver installation (??) why were the headers not installed.
[/quote]

You just pass the flags "-lGL -lGLU -lglut" to your linker when you want to link your application and they cause the correct libraries to be linked.

---

### Post by Viro on 2006-01-17
[QUOTE=megalomaniac]Looks like I'm not the only one struggling with OpenGL in Linux, might help if there were tutorials on this stuff somewhere but all the examples I can find that actually have proper explanations attached (as oppose to just being code) are windows based :-(.[/QUOTE]

[Nehe's](http://nehe.gamedev.net) OpenGL tutorials are Windows centric, but have the corresponding Linux code supplied. They should be a good place to look if you want to convert your OpenGL code from Windows to Linux.

---

### Post by megalomaniac on 2006-01-17
Thanks for the response guys. Although does anyone have any examples not using SDL? I'd really like to compare the different ways of approaching it and then decide what's best for me. Anyway it's not really the coding questions that I'm struggling with at the moment. I started programming a long time ago in Pascal and DOS and I've been programming in windows for a while now so I know the API's and languages pretty well and these are the same (or should be, not that M$ ever paid attention to any C/C++ standards ;-)) regardless of the OS. It's the Linux specifics I'm struggling with, I just need some Linux based examples to get my teeth into. My real struggle is with the ins and outs of developing in Linux, choosing and setting up the IDE's compiling and running the code etc.. With windows it's simple! You install Visual Studio and it just works, if you need to install the DirectX SDK or whatever it sets up all the relevant paths etc. for you during the install. If you click compile it compiles, click build it builds an executable file and if you click run and it runs it. All you ever need remember to do is include the appropriate files like opengl32.lib in your project settings. Linux however is a much more complicated beast when it comes to setting things like this up or a least it seems to be to the untrained eye (i.e. me). :-D

Remember I'm coming to this having never touched Linux before, I just need some nice clear instructions to follow to get me started :-).

Thanks

---

### Post by mdh on 2006-01-17
Thanks Viro and others for your helpful responses.

[QUOTE=Viro ]
The enduser libraries libGL and libGLU should always ship on any system that uses Xfree86 or Xorg. The only downside with these is that there isn't any hardware acceleration provided and everything is emulated.[/QUOTE] 

Let me paraphrase that one to make sure that I am clear on this. At this stage (before installation of nvidia drivers) what we have as libGL and libGLU are mesa libraries (software implementation of GL specification). Once we have nvidia drivers installed then 
in updated libGL and libGLU we have nvidia's implementation of OpenGL specification for their specific graphics card ?? (i.e., better performance than mesa libs)

[QUOTE=Viro]
For OpenGL development, you might want to install the mesa development headers.
[/QUOTE]

Again, paraphrasing your statement. Mesa headers contain the function declaration for the OpenGL specification and the actual implementation of **ALL** of these functions will be in the libGL and libGLU (updated by nvidia installation). In other words, the Mesa headers are compatible with nvidia's libGL and libGLU provided the OpenGL versions match.

Am I completely right here ?

Thanks Viro and others,
mdh

---

### Post by Viro on 2006-01-17
[QUOTE=mdh]
Let me paraphrase that one to make sure that I am clear on this. At this stage (before installation of nvidia drivers) what we have as libGL and libGLU are mesa libraries (software implementation of GL specification). Once we have nvidia drivers installed then in updated libGL and libGLU we have nvidia's implementation of OpenGL specification for their specific graphics card ?? (i.e., better performance than mesa libs)
[/quote]

That is correct.

[QUOTE=mdh]
Again, paraphrasing your statement. Mesa headers contain the function declaration for the OpenGL specification and the actual implementation of **ALL** of these functions will be in the libGL and libGLU (updated by nvidia installation). In other words, the Mesa headers are compatible with nvidia's libGL and libGLU provided the OpenGL versions match.
[/quote]
You are right again :)

---

### Post by richardhp on 2006-01-17
I don't know much about opengl but I have been programming in C for a bit and would like to learn.

I cannot find the OpenGl header files (gl.h, etc) on the internet and am not sure whether they are already installed on ubuntu.

Is there anything else I need to install in order to compile Gl Code or can I just copy the header files (assuming I can get hold of them) into the /Include Directory and then compile?

---

### Post by mdh on 2006-01-17
Viro,

Thanks a ton for your clarification. I am very glad that I made the switch to ubuntu, trust me it is worth it just for the amount of information and help you can get from these forums. 

Thanks,
mdh

---

