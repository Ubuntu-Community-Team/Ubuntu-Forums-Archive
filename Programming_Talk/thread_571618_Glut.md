---
title: "Glut"
date: 2007-10-09
forum: Programming Talk
---

### Post by knutsford on 2007-10-09
I had some general questions about using GLUT in ubuntu. Also I would like to note that I am fairly new to using Linux.

1. Do I have to link the libraries in to any path or is that already done? If I do need to link it which folder, where and how do I do that? 

2. Are there any alternate glut files I should download using synaptic manager?

As a side note we are using GLUT for our game that we are making in case you were wondering. It is a 2D top down adventure type game.

Thanks.

---

### Post by Wybiral on 2007-10-09
Assuming you're using C or C++:

You mean link to the GLUT library when compiling? Just use the "-l" flag, something like this:

```

gcc my_code.c -lglut -lGLU -lGL -o my_program

```

That will link to glut, GLU, and OpenGL.

Also, for a game, GLUT isn't always the best option. It's meant to just get the window up quickly with minimal code, but it isn't really designed very well for writing games. A possible alternative would be SDL. It has supporting libraries to load images/play sound/handle input/handle threads/handle event messages... And so on. It's also really portable and really widely used.

---

### Post by moma on 2007-10-10
I want to add this.

In Debian / Ubuntu you will need the "freeglut3-dev" package.
$ [COLOR="SeaGreen"]sudo apt-get install freeglut3-dev[/COLOR]
Or install it via the Synaptic Package Manager (in the menu).

Here you will find a lot of good GLUT examples.
Browse to [this site...]("http://ubuntuforums.org/showthread.php?p=2816470#post2816470") and study the links under the "**Note 5**".  
Especially read the "example: how to run the lessons..."

---

### Post by gnusci on 2007-10-10
Give a look to this sticky:

[http://ubuntuforums.org/showthread.php?t=554070](http://ubuntuforums.org/showthread.php?t=554070)

---

