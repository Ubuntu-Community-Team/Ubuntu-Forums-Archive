---
title: "C++, GUI's and Linux"
date: 2011-01-12
forum: Programming Talk
---

### Post by Ravenshade on 2011-01-12
Hi there, 

I'm a newbie to C++ so I've skirted the shallow end, headed to the diving boards...climbed all the way to the top one and I'm about to jump. Knowing me I'll sink and I won't be coming up for a while. :popcorn:

Still... I've found some reasonable stuff that I want to get on with. I want to have a go at developing a GUI and I've found two things that I should probably install. OpenGL and SDL (So I have both 3D and 2D capabilities...yes it's game development, but nothing complex).

Strange thing is though...with the repositories and all I'm not exactly sure 'which' to install, they all have so many different names and versions that I'm a little er... confuzzled. :confused:

Can anyone point me to the correct items I need to install so that I have decent if not simple libraries to use for creating an interface? 

Oh and before anyone tries pointing me to an IDE... I hate them all. Code::lite or is it code blocks...not sure. Both of them hate me. Netbeans is the only one I can get to work, but that only works for Java (won't even look at cpp files) so stuck there. On the other hand...I'm quite useful for g++, the terminal and my trusty gedit program.

---

### Post by Joeb454 on 2011-01-12
*Thread moved to **Programming Talk**.*

---

### Post by Ravenshade on 2011-01-12
Uh...I was actually asking about what programs to get not...chat about the programming itself. But no matter, hopefully this place is just as good.

---

### Post by dwhitney67 on 2011-01-12
See if the info in this post is helpful...
[http://www.gamedev.net/topic/575297-installing-opengl-and-sdl-for-ubuntu-linux/](http://www.gamedev.net/topic/575297-installing-opengl-and-sdl-for-ubuntu-linux/)

---

### Post by nvteighen on 2011-01-12
Hm... for SDL, install libsdl-dev. It's a virtual package that will grab the development files for SDL. Similarly for OpenGL, install libgl-dev.

---

### Post by Ravenshade on 2011-01-12
This somewhat helps, I assume it works for g++ as well as the gcc compiler (which apparently doesn't like C++ code).

---

### Post by worksofcraft on 2011-01-12
> **Ravenshade said:**
> This somewhat helps, I assume it works for g++ as well as the gcc compiler (which apparently doesn't like C++ code).

I think gcc is just a front end that calls appropriate compiler components for the selected languages... so g++ would simply be the same thing as gcc but with specific c++ options implied.

---

### Post by dwhitney67 on 2011-01-12
> **worksofcraft said:**
> I think gcc is just a front end that calls appropriate compiler components for the selected languages... so g++ would simply be the same thing as gcc but with specific c++ options implied.

"g++" == "gcc -lstdc++"

---

### Post by nvteighen on 2011-01-12
gcc is the GNU Compiler *Collection*... not the "GNU C Compiler".

For example, to compile Objective-C, you use gcc -lobjc. Of course, some languages have got a shortcut, like g++ or gfortran, but it's all the same ol' gcc.

---

### Post by Ravenshade on 2011-01-17
> **nvteighen said:**
> Hm... for SDL, install libsdl-dev. It's a virtual package that will grab the development files for SDL. Similarly for OpenGL, install libgl-dev.

Synaptic Package Manager returns....a lot of packages for libgl nothing for libgl-dev.  Any particular one you would recommend?

---

### Post by F.G. on 2011-01-17
hi,
you can use c++ in netbeans if you go to Tools, Plugins and install the C/C++ one. also not using a IDE I generally use gedit as my editor as it has syntax highlighting and compile with the g++ command (you may also wish to use the -o option to name the output file, so it looks like 
'g++ -o program program.cpp', otherwise they are all labeled 'a.out'). to run compiled programs you need to preceed them with ./ I'm sure you probably know all this.
Regarding GUI's in linux you may want to look at GTK+ which is free, or also Qt, which I think is only free for non-commercial purposes. 
good luck.

---

### Post by Ravenshade on 2011-01-17
> **F.G. said:**
> hi,
you can use c++ in netbeans if you go to Tools, Plugins and install the C/C++ one. also not using a IDE I generally use gedit as my editor as it has syntax highlighting and compile with the g++ command (you may also wish to use the -o option to name the output file, so it looks like 
'g++ -o program program.cpp', otherwise they are all labeled 'a.out'). to run compiled programs you need to preceed them with ./ I'm sure you probably know all this.
Regarding GUI's in linux you may want to look at GTK+ which is free, or also Qt, which I think is only free for non-commercial purposes. 
good luck.

My Netbeans doesn't have that option unfortunately, otherwise I would have chosen it. I have no idea why it doesn't have that option, perhaps my particular installation was corrupted some how.

I have also installed GTK...I'll see how that goes.

---

### Post by Simian Man on 2011-01-17
> **F.G. said:**
> Qt, which I think is only free for non-commercial purposes.

QT has been totally free for a long, long time.  For the record, QT and GTK+ are "GUI" libraries, whereas OpenGL and SDL are usually called "Graphics" libraries.

If you want to do 3D graphics, I personally would not use OpenGL unless I absolutely had to.  There are graphics engines like Irrlicht and Ogre which will allow you to get better results, quicker.  Thought that's just my 2 cents.

Lastly, you can try Geany which is a very simple IDE somewhat between a full one and a text editor.  It is pretty nice, altough I prefer Eclipse as my IDE.  The CDT is extremely good.

---

### Post by Ravenshade on 2011-01-17
I'm...not having any joy with GTK... I've installed the relevant packages, but the file just won't compile. note to self...stay away from c. 

As you can see I'm not a skilled programmer, I'm kind of trying to learn. As I've mentioned before the only thing I'm trying to do at the moment is try and find a way to get C++ to display a window...which is proving a little harder than one might imagine. 

Eclipse unfortunately doesn't work for me...not entirely sure why, I've just never been able to configure it correctly...maybe that's half the problem. -.-;

Trying SDL now... 

Setting up was surprisingly simple thanks to this website...
[http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development](http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development)

---

### Post by Simian Man on 2011-01-17
> **Ravenshade said:**
> I'm...not having any joy with GTK... I've installed the relevant packages, but the file just won't compile. note to self...stay away from c.
Yeah, it's pretty messy stuff :).

> **Ravenshade said:**
> As you can see I'm not a skilled programmer, I'm kind of trying to learn. As I've mentioned before the only thing I'm trying to do at the moment is try and find a way to get C++ to display a window...which is proving a little harder than one might imagine. 

What do you want to put into that window?  If it's 2D graphics, I'd recommend SDL which is one of the best libraries I've ever used.  If it's GUI stuff like buttons, text boxes etc, QT is the best option overall, but it's *quite* tricky to get up and running.  For simple stuff, wxWidgets is possibly the best bet.  For 3D graphics, I'd say Irrlicht is the simplest way to get going.

---

### Post by dwhitney67 on 2011-01-17
> **Ravenshade said:**
> I'm...not having any joy with GTK... I've installed the relevant packages, but the file just won't compile. note to self...stay away from c. 

As you can see I'm not a skilled programmer, ...

Using GTK+ is difficult because the API was written by monkeys.  I've found that Gtkmm (which is the C++ wrapper around GTK+) is a little more comprehensible.  You can find a half-decent tutorial [here]("http://library.gnome.org/devel/gtkmm-tutorial/stable/").

Based on your remark that you are an inexperienced programmer, I would suggest that you refrain from using any IDE until you learn to compile your programs using the command line.  A typical single-module GTK+ application is compiled using something similar to the following:
```

gcc MyModule.c `pkg-config --cflags --libs gtk+-2.0` -o myapp

```
For Gtkmm, something like:
```

g++ MyModule.cpp `pkg-config --cflags --libs gtkmm-2.4` -o myapp

```

Once you understand the underlying principles as to what is taking place above, then you can incorporate that knowledge into configuring an IDE project.

---

### Post by worksofcraft on 2011-01-17
> **dwhitney67 said:**
> Using GTK+ is difficult because the API was written by monkeys...

I agree... and here is the evidence:
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/f/f1/Monkey-typing.jpg/250px-Monkey-typing.jpg[/IMG]

Rumor has it that these were the very same monkeys that typed the [complete works of Shakespeare]("http://en.wikipedia.org/wiki/Infinite_monkey_theorem")

:D

---

### Post by Ravenshade on 2011-01-17
Results thus far: OpenGL don't know which files to install...same with GTK to be honest. I can't seem to operate GTK due to it's dominance on the C language and me being as dumb as I look. 

SDL however, seemed to install fine, but there is no set method it seems and many of the tutorials are based on Windows Developers...

Can anyone recommend a good tutorial for C++/SDL on Linux? 

---------------------------------------------------------------------------

@Simian man: I would love to eventually get a game up and running, I was thinking about the potential for 3D graphics and therefore SDL is the ideal choice due to OpenGL support. 

@dWhitney: I generally use gedit and g++; I haven't actually gone wrong with the command line interface before and I enjoy it immensely compared to using IDE's which I just see as cumbersome at the moment. This is the syntax I generally use to compile C++ files...

g++ file.cpp -o File 

Seeing as how it doesn't follow a specific syntax I think that seems the most logical... although adding libraries into this is definitely going to skew that perspective.

---

### Post by unknownPoster on 2011-01-17
> **Ravenshade said:**
> Results thus far: OpenGL don't know which files to install...same with GTK to be honest. I can't seem to operate GTK due to it's dominance on the C language and me being as dumb as I look. 

SDL however, seemed to install fine, but there is no set method it seems and many of the tutorials are based on Windows Developers...

Can anyone recommend a good tutorial for C++/SDL on Linux? 



SDL is cross platform. There is no difference in SDL API for the various Operating systems.

Regardless, here's a tutorial: [http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php)

Also, SDL is a C library, so you'll be writing a mixture of C and C++ code.

---

### Post by worksofcraft on 2011-01-17
If you want to do gaphics for games you might find that AGG is just what you need. It comes as a template library for C++ and has some impressive [demo programs]("http://www.antigrain.com/demo/index.html#PAGE_DEMO_aa_demo") but it's not got any 3D modeling capabilities. It works on Windows and Linux and Sun OS and some Amiga and Apple computers too I heard.
[IMG]http://www.antigrain.com/demo/image_perspective_s.jpg[/IMG]

p.s. ATM I'm working on developing a full GUI widget set to rival gtkmm but using AGG instead of GTK.

---

### Post by Ravenshade on 2011-01-18
Hint taken. I'll go learn some c. Hopefully it'll broaden my perspective some. 

I'll take a look at AGG, but I fear that it will limit me if I ever want to expand the game.

---

### Post by nvteighen on 2011-01-18
Uh... I'm not sure what decision you've finally taken, so if you're still interested in SDL and OpenGL:

It's package libsdl1.2-dev. It seems Ubuntu hasn't followed Debian's much saner approach of providing a metapackage that grabs whatever the last SDL version is...  

Forget Synaptic, open a terminal and type:

```

sudo apt-get update
sudo apt-get install libsdl1.2-dev

```

For OpenGL... the same... Who's in charge of Ubuntu's repositories!? Try this, it should work:
```

sudo apt-get install freeglut3-dev

```

On GTK+: Well, GTK+ is for GUIs, not for graphics. Those are two completely different concepts. Now, on which is better, whether GTK+ or Qt... that's an endless and pointless discussion, IMO. Anyway, I think the GTK+ API is quite good... just that it was written in C and that makes its C++ or Python bindings look a bit odd compared to their Qt counterparts.

---

### Post by Ravenshade on 2011-01-18
Ah! 

I found some useful information on the SDL concerning the repositories of which ones I needed, I'll run the apt-get commands though just in case. 

Thanks for the addition!


.....
Thanks to the help of all responders thus far, I hadn't cliked on Lazy Foo's tutorials because I had assumed wrongly that it would have been the same as the others. It is however, by far the best tutorial for SDL (in terms of clarity) that I have thus far read. 

And I've achieved my goal, so...in effect, I guess this means, topic solved.

---

### Post by Simian Man on 2011-01-18
> **Ravenshade said:**
> Thanks to the help of all responders thus far, I hadn't cliked on Lazy Foo's tutorials because I had assumed wrongly that it would have been the same as the others. It is however, by far the best tutorial for SDL (in terms of clarity) that I have thus far read. 

Yes they are.  I was going to recommend them too, but unknownPoster beat me to it!  SDL really is a fantastic library, if you get stuck with it I, and many others, have used it a lot so post back.  Best of luck!

---

