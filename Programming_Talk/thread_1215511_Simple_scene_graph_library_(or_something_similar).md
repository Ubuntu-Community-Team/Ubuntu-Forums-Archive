---
title: "Simple scene graph library (or something similar)?"
date: 2009-07-17
forum: Programming Talk
---

### Post by yesint on 2009-07-17
Dear All,
I'm searching for some library to simplify the coding with OpenGL. I need something which will take care of sorting the transparent objects, picking with the mouse and the like. I examined OpenSceneGraph and OpenSG and found both very complicated and extremely confusing at first glance. There are probably some reasons why the APIs are so insanely complicated, but I really need something simpler. 
Anyone know other good simple libraries of that kind (not necessary the full-blown scenegraph)?

---

### Post by moma on 2009-07-17
Hello.

Clutter is what you are looking for.
[http://www.clutter-project.org](http://www.clutter-project.org)

Ubuntu has ready-made packages for it. Check: 
$ [COLOR="SeaGreen"]aptitude search clutter[/COLOR]

And there are some demos on the [blog page...]("http://www.clutter-project.org/blog/")

We stronly believe that Clutter will be part of the upcoming GNOME 3.0 desktop and GTK 3 toolkit. Google's Chrome OS will also use Clutter, AFAIK ;-)
----

[COLOR="Red"]EDIT:[/COLOR] Maybe best you start with Clutter version 0.8. It seems to me that Clutter 9.0 is under development and its API fluctuates, therefore some examples will not compile under it yet.
**My recommendation is this**

**1)** Install Clutter version 0.8 from Ubuntus repo.
$ [COLOR="SeaGreen"]sudo aptitude install build-essential libclutter-0.8-dev libclutter-cairo-0.8-dev libclutter-gtk-0.8-dev[/COLOR]

**2)** Browse to this tutorial and advance step by step
[http://www.openismus.com/documents/clutter_tutorial/0.8/docs/tutorial/html/index.html](http://www.openismus.com/documents/clutter_tutorial/0.8/docs/tutorial/html/index.html)

**3)**Learn to compile and link your code. Here is an example.

Download first the main.c and images/ directory with some images from 
[http://svn.o-hand.com/view/clutter/trunk/clutter-tutorial/examples/full_example/?rev=2925#dirlist](http://svn.o-hand.com/view/clutter/trunk/clutter-tutorial/examples/full_example/?rev=2925#dirlist)

Compile and link the code
$ [COLOR="SeaGreen"]gcc -Wall -g `pkg-config clutter-0.8 clutter-gtk-0.8 --cflags  --libs` main.c -o main[/COLOR]

Then run it 
$ [COLOR="SeaGreen"]./main[/COLOR]

You should have some images in the images/ directory.

**4)** Here is the API-reference for Clutter v0.8
[http://www.clutter-project.org/docs/clutter/0.8/](http://www.clutter-project.org/docs/clutter/0.8/)
----

**Other examples**

* The Intel's Moblin interface uses Clutter too. Take a look at the samples.
[http://moblin.org/documentation/moblin-sdk/create-new-application](http://moblin.org/documentation/moblin-sdk/create-new-application)

* This [Pong game...]("http://damino.ca/?p=106") uses Clutter + Cairo graphics. Use the "git clone..." command to download it.
Run "sh autogen.sh" to generate a configure + Makefile. Then compile with "make".
----

---

### Post by curvedinfinity on 2009-07-17
Technically an "engine", but all of its components are optional.

[http://irrlicht.sourceforge.net/](http://irrlicht.sourceforge.net/)

I've just used the scenegraph and model/texture loading before, and it worked great. Its very simple to use.

---

### Post by yesint on 2009-07-20
> **moma said:**
> Hello.

Clutter is what you are looking for.
[http://www.clutter-project.org](http://www.clutter-project.org)
----

I'm not that sure. As far as I understand Clutter is just an API for creating "2.5D" user interfaces, while I need full 3D scenes with materials, lighting, etc.

---

### Post by moma on 2009-07-20
Ok, I understand. You are looking for a library with complete 3D capabilities.

Maybe you are better off with one of [these...]("http://ubuntuforums.org/showthread.php?p=3635764#post3635764") libs. 
(SDL is a 2D library even it allows you to program in pure OpenGL too).

---

### Post by yesint on 2009-07-21
> **moma said:**
> Ok, I understand. You are looking for a library with complete 3D capabilities.

Maybe you are better off with one of [these...]("http://ubuntuforums.org/showthread.php?p=3635764#post3635764") libs. 
(SDL is a 2D library even it allows you to program in pure OpenGL too).

Thank you for the link! I've made a quick look and panda looks really very nice. The only thing is that all these game engines are far too heavy for my task. After some critical study of my needs I see that the only thing, which I currently can't do in plain OpenGL is handling transparency (correct polygon sorting).

---

