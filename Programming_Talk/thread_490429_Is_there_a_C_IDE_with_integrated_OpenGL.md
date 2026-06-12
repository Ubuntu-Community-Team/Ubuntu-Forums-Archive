---
title: "Is there a C IDE with integrated OpenGL?"
date: 2007-07-02
forum: Programming Talk
---

### Post by Game_boy on 2007-07-02
I'm interested in learning C so I can possible eventually contribute to the Linux community and application base (I'm 15). Is there an IDE that has the standard library and OpenGL easy to use within it, and compiles for Linux using GCC and possibly Windows ("Compiles for" means "binaries that run on")? Your start guide only gives one suggestion and I assume it's not the most accessible. Thanks.

---

### Post by LaRoza on 2007-07-02
> **Game_boy said:**
> I'm interested in learning C so I can possible eventually contribute to the Linux community and application base (I'm 15). Is there a simple, graphical IDE that has the standard library and OpenGL easy to use within it, and compiles for Linux and preferably Windows? Your start guide only gives one suggestion and I assume it's not the most accessible. Thanks.

Your question is slightly confusing. You say you are interested in learning C, what other programming languages do you know?

All IDE's are graphical, and none are simple. There is a sticky in this forum about IDE's.

An IDE is not a compiler. 


To get the programming tools:
```

sudo aptitude install build-essential

```

"...and compiles for Linux and preferably Windows?", what does this mean?

---

### Post by crislosi on 2007-07-02
Hi, I don't know any IDE integrating OpenGL but I've compiled my own programs writng in C++ with OpenGL with Eclipse, Qt3 and Anjuta ides. 
I can't explain about this because my english is very poor and the explanation is very long and very technical.
I've made a videotutorial about this using easyeclipse but this is in spanish, sorry :(  and the quality is very poor.The link is

[Link Video]("http://tobal.lynksee.com/blog/2007/04/10/tutorial-para-utilizar-cc-con-easyeclipse-y-eclipse-incluye-opengl/")

Greetings :popcorn:

---

### Post by LaRoza on 2007-07-02
> **crislosi said:**
> Hi, I don't know any IDE integrating OpenGL but I've compiled my own programs writng in C++ with OpenGL with Eclipse, Qt3 and Anjuta ides. 
I can't explain about this because my english is very poor and the explanation is very long and very technical.
I've made a videotutorial about this using easyeclipse but this is in spanish, sorry :(  and the quality is very poor.The link is

[Link Video]("http://tobal.lynksee.com/blog/2007/04/10/tutorial-para-utilizar-cc-con-easyeclipse-y-eclipse-incluye-opengl/")

Greetings :popcorn:

Your english is better than my Spanish.

---

### Post by Game_boy on 2007-07-02
Let me restate.

I want an C IDE where I can use OpenGL functions just as easily as C ones. I want it not simple, but powerful enough so I don't need to edit config files or use a terminal. I want it to automatically use GCC to complie to Linux too.

So what you're basically saying is that C is completely inaccessible to anyone who hasn't already learnt it. Well, thanks anyway.

---

### Post by LaRoza on 2007-07-02
> **Game_boy said:**
> Let me restate.

I want an C IDE where I can use OpenGL functions just as easily as C ones. I want it not simple, but powerful enough so I don't need to edit config files or use a terminal. I want it to automatically use GCC to complie to Linux too.


Sorry, I don't use IDE's. Compiling with  the terminal is not difficult, and if your program is command line, it is easier, and faster.


> **Game_boy said:**
> 
So what you're basically saying is that C is completely inaccessible to anyone who hasn't already learnt it. Well, thanks anyway.

No, you can learn C. But starting out with C and OpenGL is a lofty goal. Check out my sig for learning how to program.

If you are just starting out, which it seems like, you should consider learning Python. It is easy to learn, it is powerful, it is easy to make GUI's with it, and it is completely portable between Windows and Linux. (You also don't need to compile)

Check out my wiki and good luck!:D

---

### Post by Game_boy on 2007-07-02
Actually I do use a sort of interpreted (but slow and DirectX dependent) language that has built-in everything - debug, forced OOP, fast and automated compilation to executable, huge standard library.

The problem is it's not free software, it's 100 times slower than C and again, it only runs on Windows.

But I do have a grasp of what programming is about from it, so "Learning to Program" is not an issue with me.

Is there no such thing as an IDE which natively does OpenGL? Say I wanted to make Pong with it - what would be the fastest and/or easiest way?

---

### Post by LaRoza on 2007-07-02
> **Game_boy said:**
> Actually I do use a sort of interpreted (but slow and DirectX dependent) language that has built-in everything - debug, forced OOP, fast and automated compilation to executable, huge standard library.

