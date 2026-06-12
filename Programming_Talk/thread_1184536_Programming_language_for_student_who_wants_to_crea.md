---
title: "Programming language for student who wants to create games"
date: 2009-06-11
forum: Programming Talk
---

### Post by tdrusk on 2009-06-11
As the title says, I am going to be tutoring a teenager who wants to make games. I talked to his mom on the phone and informed her I don't actually know how to make games, but I can definitely get him going in the right direction. I told her in order to make games he needs to understand programming. Basically he needs to learn to walk before he can run. 

I have had classes in both Java and C++. After some slight research I understand that they both support OpenGL and DirectX. I like this because which ever direction I steer him it he can probably use to make a game.

So I was just wondering what programming language would be suitable for teaching somebody new to programming that eventually wants to learn to create games. I am thinking Java because it is easier to debug and I know it pretty well. What are your thoughts?

---

### Post by benj1 on 2009-06-11
well it basically come down to which programming language to learn to start programming.
my first language was c++ but i wasn't trying to learn games programming, and i don't think you would be able to jump straight in to games programming easily, if you want that, something like python and pygame might be better.
i suppose it comes down to the person you are teaching, if they want 'instant' results, python might be better.
if they have the patience and are willing to put the time in, and want to get to the point of making professional quality, resource intensive games, then by all means go with c++ or java

---

### Post by tdrusk on 2009-06-11
> **benj1 said:**
> well it basically come down to which programming language to learn to start programming.
my first language was c++ but i wasn't trying to learn games programming, and i don't think you would be able to jump straight in to games programming easily, if you want that, something like python and pygame might be better.
i suppose it comes down to the person you are teaching, if they want 'instant' results, python might be better.
if they have the patience and are willing to put the time in, and want to get to the point of making professional quality, resource intensive games, then by all means go with c++ or java
Okay cool. I just wanted to find a happy place between creating boring programs and fun games. I think I am going to give him assignments such as create a character using a class with weapons, health, etc. 
I'll try to make the learning environment fun. 

I have been meaning to learn python, so that wouldn't be that bad of an option except when he hits college(considering he is going to my university) he will have to learn Java and C++ anyway. 

Whichever programming language I choose, it should definitely help him move into a positive directing when learning another.

I don't feel like making a new thread for this. Is there a guide to drawing out programs, like on a piece of paper? I want him to be able to map out his ideas before programming.

---

### Post by Neon Lemmy Koopa on 2009-06-11
flow charts aren't a bad idea.

[IMG]http://www.codeproject.com/KB/cpp/gx_recursion_articles/recursion_flowchart2.png[/IMG]

in which parallelograms represent i/o actions, ellipses (obviously) are the beginning and end, the rectangles are data processing, and the diamonds are conditionals (if statements, for loops, etc)

