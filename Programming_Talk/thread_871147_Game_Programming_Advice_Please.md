---
title: "Game Programming Advice Please"
date: 2008-07-26
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-07-26
hi

i want to start making small games that i can do as a hobby in my spare time.

i have a small amount of programming experience (i can do basic object oriented programming in C# and can say "hello world" in c/c++, assembler (kinda), python, and java)

what would be the best language for me to start learning to program games in?

i realize the best way to learn is to buy some books but i needed to be pointed in the right direction 

thanks in advance

---

### Post by slavik on 2008-07-26
any language with OpenGL bindings :)

---

### Post by Wybiral on 2008-07-26
> **slavik said:**
> any language with OpenGL bindings :)

Well, you can do OpenGL in assembly... But I wouldn't recommend it. In fact, since I'm assuming the OP wants 2d games, I would probably stay away from OpenGL for now. I'd say any high level language with a good SDL binding would be a good start. Since you already know Python, why not try [PyGame]("http://www.pygame.org")?

---

### Post by Lster on 2008-07-26
You might want to look at SDL, OpenGL and OpenAL... and possibly some "ready made" game engines. A good website for game development of all types is GameDev:

[http://www.gamedev.net/](http://www.gamedev.net/)

---

### Post by jimi_hendrix on 2008-07-26
> **Wybiral said:**
> Well, you can do OpenGL in assembly... But I wouldn't recommend it. In fact, since I'm assuming the OP wants 2d games, I would probably stay away from OpenGL for now. I'd say any high level language with a good SDL binding would be a good start. Since you already know Python, why not try [PyGame]("http://www.pygame.org")?

well i wouldnt't say i "know" python but it looks relativly simple compared to c/c++/c#

also whats an open GL and SDL binding(im still not that advanced yet to know all this :))?

---

### Post by jimi_hendrix on 2008-07-26
also is there a python ide i can get or do i have to use notepad

---

### Post by ceclauson on 2008-07-26
A basic python IDE is IDLE.  You can get it as a package for ubuntu, its name is just idle.  I don't know of any other more advanced IDE's, but another poster might.

If you're interested in going the C/C++ route, I found [these]("http://lazyfoo.net/SDL_tutorials/index.php") tutorials to be helpful.

---

### Post by samjh on 2008-07-26
> **jimi_hendrix said:**
> well i wouldnt't say i "know" python but it looks relativly simple compared to c/c++/c#

also whats an open GL and SDL binding(im still not that advanced yet to know all this :))?

OpenGL is a low-level graphics library, best known for its use in 3D.  It is used on multiple platforms.

SDL is a cross-platform library for common gaming functions, like graphics, sound, input devices, etc.  It's a bit like DirectX on Windows, but not as comprehensive.

---

### Post by jimi_hendrix on 2008-07-26
ok ill give all of this stuff a look and reply if i have any other questions btw nice picture samjh

---

### Post by jimi_hendrix on 2008-07-26
can u post a link to IDLE i cant find it via google

---

### Post by Kadrus on 2008-07-26
I suggest learning more Python and then jump into Pygame,you'll find it nice and easy.
There are a lot of resources on C++ game programming and Java if you are interested,have a look at them.But since it's your spare time I do sugest Pygame
[PyGame]("http://pygame.org") : The Website
[PyWeek]("http://www.pyweek.org/"): Python Game programming Challenge

---

### Post by jimi_hendrix on 2008-07-26
i was planning to but im at the state were i need an IDE to compile the code or do some complicated thing with a path or something like that that i have no idea how to do and dont want to mess up my computer

---

### Post by ceclauson on 2008-07-26
Here's a link that describes the usage of idle on python.org:
[http://www.python.org/idle/doc/idlemain.html](http://www.python.org/idle/doc/idlemain.html)

If you're using Ubuntu, you can get idle by typing "sudo apt-get install idle" at the command prompt, or going to System > Administration > Synaptic Package Manager and searching for idle.

After it's installed, you can find it under the Applicatons > Programming menu.

---

### Post by jimi_hendrix on 2008-07-26
> **ceclauson said:**
> Here's a link that describes the usage of idle on python.org:
[http://www.python.org/idle/doc/idlemain.html](http://www.python.org/idle/doc/idlemain.html)

If you're using Ubuntu, you can get idle by typing "sudo apt-get install idle" at the command prompt, or going to System > Administration > Synaptic Package Manager and searching for idle.

After it's installed, you can find it under the Applicatons > Programming menu.

when i click on that link i go to the page i then go to the download link and then i get this weird directory thing what do i do from there...even though i am dual booting ubuntu so the sudo apt-get would be easier i have all of my programming stuff on my windows side so i need to download it the hard way (i prefer terminal :))

EDIT: acually ill just start a new thread on that...thanks all

---

### Post by ceclauson on 2008-07-26
If you downloaded Python for windows, or at least did it the same way I did, you should already have it. On my system it's under Lib\idlelib\idle.py.

Because it's a Python program, you'll need to run it with the Python interpreter.  I just have a batch file in my Python folder called "runidle.bat" with the following contents:

```

python Lib\idlelib\idle.py

```

If I double click on it, it'll run idle for me.

---

### Post by jimi_hendrix on 2008-07-26
not working but thats ok...i alrdy did that other thread for IDE's

---

### Post by nanotube on 2008-07-27
i'd say go with geany instead of idle (in the repos, package 'geany')

---

### Post by jimi_hendrix on 2008-07-27
the only thing is when i type code in geany all of the compile buttons are grayed out

---

### Post by henchman on 2008-07-28
Iam sure if you look for [python IDLE]("http://www.google.de/search?hl=de&client=firefox-a&rls=org.mozilla%3Ade%3Aofficial&hs=3SO&q=python+IDLE+&btnG=Suche&meta=") you will find your information :)

---

### Post by samjh on 2008-07-28
> **jimi_hendrix said:**
> the only thing is when i type code in geany all of the compile buttons are grayed out

You don't need Geany, IDLE, or any other fancy IDE/editor for Python programming.

You can simply use Gedit (if using Ubuntu or any Gnome desktop) or Kate (if using Kubuntu or any KDE desktop) to write the code.  Then you can just run your program by issuing this command in the program file's directory:
```
python yourfile.py
```
To make your file executable, simply do:
```
chmod +x yourfile.py
```...then you can run it by:
```
./yourfile.py
```

Try not to be too reliant on editors or IDEs.  Once you learn to use Python or any programming language from the command-line, learning editors or IDEs become a whole lot easier than if you start out by relying on IDEs. :)

---

### Post by jimi_hendrix on 2008-07-28
ok thanks all

---

