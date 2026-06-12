---
title: "Graphics in C++"
date: 2009-01-26
forum: Programming Talk
---

### Post by Zorgoth on 2009-01-26
Hi, I am interested in learning about graphics in C++, eventually including 3D graphics.  I'm under the impression that the appropriate thing to study would be OpenGL.  Currently I have a very basic knowledge of Qt along with a perfectly serviceable knowledge of console programming in C++.  My most ambitious project in Qt was a grapher/tabulator that takes 2D coordinates from several sets of data and plots them against each other in either an ordinary or a log-log scale with zooming/stretching/recentering features.

I have no real concept of the computing theory behind 3D graphics but I almost certainly know the math behind it.  What book/tutorial (preferably book) would you recommend for learning OpenGL in C++ from the very basics?  By the very basics I mean for someone who knows how to program C++ in a terminal and that's it.

This isn't completely relevant, but I am also learning Common Lisp (still in the early stages) and would like to use it behind the scenes for things like parsing and analyzing mathematical functions for a 3D grapher (one of the projects I would eventually like to do to test myself - a very long-run consideration; note that that is not the only thing I want to do) while using C++ to handle the rest of the program.  Is that possible to do that efficiently, and are there any tools that could help me?

---

### Post by nrs on 2009-01-26
[http://nehe.gamedev.net](http://nehe.gamedev.net)
The Redbook. 

Depends what you mean by C++, if you mean simply capable of being compiled by a C++ compiler then just use the C examples, if you mean C++ as in templates, OO, etc. You're not going to find that unless you're using some abstracted library -- I wrote my own -- the base is C / state machine.

---

### Post by Kilon on 2009-01-26
> **Zorgoth said:**
> Hi, I am interested in learning about graphics in C++, eventually including 3D graphics.  I'm under the impression that the appropriate thing to study would be OpenGL.  Currently I have a very basic knowledge of Qt along with a perfectly serviceable knowledge of console programming in C++.  My most ambitious project in Qt was a grapher/tabulator that takes 2D coordinates from several sets of data and plots them against each other in either an ordinary or a log-log scale with zooming/stretching/recentering features.

I have no real concept of the computing theory behind 3D graphics but I almost certainly know the math behind it.  What book/tutorial (preferably book) would you recommend for learning OpenGL in C++ from the very basics?  By the very basics I mean for someone who knows how to program C++ in a terminal and that's it.

This isn't completely relevant, but I am also learning Common Lisp (still in the early stages) and would like to use it behind the scenes for things like parsing and analyzing mathematical functions for a 3D grapher (one of the projects I would eventually like to do to test myself - a very long-run consideration; note that that is not the only thing I want to do) while using C++ to handle the rest of the program.  Is that possible to do that efficiently, and are there any tools that could help me?


C++ can get really complex really fast. And 3d graphics are no easy feat. I am not only doing 3d graphics as code but also as art. Be Prepared for chaos.  

My advice move as away as you can from C++. Prefer a higher level language like python or prepared for some real pain. 

Using directly OpenGl is not advisable as well even if you want to use C++ there are libraries that can make your life alot easier.

It is one thing to make a console app in C++ or even some basic GUI and another to make a full blown 3d app in C++.

---

### Post by hessiess on 2009-01-26
I recommend using a higher level graphics engine such as Irrlicht to begin with, as it hides a lot of the complexity. Be aware that 3D maths can get very complicated, most of which I don't currently understand, So unless you have a good understanding of vectors and matrices, start with 2D.

---

### Post by SIGTERMer on 2009-01-26
from what I've understood, you want to program a 3D application but have not specified what your goal is, if you want to used it to represent mathematical equations, plots, or other CAD operations, using a specialized graphics engine might not be a good idea.

anyway, it really doesn't matter as long as you know the basics. as for me, all my programs are written in C and openGL (sometimes POSIX too ;)). i personally recommend the red book (The OpenGL Programming Guide). although at the beginning you might hit a steep learning curve if you don't have any prior graphics experience. my advice, keep on reading :)

---

### Post by nrs on 2009-01-26
> **Kilon said:**
> C++ can get really complex really fast. And 3d graphics are no easy feat. I am not only doing 3d graphics as code but also as art. Be Prepared for chaos.  

