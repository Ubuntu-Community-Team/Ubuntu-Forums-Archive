---
title: "Programming using OpenGL"
date: 2008-10-08
forum: Programming Talk
---

### Post by LinksAwakener on 2008-10-08
Okay, I've spent a couple days trying to figure this out, and it's really starting to irritate me. I can't figure out how to develop OpenGL programs. I don't have the headers (or the entire GL/ directory) and I've read something about installing Mesa, but that failed. What do I do?? All I want to do is program! ](*,)

---

### Post by snova on 2008-10-08
Just in case you installed the wrong package, it's "mesa-common-dev".

How exactly did it fail?

---

### Post by Sockerdrickan on 2008-10-08
install freeglut dev and you'll get everything

---

### Post by snova on 2008-10-08
Yes, I agree. However, although GLUT makes starting off with OpenGL simpler, it won't suffice for everything, and you'll eventually have to learn usage of a complete widget toolkit to do much more. Fortunately, although a lot of tutorials use GLUT, most of the code can be adapted to another toolkit.

The package in this case is "freeglut3-dev".

---

### Post by leg on 2008-10-08
Also take a look at [Ogre]("http://ogre3d.org/"). It is a very good lib and wraps opengl.

---

### Post by sidran on 2008-10-08
I've had to do a bit of OpenGL programming myself.  I would suggest freeglut, as others have.  If you're starting out, it's a great place to go.  It has general functions that do a lot for you, including setting up OpenGL and a window to draw to.

Once you install the dev packages (you NEED to get the headers and libraries) I would recommend using the online versions of the red and blue OpenGL reference books.  Those have always been my first reference point if I had any questions.  They do a good job of explaining OpenGL's gl, glu, and glut functions (you'll see the difference when you read through them).

Here's the links for the blue book and the red book:
[http://www.opengl.org/documentation/blue_book/](http://www.opengl.org/documentation/blue_book/)
[http://www.opengl.org/documentation/red_book/](http://www.opengl.org/documentation/red_book/)

Links to the HTML versions are at the bottom of each page.

---

### Post by LinksAwakener on 2008-10-08
Wow...you guys gave me much more help than I expected. Thank you! Freeglut was exactly the package I was looking for, but my thought was to get gl and glu working, then worry about glut. Silly me for not thinking there'd be a package of all three. :p

I'll check out the other packages after a bit, once I get familiar with the new information I've received. Thanks again, all of you, for your help!

EDIT: Is Ogre an OO wrapper for OpenGL?

---

### Post by Sydius on 2008-10-08
> **LinksAwakener said:**
> 
EDIT: Is Ogre an OO wrapper for OpenGL?

It's a 3D engine/framework.  It does a whole lot more than just OpenGL, like scene composition, etc.  I loved it, but I do mostly 2D games (with OpenGL), so it isn't for me.  I use SDL (Simple DirectMedia Layer) instead.

---

### Post by shadylookin on 2008-10-08
Also for whatever its worth there are openGL bindings for java with jogl, and python if you don't like using C/C++

---

### Post by Mickeysofine1972 on 2008-10-09
The link to the Ubuntu Games Developer Wiki on my signature is a good place to start, it has install guides and a few examples too

[http://ubuntu-gamedev.wikispace.com](http://ubuntu-gamedev.wikispace.com)

Mike

---

### Post by leg on 2008-10-09
> **LinksAwakener said:**
> 

EDIT: Is Ogre an OO wrapper for OpenGL?
As stated Ogre is more than just a wrapper and will provide you with scene graph/resources etc management. It is also cross platform and will wrap opengl when on a Linux platform but can be used wrapping Directx if you run your program on a Windows platform. Very much worth a look.

---

### Post by rnodal on 2008-10-09
My humble 2 cents. As many have mentioned, you will eventually realize that glut and friends are very limited and eventually will be forced to move to another library like SDL, GLFW etc. So I recommend you move into any alternative library right of way. All you need to do is to find a library that handles input, can open a window for you to create a OpenGL context. After that, then you are set to go to develop with OpenGL. I don't know which IDE you will be using(if any) but if you decided to go with Codeblocks then you may want to take a look at my project's codeblocks project file. Take care,

-r

---

### Post by BobCFC on 2008-10-11
There are some great screencasts at [http://www.videotutorialsrock.com/](http://www.videotutorialsrock.com/) which walk you through the basics of making simple games.

You especially might want to look at **Lesson 0c: Getting OpenGL Set Up on Linux **
[http://www.videotutorialsrock.com/opengl_tutorial/get_opengl_setup_linux/home.php](http://www.videotutorialsrock.com/opengl_tutorial/get_opengl_setup_linux/home.php)


I found it handy for setting up the libraries and make files etc and then from then on you can use any ordinary OpenGL tutorial, even those for windows.

---

