---
title: "[C++] program ideas?"
date: 2008-10-18
forum: Programming Talk
---

### Post by StOoZ on 2008-10-18
Hi,
im looking for a program ideas , anyone can help me to get some ideas , for any kind of programs (except from games...)?

in the last couple of months , I already developed some app's , like mp3 file corrector (heavily used wxwidgets + TagLib...) , also a googles crawler (cURL was used here....) , im running out of ideas , im not looking for something special , just to write something , since I really like programming in C++ , but I have  nothing in mind right now...
:confused:

10x

---

### Post by nvteighen on 2008-10-18
A natural language parser capable of morpho-syntactic analysis. 

It should be able to catch all possible syntactic interpretations according to a lexicon (where each word is associated to its syntax) and some generative-transformational grammar rules given by the user using some convenient format. Of course, this means you should also code an editor for creating those databases.

:)

EDIT: Seriously, maybe you need a break; I don't know, why not learn a new programming language? (Lisp!!)

---

### Post by StOoZ on 2008-10-18
the NLP stuff is way above my understanding at the moment , but thanks anyway for the suggestion.

do you have anything else in mind?
:KS

---

### Post by nvteighen on 2008-10-18
> **StOoZ said:**
> the NLP stuff is way above my understanding at the moment , but thanks anyway for the suggestion.

do you have anything else in mind?
:KS
It's above mine too... :p And I really doubt you can do that in C++...

If you knew Scheme (a Lisp-dialect), I'd invite you to my project (see sig)...

---

### Post by StOoZ on 2008-10-18
Thanks,
Actually I tried to look at sourceforge , etc, but it didnt help.
im looking to start something of my own , from a scratch.
could be almost anything , a small app , large one , I just need to think about something :(

btw : interesting stuff u got there (ur sig)

---

### Post by nvteighen on 2008-10-18
Thanks! It's a popular Atlantic-coast South American card game... If interested, look at [http://en.wikipedia.org/wiki/Truco](http://en.wikipedia.org/wiki/Truco) and [http://www.pagat.com/put/truco.html](http://www.pagat.com/put/truco.html) I've found different projects (mainly in Java) of implementing this game, but I wanted to use something "different" and also use a completely different approach.

Another idea: have you ever coded GUIs in C++? If not, maybe it's time to learn Qt or GTK+...

---

### Post by StOoZ on 2008-10-18
yes , for GUI I always use wxwidgets , already written a project with it.

---

### Post by pmasiar on 2008-10-18
see wiki in my sig. Plenty of training tasks for beginner. You can solve them in any language; I always suggest Python as first language for beginner (see sticky for arguments pro and con) but do whatever you want 8-)

---

### Post by Flynn555 on 2008-10-18
.

---

### Post by snova on 2008-10-18
Write a kernel! That'll keep you busy for months. Or at least until you give up. :)

How about something graphics/CPU intensive? Like a fractal generator or a basic software rendering engine.

Design and implement an algorithm for simulating Conway's Game Of Life on as large a scale as you can.

Can't think of anything else right now... How about a quick little script to add vectors? (Could use one for physics about now!)

---

### Post by ihavenoname on 2008-10-18
why don't you try remaking tomboy in C++? As it stands now it's in C# you'll even have lots of "help" by looking at their code when you get lost. I was working on something like that and it taught me a lot about how these things work.

---

### Post by StOoZ on 2008-10-18
Kernel? with C++? usually its done with C.
and if I had the skills to do that , I would have already started , even if this task could take years of dev.

the reason I dont think about games , is , usually those require some knowledge of math , which now , I dont really have (I had , but im not in "shape" now...)
Im begining my BSc in Computer science next week , so then I might think about it.

---

### Post by StOoZ on 2008-10-18
> **ihavenoname said:**
> why don't you try remaking tomboy in C++? As it stands now it's in C# you'll even have lots of "help" by looking at their code when you get lost. I was working on something like that and it taught me a lot about how these things work.

hmmm , good idea!.
I might do that , will use WxWidgets for the GUI.

---

### Post by Can+~ on 2008-10-18
> **StOoZ said:**
> Kernel? with C++? usually its done with C.

If you write a kernel with C++, you'll get a letter directly from Linus Torvalds (and a new name for an ubuntu distro).

---

### Post by StOoZ on 2008-10-18
> **Can+~ said:**
> If you write a kernel with C++, you'll get a letter directly from Linus Torvalds (and a new name for an ubuntu distro).

do you imply that its not possible? ( a kernel with cpp )

