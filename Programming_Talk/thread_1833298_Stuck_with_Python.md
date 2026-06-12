---
title: "Stuck with Python"
date: 2011-08-25
forum: Programming Talk
---

### Post by Neoncamouflage on 2011-08-25
A couple weeks ago I started looking into Python as my first language, and like everyone said, it was very easy to pick up. I read through probably a dozen beginner/tutorial books and now I'm not sure where to go. I look at advanced Python code and specialized books but have no clue what a lot of it is, but I pick up a general book or one with tutorials and such and I've already covered the contents several times over. It's like I'm stuck in between "newbie" and "advanced" but can't find anything to carry me forward. 

Any suggestions?

---

### Post by cgroza on 2011-08-25
You don't really master a language until you start a project with it.
Any project will teach you a lot because that will make you look and think for solutions, ways to apply and implement them.

---

### Post by Smart Viking on 2011-08-25
> **cgroza said:**
> You don't really master a language until you start a project with it.
Any project will teach you a lot because that will make you look and think for solutions, ways to apply and implement them.
Absolutely agreed.

Three suggestions for projects:
[B]
Easy[/B]: Create an alarm clock, that will play a sound file at a given time.
[B]
Medium[/B]: Create an alarm clock with Pygame, where it shows what the current system time is like a digital alarm clock would, and other stuff.
[B]
Hard[/B]: Create an alarm clock with a GUI toolkit like GTK+, where it shows the current system time, and other important stuff. You should also be able to change the alarm music, change the time when the alarm clock rings, and have a menubar with attached keyboard shortcuts, and anything else you feel should be there.

That's how you learn stuff! That way you have to continuously search the web for documentation on modules(or "libraries") you're using, and when you get to know a module well, then you can make really powerful stuff in a short amount of time!

After a while, you will also get much better at locating information on the web quickly.

---