My advice move as away as you can from C++. Prefer a higher level language like python or prepared for some real pain. 

Using directly OpenGl is not advisable as well even if you want to use C++ there are libraries that can make your life alot easier.

It is one thing to make a console app in C++ or even some basic GUI and another to make a full blown 3d app in C++.

The OP isn't going to learn anything about OpenGL if he just uses some library that abstracts everything away. No matter the library there'll always be the need to extend on it. Rudimentary knowledge of the core API is completely necessary. 

I couldn't disagree more with:
> It is one thing to make a console app in C++ or even some basic GUI and another to make a full blown 3d app in C++.It is one thing to make a simple test platform for rendering, etc. in languages like Python, utilizing it as your language of choice for your engine proper is completely different. 

Unless you're making toys, this is one of the few areas that speed of execution generally does matter, making it not particularly suitable (at least in a rendering capacity.) for large, professional work. 

That said the OP is isn't doing that so a higher-level language like Python may not be a bad choice.

---

### Post by Zorgoth on 2009-01-26
Well, thank you all for your helpful comments!  Math(s) isn't a problem for me; I'm Cantabrigian :), but I probably will start with 2D just to pick up basic concepts before I move onto 3D.  A lot of people here and elsewhere seem to like the Red Book; I will certainly look into that.

I'll probably stick to C++ because although I am a hobbyist and Python would probably make more sense for me if I was programming for the sake of programs, I'm a mathmo hobbyist, so I'm programming for the sake of programming, which is why most of the non-math-interest tools I'm learning are lower level.

If anyone has any other recommendations I still am very much interested and looking for more suggestions about any helpful references, tools, tips, or whatever else people may have to help!  Thank you again!

Also, if people think the Red Book is tough early on, is there something I could read up on/practice first to make it easier or should I just dive in?

---

### Post by Kilon on 2009-01-27
> **nrs said:**
> 

Unless you're making toys, this is one of the few areas that speed of execution generally does matter, making it not particularly suitable (at least in a rendering capacity.

The success of Wii is here to prove you wrong . On other hand python can create full blown 3d apps , highly professional. The slowness argument is highly exaggerated and so are the corresponding benchmarks. 

I have seen far too many 3d "toys" in C++ . And it is a language alot more likely to make "toys" cause is very difficult to master.

It all takes google to see what people have produced in Python and Java , but the OP decided on C++ , I have nothing more to add.

---

### Post by CptPicard on 2009-01-27
> **Zorgoth said:**
> 
This isn't completely relevant, but I am also learning Common Lisp (still in the early stages) and would like to use it behind the scenes for things like parsing and analyzing mathematical functions for a 3D grapher (one of the projects I would eventually like to do to test myself - a very long-run consideration; note that that is not the only thing I want to do) while using C++ to handle the rest of the program.  Is that possible to do that efficiently, and are there any tools that could help me?

Integrating Common Lisp into a C++ project is hard if not impossible (never heard it being done), as the CL system is such an complete environment in its own right. However, you might be interested in embedding some lightweight scripting-lisp (Guile?) into your "3D engine" written in C++.

---

### Post by nrs on 2009-01-27
> **Kilon said:**
> The success of Wii is here to prove you wrong .

Ugh. what? What about the Wii? 

> **Kilon said:**
> 
 On other hand python can create full blown 3d apps , highly professional. The slowness argument is highly exaggerated and so are the corresponding benchmarks. 

I have seen far too many 3d "toys" in C++ . And it is a language alot more likely to make "toys" cause is very difficult to master.

It all takes google to see what people have produced in Python and Java , but the OP decided on C++ , I have nothing more to add.
Python's slowness isn't exaggerated, it is easily demonstrable -- most of the time it's irrelevant and easy to forgive because of the increased speed of development, but (serious) rendering usually isn't one of these times. 

Can you name a single large scale, graphically intensive. game that utilizes it for rendering? Perhaps EVE Online, which wouldn't be surprising considering how slow it is, but it is hardly graphically intensive -- at least it shouldn't be.

