---
title: "window"
date: 2012-10-28
forum: Programming Talk
---

### Post by thedardanius on 2012-10-28
hey,
 
Im creating an opengl cross-platform game engine. Im done with Windows, now I want linux support. How do I create a window in linux WITHOUT any 3rd party libraries like Qt or something. SRSLY, I CANT GOOGLE ANY SOLUTION WITHOUT THE USE OF THESE LIBS. I want my engine to provide the low level itself. On windows, I used the standard win API. Is these also a standard windows manager in linux? BTW im reasonably new to Linux. language: C++/C;

---

### Post by xytron on 2012-10-28
> **thedardanius said:**
> hey,
 
 On windows, I used the standard win API. Is these also a standard windows manager in linux? 

No there isn't a standard window manager in Linux.

The only thing approaching the Windows API on Linux would be using Xlib. 

Xlib provides the tools to build a user interface but it does not directly specify menus, scroll bars, dialog  boxes or how your application will respond to user input.

In order to create an OpenGL Window you would use Xlib and GLX.
GLX is an API that provides OpenGL functions to an X Window System application.

I can tell you that it will be a lot of work and time for you to program all these GUI widgets yourself just using Xlib. That has already been done by the higher level graphics library toolkits.

If you only used Xlib to create your GUI then your application doesn't need any GUI libraries (Xlib is standard on every Linux distribution).  Just remember Xlib only provides a way to create a GUI but all the hard work of responding to user input and Windows and text, colours, dialog boxes..etc will have to be programmed by you.

I don't recommend that at all just use a GUI toolkit, there are many good ones to choose from and I'm sure there's one that will suit your needs. 

Otherwise time that you could be spending on your application will be spent learning Xlib and creating GUI widgets, and the result will never be as good as just using a toolkit.

---

### Post by SledgeHammer_999 on 2012-10-28
> **thedardanius said:**
> hey,
 
Im creating an **opengl** cross-platform **game** engine. 

