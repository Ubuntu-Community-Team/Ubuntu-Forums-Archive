---
title: "Coming from Widows"
date: 2008-03-01
forum: Programming Talk
---

### Post by lordfallout on 2008-03-01
Hello all, i was hoping anyone could suggest some alternatives to me. So first an introduction.

Hey, im a c++ programmer, have been for the past 5 years, im also just getting into c# and i've dabled in Java. I mainly program games, but some applications (mainly c# game editors). I really like Ubuntu but i hate the fact that gaming sucks here. Maybe i can help to change this. I've mainly programmed using directX on Windows, using Visual studio and was looking for alternatives for Ubuntu, i've gotten used to the Visual Studio IDE and can do alot more with an IDE than i can with command line. 

I was planning to learn OpenGL but was wondering if anyone can suggest a development environment i can use to program 3D games, or cross platform applications on Ubuntu. Obviously i could use Java, but i hate the feel of the language and its not very good for games, with the Auto garbage collection.

I dont intend to just program games however i would love to program applications for the platform and give something back.

---

### Post by NathanB on 2008-03-01
Take a look at FreeBASIC or Gambus.

---

### Post by mike_g on 2008-03-01
Since you have used Java you have probably used Netbeans which is a  nice IDE for large projects. Theres a C/C++ plugin for it. Never used it myself as I only tend to code little things in C, so I dont know how well it would work. The only Linux C/C++ IDE I have used is Anjuta which is pretty lightweight in comparison to VS.

---

### Post by LaRoza on 2008-03-01
The sticky might interesting you.

---

### Post by popch on 2008-03-01
> **LaRoza said:**
> The sticky might interesting you.

Why do I have a damp tissue in my pocket?

---

### Post by lordfallout on 2008-03-01
> **mike_g said:**
> Since you have used Java you have probably used Netbeans which is a  nice IDE for large projects. Theres a C/C++ plugin for it. Never used it myself as I only tend to code little things in C, so I dont know how well it would work. The only Linux C/C++ IDE I have used is Anjuta which is pretty lightweight in comparison to VS.

I had no idea Netbeans had a C/C++ plug-in and the assumption you made was correct, i've used Netbeans for servlet / applet development, it was quite nice and the thought of it never even entered my head. :)

I've loaded Anjita and i didnt like it, thats just based on first impressions however, i've loaded and tried out code::blocks but i got a similar feel, no matter how bad it is, i actually like the VS environment, i've gotten used to it and like the feel, just the project configuration files i don't like. I've read a couple of forum post along the lines of mine and seen a lot of answers similar to 'So why did you bother with Linux', basically i just wanted to try out something different, my PC still runs windows at the moment since i still rely heavily on DX but would like to change that so, am slowly adapting, with the use of my laptop :P

Any other suggestions would be lovely :P

---

### Post by ninjarat on 2008-03-01
Cross platform extensible game development language:
[BlitzMax]("http://www.blitzbasic.com")

And there's a new release of C::B if you're interested in that.  I also think that if you want to build your engine from the ground up you will like Linux system programming a lot more.  Lastly, learn OpenGL.  DirectX?  That's messier than my desk.  OpenGL is simple and intuitive and the functions are arranged uniformly and have logical names.  And it's faster, too.

Code on.  Linux rocks!
:guitar:

---

### Post by lordfallout on 2008-03-01
> **ninjarat said:**
> Cross platform extensible game development language:
[BlitzMax]("http://www.blitzbasic.com")

And there's a new release of C::B if you're interested in that.  I also think that if you want to build your engine from the ground up you will like Linux system programming a lot more.  Lastly, learn OpenGL.  DirectX?  That's messier than my desk.  OpenGL is simple and intuitive and the functions are arranged uniformly and have logical names.  And it's faster, too.

Code on.  Linux rocks!
:guitar:

I've a friend who's only ever used OpenGL, and he tried to make a simple 3D app in DX, i couldn't believe how much stuff he didn't know about and claimed he didnt need in OpenGL it was insane, i think i'll use OpenGL as a hobby at the moment i need DirectX as my mainl API for comercial projects atm, but that should change once i get to make a choice :P

I'm gonna be using OpenGL for now, and comparing the two. I'll give code::blocks a shot again, is it quite easy to configure / use. Is there any way to visually create apps on there, similar to using c# with VS?

---

### Post by pmasiar on 2008-03-01
There are many projects working on FOSS games
- [http://worldforge.org/](http://worldforge.org/)
- many game clones like FreeCiv (Civilization), Battle of Wesnoth, etc
- many many smaller games
- many game frameworks, like PyGame

Python is excellent cross-platform language (you can always add C for spped - but only if you need it).

There are discussions about IDEs, pro and con, see sticky. Here let me only mention that many FOSS developers work daily with many languages, so universal editor like Vim or Emacs is more important for them than single IDE (lacking the features accumulated in universal editors in those 20+ years of development).

---

### Post by LaRoza on 2008-03-01
> **popch said:**
> Why do I have a damp tissue in my pocket?

Cause you accepted it back. :)

---

