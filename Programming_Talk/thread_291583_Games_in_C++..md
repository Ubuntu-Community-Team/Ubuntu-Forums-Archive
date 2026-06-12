---
title: "Games in C++."
date: 2006-11-02
forum: Programming Talk
---

### Post by Note360 on 2006-11-02
Any way, my friend out of no where thought it would be a good idea to make a 3rd Person game. I am like, cool. Who is gonna do the programming. He laughed and said, you and me. I am like, oh **** I know, near no C++ (the language he wants). I only have experience with Python, Ruby, Perl and a bit of C, C# and Nemerle. Now I dont have a XP machine. So two concerns arise. Since neither of us know C++ where do we learn, and compiler issues. HE is using Visual C++ and I am using GCC. I told him that he was crazy, but he wont listen.

---

### Post by Choad on 2006-11-02
you are both crazy, but good luck to you

i would not hold out much hope for the 2 different dev environments, but you can get him to install cedega and gcc/g++

openGL, c++ and general 3d programming is a ******* bitch, i have been programming for 3 years and tried loads of times to get in to it but i have never been able to (and 3 years is nothing)

---

### Post by UK-sHaDoW on 2006-11-02
[http://nehe.gamedev.net/](http://nehe.gamedev.net/)

Probably the best place to look.

I've been using openGL for years, and i still suck.
I'm sure theres a windows version of GCC. Its in the bloodshed ide. I don't know if its any different.

You might have to wright two separate pieces of code to get the engine start up on windows and linux, but once you got that code base, you can do whatever.

I encapsulated my engine in an object, when i created it,i passed a pointer to it. The pointer pointed to a bool array of keys representing the keyboard. This array got updated differently depending on the os. Then i looped the engine like this
 Loop
{
gameengine.update()
 gameengine.render();
}
The engine was the same but different start up code for the different os's. If you get me.

I'm well bad at explaining things

There is also a cross platform opengl helper library though.

---

### Post by hod139 on 2006-11-02
Also check out
SDL: [http://www.libsdl.org/index.php](http://www.libsdl.org/index.php)
G3D: [http://g3d-cpp.sourceforge.net/](http://g3d-cpp.sourceforge.net/)
Blender: [http://blender.org/cms/Home.2.0.html](http://blender.org/cms/Home.2.0.html)
OpenSceneGraph: [http://www.openscenegraph.org/](http://www.openscenegraph.org/)

**Edit:** How could I forget Open Dynamics Engine: [http://ode.org/](http://ode.org/)

---

### Post by Relain on 2006-11-02
How about just hacking at one of the open source engines for a while, to get a grip with what's going on.

Also, cross platforming sounds fun and OpenGl is slightly easier on to use with C than C++ IMHO.

---

### Post by APNelson.L on 2006-11-03
Good luck with the game. I would recommend using the same environment and compilers though. If you want to learn about c++ programming in general than I would recommend the book Thinking in C++ you can download it here [http://www.mindview.net/Books/DownloadSites]("http://www.mindview.net/Books/DownloadSites")

---

### Post by amo-ej1 on 2006-11-03
Try looking at some open source game engines, I once played with Irrlicht (  [http://irrlicht.sourceforge.net/](http://irrlicht.sourceforge.net/) ) which gives you very soon results. 

The second tutorial for examples enables you to render a full quake 3 map.

---