Is there no such thing as an IDE which natively does OpenGL? Say I wanted to make Pong with it - what would be the fastest and/or easiest way?

What is Pong?

---

### Post by Game_boy on 2007-07-02
It's the most basic (but graphical) 2D game I could think of. Two bats, one ball. First to 10 points wins. Repeat.
[IMG]http://upload.wikimedia.org/wikipedia/en/thumb/f/f8/Pong.png/250px-Pong.png[/IMG]

---

### Post by LaRoza on 2007-07-02
Just found Pong on Wikipedia, if you have no experience with GUI programming, that will be difficult. You would want to use C/C++, but you would probably want to build up experience with GUI programming with a simpler language like Python and one of its GUI modules.

I am not into GUI programming, so I can't make any recommendations.

What is this language you know?

---

### Post by Game_boy on 2007-07-02
er... GML...

[http://en.wikipedia.org/wiki/Game_Maker_Language](http://en.wikipedia.org/wiki/Game_Maker_Language)
[http://en.wikipedia.org/wiki/Game_Maker](http://en.wikipedia.org/wiki/Game_Maker)

Like I said, it's not technically a programming language, but it helped me to realise I wanted to use C/C++. It's severely limiting.

---

### Post by LaRoza on 2007-07-02
If you have never used another language, looking at python will help. I would also recommend looking at Java, however Java is...different but it will probably do what you want.

I take it that this GML is not command line? When using other programming languages, like C/C++, Java, Python, and most others, you will have to write CLI programs first.

---

### Post by Game_boy on 2007-07-02
OK. Thanks. I'll take another look at all the options.

---

### Post by LaRoza on 2007-07-02
With programming, there is  constant learning, that is what I love about it.

---

### Post by Rui Pais on 2007-07-02
> **Game_boy said:**
> I'm interested in learning C so I can possible eventually contribute to the Linux community and application base (I'm 15). Is there an IDE that has the standard library and OpenGL easy to use within it, and compiles for Linux using GCC and possibly Windows ("Compiles for" means "binaries that run on")? Your start guide only gives one suggestion and I assume it's not the most accessible. Thanks.

Hi,
may i suggest Code::Blocks. It's a nice and simple IDE for C and C++, pretending to be the more pluri-platform possible and that can be set to work with openGL.
Here some links:
[http://wiki.codeblocks.org/index.php?title=FAQ](http://wiki.codeblocks.org/index.php?title=FAQ)
[http://forums.codeblocks.org/index.php/board,20.0.html](http://forums.codeblocks.org/index.php/board,20.0.html) (Download NightlyBuild, stable than old official release)
Some tips for windows:
[http://www.sci.brooklyn.cuny.edu/~goetz/codeblocks](http://www.sci.brooklyn.cuny.edu/~goetz/codeblocks)
Tips for openGL:
[http://www.sci.brooklyn.cuny.edu/~goetz/codeblocks/glut](http://www.sci.brooklyn.cuny.edu/~goetz/codeblocks/glut)

---

### Post by Praill on 2007-07-02
If you wanted to start off making little games like pong you'd be better off using a different library. OpenGL can be a nightmare (as others have stated) and is a bit more advanced. Some good libraries to start with for graphical programming are allegro and SDL (the latter of which is much nicer).
Here's a nice beginning SDL tutorial that even shows you how to make Anjuta (native GTK IDE) work with it.
[http://lazyfoo.net/SDL_tutorials/index.php]("http://lazyfoo.net/SDL_tutorials/index.php")

This tutorial is probably exactly what youre looking for. At the end it even helps you get started with OpenGL.

---

### Post by maddog39 on 2007-07-02
> **Game_boy said:**
> er... GML...

[http://en.wikipedia.org/wiki/Game_Maker_Language](http://en.wikipedia.org/wiki/Game_Maker_Language)
[http://en.wikipedia.org/wiki/Game_Maker](http://en.wikipedia.org/wiki/Game_Maker)

Like I said, it's not technically a programming language, but it helped me to realise I wanted to use C/C++. It's severely limiting.
Can you say, "huge pile of smoldering proprietary crap that only runs on windows?"

---

### Post by runningwithscissors on 2007-07-03
There is no such thing as a C IDE with "integrated OpenGL". That's like asking if there is an IDE with "integrated libxml or integrated <insert any C library here>". OpenGL is a library like any other.
So, if you want code-completion for OpenGL functions, I suppose any modern IDE (KDevelop?) would do the job. By default it generates Linux binaries, but I suppose you could wrestle with getting a cross-compiler to work with it to generate binaries for Windows.

---