Disclaimer: Image source =[ http://www.codeproject.com/KB/cpp/gx_recursion_articles.aspx?display=Print]("http://www.codeproject.com/KB/cpp/gx_recursion_articles.aspx?display=Print")

You could also use what is known as psuedocode.  Thats writing down the program in pure english, and then use that to write the actual code.

Example:
A program to average 2 exam scores:

PSUEDOCODE:
```
Get the two scores
Calculate the average
Print out the average
```Python code:
```
def main(): 
     score1, score2 = input("Enter two scores separated by a comma: ") 
    average = (score1+score2)/2.0 
 
    print "The average of the scores is", average 
 
main()
```

---

### Post by HavocXphere on 2009-06-11
Go with C++ and OpenGL.

C++ because there are tons of game examples and most of the game orientated code is C++/C.

OpenGL because the basics of 3D are easier to understand than with DX. For serious game dev one would want DX though.

With OGL you'll want to use a framework piece of code...cause it needs a bunch of stuff for initializing etc that will make him lose interest.

---

### Post by NielsBhor on 2009-06-11
Game programming exceeds just basic amatuer programming. It involves understand of physics, rendering, shaders, GPU innerworks, etc...

Most games are built on a very fast compiling language such as C and C++ as someone else have stated. This is why there are more books on game programming that uses C and C++. In fact, the PS2 games uses mostly C++ code.

openGL is available for you to get started. You can start to get familiarizes yourself with freeglut libraries and open up some searches on tutorials with openGL. Once you get the hang of the syntax, you can study how the rendering pipeline works using shaders, z-buffers, etc...

Spend alot of time focusing and reading. My recommendation.

---

### Post by Neon Lemmy Koopa on 2009-06-11
You've got alot going.  You could teach game programming in C++ or Java.  With C++ you have OpenGL and SDL available, and with Java you have OpenGL, and numerous game libraries available (I recommend LWJGL).  It's pretty much a matter of choice.

Only downside to Java is that documentation is limited, so unless you're good at reading Javadocs and source code, you may not learn much for Java.

---

### Post by Ariel David Moya Sequeira on 2009-06-11
I'd go with Python and Pygame. I think it's the easiest way to make 2D games without the need to learn a lot about programming theories. However, if your student is anxious to learn how to make 3D games, then I'd recommend using Blender. It uses Python as programming language.

Anyway, the most important part of a game is it's design. That will determine if the software is going to be very complex or rather simple. The programming language is not an issue if you know it well.

I can say it really pays to make the game design a priority because the first complete games I programmed were PONG and SNAKES in Assembly. After that, I had to program a Backgammon game in PASCAL, with 'Artificial Intelligence' included.

My last recommendation: start with simple games. Don't overwhelm your student with too complex codes and theories.

---

### Post by phrostbyte on 2009-06-11
Ogre3D is a modern C++ rendering engine

---

### Post by noerrorsfound on 2009-06-11
Not C++. For a beginning programmer learning it as a first language, it's too difficult and takes too long to get satisfying results. It's hard to stay motivated when you can't make any of those cool games you want to make and you know that it'll be a long time before you can.

From personal experience.

---

### Post by Neon Lemmy Koopa on 2009-06-11
> **noerrorsfound said:**
> Not C++. For a beginning programmer learning it as a first language, it's too difficult and takes too long to get satisfying results. It's hard to stay motivated when you can't make any of those cool games you want to make and you know that it'll be a long time before you can.

From personal experience.
I second that.  Even with Java.  I wanted to write a game in java, but it's been two years since I started and I still don't have the skill (and currently motivation), to get going.

My suggestion is Python.  It's designed to be a very simple language while at the same time still being VERY powerful.  Python will have you more focused on actually writing your program instead of debugging it.  In my experience with Java, I have had countless times where I had to correct syntax errors and such.  Numerous ones.  Python isn't like that, as I don't run into as many exceptions.

Python also allows you to use PyGame, which is a port of the C library SDL to Python, giving you access to graphics, sound, input, and so on.  PyGame itself is relatively easy to learn.  Matter of fact, I know some people who didn't do crap with Python and went straight to PyGame.  And they still pulled it off, and learned some Python from it.

---

### Post by jimi_hendrix on 2009-06-11
python

then use Panda3d as the engine

maybe teach him some C++ on the side...

also, definitely use an engine, do not use straight opengl...it just saves so much time and pain

---

### Post by NielsBhor on 2009-06-11
Try going to this site. It has some stuff on the Quake 2 open source code in C ported over the C++ .net.

[http://www.codeproject.com/KB/mcpp/quake2.aspx](http://www.codeproject.com/KB/mcpp/quake2.aspx)

Interesting for those who are interested in it.

---

### Post by soltanis on 2009-06-11
> **HavocXphere said:**
> Go with C++ and OpenGL.

C++ because there are tons of game examples and most of the game orientated code is C++/C.

OpenGL because the basics of 3D are easier to understand than with DX. For serious game dev one would want DX though.

I'd like to point out two things, second first, DirectX and OpenGL are in the field of graphics one and the same -- neither is particularly better than the other (though OpenGL is definitely cross-platform, for all that's worth).

C++ would not be a good choice for someone who cannot program yet. Forcing someone to learn the basic concepts of programming, then heaping on top of that manual memory management, pointers (or references or whatever you C++ blokes call your pointer clones), the concepts of the standard library and all that jazz will only serve to frustrate the student.

His first programs are not going to be production quality anyway. Better teach him how to walk, as OP said, before he runs, so I would learn him on Python/pygame.

---

### Post by tdrusk on 2009-06-11
I'm really digging the idea of Python. I don't know Python, but after looking at some tutorials I think I can teach it if I stay ahead a little bit. This will help me and him at the same time.

Awesome. Thanks guys!

btw that flowchart image is helpful. Thanks.

---

### Post by rizman on 2009-06-12
Might I suggest something different? (hopefully noone will hunt me down for suggesting this :-))

