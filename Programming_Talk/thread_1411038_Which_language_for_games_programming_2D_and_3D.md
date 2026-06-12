---
title: "Which language for games programming? 2D and 3D"
date: 2010-02-19
forum: Programming Talk
---

### Post by Richard1979 on 2010-02-19
I'm interested in learning how to write games and I've read through the excellent free Python book you can get about starting to use PyGame ( [http://inventwithpython.com/](http://inventwithpython.com/) ).

Is PyGame good enough for creating a decent platform game with full sound etc?
I'm thinking along the lines of great games like Mickey Mouse: Castle of Illusion, Plants vs Zombies and others like Cannon Fodder.

I'm also interested in creating a game with very high res textures and full 3D effects like HDR a few years down the line.
I've looked at engines such as Ogre and the now-GPL Quake 3 and they look good although the Quake 3 one really shows it's age now.

Which languages would you recommend for 2D or 3D games programming?
Do you think it's possible to create something good with Python or is it just not fast enough?
I am learning C and C++, it's looking more and more like C++ is the way to go but I'm interested if anyone has experience using Python and how fast it is.

---

### Post by chiisu on 2010-02-19
I've finally moved from C to C++, so that's what I'm used to.  I'm not familiar with Python, but supposedly you can add in some C/C++ code for certain parts for performance reasons, so maybe a hybrid approach is one possibility?

---

### Post by donkyhotay on 2010-02-19
Python and pygame can do well creating games. I don't know about the other games you mentioned but there are a few [tower defense games on the pygame webpage](http://www.pygame.org/tags/towerdefense) similar to plants vs zombies. I think python/pygame are great for learning how to code and getting started on building your first game. While you might eventually want to move to something a little more powerful/faster like C++, python does just about everything I currently want to do when coding. It's what I use on my current project which is a FOSS remake of [Moonbase Commander](http://en.wikipedia.org/wiki/Moonbase_Commander) called [MoonPy](http://code.google.com/p/tether). MoonPy has in-game music, sound effects, and 2D graphics, without needing to go the hybrid approach mentioned above (which does exist). I theoretically *could* have done 3D instead but I'm not that good of a programmer and 3D is unnecessary given the type of game it is. If you really want to know what python/pygame can do check out the games on [pygame website](www.pygame.org) and compare that to what you have planned.

---

### Post by love to learn on 2010-02-19
Now that was a real informative post there chiisu;)

I started out and still use SDL which is a pretty decent api for anything required to write games,including support for joysticks and things.
Pygame is just a wrapper around SDL so yes  if you are comfortable with python then thats the place to start.
Move on to the rest later.

---

### Post by munky99999 on 2010-02-19
Well your typical 2d game can pretty much be coded in anything. So long as it is coded competently. 

Your typical 3d game can be c, c++, or java. Though thats more for the performance core. It's common to use python or lua for the non-performance parts for easier programming and modability.

on top of that.. it depends on where you intend to put it.

web browser games like runscape are often java or flash. The future though will have browser games coded in html5

[http://freeciv.net/](http://freeciv.net/)

homebrew handheld games because of limited resources and high expectations will pretty much guarantee 100% c/c++

console stuff generally isnt an option they force devs to pay to be eligible. Though im told c# is the only option for xbox360.

---

### Post by d3v1150m471c on 2010-02-19
Python can write just about anything but the problem you run into with large programs like games is python's lack of speed compared to c languages. Python isn't fully compiled and requires more translation from the machine. This could cause no difference or a large one depending on the code in your program.

---

### Post by xander98989 on 2010-02-19
To dabble you should try [Blender]("http://www.blender.org"). It's a fun and easy way to make 3d games that allows you to concentrate on the modelling and do most of what you need (controls, physics) with menus and Python scripts. For a serious project (your own 3d engine) you need C++ with OpenGL.

---

### Post by love to learn on 2010-02-20
Richard, you are just going to get more confused here.
Stick to pygame using python for starters.
Once you are comfortable there,you can bump it up to SDL written in c.
You will never learn to swim if you jump into the deep end without water wings ;)
 And btw the 'mame' 'multiple arcade machine emulator' uses SDL as a backend for  sound and graphics,so theres absolutely no problems with it.(as for speed its lightning fast. Mame is emulating a gazillion processors and other components WHILE it is showing graphics and sound.)
And its sooooo easy to learn.

---

### Post by munky99999 on 2010-02-20
[http://en.wikipedia.org/wiki/Irrlicht_Engine](http://en.wikipedia.org/wiki/Irrlicht_Engine)

probably best open source engine atm.

[http://www.jenkinssoftware.com/raknet/index.html](http://www.jenkinssoftware.com/raknet/index.html)

raknet probably the best network engine.

---

### Post by Sslaxx on 2010-02-21
Well, [OGRE]("http://www.ogre3d.org/") has [bindings for Python]("http://www.pythonogre.com/") [and C#/.NET/Mono]("http://www.ogre3d.org/addonforums/viewforum.php?f=8"), so that might be worth a try?

---

