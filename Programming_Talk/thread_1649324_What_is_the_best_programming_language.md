---
title: "What is the best programming language"
date: 2010-12-20
forum: Programming Talk
---

### Post by ki4jgt on 2010-12-20
Hey everyone. I have been looking for a programming language to try my next project in. I'm under the firm belief that you can use mostly any language to accomplish anything. I understand that most languages are written to handle some situations better, but I still believe any language can be setup for any purpose. With that said. I program in a very windows style BASIC. I've been wanting to work on multiple platforms and I had gotten a lot of bad comments on how BASIC was old and outdated and I needed to switch to Python. So I tried Python, now, no one can give me an internal way to clear the screen, without just printing out a bunch of blank lines. Every website I go to gives me os.system("clear") but the developers here say that is not the way to do it, but all that happens no matter what method I use, is the contents of the screen just get printed out of the users sight, but are still in the terminal. Now that I'm finished complaining, I like Python it's functionality is simply great, but I came from a language which had a built in way to get rid of everything and it didn't remain in the terminal at all. I've tried gambas and a bunch of other programming editors but I kind of like the straight forward editors like:

print "happy"
print A
input "press 'enter' to continue"; ent

My last program had over 1000 lines of code but I can't stand these editors where you have to define this and that before you can start coding. I guess I'm trying to find Python with a little more features, like clearing screen for one. I mean other than that I can't think of anything else I hate about it! Can someone reccomend me a language which:

- is straight text no defining classes or anything
- Simple
- Powerful
- Works on a lot of platforms
- Has basic commands for things like clearing screen w/o having to import

Any help would greatly be appreciated :-) thanks

---

### Post by VastOne on 2010-12-20
> **ki4jgt said:**
> Hey everyone. I have been looking for a programming language to ...

 Can someone reccomend me a language which:

- is straight text no defining classes or anything
- Simple
- Powerful
- Works on a lot of platforms
- Has basic commands for things like clearing screen w/o having to import

Any help would greatly be appreciated :-) thanks


There is a thread on here that has a lengthy discussion on this subject and links to where to get the best help from...

I believe it is a sticky in this section...

---

### Post by ssam on 2010-12-20
if you want more control over what is displayed in the terminal then you could use the curses library (its available in python and other languages). it will let you clear the terminal.

---

### Post by GenBattle on 2010-12-20
You're asking the wrong question.

what you need to ask is not "What language should i use to do X?", it is "What libraries/methods should i use to achieve effect Y with language X?". As you say, any language can be set up for just about any purpose, with enough fiddling.

In this case you need to pick up an external library to serve as your interface instead of the standard default libraries. Someone mentioned curses, probably a good place to start if you want this functionality, otherwise you could hook into an API such as GTK+ and build a GUI app instead of a console one.

As for your best language - everyone's answer is subjective: you need to experiment and determine what is best for you. You should be able to pick up what's popular by cruising around these forums and the internet at large, then give the interesting ones a try and see what works for you.

But if you want something fast - stick to Python or some other high-level scripting language. They will save you alot of time over trying to learn C/C++ from scratch coming from a BASIC background.

All of the points you mentioned you are looking for in a language are actually already possible with python. Python has a great standard library, but it is by no means the complete python toolset and language. So to get features like screen clearing and stuff you need to pick up a library developed by someone else and use that instead of the default terminal. Oh, and by default you do not have to define classes or a mian method in python if you don't want to; all Python scripts simply execute from the first line of the python file to the bottom, so it is not compulsory to arrange your program into classes and methods. This is just best practice.

---

### Post by nvteighen on 2010-12-20
The behaivor you're getting is because a UNIX/Unix-like terminal is a line-buffered file you write to. It will happen no matter whether you use Assembly, C, C++, Python, BASIC or Common Lisp. Wiping the whole thing is impossible (well, close the terminal...) so what you have to do is to modify the terminal content's accessing each character it's *showing*... A trivial way is what the clear command does: calculate how many newline characters you need to place the prompt back into the first line. 

A more complex way is to manipulate the terminal's contents character-wise: this can be done manually using the termios and terminfo terminal-manipulation nightmere-libraries... or using ncurses, which makes it quite easier for everybody.

---