---

### Post by snova on 2008-10-18
Eh, it takes a little bit (very little, actually, unless you want to use "fancy" stuff like exceptions and RTTI) of setup, but it's possible. I haven't had much opportunity to actually take advantage of it yet.

Oh, and Conways Game of Life isn't really a "game", but a simulation. The rules are really simple, it's doing it efficiently when there are thousands of cells in the simulator that's the tricky bit. So it's more of an algorithms exercise.

> **Can+~ said:**
> If you write a kernel with C++, you'll get a letter directly from Linus Torvalds (and a new name for an ubuntu distro).

Please explain. :confused:

---

### Post by Can+~ on 2008-10-18
> **StOoZ said:**
> do you imply that its not possible? ( a kernel with cpp )
> Please explain. :confused:
I wasn't being serious, it's just because some of the things Torvalds said (possible strong language):

Linus Torvalds on C++:
[http://thread.gmane.org/gmane.comp.version-control.git/57643/focus=57918](http://thread.gmane.org/gmane.comp.version-control.git/57643/focus=57918)

And he called the "Security Circus" a bunch of [Mastu****** Monkeys](http://news.cnet.com/Torvalds-attacks-IT-industry-security-circus/2100-1007_3-6243900.html), and then Wanki** Warluses. The Digg crowd joked around this names and called them "ubuntu codenames".

---

### Post by trekkie690 on 2008-10-18
do some form of Voice over IP application.
Or write a driver for a Wii, XBox, or PS3 controller to be used on Ubuntu
OR find some old device you use to play with and figure out how to interface it with your machine, and then get it to work on Ubunut

---

### Post by jimi_hendrix on 2008-10-18
CLI game? little to no math needed

---

### Post by jimi_hendrix on 2008-10-18
i have this same exact problem...ive hit a rock wall with my main goal: game programming because of M$ and lack of books that will teach openGL 

(basically M$ changes so much junk in their compiler and most other compilers wont compile DirectX /end rant)

now i try to find things to make that will help me with school (a quiz program or a quick emailer that will send attachments to my self...)

also gotten interested in a CLI OS...nothing GUI that would be to hard

---

### Post by nvteighen on 2008-10-19
> **snova said:**
> 
Can't think of anything else right now... How about a quick little script to add vectors? (Could use one for physics about now!)

There's GeoVectors (Python): [https://launchpad.net/gv](https://launchpad.net/gv) (I've contributed to them with some translations... it seems interesting).

> **jimi_hendrix said:**
> 
also gotten interested in a CLI OS...nothing GUI that would be to hard

That gives me an idea for you snova: why don't write a little command line shell? Give it some few basic features (mainly, program execution) and then add it whatever you like.

And btw, jimi_hendrix: if you design your program in a strict modular style, adding a GUI shouldn't be hard, as it would just be a way to call functions defined in a library.

---

### Post by jimi_hendrix on 2008-10-19
@nvteighen

ya but first i have to get a bootable OS to work and i cant find tutorials that dont involve floppy disks...but enough about this if you want to comment find my thread on the subject

@OP you might want to find your weakest area and try to do something to strenghten it

---

### Post by nvteighen on 2008-10-19
> **jimi_hendrix said:**
> @nvteighen

ya but first i have to get a bootable OS to work and i cant find tutorials that dont involve floppy disks...but enough about this if you want to comment find my thread on the subject


Yeah, I read about that. An interesting project (and I wish you good luck).

But I thought you were talking about GUIs in general and using your project as a particular example...

---

### Post by snova on 2008-10-19
> **nvteighen said:**
> There's GeoVectors (Python): [https://launchpad.net/gv](https://launchpad.net/gv) (I've contributed to them with some translations... it seems interesting).

Interesting... but probably more than I need in that it's 3D (and I already wrote something for my purposes).

> **nvteighen said:**
> That gives me an idea for you snova: why don't write a little command line shell? Give it some few basic features (mainly, program execution) and then add it whatever you like.

I once tried that. shell.py:

[PHP]
#!/usr/bin/python
import os, readline, rlcompleter, socket, sys
readline.parse_and_bind( 'tab: complete' )
def prompt():
   # PYSHELL: has to be prepended because otherwise I can't tell whether I'm
   # still running Bash!
   return 'PYSHELL: ' + os.getenv( 'USER' ) + '@' + socket.gethostname() + \
          ':' + os.getcwd().replace( os.getenv( 'HOME' ), '~' ) + '$ '