One of the great things about these types of arguments is you can actually prove what you're saying, unlike political arguments which are just one giant opinion-fest. I'm willing to write a simple OpenGL/GLUT program to prove my point, but when I do demonstrate you're wrong I expect you to admit it. Fair? :)

---

### Post by Kilon on 2009-01-27
> **nrs said:**
> Ugh. what? What about the Wii? 


Python's slowness isn't exaggerated, it is easily demonstrable -- most of the time it's irrelevant and easy to forgive because of the increased speed of development, but (serious) rendering usually isn't one of these times. 

Can you name a single large scale, graphically intensive. game that utilizes it for rendering? Perhaps EVE Online, which wouldn't be surprising considering how slow it is, but it is hardly graphically intensive -- at least it shouldn't be.

One of the great things about these types of arguments is you can actually prove what you're saying, unlike political arguments which are just one giant opinion-fest. I'm willing to write a simple OpenGL/GLUT program to prove my point, but when I do demonstrate you're wrong I expect you to admit it. Fair? :)

Wii eliminated the myth that a good game is about high end graphics. It show the world that programs should always have quality and not quantity. 


I never said that python is not considerably slower to C++. 

But I have done and I am doing my own real practical benchmarks. 
I am using jython which is even slower to python because it does not interface with C/C++ like python but JAVA instead. 

The benchmarks were clear 300X - 50X times slower than JAVA. That is pretty unusable is it not!!!! Imagined my surprise when I have found out that the slowness factor was no more than 3 times!!! This is quite a gap. 

Of course in order to achieve the slowness that most benchmarks are showing for python,  some special conditions must be met. One should wonder however when these conditions are being met during a development program. For example a big factor is that the benchmarks code is based on the python functionality , in short python calling python. But I huge part of python is written in C/C++ and calling these functions will give close to C/C++ speeds. 

Now the argument about "serious" games written in python is an old one and done to death. But you may think that popularity of C++ is due to its speed. Ehhhh .... no it is not.... I happen to be an ex Delphi developer. Delphi can dance around C++ any time. They have been benchmarks of Delphi outperforming C++ square and fair. Of course I exclude that Delphi code can be mixed with Assembly code inside the same source file and that alone makes C++ lag seriously behind. 

Alot less "serious" games in Delphi , compared to C++ even compared to python. Why ? Is it because of lack of libraries ? Nope Delphi has libraries for DirectX and Opengl many C++ libraries have been converted to Delphi . Difficult langauge ? Nahh.... Delphi is very close to python syntax and many of its features were stolen by JAVA (see JAVABEANS ) and .NET (see winforms) as they were envied by all major languages. 

The problems is that the software market is prejudiced , highly prejudiced and stereotyped. You can see in the unimportant updates, the ugly unusable  guis , and the obsession to follow the crowd.        

Ok let us sum up what the average 3d coder should worry about 

1) Polygons
2) IKs
3) Textures
3) Bump Maps
4) Normal maps
5) Lighting
6) Particles
7) Fluids Dynamics
8) Crowd logic
etc. etc.

And you have to manage all these things through the ugliness and inefficiency of c++ langauge. Why ? Speed I hear you say, but after all this headache speed is the least of your problems.  What good is speed to an ugly looking game with ugly looking code ?  


I am not a C++ phobic , I have no objection someone using C++ ,I actually encourage it, C++ can enhance speed and give access to functionality that might be not available to python but there is absolutely no reason why someone should not use python along with his C++ code. And of course there are loads of reasons to start with python and then move to C++ **ONLY** if it is **necessary**.

C++ is highly unsuitable for sole programmers. IT is extremely difficult to master and hardly pays you for the effort.
But as any language it has its uses.

---

### Post by SIGTERMer on 2009-01-27
although i really can't say i don't understand your astounding hatred towards C/C++, but still, c is usable by itself. at least i use it. and it isn't as bad as you make it seem to be.
what i'm trying to say is that all Zorgoth asked for was a few good references and some good advice. not a fight over which programming language is best. because if such a language existed, we wouldn't be having this argument.

---

