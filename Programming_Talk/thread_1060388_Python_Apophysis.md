---
title: "Python Apophysis?"
date: 2009-02-04
forum: Programming Talk
---

### Post by djbushido on 2009-02-04
EDIT: Please if you would like to help, send me a PM or something. email is [email]bspeice.nc@gmail.com[/email]. Don't spam please. But we could use all the help we can get.

I was asking this to try and gauge community support for a new version of Apophysis, written in Python. The idea was to make a portable (Windows/Linux/Mac) version of this popular fractal flame program. I will help as I can, but don't know nearly enough (I'm sure) as would be needed to do this. Thus, I would look for a mentor and some other people to help out.

There is a port in java of this, but wanted to do this as a project to learn python, and allow better integration between plugins (written in C).

The other idea was to get a better fractal flame editor for linux. There are problems using Apophysis via WINE, and the Qt alternative (Qosmic) is hard to compile and in my opinion very bad relatively. This would aim at being a better editor that was easily portable and extensible.

Finally, as stated previously, I would definitely need some help. I have some friends who could help, but we aren't sure where to start, or how to do most of this. I know it is a lot to ask for someone to mentor something like this, but it would help a lot.

Finally Finally, the source code (in Delphi) is [here]("http://www.apophysis.org/apo202src.zip") (note: link will automatically download - go to [http://www.apophysis.org](http://www.apophysis.org) to manually download.)

Thank you!

---

### Post by jimi_hendrix on 2009-02-04
i dont know a lot about fractals (other than the definition and they look cool!)...but if you want me to hack a C module just call

---

### Post by djbushido on 2009-02-04
Okay, the basic idea of how to render a fractal - there is a formula, and random values are selected and graphed according to the formula. The Sierpinese (spelled wrong i'm sure) triangle is a good example of a basic fractal.

As to hacking C - the rendering engine (flam3, found [here]("http://www.flam3.com")) has a set amount of variations. I am trying to figure out how to add variations from the apophysis plugins source code for a custom flam3 version with support for more variations. The original functions are in the flam3.c file. For sake of you getting it yourself, follow the above link to the source code. An example of an Apophysis plugin source is [this]("http://sourceforge.net/project/showfiles.php?group_id=201476&package_id=239686"). I was wanting to add in some of these plugins, since the flam3 engine produces better images, but doesn't support nearly as many variations, so can't animate, etc.

Some of the plugins are probably also written in Delphi as well, so that would need to be ported also.

Thanks for help, let me know if you can work with me on this.

---

### Post by jimi_hendrix on 2009-02-04
i will try...i do know basic pascal (delphi) but i also have school and stuff

so basically you want me to port functions from one source to another? (and translate pascal to C)

---

### Post by djbushido on 2009-02-04
Thanks!
And just to let you know, I'm not sure how they get integrated, etc. I need to look at the source more in depth (maybe ask Erick Reckase or Sp0t too...)

Anyway, I am looking at fully going through with this kind of project. The rendering/preview engine is written (flam3 - I am looking at just extending this for plugins and integrating with python since flam3 is C), most of what needs to be done is the interface programming. Which is still quite a daunting task.

And thank you for translating. The code isn't too complex, but I know next to nothing of pascal, and only what little C has to be known (or is known from learning) with C++.

If you would like to help, send me a PM so I can organize what's going on.

---

### Post by djbushido on 2009-02-05
Huzzah! SourceForge page created. Project name Apo-Python.

---

### Post by djbushido on 2009-02-05
Also Also: If you can help or are willing to mentor, please please PLEASE leave me a PM or post so I can organize what's going on. Maybe a mailing list or something.

---

### Post by kavon89 on 2009-02-06
Wouldn't porting it from Java, a cross-platform language, to Python be sort of useless if the only major difference is that Python is even slower than Java?

Just putting that out there.

---

### Post by djbushido on 2009-02-07
True, Python would probably be slower than Java.
However, there are a few reasons why I (and my friends) are doing this:
1. No memory management - The Java VM is limited by how much memory it can use, and most users wouldn't know how to change this - Python doesn't have this problem
2. Better integration with flam3 - The flam3 rendering engine produces better results than the Apophysis render, but can't use variation plugins. I find that annoying. So, this way, users can put in their own variations and still get great results
3. Time is actually not really an issue - Python will be done for the _interface_ programming - the preview and rendering will all still be done with flam3 (C) so users probably won't notice much of a change
4. Better flam3 portability - Since only the flam3 source code will be needed (Python extensibility to C) people (especially on Linux) don't need to compile flam3 themselves, the program should be able to just use the source code.
5. Looks great on college applications - Yeah, so it's a bit selfish
6. Something to do - we're bored programmers, the robotics season is winding down, and this will give us something to work on.
7. Experience with Python - I'm learning python, and this project is a great way for us to get some hands-on experience coding for something we love.

If I think of anything else, I'll edit this.

---

### Post by djbushido on 2009-02-07
Thanks to whoever said they would mentor! Could you please send me a PM with your email or such so we can integrate you with the group?

---

### Post by hellocatfood on 2010-12-12
Is this project still going ahead

---

### Post by djbushido on 2010-12-12
I apologize that I haven't updated this thread with more information - the "Python Apophysis" project has been disbanded as another one was already in development - fr0st.
fr0st pretty much intended to do all that I wanted to do, only the designer was a much more experienced coder than I.
You can find news about fr0st [here]("http://fr0st.wordpress.com"), and it can be downloaded [here]("https://launchpad.net/fr0st/+download").

---

