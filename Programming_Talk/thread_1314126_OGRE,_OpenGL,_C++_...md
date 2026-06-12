---
title: "OGRE, OpenGL, C++ .."
date: 2009-11-04
forum: Programming Talk
---

### Post by hungryOrb on 2009-11-04
Hi all,
I want to start learning some stuff, and hopefully give back to the community. I'd like to learn a bunch of the above systems, and would basically like some referrals to some software to use..
Editor, compiler and whatever else is needed.. I need to put my trust in someone, somewhat blindly, to get this started.
Thanks for considering.
Robin

---

### Post by Simian Man on 2009-11-04
OK well I think we need a bit more information from you first.  What exactly are you hoping to accomplish?  Do you want to program a game for Linux?  What exactly is your programming experience?

If you have never programmed before, I'd heavily recommend against starting with C++.  There are much better languages to learn to program with such as Python.  Also if you are beginner, you will have to spend some time getting comfy with programming in general before you begin writing 3D games as that is a whole 'nother layer of complexity and it is best to deal with them one by one.

---

### Post by Vernünftiger Verbrecher on 2009-11-04
In any event, I would highly recommend learning SDL before learning OpenGL. Programming with SDL is really beginner - intermediate level, whereas OpenGL is more advanced, in my opinion.

---

### Post by shae on 2009-11-04
Well, you should start with mastering C++.

A good beginning tutorial is here: [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

I personally suggest that you stay away from IDEs until after you master programming in a language or two.  This will prevent you from over-relying on the nice things that IDEs offer.

Thus, you should already have what you need to start writing small terminal C++ programs: gedit for coding and terminal.

When you want to compile, pop open a terminal and use the following command:

```
g++ *test.cpp* -o *test*
./*test*
```

Starting with C++ is the absolute best thing to do if you want to program in those 3D libraries.

Once you have a good knowledge of C++ and have written some non-trivial console programs in it, you should move on to SFML, small fast media library.  I suggest this library because their site has an excellent tutorial to beginning 2D programming and can also be used as the window/input/sound provider for OpenGL and, as far as I recall, Ogre too.

Then, after you have completed several basic games with SFML, then you can start experimenting with Ogre and OpenGL.  You should probably focus on Ogre if you are wanting to create games whereas you might want to focus on OpenGL if you are wanting to just mess with 3D tech effect demos.

You have an insanely long road ahead of you so you better get started! ):P

---

### Post by grayrainbow on 2009-11-04
Since OGRE is written in C++, and OpenGL is generally C API you'll need C++ first, logicaly :) Then OGRE will involve some general computer graphics learning(let say like what different kind of blending mean), which mean OpenGL goes befor it.
About OpenGL - it's quite easy at start up(I challenge everybody who thing otherwise to take a look at DirectX), [http://www.starstonesoftware.com/OpenGL/](http://www.starstonesoftware.com/OpenGL/), other graphics API will be generally waste of time. But you'll need to develop bit of a matrix understanding if you are really in graphics stuff, couse that's what 3D is all about :)

---

### Post by hungryOrb on 2009-11-04
> **shae said:**
> Well, you should start with mastering C++.

A good beginning tutorial is here: [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

I personally suggest that you stay away from IDEs until after you master programming in a language or two.  This will prevent you from over-relying on the nice things that IDEs offer.

Thus, you should already have what you need to start writing small terminal C++ programs: gedit for coding and terminal.

When you want to compile, pop open a terminal and use the following command:

```
g++ *test.cpp* -o *test*
./*test*
```

Starting with C++ is the absolute best thing to do if you want to program in those 3D libraries.

Once you have a good knowledge of C++ and have written some non-trivial console programs in it, you should move on to SFML, small fast media library.  I suggest this library because their site has an excellent tutorial to beginning 2D programming and can also be used as the window/input/sound provider for OpenGL and, as far as I recall, Ogre too.

Then, after you have completed several basic games with SFML, then you can start experimenting with Ogre and OpenGL.  You should probably focus on Ogre if you are wanting to create games whereas you might want to focus on OpenGL if you are wanting to just mess with 3D tech effect demos.

You have an insanely long road ahead of you so you better get started! ):P

Shae, this seems a nice place to start! I'm confused about the compiler and editor though.. I realise linux has it's own compiler the g++ right? But what about editor? How do you use the terminal to write out that?
If I write one of the lines of the tutorial "#include <iostream>" how do I go to next line without executing that line in singular? Did you mean use gedit? Thanks..

---

### Post by whoop on 2009-11-04
> **hungryOrb said:**
> Shae, this seems a nice place to start! I'm confused about the compiler and editor though.. I realise linux has it's own compiler the g++ right? But what about editor? How do you use the terminal to write out that?
If I write one of the lines of the tutorial "#include <iostream>" how do I go to next line without executing that line in singular? Did you mean use gedit? Thanks..

Yeah, you can use gedit. You are supposed to save your code in a text-document (helloworld.cpp for example), after you saved that you can compile it via the terminal as suggested above (g++ helloworld.cpp -o helloworld). The compiler (if you have no errors in your text-document) will create a binary executable file for you (in this case helloworld)
You can execute/start this program in the terminal as well (./helloworld)

try pasting this testprogram in a textfile and compile it:
```

#include <iostream>
int main()
{
  cout << &#8220;Hello World!\n&#8221;;
  return 0;
}

```
It should print "Hello World!" in your terminal.

Be prepared you will need allot of time to get really productive, especially if you want to do 3D stuff. 
So take sweet time, I'll see you in a couple of years :D

---

### Post by efexD on 2009-11-04
if you're starting C++ Ogre would be the exact opposite of what you should be doing. it's more for advanced C++ users.

Get a free C++ book like Thinking in C++ to get you started.

(stay away from devC++ and C++ for dummies)

---

### Post by hungryOrb on 2009-11-04
> **whoop said:**
> Yeah, you can use gedit. You are supposed to save your code in a text-document (helloworld.cpp for example), after you saved that you can compile it via the terminal as suggested above (g++ helloworld.cpp -o helloworld). The compiler (if you have no errors in your text-document) will create a binary executable file for you (in this case helloworld)
You can execute/start this program in the terminal as well (./helloworld)

try pasting this testprogram in a textfile and compile it:
```

#include <iostream>
int main()
{
  cout << “Hello World!\n”;
  return 0;
}

```
It should print "Hello World!" in your terminal.

Be prepared you will need allot of time to get really productive, especially if you want to do 3D stuff. 
So take sweet time, I'll see you in a couple of years :D

Whoop, thankyou for clarifying. It's the key I needed..
Hopefully less time :D

---

### Post by hungryOrb on 2009-11-04
thankyou for each reply!

---