Try C# and XNA under...cough...Windows...cough. That is, if you have a Windows PC at your disposal.

No seriously. You said that you already know Java and C++. Then you will have no problem at all to start using C#. At least from a syntex point of view. 

XNA, in short, is a managed framework which is aimed at game development. Internally it uses DirectX, but provides a very easy to learn API and you can get your game prototyped pretty fast. If you buy a Creators Club membership, you can even play your games on the Xbox360. If you live in the US, UK and some other countries, you can even make money with your games by uploading your game to the Xbox Live service.

Check out [http://creators.xna.com](http://creators.xna.com)

There is a really great and helpful community building around XNA currently. 

A few days ago, XNA 3.1 has been released. With it you can use your XBox live Avatars (similar to Nintendo's Mii's) in your games. Pretty cool if you ask me.

A month ago, when I completely ditched Windows from my PC, letting go of XNA was the hardest part. It was the one thing which kept my Windows partition alive for a long time :-)

---

### Post by benj1 on 2009-06-12
[this]("http://openbookproject.net/thinkCSpy/index.xhtml") is a very good basic introduction to programming, it uses python, it also includes a few basic game examples, so may be good to start.

---

### Post by hessiess on 2009-06-12
> **benj1 said:**
> [this]("http://openbookproject.net/thinkCSpy/index.xhtml") is a very good basic introduction to programming, it uses python, it also includes a few basic game examples, so may be good to start.

Unless you are good at vector/matrix/quaternion mathematics I recommend that you start with simple 2D applications. Whatever you do don't use SDL directly, It is resolution dependent and lacks basic features like rotation, scaling and alpha blending. Sure these can be done with libs but you eather end up using OpenGL directly which is messy and complicated(IMO), or you end up depending on a huge number of other SDL extension libs.

For 2D development, use a 3D engine like Irrlicht, and forget about the `z' component (treat it as `layers'), Or Quad-Ren (basically Irrlicht for 2D).

---

### Post by HavocXphere on 2009-06-12
> **soltanis said:**
> the concepts of the standard library and all that jazz will only serve to frustrate the student.
90%+ of the examples out there are C++, especially if you start with more complicated stuff like BSP trees etc. Online resources (tutorials, forums etc) are thin for every other language & it makes it frustrating to learn the stuff since you are trying to code in Language X while all references are in C++/C. Been there, done that. Its no fun (even worse than pointers & mem management).

---

### Post by eilios on 2009-06-12
Definately python. It will teach him how to program, after he has learned how to navigate, pygame will be like teaching someone who knows how to walk to run. The only problem is learning basic game design, but once he knows the basics(arrays, classes) he can create a game easily. And if he knows pygame and wants to do something 3d, Panda3d is always an option.

---

### Post by jimi_hendrix on 2009-06-12
> **rizman said:**
> Might I suggest something different? (hopefully noone will hunt me down for suggesting this :-))

Try C# and XNA under...cough...Windows...cough. That is, if you have a Windows PC at your disposal.

No seriously. You said that you already know Java and C++. Then you will have no problem at all to start using C#. At least from a syntex point of view. 

XNA, in short, is a managed framework which is aimed at game development. Internally it uses DirectX, but provides a very easy to learn API and you can get your game prototyped pretty fast. If you buy a Creators Club membership, you can even play your games on the Xbox360. If you live in the US, UK and some other countries, you can even make money with your games by uploading your game to the Xbox Live service.

Check out [http://creators.xna.com](http://creators.xna.com)

There is a really great and helpful community building around XNA currently. 

A few days ago, XNA 3.1 has been released. With it you can use your XBox live Avatars (similar to Nintendo's Mii's) in your games. Pretty cool if you ask me.

A month ago, when I completely ditched Windows from my PC, letting go of XNA was the hardest part. It was the one thing which kept my Windows partition alive for a long time :-)

XNA is great too...in a weekend i made a mario clone (yes i did rip the images....i am not an artist)

---

### Post by eilios on 2009-06-12
> **jimi_hendrix said:**
> XNA is great too...in a weekend i made a mario clone (yes i did rip the images....i am not an artist)
The problem with XNA is it is extremely limiting, you can't make apps for anything except windows & xbox 360. A better alternative would be to learn c++ and a graphic engine like OGRE, and you could develop for all three systems without having to completely rewrite the game in another language.

---

### Post by NielsBhor on 2009-06-12
That was the point with XNA. Only for Windows and xbox 360. Its intention was exclusively designed for game development.

