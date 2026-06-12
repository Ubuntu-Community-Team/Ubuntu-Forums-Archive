---
title: "Python Difficulties"
date: 2006-10-14
forum: Programming Talk
---

### Post by thomasaaron on 2006-10-14
Guys, I'm trying to learn Python and hating every single solitary minute of it!

For godsake! Why can't it have a simple keyboard polling equivalent to basic's inkey$? Instead you have to spend hours trolling around on the Internet or mucking around in Pythons (way the hell too extensive) libraries to figure out how to use (the utterly, fricking, mindboggling) curses crap.

And Object Oriented Programming. I was reared on Basic, and this stuff is killing me. I'm starting to wonder if this old dog can be taught any new tricks!

Thanks for the vent, by the way.

Is there an equivalent of inkey$ for keyboard polling in BASH that I can call up into Python? So far, none of the help I've gotten on the forums regarding keyboard polling have I been able to integrate into my program.

Is there a way to incorporate a yabasic subroutine into Python that would add keyboard polling to the program?

I'm within an inche of giving it up with Python. There's got to be an easier way. I hate to go to Gambas because it is not compatible on non-linux platforms.

If any of you guys can coddle me with some philosophical and calming reasoning, I'm game.

Otherwise, can somebody mail me a bullet?

Best,
Tom

---

### Post by nereid on 2006-10-14
I don't remember my Basic days anymore but is inkey$ an input line or simply a key press? For an input line use raw_input but I don't know how to get a single keypress.

---

### Post by ghostdog74 on 2006-10-14
what is your code like?
and have you tried getch() in curses ? 
Reference:
[http://www.amk.ca/python/howto/curses/]("http://www.amk.ca/python/howto/curses/")
[http://docs.python.org/lib/module-curses.html]("http://docs.python.org/lib/module-curses.html")

From the docs, it also mentioned a few examples can be found in the Demo/curses directory from Python source. you may want to check that out.

---

### Post by thomasaaron on 2006-10-14
So far, this is the best I've been able to do with curses.
It works, in a fahion.
But when incorporated with a textmode program, it blanks out everything (i.e. my menu) that is on the screen.

run it and you'll see what I mean.


[PHP]#!/usr/bin/env python

#keystroke.py

loop = True

import curses

print "This is the first line"
print "This is the second line"
print "This is the third line"


stdscr = curses.initscr()


curses.noecho()
curses.cbreak()

while loop:
    c = stdscr.getch(0,0)
    d = c-48
    print d


curses.nocbreak()
curses.echo()
curses.endwin()  [/PHP]

---

### Post by ghostdog74 on 2006-10-14
can you show your "textmode" program as well?
AFAIK, you can add text using :
stdscr.addstr("This is line1").

---

### Post by thomasaaron on 2006-10-14
Yes. It's at work. I'll post it Monday.
Thanks for your help.
And I'll also try your suggestion about stdscr.adstr

Best,
Tom

---

### Post by ghostdog74 on 2006-10-14
> **thomasaaron said:**
> Yes. It's at work. I'll post it Monday.
Thanks for your help.
And I'll also try your suggestion about stdscr.adstr

Best,
Tom

if you do a google search for "Demo/curses" and "Python"
you can find examples of curses python demo scripts.
eg [http://python-psp.net/svn/trunk/python/Demo/curses/]("http://python-psp.net/svn/trunk/python/Demo/curses/") and there are others..
maybe you could learn something from those demo scripts.

---

### Post by thomasaaron on 2006-10-16
Whew!
OK, that did it.
I had to fool around with curses for quite a while to get it to work right, and the suggestion for entering text on the curses window object worked fine.

SO! I went out and purchased "Python for Dummies."

I think its time for me to just go back to square one and get the basics of python down.

Thanks a lot for your help, guys.

Best,
Tom

---

### Post by Note360 on 2006-10-18
If you dont like it dont program it. It is simple.

---

### Post by foxylad on 2006-10-18
I'm an old bugger who has progressed from basic, to c, to c++ to python. And it is a progression - there are still things that I use c for (speed), but python is a breath of fresh air. I won't go on too long, but my python programs have a far greater chance of running first time. Add the readable syntax (even non-programmers can figure out what's happening) and the modern design, and I completely understand why python is so popular.

Objects confused me for a long time, I think because I took the name too literally. But given that it makes sense to group data together (say name, age and sex for a person) so you can pass it as a chunk to a function, it is only a small leap to add functions to the chunk. 

For instance, given our mythical person chunk/object, we probably need a way to represent it as a string - we need a function that takes ('Greg',45,'M') and prints out 'Greg is a 45 year-old male'. We can write a printPerson() function to do that, and it gets lost in all the other functions we have littering our program. Or we can add a print() function to the person object - it is bound to the person object so it won't get used on a parson object by mistake, and if our person object is useful enough to use in other programs, we can move the person object into it's own file and not have to worry about weeding out all the person-specific functions from our code.

Anyhow, my advice is stick with python. Unfortunately you have chosen a rather tricky first example (Basic makes this easy because it depends on a given operating system), but I think before long you'll be starting to think "Oh neat!" quite often. And don't be afraid to scavenge other's code - it's the basis of open source, and you learn a huge amount from examining other's code. God luck!

---

### Post by thomasaaron on 2006-10-19
Thanks for the words of encouragement.
I think I'm starting to get the hang of it.
I'm writing a program now to back up my files to multiple locations at once.
It's going pretty well, and the Python for Dummies book is helpful.

I'd definitely recommend it for those who only know Basic and need to make a smooth transition to Python.

---

