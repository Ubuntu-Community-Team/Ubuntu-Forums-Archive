---
title: "Which language for this?"
date: 2010-04-21
forum: Programming Talk
---

### Post by HalfEmptyHero on 2010-04-21
I know this question has been asked a lot, but people always say it depends on what you want to do with it. Well I know what I want to do with it: I want to write a word processor for writers, like Scrivener for Mac. I have tried many of these on linux, but none of them fit my needs. So the question I have is: what language should I use to write it.

The only program I know anything about is python, but my knowledge of it is quite minuscule. However, I need a hobby, so might as well learn programming. I use gnome, so the program would be in gtk, but other than that I have no requirements. Now, in all honesty, I will probably never write this program, or even fully learn a programming language, but whatever. Better to have a goal I guess.

---

### Post by NovaAesa on 2010-04-21
I think python w/ gtk should be a fairly good choice for this kind of thing. It's a bonus that you already know some of it.

---

### Post by trent.josephsen on 2010-04-21
> **HalfEmptyHero said:**
> I know this question has been asked a lot, but people always say it depends on what you want to do with it. Well I know what I want to do with it: I want to write a word processor for writers, like Scrivener for Mac. I have tried many of these on linux, but none of them fit my needs. So the question I have is: what language should I use to write it.

The only program I know anything about is python, but my knowledge of it is quite minuscule. However, I need a hobby, so might as well learn programming. I use gnome, so the program would be in gtk, but other than that I have no requirements. Now, in all honesty, I will probably never write this program, or even fully learn a programming language, but whatever. Better to have a goal I guess.

Better to have no goal at all than one that will never be achieved, or one that is too distant to be clearly seen.

You need more than a miniscule knowledge of Python to even know where to begin.  Learn more Python.  Learn *lots* more Python.  Get a copy of *Programming Python* and read the entire thing.  Familiarize yourself with the most common standard library modules and learn how Python programmers do things.  Write some PyGtk stuff while you're at it, and learn how to interact with the Gtk+ libraries.  When you're 100% confident with Python and feel like it has nothing more to teach you, then move on to something more challenging; I usually recommend C, which works because you want to use Gtk+.

But Python and C alone won't give you the competence necessary to see this sort of thing through.  Learn Perl at least (which has immense practical use), Lisp, and possibly Java (others will have different recommendations).  Also, I would recommend picking up a copy of Knuth, which uses a hypothetical assembly language and will teach you yet more.

Get a job in a software shop and take classes if they are available.  Learn about the tools used in your workplace and get a feel for how well they work and what they are useful for.  No amount of class time or self study can compensate for lack of real life experience.

You'll know when you are ready to start working on your project because you won't need other people's help knowing where to begin ;).  But don't hold your breath and Google "Teach Yourself Programming in Ten Years" for a better idea.

---

### Post by HalfEmptyHero on 2010-04-21
The only thing I wonder about python is if a complex gui can be put today from it. Most of the pygtk programs I have seen have had relatively simple interfaces. Would I be able to do things such as split screen text editing and stuff like that in pygtk?

---

### Post by Bachstelze on 2010-04-21
> **HalfEmptyHero said:**
> The only thing I wonder about python is if a complex gui can be put today from it. Most of the pygtk programs I have seen have had relatively simple interfaces. Would I be able to do things such as split screen text editing and stuff like that in pygtk?

The Ubuntu Software Center, for example, is written in Python. Does that answer your question? ;)

---

### Post by slavik on 2010-04-22
> **HalfEmptyHero said:**
> The only thing I wonder about python is if a complex gui can be put today from it. Most of the pygtk programs I have seen have had relatively simple interfaces. Would I be able to do things such as split screen text editing and stuff like that in pygtk?
gtk can do split screen stuff.

ss for python for text editing. I would recommend Perl simply for the fact that making use of regex is simpler (no need to compile, match, etc).

---

### Post by diesch on 2010-04-22
> **trent.josephsen said:**
> Better to have no goal at all than one that will never be achieved, or one that is too distant to be clearly seen.


I'd rather say that having a goal is a fantastic way to learn programming, even if you may never fully reach your goal.

> **trent.josephsen said:**
> 
You need more than a miniscule knowledge of Python to even know where to begin.  


Of course one can't start with just "Now I want to write a word processor", but something like "I want to start with something that may evolve into a word processor over time" can something to begin with. 

A window with a text field and a "Save" button may be a start that doesn't require much knowledge. From that one can go on.

Most likely the first few attempts will sooner or later end in a bunch of buggy code that is hard to understand and about impossible to extend. That's a good chance to learn what you should avoid when writing programs. Have a look at other people's code and try to make it better with your next attempt.

---

### Post by gmargo on 2010-04-22
> **HalfEmptyHero said:**
> I want to write a word processor for writers, like Scrivener for Mac. I have tried many of these on linux, but none of them fit my needs. 

I need a hobby, so might as well learn programming.


That's quite a goal; from Hello World to Word Processor in one step.  You definitely rock. :guitar:

You've tried many word processors but none fit your needs.  But which one was closest?  Or felt the best to you?  Then consider starting with the source code of that program and adding the features you believe are lacking.  Learn whatever language it is written in.  Contribute the changes back to that project if possible.

---

### Post by diesch on 2010-04-22
Scrivener is not a word processor like you have in a office suite but a tools for novelists and such that allows you to manage outlines and pieces of text with associated information.

I think it's not that bad for a pet project.

---

### Post by Dragonbite on 2010-04-22
> **diesch said:**
> I'd rather say that having a goal is a fantastic way to learn programming, even if you may never fully reach your goal.

+1

The best way I learn things is if I have a project, and some sort of a deadline or laid-out plan, because if it weren't for the last minute nothing would get done!

I'm doing that right now; I have a project I'm putting together in PHP and MySQL.  They are not all that difficult, but its very new to me (development, IDE, syntax, etc.) since I'm primarily a VB/.NET/MS SQL guy.  Yes my prior experience helps which is one of the reasons WHY I'm willing to take on this project in the first place.

I've heard good things about Python and have read that it is one of the growing languages.  Get a good reference manual and find the supportive sites for questions, even if its the Ubuntu forums.

I'm thinking of looking into Python next, not quite so interested in Mono anymore.

Good luck!  Keep us up on how the project goes.

Rock On!:guitar:

---

### Post by HalfEmptyHero on 2010-04-22
> **diesch said:**
> I'd rather say that having a goal is a fantastic way to learn programming, even if you may never fully reach your goal.



Of course one can't start with just "Now I want to write a word processor", but something like "I want to start with something that may evolve into a word processor over time" can something to begin with. 

A window with a text field and a "Save" button may be a start that doesn't require much knowledge. From that one can go on.

Most likely the first few attempts will sooner or later end in a bunch of buggy code that is hard to understand and about impossible to extend. That's a good chance to learn what you should avoid when writing programs. Have a look at other people's code and try to make it better with your next attempt.

Thats the sort of thing I want to do. Start small, and build off of that. Sure, I'm not making the next OpenOffice, but I don't want to either.

But now I have another question, should I continue learning python 2 or start learning with 3?

---

### Post by diesch on 2010-04-22
Stay with Python 2 as a lot of libraries, including PyGtk, aren't compatible to Python 3 yet.

But having a look at the changes in Python 3 to avoid unnecessary incompatibilities may make it easier to migrate to python 3 later.

---