---

### Post by rizman on 2009-06-12
> **eilios said:**
> The problem with XNA is it is extremely limiting, you can't make apps for anything except windows & xbox 360. A better alternative would be to learn c++ and a graphic engine like OGRE, and you could develop for all three systems without having to completely rewrite the game in another language.

Considering that he wants to teach his student how to program games, I don't think cross-platform is an issue. C# is very easy to learn. You don't have to mess around with pointers, you have garbage collection so you don't need to care for memory allocation and freeing. IMHO it is much better suited to start game developement.

Indeed it is not possible to develop for Linux, but I tell you: it is great to see your game running on the 360. That I think is a great motivation for aspiring game developers

---

### Post by eilios on 2009-06-12
Rizman, telling people to use windows only programs on an ubuntu linux forum isn't really best for the community here. :P
 
While I will admit that is a good thing to see, if you really want to see things appear on a platform you could always program for something like the [pandora](www.openpandora.org) and then have him see his games show up on a handheld.
 
As for easy to learn, python + pygame is much easier to learn then c# IMHO, not to mention it is faster to program with, cross platform, and totally free to use. If he wants to use 3d, I also said Panda3d will allow him to do that while still using his language-of-choice.

---

### Post by soltanis on 2009-06-12
Cross-platform is completely irrelevant in this case; I don't think this student really cares where his games run, only that they run.

I still stand by python/pygame in this instance; C#, despite its simplifications, is still more difficult to learn than the very straightforward Python.

---

### Post by Flimm on 2009-06-12
What about game art? If he's an artist, he may not need to program much at all. If he's a blender artist, for example, he could make a new game from Yo Frankie! without touching much code.

---

### Post by kkkkdddd on 2009-06-12
Java :D

For GUI you have Swing and JavaFX and for 3D Java3D and jMonkeyEngine. You can also mix the code with other languages for JVM like Groovy, JRuby or Scala.

---

### Post by jimi_hendrix on 2009-06-13
> **eilios said:**
> Rizman, telling people to use windows only programs on an ubuntu linux forum isn't really best for the community here. :P
 
While I will admit that is a good thing to see, if you really want to see things appear on a platform you could always program for something like the [pandora]("http://www.openpandora.org") and then have him see his games show up on a handheld.
 
As for easy to learn, python + pygame is much easier to learn then c# IMHO, not to mention it is faster to program with, cross platform, and totally free to use. If he wants to use 3d, I also said Panda3d will allow him to do that while still using his language-of-choice.

> **soltanis said:**
> Cross-platform is completely irrelevant in this case; I don't think this student really cares where his games run, only that they run.

I still stand by python/pygame in this instance; C#, despite its simplifications, is still more difficult to learn than the very straightforward Python.

Well C# was my first language...I had no problem with it.

also, if he only runs windows and is just learning, he wont distribute anything anyway

---

### Post by tdrusk on 2009-06-14
Okay, on to the subject of Python and Pygame...

Now I feel it is unnecessary to teach him python 2. 6.2 since 3.0.1 is out and includes changes, but at the same time pygame is better supported in 2.6.2. What do you suggest I do?

---

### Post by Neon Lemmy Koopa on 2009-06-14
I would suggest 2.6.2 for a few reasons.

[LIST=1]
[*]It is still relatively well known and probably more used than 3
[*]The changes in Python 3 are said to be minor, though it isn't backwards compatible.
[*]As you said, PyGame supports 2.6.2 better
[*]Python 2 will probably still be around for a while after 3 is released
[*]Besides PyGame, other libs will be more compatible with 2
[/LIST]
That's my view on it.  That's why I chose to study 2 first and work my way onto 3.

---

### Post by tdrusk on 2009-06-14
> **Neon Lemmy Koopa said:**
> I would suggest 2.6.2 for a few reasons.

[LIST=1]
[*]It is still relatively well known and probably more used than 3
[*]The changes in Python 3 are said to be minor, though it isn't backwards compatible.
[*]As you said, PyGame supports 2.6.2 better
[*]Python 2 will probably still be around for a while after 3 is released
[*]Besides PyGame, other libs will be more compatible with 2
[/LIST]
That's my view on it.  That's why I chose to study 2 first and work my way onto 3.
Okay. That sounds swell then. I found some things easier in Python 3.01, but I don't want any flaws when trying to teach someone Pygame.

---