l = {}
try:
   while True:
      line = raw_input( prompt() )
      try:
         exec line in l
      except:
         os.system( line )
except EOFError:
   print
[/PHP]

That actually sounds fun. Fish looks like something I could learn from (based on the little I know, they got rid of several quirks that shells have had for ages).

> **nvteighen said:**
> And btw, jimi_hendrix: if you design your program in a strict modular style, adding a GUI shouldn't be hard, as it would just be a way to call functions defined in a library.

The trick is trying to separate the kernel from the GUI code- where do you draw the line between kernel level graphics card interfaces and user level GUI code? If anybody can come up with a suitable way to do that, I'd love to hear it.

---

### Post by nvteighen on 2008-10-19
> **snova said:**
> Interesting... but probably more than I need in that it's 3D (and I already wrote something for my purposes).

Er... if you have vector A defined as (7, 8, 0) and vector B as (3, 4, 0), you're in 2D as both vectors share the same plane.

But glad to hear you've used your skills for something useful for you! That's great! (Actually, a natural language parser would be what I need for my studies... :p)

> I once tried that. shell.py:

...

Funny... but that's just a Bash-wrapper in Python. No, I mean a completely new shell, with its own scripting language, etc. I've been thinking these days how I'd do that...

> The trick is trying to separate the kernel from the GUI code- where do you draw the line between kernel level graphics card interfaces and user level GUI code? If anybody can come up with a suitable way to do that, I'd love to hear it.

Good question...

---

### Post by snova on 2008-10-19
Actually, anything that does more than derive the components of two vectors defined in terms of angle and magnitude, add them together, and then compute the angle and magnitude of the third vector, is more than I need right now.

> **nvteighen said:**
> But glad to hear you've used your skills for something useful for you! That's great! (Actually, a natural language parser would be what I need for my studies... :p)

Does source code count as "showing your work", I wonder. :)

> **nvteighen said:**
> Funny... but that's just a Bash-wrapper in Python. No, I mean a completely new shell, with its own scripting language, etc. I've been thinking these days how I'd do that...

I was trying to preserve the Python-ness while still being able to run normal commands. Mostly I was just tired of weird shell syntax. Like, what is the difference between [, [[, (, and (( in an if statement? I still don't know.

Besides, it was never more than an experiment (~/Projects/Experiments) to see how it would go. Might enjoy writing a shell anyway, though. ONE THAT MAKES SENSE.

---

### Post by jimi_hendrix on 2008-10-19
> **snova said:**
> Might enjoy writing a shell anyway, though. ONE THAT MAKES SENSE.

on my infinite list of things to do

i wish i could win the lottery and just knock some things off of my "list"

---

### Post by nvteighen on 2008-10-20
> **snova said:**
> 
I was trying to preserve the Python-ness while still being able to run normal commands. Mostly I was just tired of weird shell syntax. Like, what is the difference between [, [[, (, and (( in an if statement? I still don't know.

Besides, it was never more than an experiment (~/Projects/Experiments) to see how it would go. Might enjoy writing a shell anyway, though. ONE THAT MAKES SENSE.

Well, I really don't actually know what that weird syntax rules mean for if's in bash... (and sh?). It's one of the things that's preventing me to learn shell scripting (though I know I'll have to face that one day...). Yeah, I may sound a bit superficial here, but for some reason, I feel those languages are a bit messy... (if I'm wrong, please tell me!... I mean it honestly!).

EDIT: If you make a shell that makes sense ("Shense", "Shell-sense"?), please tell us!

---

### Post by snova on 2008-10-20
I think all the different variants of "test" are there because of a long and complicated shell family tree. Csh might have added one or two of them. Arrays are from Ksh (I think?), which had indexes starting from 1- Zsh lets you start at 0 instead.

Fish might be worth looking into for inspiration. They've cleaned up a lot of that. Naturally it isn't compatible at all, but who cares? I'm going to install it. I may even keep it as a replacement for Zsh (unlikely...).

Whoa... it's better than *Zsh* in some regards.

---

### Post by StOoZ on 2008-10-26
Ok , news news.... eventually I decided to go with this (mentioned here...)
[http://en.wikipedia.org/wiki/Conways_Game_of_Life]("http://en.wikipedia.org/wiki/Conways_Game_of_Life")

up to now , its going pretty good , I already finished most of the main algorithm , and it works pretty good , seen on console , with 9 = dead , 1 = alive :popcorn:
will create a GUI for that , in wxwidgets. :guitar:

---