### Post by Kilon on 2009-01-27
> **SIGTERMer said:**
> although i really can't say i don't understand your astounding hatred towards C/C++, but still, c is usable by itself. at least i use it. and it isn't as bad as you make it seem to be.
what i'm trying to say is that all Zorgoth asked for was a few good references and some good advice. not a fight over which programming language is best. because if such a language existed, we wouldn't be having this argument.

Of course there is no "best" language 

nor there is a "best" game

nor there is "best" programmer

nor there is "best" programm

nor there is anything "best"

so why try ??? 

go home ... have a beer and spend the rest of your life staring at the ceiling .... it is all the same.

Damn... again I repeat myself. Well enough talk , back to coding.

---

### Post by happysmileman on 2009-01-27
> **Kilon said:**
> They have been benchmarks of Delphi outperforming C++ square and fair. Of course I exclude that Delphi code can be mixed with Assembly code inside the same source file and that alone makes C++ lag seriously behind.

C/C++ can do this too, and it's not a new thing either, please, when ranting about a language at least do a simple google search before making your claims.

---

### Post by Kilon on 2009-01-28
> **happysmileman said:**
> C/C++ can do this too, and it's not a new thing either, please, when ranting about a language at least do a simple google search before making your claims.

I have to be sincere, did not know that C/C++ can inline assembly code. Is it a feature that it was always there ? The last time I studied C++ was 1995. There was no mention of inline assembly code neither I saw source code use it. While in Delphi is quite popular. Well... it does not matter because it was not the point I wanted to make.

---

### Post by SIGTERMer on 2009-01-28
> **Kilon said:**
> 
nor there is a "best" game
nor there is "best" programmer
nor there is "best" programm
nor there is anything "best"
so why try ??? 


i never said that! all i said is that no language can be the best in every situation because of trade offs. but as you said before, less talk more coding

---

### Post by Kilon on 2009-01-28
> **SIGTERMer said:**
> i never said that! all i said is that no language can be the best in every situation because of trade offs. but as you said before, less talk more coding

And I never said I hate C++ nor did I said that C or C++ is useless (actually I said the opposite) . All i said that if you are going to dive inside the enormous complexity of 3d you will most likely prefer to have an "easy to use" programming language helping you simplify an already complex situation. If you were a 3d artist I would probably advice an "easy to use" software like Cinema 4D or Softimage XSI or Zbrush (actully Zbrush is the python equivalent here) and not Maya, Blender or 3D Studio max.

---

### Post by SIGTERMer on 2009-01-28
you like to argue, don't you?
ok then, everybody uses what works for them.

btw, don't mistake language simplicity with library simplicity. c is the simplest language i came across (in my opinion. don't kill bite my head off if you think otherwise). sure it doesn't offer built-in "futures" other languages do, but it offers enough. I just finished writing a 3D game engine a couple of weeks ago, and it was written in PURE c (along with openGL and POSIX). looking back, if i had to write another graphics project, i would still choose C!

in the end, i am absolutely sure you feel the same way i do about python. and because of that, this argument will continue on for a while. that is why i will try to stop it by saying this:

[CENTER]Everybody should use the language/tools they are comfortable with.  [/CENTER]

if python is as good as you clam it is, then i'm pretty sure every one will use it instead of c. including me!

PS: this is not the first time i have this discussion.. and unfortunately, it's probably not going to be the last.

---

### Post by CptPicard on 2009-01-28
Cut it off. 3D graphics is just undergrad linear algebra, and having a library like OpenGL helps you a lot.

C++ is a bit messy but it is not *that* messy.

---

### Post by Kilon on 2009-01-28
> you like to argue, don't you?

No . I love to argue. What is so wrong with arguing if it remains it the realms of civilized discussion ? 

> ok then, everybody uses what works for them.


I used many languages , software, tools and whatever in my life . I test anything I can get my hands on. Many have not worked for me. It took me some time and some real practice to draw my final conclusions. But even now I have my doubts "how final " they are. 


> btw, don't mistake language simplicity with library simplicity.
this argument makes sense, but is rare for a simple language to implement a difficult library. 