Maybe you should look at [SDL](https://en.wikipedia.org/wiki/Simple_DirectMedia_Layer) or [Ogre3d](https://en.wikipedia.org/wiki/OGRE3D)

---

### Post by thedardanius on 2012-10-29
thanks, xlib ang glx is waht im looking for. you coudl also say:
why didnt you use qt on windows? why didnt you use glut.
Well for those lazy *sses out there:
- I want to learn how these things work
- I want my engine to be complete independatn from the libraries, so the engine should ahndle all the low level things, what I did on windows. SO on linux, it shouldn't be that different. I need to study some linux anyway ;p

---

### Post by thedardanius on 2012-10-29
no thanks...

---

### Post by nvteighen on 2012-10-29
I just want you to reflect on something. On one hand, you're completely comfortable in Windows with using the standard Windows API. But on the other hand, you are completely uncomfortable in using any library on GNU/Linux OS. I really don't get it.

And no, the low-level thing doesn't count for me. The Windows API is quite high-level.

---

### Post by thedardanius on 2012-10-29
well its like this:
I dont want my engine to use any 3rd party dependancies. I expect x windows system and glx to be available on every linux system. Its like the win API is available on all the windows NT.

---

### Post by thedardanius on 2012-10-29
BTW the winAPI is quite low level, you need to do message handling and window creating  yourselfs, just like in glx and x11

---

### Post by Tony Flury on 2012-10-30
> **thedardanius said:**
> BTW the winAPI is quite low level, you need to do message handling and window creating  yourselfs, just like in glx and x11

From memory though The windows API though has calls to create buttons, menus on your windows, will tell you relative co-ordinates of mouse moves, will tell you when a given widget is actually clicked on  by the mouse etc. It handles things like scroll the contents of lists for you, the contents and state or the widgets. repaint the windows one manus and pop-ups are deleted etc etc etc.

The XLib API does not - you paint a region on a screen and you get told where on the screen the mouse was clicked - you have to work out if that mouse click was on part of your region that you are interested in, and if that region is a menu, or button, or combo box, or a list , and how they scroll etc etc etc.

Xlib is much lower level than Windows API - or it's linux equivalents like QT, KDE or GTK.

---

### Post by thedardanius on 2012-10-30
you definitely never programmed with winAPI before? WinAPI has the lowest level things for C to program on windows. you're prbably refering to MFC, a thin layer upon WINAPI.
Btw I took a look at xlib, and it appears to my eye and experiences to be just slightly lower level than winAPI.
 
THanks anyway.

---

### Post by trent.josephsen on 2012-10-30
I'm going to say this once, because you're acting very arrogant for someone completely new to Linux programming asking for advice on a forum frequented by the more experienced, and I have no desire to start arguing with a wall.

[Linux is **different** from Windows.](http://linux.oneandoneis2.org/LNW.htm) To become a successful Linux programmer, or user for that matter, you're going to have to unlearn some of the fundamental assumptions that you operate under on Windows. You cannot come to Linux and think, "I know how to do this on Windows, so it [shouldn't be that different](http://ubuntuforums.org/showpost.php?p=12324243&postcount=4) on Linux." Everything is at least a little bit different on Linux. One of those things is graphical programming. On Windows you can assume WinAPI is available, I guess (haven't done Windows programming, ever, myself). On Linux you can't assume anything. [Not even](http://directfb.org/) [Xlib](http://wayland.freedesktop.org/). On Windows, lower-level libraries may be more universal because the Windows base is always the same; but there simply *isn't* a lowest-common-denominator "universal Linux". It's the double-edged sword of being open and modular. Therefore, there's no qualitative difference between saying "this application uses Xlib" and "this application uses Gtk+", except that one of them won't work on Windows, OSX, or Wayland. "Low-level" does not translate to "cross-platform"; quite the opposite.

Now, all that said, I'm now going to ask what your goal is. If you want to learn Xlib, sure, maybe making a game engine could be one way to do that. But why do you want to learn Xlib when there are higher level, more portable, and newer libraries you could use to do things better and faster? If your goal is to make a game engine, or to learn about graphical programming in Linux, use a layer like SDL that removes most of X's cruft and will still be relevant when Wayland or some equivalent takes over.

Good luck.

---

### Post by thedardanius on 2012-10-30
thank you. sorry for my arrogance, maybe I conveyed myself too egocentric ;p
 
anyway:
youre now telling me even xlib isnt available on each linux system? But whats the entire use of the xlib then? Wasn't it the lowest window libraries before you hit the kernel?
and I'm getting strange error with code::blocks with gcc. when I compile command line, its alright. If I compile with IDE, errors start to occur with the same code. Really strange, still have to figure all that mess out. And you;re completely right: after 2 days explorering linux I must admit it is totally different. It is now like im relearning to use a PC ;p

---

### Post by SledgeHammer_999 on 2012-10-30
> **thedardanius said:**
> youre now telling me even xlib isnt available on each linux system? But whats the entire use of the xlib then? Wasn't it the lowest window libraries before you hit the kernel?

Think of a headless distro. ie one that operates using the terminal and it doesn't have X installed. xlib won't be available on that.

You should target some specific linux distros, because linux isn't an "OS". A distro is an OS. Or set some requirements for your project to be used on every possible linux distro. Eg state that your engine depends on Xlib or SDL or Gtk or whatever. All these libraries(and some others) are pretty common on linux distros and very very easy to be installed by a user.

Also as **trent.josephsen** mentioned what happens when [X](https://en.wikipedia.org/wiki/X_Window_System) gets replaced by [Wayland](https://en.wikipedia.org/wiki/Wayland_%28display_server_protocol%29) on the major distros? You cannot expect for xlib to exist on those too.

(It goes without saying, that if you are making this engine just to learn how things work on linux on a low level API then you should continue doing that.)

> **thedardanius said:**
> and I'm getting strange error with code::blocks with gcc. when I compile command line, its alright. If I compile with IDE, errors start to occur with the same code. 

Have you set the compiler switches/options/commandline correctly in code::blocks? If you need help on that, please create a new thread and post the commandline you use to compile in the console.

---

### Post by trent.josephsen on 2012-10-30
Thanks SledgeHammer for clearing that up a bit. My post was a bit harsh...

> **SledgeHammer_999 said:**
> Think of a headless distro. ie one that operates using the terminal and it doesn't have X installed. xlib won't be available on that.
Even assuming a graphical environment, xlib may still not be available. DirectFB worked with both Qt and Gtk+ last I checked and Wayland may be there very soon. (Granted neither of those is as popular as Xlib, but see final paragraph.) There's been a recent surge of interest in Wayland that I've noticed on places like Slashdot and certain distro-specific forums.

> You should target some specific linux distros, because linux isn't an "OS". A distro is an OS.

This is probably the thing that is most different from Windows. Windows is both a kernel and an OS; they're almost inseparable and there's little modularity below the level of third-party libraries, whereas with Linux -- everything is a third-party library. Some distros, including Debian, Gentoo and Arch, even allow you to swap out the Linux kernel itself for something different, like FreeBSD, Darwin, or HURD. This kind of system-level modularity is completely foreign to Windows. On Linux and other Unix-likes, X is more popular than its competitors because it's been around for quite a while and there are a lot of useful programs based on it, not because it's the Official Linux Standard Display Protocol. And with Wayland on the way we can always hope it will soon be replaced as most popular, too (although I'm not as optimistic as some).

---