### Post by scruff on 2008-03-01
For a full fledged C++ IDE give [kdevelop]("http://www.kdevelop.org/") a try.

---

### Post by mb108 on 2008-03-02
Nobody likes Eclipse?

If you're interested in cross-platform game development in C++, you might check out [_SDL_]("www.libsdl.org/"), and SCons or CMake for building.

Glade allows you to visually set up a GTK+ UI and generates an XML file you can parse in your application. The corresponding library for C++ would be [_gtkmm_]("www.gtkmm.org/"). GTK+/Glade is cross-platform, and has bindings for many languages.

... that being said, if you're not used to spending some time at the command line or hacking config files, the whole SCons/Cmake C++ cross-platform build thing can be pretty daunting... though Kdevelop can generate a CMake project, and Code::Blocks was working on support (not sure of the status on that).

Python is the language of choice for getting things up and running with a minimum of fiddling.

---

### Post by lordfallout on 2008-03-02
I've used Python before, but as an interface to other things in a game, config loading etc. I do not want to use it for any actual game development, and SDL is good, not for me however, i need more low level access, i'm just going to have a go with OpenGL, just need the cross platform window wrapper, but i think the GLUT will take care of the window management you might need for a game running completely in OpenGL I'm not sure however since i've never used it. :S  I've also had a look at wxWidgets, has anyone any experience of this?

---

### Post by pmasiar on 2008-03-02
> **lordfallout said:**
>  i need more low level access, i'm just going to have a go with OpenGL, just need the cross platform window wrapper, ... wxWidgets, has anyone any experience of this?

Python has bindings for many libraries. wxPython is available too. Just FYI. :-)

You will be calling exactly the same libraries, regardless if you write in in C++ or Python.

---

### Post by lnostdal on 2008-03-02
i've heard [http://glfw.sourceforge.net/](http://glfw.sourceforge.net/) mentioned as "a better glut"

---

### Post by ninjarat on 2008-03-03
GLUT is good, but I don't like trusting my app to something I can't really see inside.  If you want full robust control, X11 system programming is not hard.  For example, you know how on Win32 you have to create a callback, and do message translating / dispatching and all that?  On X11:

Pseudocode:
```
Display *display;
XEvent event;

// called right before we swap buffers
void Update()
{
    while (XPending(display))
    {
        XNextEvent(display,&event);
        switch (event.type)
        {
             [handle events here]
        }
    }
}
```
and swapping buffers is just as easy as
glxSwapBuffers(display,window);

It shouldn't be that hard to do from the ground up.  To see the basics you should go to the [NeHe's GL Lesson 7]("http://nehe.gamedev.net/data/lessons/lesson.asp?lesson=07"), which has a Linux/X11 version.  As you will see, it's very simple.  Get that source [here]("http://nehe.gamedev.net/data/lessons/linuxglx/lesson07.tar.gz").

Also, if you want stuff which is less remedial, and has a little more meat on it's bones, then I suggest you have a look at [my WIP game engine]("http://rampancy.g0dsoft.com/").  I'm plugging it here because I want to raise interest, seeing as how I'm just getting past the foundations of everything and am just about ready to get started on serious systems like rendering, audio, etc.

---

### Post by cb951303 on 2008-03-03
I recommend Eclipse + CDT for IDE. For game dev. SDL + OpenGL is becoming a standard now. Also there are more high level gaming libraries such as Allegro (which can be used with OpenGL too)

cheers

---

### Post by cb951303 on 2008-03-03
> **lordfallout said:**
> I've a friend who's only ever used OpenGL, and he tried to make a simple 3D app in DX, i couldn't believe how much stuff he didn't know about and claimed he didnt need in OpenGL it was insane, i think i'll use OpenGL as a hobby at the moment i need DirectX as my mainl API for comercial projects atm, but that should change once i get to make a choice :P

I'm gonna be using OpenGL for now, and comparing the two. I'll give code::blocks a shot again, is it quite easy to configure / use. Is there any way to visually create apps on there, similar to using c# with VS?

OpenGL is an alternative to Direct3D not DX ;) your friend probably compared opengl to directx which is meaningless since opengl doesn't do anything but 3d graphics 
;)

---

### Post by moma on 2008-03-03
Hello,

Here is a good starting point. 
[http://ubuntuforums.org/showthread.php?p=3627418&posted=1#post3627418](http://ubuntuforums.org/showthread.php?p=3627418&posted=1#post3627418)

The **Note 5)** lists all neccessary guides to start with OpenGL programming. OpenGL (GLUT library) is cross platform and very fast. Go for it !

---

### Post by theshadowwithanmp5n on 2008-07-10
what about for Allegro
i've been using it on windows, and i configured Dev-C++ fine
but now i'm using windows more than I want to.
i tried configuring codeblocks to work with allegro, but i can't figure it out
i always get wierd errors about functions that i don't even know exist.
and KDevelop is primitive.
I can't even figure out how to use Geany.
and I tried Eclipse but I couldn't figure out how to get to C++.
I'm already comfortable in code::blocks, and i don't want to change IDE's can someone please help?

---