> c is the simplest language i came across (in my opinion. don't kill bite my head off if you think otherwise). sure it doesn't offer built-in "futures" other languages do, but it offers enough. 


I personally find difficult , pointers, memory management and low level libraries like opengl or directx. I would not say that these things requires a huge effort compared to python to be accomplished. I am not saying a beginner could not deal with these things.  But it is my opinion that these can slow you down and you can avoid them without any big sacrifices. 


> I just finished writing a 3D game engine a couple of weeks ago, and it was written in PURE c (along with openGL and POSIX). looking back, if i had to write another graphics project, i would still choose C!

it is your choice. Do you think I am going to stop you ? 

> 
in the end, i am absolutely sure you feel the same way i do about python. and because of that, this argument will continue on for a while. that is why i will try to stop it by saying this:



[CENTER]Everybody should use the language/tools they are comfortable with.  [/CENTER]

Even my mother is not absolutely sure about me. 

And a slave might be comfortable be a slave. The thought of being free might make him feel uncomfortable . Should he remain a slave ?

I say use the tools that make you productive . It is easy to fell in love with tools that make you more productive even if in the start you feel pretty uncomfortable with them. 

I am saying this 

Explore , test , improve , evolve....  

> if python is as good as you clam it is, then i'm pretty sure every one will use it instead of c. including me!

Unfortunately it does not work like this. If it did most people would be using Ubuntu or MAcOS instead of windows. People follow popular choices. Python is no the start , or the end  only part of the big equation. 

> PS: this is not the first time i have this discussion.. and unfortunately, it's probably not going to be the last.

No .... but you should not feel bad about it. I have observed that people feel so bad about the arguing that may take place in a forum. 

But simply they do not get it

Nobody knows the whole truth , we all know parts of it. Each one of us knows a different part, discussion is our meeting point, a place where we can assemble the pieces of the puzzle. 

 As long it remains a discussion we will exchange knowledge and experiences. 

Oh by the way , I am still waiting a link to the source code of your 3d engine.  I would love to see a full blown 3d project made solely  in C. And I am sure the OP will appreciate it as well.

---

### Post by NathanB on 2009-01-28
> **Kilon said:**
> Oh by the way , I am still waiting a link to the source code of your 3d engine.

Would you settle for an RTS written entirely in ASM?

[http://www.oby.ro/rts/](http://www.oby.ro/rts/)

---

### Post by NathanB on 2009-01-28
> **nrs said:**
> Python's slowness isn't exaggerated, it is easily demonstrable -- most of the time it's irrelevant and easy to forgive because of the increased speed of development, but (serious) rendering usually isn't one of these times. 


The choice of Python became a tremendous embarrassment for the One Laptop Per Child (OLPC) project when they developed the Sugar interface.  Execution times on a 500MHz CPU was painful!  :)

I'm not bashing Python here.  This was a case where the hardware team obviously did not communicate with the software team and vice-versa.  If the software people knew *ahead of time* that it had to run on a 500MHz CPU, they would have never chosen Python.  If the hardware people knew *ahead of time* that the GUI would be built in Python, they would have doubled the clock speed.

The lessons learned from poor project management...  <sigh>

---

### Post by Kilon on 2009-01-29
> **NathanB said:**
> The choice of Python became a tremendous embarrassment for the One Laptop Per Child (OLPC) project when they developed the Sugar interface.  Execution times on a 500MHz CPU was painful!  :)

I'm not bashing Python here.  This was a case where the hardware team obviously did not communicate with the software team and vice-versa.  If the software people knew *ahead of time* that it had to run on a 500MHz CPU, they would have never chosen Python.  If the hardware people knew *ahead of time* that the GUI would be built in Python, they would have doubled the clock speed.

The lessons learned from poor project management...  <sigh>

Thanks for the link , actually always really loved assembly for a strange unexplained reason. 

I have first met python in the action game "Freedom Force". The game was amazing and it until today is one of my favorite games.It has receive several excellent review from all top game magazines.  I really doubt whether the engine of the game is written in Python, probably is written in C/C++ . However all scenarios and logic of the game is written in python. Which mean that the editor and all moding tools use python to interface with the C++ engine. 

