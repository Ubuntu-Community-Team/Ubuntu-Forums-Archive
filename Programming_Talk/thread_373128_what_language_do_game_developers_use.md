---
title: "what language do game developers use?"
date: 2007-02-28
forum: Programming Talk
---

### Post by billdotson on 2007-02-28
What programming language do videogame developers use?  C++?

---

### Post by joflow on 2007-02-28
a game can be written in just about any language.  Most professional studios use C++..I believe for performance.  Alot of games use more then one language...for instance C++ for the game engine and python or some similar scripting engine for script game events.

---

### Post by Praill on 2007-02-28
Usually for large projects, yes.
Smaller browser games are written in java or flash.
Even some large scale games have been written in flash actually ([http://www.dofus.com]("http://www.dofus.com"))

It all depends. But usually its C++.

---

### Post by Wybiral on 2007-02-28
Quake was written in C.

Believe it or not, C is actually faster than C++ because it looses some of its overhead.

But, most 3d games are written in C++ because it's easier (object oriented languages make game development much simpler)

But... 2d games, it does matter. Most languages run fast enough for simple 2d games so why waste your time in C/C++ if you can whip it up quickly in python/perl/php/BASIC???

---

### Post by billdotson on 2007-02-28
could games be written in python??  

If I wanted to write  couple simple games how long do you think it would take me to learn enough C++ (or Java, Flash) to be able to do it?

I am talking about at first just a simple game but maybe even a 30 minute long side-scroller type game.

Also, if games could be written in Python why aren't there any?  Python seems very simplistic compared to C++.  The hello world for python is one line where C++ is 6-7 lines

---

### Post by Wybiral on 2007-02-28
There have been a few games written in python. I think games haven't been written in it because the modules are fairly new.

I suggest pygame or OpenGL+GLUT (there are python modules for these)

Or... You can always check out my OpenGL module, viper: [http://p13.wikispaces.com/viper](http://p13.wikispaces.com/viper) (I ported some NeHe tutorials and some examples of my own that you might be able to learn from as well)

But, I strongly recommend you learn some OpenGL if you plan to get into game development.

As far as learning C/C++ for gamedev... How much math do you know? Physics? Vector/matrix math? Do you have a semi-decent understanding of programming logic?

Btw, feel free to PM me about ubuntu gamedev if you need help. I want to contribute because I know a lot about game development and I'd like to see more ubuntu-friendly games out there.

---

### Post by joflow on 2007-02-28
> **billdotson said:**
> could games be written in python??  

If I wanted to write  couple simple games how long do you think it would take me to learn enough C++ (or Java, Flash) to be able to do it?

I am talking about at first just a simple game but maybe even a 30 minute long side-scroller type game.

Also, if games could be written in Python why aren't there any?  Python seems very simplistic compared to C++.  The hello world for python is one line where C++ is 6-7 lines

python is an interpreted scripting language...the code isn't complied and so its slow in comparison to something like c++.  Thats why it isn't used for big game projects.  For a small project...its fine.

---

### Post by billdotson on 2007-02-28
I just started reading "How to Think Like a Computer Scientist" the Python version which ia a PDF book off of greenteapress.com 2 days ago so I am VERY new to programming.  In Python I have built my first couple of converter programs.  Here is the code for them:

```
 import math
print "What is the temperature in Fahrenheit?" 
temp = input()
C = ( temp - 32 ) * (5 / 9)

print "So the temperature in Fahrenheit =" , temp 

print "To find the degrees in Celsius we take the value of the the degrees in Fahrenheit, minus 32 from that value and then multiply  that value by 5/9."  

print "The product of that series of operations gives us the temperature in Celsius." 

print "The temperature" , temp,  "in Celcius is" , C , "degrees."  

print "So, the equation to convert degrees in Fahrenheit to degrees in Celcius is Degrees in Celsius = (Degrees in Fahrenheit - 32) * (5/9)" 
```

that is my program to convert Fahrenheit to Celsius, and here is my program to tell you the circumference of a circle given the radius :

```
 import math
print "What is the radius?" 
radius = input()
circle = radius * radius * math.pi 

print "So the radius of the circle =" , radius 

print "To find the circumference of the circle we first take the value of the radius and sqaure that value.  Then we take the value of the radius sqaured and multiply that value by the value of pi which is approximately 3.14"  

print "The product of that series of operations gives us the circumference of a circle." 

print "The circumference of a circle with a radius of" , radius , " is" , circle , "units."  

print "So, the equation for the circumference of a circle is circumference = (radius*radius)*pi" 
```

As you can see I am clearly a beginner.

---

### Post by runningwithscissors on 2007-03-01
id software's games are written in C.

---

### Post by slavik on 2007-03-01
python is not as interpreted as you think, python/perl/php are actually as 'compiled' as java, except the interpreter does not give you the compiled version, whereas java compiler does ...

---

### Post by Enselic on 2007-03-01
> **Wybiral said:**
> 
Believe it or not, C is actually faster than C++ because it looses some of its overhead.


If you don't use C++ features like virtual methods, then no. And the performance loss is absolutely nothing to care about on todays desktop computers.

> **runningwithscissors said:**
> id software's games are written in C.

Not the newer ones.

---

### Post by pmasiar on 2007-03-01
> **billdotson said:**
> What programming language do videogame developers use?  C++?

All sorts of languages are used. Most use statically typed compiled language for speed: C, C++. Runescape is in Java. First ColossalCave RPG was in Fortran. Some games now are written in Python - it is easy to profile it, find the bottlenecks, and rewrite only those in C. Patterns used: "speed is not the problem until it is a problem" "premature optimization is root of all evil" and "to optimize, do not guess: measure". Python games I found for another questions couple days ago: galcon (multiuser galactic conquest, warning: fast paced and addictive), eve-online (MMORPG in space, top: 32K users in 1 world). Pygames is popular game library.

If you want to start programming by writing games, take a look at [http://en.wikipedia.org/wiki/Game_maker](http://en.wikipedia.org/wiki/Game_maker) - extremely intuitive GUI for writing games and games only - 10 years old can do it and have fun. In most cases, no code needs to be written - all you need is to assmble objects from palette and manipulate them. Free as beer, really easy and  fun, but Windows only.

---

### Post by pmasiar on 2007-03-01
> **slavik said:**
> python is not as interpreted as you think, python/perl/php are actually as 'compiled' as java, except the interpreter does not give you the compiled version, whereas java compiler does ...

yes and no: Python does compile the code and saves it as .pyc - you can even distribute .pyc files instead of .py. Python by default compiles into architecture-independent bytecode which is interpreted (and multiple compilers into native code is available if you want them), while Java's bytecode is compiled into native code before execution.

Perl does not save compiled version at all (discards it after executing), PHP - I am not sure if it does.

The main difference between Python and Java is that they are compiled differently: Python uses dynamic "duck" typing (delaying check for type info to runtime) while java check most of typing issues at compile time (forcing programmer to be very strict with types).

---

### Post by slavik on 2007-03-01
> **pmasiar said:**
> yes and no: Python does compile the code and saves it as .pyc - you can even distribute .pyc files instead of .py. Python by default compiles into architecture-independent bytecode which is interpreted (and multiple compilers into native code is available if you want them), while Java's bytecode is compiled into native code before execution.

Perl does not save compiled version at all (discards it after executing), PHP - I am not sure if it does.

The main difference between Python and Java is that they are compiled differently: Python uses dynamic "duck" typing (delaying check for type info to runtime) while java check most of typing issues at compile time (forcing programmer to be very strict with types).
Umm, not ALL Java code is JIT compiled :) even so this is a very recent 'happening' as for PHP, I expect the PHP interpreter to act the same as the Perl interpreter because of PHP's origins (directly from Perl) ...

---

### Post by gga73 on 2007-03-01
> **billdotson said:**
> What programming language do videogame developers use?  C++?

For today's 3d games, you will find more or less the following to be true:

- C++                                                        99%
- Propietary scripting language           60%
- Lua                                                          30%
- Python                                                    5%
- Others                                                     5%

However, for other types of games that do not need to be so cpu intensive (solitaires, simple 2d games, etc), you will find that almost any scripting language is suitable.    Frozen Bubble (Perl) or pysol (Python) are good examples.

Lua in general is pretty popular as a scripting language in the professional game community because it is very fast and it is also the only one of the popular scripting languages that is truly multi-thread safe currently (Python, Perl, Ruby are not, for example).

Games written to be played on the browser often are Flash or Shockwave based, as those plugins are often very lite and available across most platforms and browsers.

As with all things with technology, expect the above to change drastically in the upcoming years.

---

### Post by hod139 on 2007-03-01
> **gga73 said:**
> For today's 3d games, you will find more or less the following to be true:

- C++                                                        99%
- Propietary scripting language           60%
- Lua                                                          30%
- Python                                                    5%
- Others                                                     5%

But this list only covers 199%! In other news, 86.2% of all statistics are made up on the spot.

---