### Post by F.G. on 2011-08-25
hey, so what i found really helpful were the google developer talks on python, here's a link to the first one:
[http://www.youtube.com/watch?v=tKTZoB2Vjuk](http://www.youtube.com/watch?v=tKTZoB2Vjuk)
i also did some of the python challenges at: [www.pythonchallenge.com](www.pythonchallenge.com)
i quite enjoyed these, though they can be a bit too cryptic.
i've been using pyqt4 to write a GUI and its pretty good.

---

### Post by GenBattle on 2011-08-26
Another option for programming challenges is [Project Euler]("http://projecteuler.net/").

I definitely agree with others, you need to find a problem, and solve it. I always find things like file parsing or web scraping to be good straightforward exercises for learning new languages.

---

### Post by ofnuts on 2011-08-26
> **GenBattle said:**
> Another option for programming challenges is [Project Euler]("http://projecteuler.net/").

I definitely agree with others, you need to find a problem, and solve it. I always find things like file parsing or web scraping to be good straightforward exercises for learning new languages.Isn't it just a matter of taking your regexps from Language N-1 and slapping them in some Language N glue?

---

### Post by juancarlospaco on 2011-08-26
Python, get Bottle, use HTML5.

---

### Post by cgroza on 2011-08-26
> **juancarlospaco said:**
> Python, get Bottle, use HTML5.
Are you the creator of Bottle?

---

### Post by Senesence on 2011-08-27
> **cgroza said:**
> You don't really master a language until you start a project with it.

You don't really master a language until you start a couple of projects with it, and manage to finish a few of them.

In either case, to truly "master" something takes years. For a discipline as inherently complex as programming, I would say that the baseline is close to a decade or so.

.... Although, I guess this all depends on your definition of "master" - some people think that knowing the syntax is knowing the language, or, more generally, knowing to program.

---

### Post by mandza on 2011-08-27
is it posible to compile python programs and can python listen ports???

---

### Post by cgroza on 2011-08-27
> **mandza said:**
> is it posible to compile python programs and can python listen ports???
You can't "compile" them like in C or C++, but you can use cxfreeze and py2exe to achieve something similar.
Yes, python can do that.

---

### Post by HarrisonNapper on 2011-08-29
> **mandza said:**
> is it posible to compile python programs and can python listen ports???

Note py2exe above for making your program for Windows users. Not only can python listen on ports, there are a number of web server applications developed exclusively in Python or that use primarily Python. If you are thinking about doing web development, Django and web2py (formerly gluon) are both great frameworks to start with.

The main drawback I've run into with Python is handling some streaming data, but that's nothing a mixing a little C/++ code in can't handle. And by a little, I mean a lot. Python will pamper you :)

---

### Post by juancarlospaco on 2011-08-29
> **cgroza said:**
> Are you the creator of Bottle?

nope (¬&#8255;¬)

---

### Post by Neoncamouflage on 2011-08-31
Alright, I decided to try the alarm clock thing, and quickly hit a problem. I can read files just fine, but only text. I can't for the life of me figure out how to *play* an MP3 for an alarm. All Google searching and asking in IRC has resulted in confusion and no help. Anybody here have a simple way of doing so?

---

### Post by Smart Viking on 2011-08-31
Now you've come to the part were you're locating information. That is the hardest part really, but believe me it's much easier eventually.

After 5 minutes of searching the web, I found a module to do the job, called "snacks". 5 months ago, I would probably use like 2 days before a tune would search its way through the speakers.

You can install it through the package manager. Make use of "apt-cache search" if you can't find it.

Import it with "import tkSnack".

Go to their website for information about how to use it, find out what file formats it supports etc.

Good luck! :popcorn:

EDIT:
Some thoughts to take with you.
Programming is HARD to learn. But it is easy to know. At times it will feel endless and impossible. Sometimes you may take a little break with programming, and return, and find out how to do stuff you previously had problems with. Some stuff will feel impossible, but after some time, believe it or not, you will have a breaking point and start to understand it.
You need to be interrested to learn anything, it must be on your own accord. If you're just sick of it all and wanna go skiing or somthing, do it, go skiing. Probably you will find out later that "man, i feel like programming today" and there you are. You don't have to "fear" that you wont get any good, as long as you're doing stuff, and reading a little here and there, you will learn stuff even thought it doesn't feel like it. 

Programming is best done with huge curiosity and a cup of coffee. 

The more you learn, the more interresting it becomes.

I hope this gave some inspiration :)

---

### Post by HarrisonNapper on 2011-08-31
The above edit is very true. I can't count the number of times I've struggled with something for hours, taken a nap or gone to do something else, and not only did the answer hit me unexpectedly, more often than not, it was a more efficient or more versatile solution than the one I had been working on in the first place. Sometimes that's kind of disheartening, as it feels like the initial struggle was "wasted" time, but it's a part of the process of improving one's ability to think about problems (notice the difference between that and "program" or "write code").

As for the sound, I have worked with pygame before and it has a very simple way of handling that as well as other things, but it's a good idea to have a feel for objects and event-loops before diving in to that. If you're stuck with playing the sound, you can always make the application do something else instead like print "PLAY A SOUND HERE" to the terminal and then go back to it. Doing that will let you tackle the problems you can tackle easily early, so the learning builds on itself, but it also helps you start writing your code in a more modular fashion.

Another piece of advice from one n00b to another: program how you think and concentrate on how to improve the thinking (the code follows) :)

---

### Post by Neoncamouflage on 2011-08-31
Not at all sure if you would be able to help, but I went ahead and got tkSnack, looks awesome and like just what I need. However, when trying to run it in any way, I get this:

```
Unable to open mixer /dev/mixer
Traceback (most recent call last):
  File "/home/chris/bin/python_scripts/PyTest2", line 9, in <module>
    sound.play()
  File "/usr/lib/pymodules/python2.6/tkSnack.py", line 274, in play
    self.tk.call((self.name, 'play') + self._options(kw))
_tkinter.TclError: Could not gain access to /dev/sound/dsp for writing.
```

Any idea what its problem is? I tried making a symbolic link between my sound directory and /dev/sound/dsp like one site said, but that did nothing.

EDIT:
Alright, in the end I just used pygame for the sound. Took about an hour of looking at examples and talking to one particularly helpful person in IRC but it's good now. Wish I'd thought of it to begin with, saved so much time.

---