[http://www.freedomfans.com//ffpc/](http://www.freedomfans.com//ffpc/)

That might not impress today but the game itself has a minimum requirements of 300Mhz CPU , I way playing it in a 200Mhz CPU , never had any issue with slow downs. Did quite a bit of modding as well.

[http://coding.derkeiler.com/Archive/Python/comp.lang.python/2004-01/1635.html](http://coding.derkeiler.com/Archive/Python/comp.lang.python/2004-01/1635.html)

Freedom force is in not the only example, other excellent games that use python for handling their C++ library. "Severance: Blade of Darkness" and one of my favorite star trek games "Bridge Commander" . It is also used in the  "MYST :URU".

---

### Post by SIGTERMer on 2009-01-29
> **Kilon said:**
> 
Unfortunately it does not work like this. If it did most people would be using Ubuntu or MAcOS instead of windows. People follow popular choices. 


you got me there :) although not so much with OSX

> **Kilon said:**
> 
Oh by the way , I am still waiting a link to the source code of your 3d engine.  I would love to see a full blown 3d project made solely  in C. And I am sure the OP will appreciate it as well.

first of all, i never said it was a "full blown 3d" and it was made "solely"  in C (i used openGL and posix as well). it was a rushed project that wasn't given it's fair amount of time. i wrote it as a graduation project for collage (they are extremely primitive and consider pointers as "advanced C", a sad realty) to get an A ;D. the code is messy, and there is a lot of dead code in there. also, i haven't taken the time to use a 3D modeler for the characters. i drew them programitcally so don't blame me if you see simple polygons and spheres making up the models. yeah, and this project was my first big thing in the field of graphics. as for the link, my site has just gone off line (self hosted; it seems there is a problem with the DNS servers so i'm moving it) so your out of luck. i will -insh2 allah- post the link once i've settled in at my new location. if you like i have a demo on youtube:
[http://www.youtube.com/watch?v=cH1CExxwGfo]("http://www.youtube.com/watch?v=cH1CExxwGfo")

[QUOTE=NathanB]
[http://www.oby.ro/rts/](http://www.oby.ro/rts/)
[/QUOTE]

ok, i admire the fact that it was written in asm, but thats just scary!

---

### Post by Kilon on 2009-01-29
> **SIGTERMer said:**
> you got me there :) although not so much with OSX



first of all, i never said it was a "full blown 3d" and it was made "solely"  in C (i used openGL and posix as well). it was a rushed project that wasn't given it's fair amount of time. i wrote it as a graduation project for collage (they are extremely primitive and consider pointers as "advanced C", a sad realty) to get an A ;D. the code is messy, and there is a lot of dead code in there. also, i haven't taken the time to use a 3D modeler for the characters. i drew them programitcally so don't blame me if you see simple polygons and spheres making up the models. yeah, and this project was my first big thing in the field of graphics. as for the link, my site has just gone off line (self hosted; it seems there is a problem with the DNS servers so i'm moving it) so your out of luck. i will -insh2 allah- post the link once i've settled in at my new location. if you like i have a demo on youtube:
[http://www.youtube.com/watch?v=cH1CExxwGfo]("http://www.youtube.com/watch?v=cH1CExxwGfo")



ok, i admire the fact that it was written in asm, but thats just scary!


Ignore the "full blown" part , in any case your source will be just fine and an excellent starting point for the OP and me . 

I can host your source code if you want. I use google sites, and I highly recommend it. It does not give much space but it is easy to use and highly reliable.

[http://www.google.com/sites/help/intl/en/overview.html](http://www.google.com/sites/help/intl/en/overview.html)

---

### Post by SIGTERMer on 2009-01-29
ok, but i goto warn you the code IS MESSY!

[https://sites.google.com/site/sigtermer/]("https://sites.google.com/site/sigtermer/")

i never thought anybody would want the source, so i never cared about commenting or spelling. so please ignore the spelling mistakes no matter how sever they may be :)
also start with main.c in the source directory. it's your best shot.

---

### Post by SIGTERMer on 2009-01-29
ps: thanks for the google sites thing :)

---

### Post by Kilon on 2009-01-29
> **SIGTERMer said:**
> ok, but i goto warn you the code IS MESSY!

[https://sites.google.com/site/sigtermer/]("https://sites.google.com/site/sigtermer/")

i never thought anybody would want the source, so i never cared about commenting or spelling. so please ignore the spelling mistakes no matter how sever they may be :)
also start with main.c in the source directory. it's your best shot.

source code is always useful. 

you do not need a rocket science degree to understand C, even whan it is not commented, the same principles apply for all languages ( or almost all). I taken a quick look to your code , it is quite an effort, I am not very experienced with C so this is an opportunity to see how a C program behaves. 

no worries for the spelling English is not my mother tongue as well. 

I loved the youtube videos as well. Those creatures are hilarious but the engine seems just fine for a first try.

---

### Post by Kilon on 2009-01-29
> **SIGTERMer said:**
> ps: thanks for the google sites thing :)
you are welcome . I have been known to give good advice from time to time ;)

---

### Post by SIGTERMer on 2009-01-29
thanks :)
just a note, there is a bug in there a can't seem to catch (it never appears in the debugger) but i'm sure it's a race condition.

---

### Post by nrs on 2009-01-29
> **Kilon said:**
> Wii eliminated the myth that a good game is about high end graphics. It show the world that programs should always have quality and not quantity. 
 
In the "I never said" vain, I never said a good game was about high-end graphics. I simply asked for a game that was graphically intensive and used Python for rendering. 
> **Kilon said:**
> 
I never said that python is not considerably slower to C++. 

But I have done and I am doing my own real practical benchmarks. 
I am using jython which is even slower to python because it does not interface with C/C++ like python but JAVA instead. 

The benchmarks were clear 300X - 50X times slower than JAVA. That is pretty unusable is it not!!!! Imagined my surprise when I have found out that the slowness factor was no more than 3 times!!! This is quite a gap. 

Of course in order to achieve the slowness that most benchmarks are showing for python,  some special conditions must be met. One should wonder however when these conditions are being met during a development program. For example a big factor is that the benchmarks code is based on the python functionality , in short python calling python. But I huge part of python is written in C/C++ and calling these functions will give close to C/C++ speeds. 

Now the argument about "serious" games written in python is an old one and done to death. But you may think that popularity of C++ is due to its speed. Ehhhh .... no it is not.... I happen to be an ex Delphi developer. Delphi can dance around C++ any time. They have been benchmarks of Delphi outperforming C++ square and fair. Of course I exclude that Delphi code can be mixed with Assembly code inside the same source file and that alone makes C++ lag seriously
I don't know why you're bringing Delphi into this, we were discussing Python in particular and interpreted languages in general. Most C/C++ compilers have provided inline assembly for eons.

And I don't think the popularity of C++ is due to its speed. There are faster languages. I think C++ is popular because of inertia most importantly, and secondly it offers a balance between speed and features, not leaning decisively in either. It's completely average in almost every regard, imo.

I have consistently stated that speed isn't always important, but where it is, **serious** rendering work for example, Python in particular and interpreted languages in general just don't cut it.

A 2D platformer written in Python that is 10X slower than a C/C++ equivalent will still probably play well -- on reasonably modern computer at least. Then are things like Crysis which are barely runnable on top of the line hardware, performance sacrifices are unforgivable. 

I also stated earlier that it was fine for simple rendering, it's probably fine for moderately stressful rendering, but even that's pushing it.

Again, in the "I never said" vain I didn't say "serious games" don't use Python or interpreted languages, many of my favourites (Civilization IV for example) use Python, more than a few use Lua. What I said is most serious games don't deploy them in performance critical areas (rendering for example.)

---

### Post by nrs on 2009-01-29
> **Kilon said:**
> I have to be sincere, did not know that C/C++ can inline assembly code. Is it a feature that it was always there ? The last time I studied C++ was 1995. There was no mention of inline assembly code neither I saw source code use it. While in Delphi is quite popular. Well... it does not matter because it was not the point I wanted to make.
I don't think it's part of the language proper, it'd be impossible to standardize. Generally a standard/common compiler extension.

---

### Post by Kilon on 2009-01-29
I read your two post and I can say that now I agree with you. What you are saying now is making a lot more sense.  

All I said is that there is no reason to start doing 3d in C++ which is far more complex language than python. When the times comes that a beginner coder realize that python is not fast enough for his specific need then he can code part of the code to a more CPU efficient language , like JAVA,C++,Assembly or whatever.

I do not think a single coder even an experienced one will be coding Assasin creed or Crysis any time soon to justify a majority of code in C++. And even if he did he would greatly benefit from converting some of its code into python, as "freedom force" and other games do so for more than a decade now, with no speed penalty.

---

### Post by NathanB on 2009-01-29
> **Kilon said:**
> I have first met python in the action game "Freedom Force". The game was amazing and it until today is one of my favorite games.It has receive several excellent review from all top game magazines.  I really doubt whether the engine of the game is written in Python, probably is written in C/C++ . However all scenarios and logic of the game is written in python. Which mean that the editor and all moding tools use python to interface with the C++ engine. 

[http://www.freedomfans.com//ffpc/](http://www.freedomfans.com//ffpc/)

The rendering engine is indeed written in C++.

[http://www.emergent.net/en/Products/Gamebryo/Technical-Details/](http://www.emergent.net/en/Products/Gamebryo/Technical-Details/)

This thread's OP did not mention anything about wanting to write an editor or moding tools.

> That might not impress today but the game itself has a minimum requirements of 300Mhz CPU , I way playing it in a 200Mhz CPU , never had any issue with slow downs. Did quite a bit of modding as well.

[http://coding.derkeiler.com/Archive/Python/comp.lang.python/2004-01/1635.html](http://coding.derkeiler.com/Archive/Python/comp.lang.python/2004-01/1635.html)

Freedom force is in not the only example, other excellent games that use python for handling their C++ library. "Severance: Blade of Darkness" and one of my favorite star trek games "Bridge Commander" . It is also used in the  "MYST :URU".

Yes, Python is commonly used for the "scenarios and logic" scripting of gameplay.  Yes, after finishing his rendering engine, the OP will likely want to choose a scripting language to more easily control his 3D objects.  I do not know what merits Python would bring to the table, but there are certainly more options available.  Depends on how far the OP wishes to develop his system, I guess.

---

### Post by skullmunky on 2009-02-01
Hey, if the OP is still reading this, also check out Processing (not C, it's based on Java, but a really quick way to learn OpenGL), and also OpenFrameworks, which is C++/OpenGL/GLUT in a nicely organized ... um ... framework.

---

### Post by Kilon on 2009-02-01
> **NathanB said:**
> The rendering engine is indeed written in C++.

[http://www.emergent.net/en/Products/Gamebryo/Technical-Details/](http://www.emergent.net/en/Products/Gamebryo/Technical-Details/)

This thread's OP did not mention anything about wanting to write an editor or moding tools.



Yes, Python is commonly used for the "scenarios and logic" scripting of gameplay.  Yes, after finishing his rendering engine, the OP will likely want to choose a scripting language to more easily control his 3D objects.  I do not know what merits Python would bring to the table, but there are certainly more options available.  Depends on how far the OP wishes to develop his system, I guess.

I used the example of games not to advice witting in C++ and then using python to simplify your code but to show how minimal the speed loss of python is when there is some careful planning. 

Actually I advice quite the opposite, total avoidance of c++. 

My life's strategy is "Start with Easy and then move to more difficult". I almost failed in one of my Law exams cause I did not take this idea very slowly. It is easy to carried away with difficult tasks  ,lose valuable time and end up with a result that in no way reflects your effort.  The choice of the right programming language and the right libraries will ease the process quite significantly and keep your focus in the thing that really matter. 

So it is a smart strategy to go the easy way first and then raise the difficult only when is deemed necessary. If and only if speed is needed and python performs slowly then only that portion will be written in C++. This way you secure that you spent the minimum amount of time for the maximum result. 

I think it takes a very long way to reach the very high standards of "Freedom Force" to start worring that you should have been using mainly C++ from the start. When you are a single developer loss of time and unecessary complexity is two things that are your biggest enemies. I do not think that the sole use of C++ is advisable for any single programmer or small teams.

---

