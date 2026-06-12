---
title: "New to Python."
date: 2009-07-12
forum: Programming Talk
---

### Post by Godd on 2009-07-12
Hey. 

I decided to learn an oop language and I chose Python to be my first.

I'm doing well but I have two questions vital to my newest program. 

First off, I'm really confused about how to set up Classes. Specifically  the _init_ thingys.

And secondly, where is a really good tutorial on multi-threading. Yet again, this is kinda vital. Ha.

Thankyou for your help in advance.

---

### Post by JordyD on 2009-07-12
> **Godd said:**
> Hey. 

I decided to learn an oop language and I chose Python to be my first.

I'm doing well but I have two questions vital to my newest program. 

First off, I'm really confused about how to set up Classes. Specifically  the _init_ thingys.

And secondly, where is a really good tutorial on multi-threading. Yet again, this is kinda vital. Ha.

Thankyou for your help in advance.

__init__ has *two* underscores(_). It's called when you first create the class. You use it to set things up. Example:
[PHP]class Ball:
    def __init__(self, diameter):
        # code to create a ball with a diameter as passed on instance creation[/PHP]

So when you create an instance for this class:
[PHP]ball = Ball(10)[/PHP]

Now you have a Ball object named ball with a diameter of 10. Notice on the definition of __init__, that you have 'self' as a parameter, that's because in Python when you call mylist = "my string".split(), "my string" is given as the first parameter to split(). Thus you need to have self as a parameter.

I don't use multi-threaded programming, so I can't give any help on that.

---

### Post by Can+~ on 2009-07-12
__init__ is the first method [COLOR="Silver"](well... __new__ is, but better don't get there yet)[/COLOR] to be called when you create a new instance of the Class.

Second thing to notice, is that every method on python classes require a [FONT="Courier New"][COLOR=#00AAFF]self[/COLOR][/FONT] parameter; this is a reference to itself ("this" on java/C++). If you are familiar with the idea of "scopes" then you should consider that methods and variables stored in an instance are found in it[FONT="Courier New"][COLOR=#00AAFF]self[/COLOR][/FONT], it's own scope (or namespace to be correct).

[Python doc]("http://docs.python.org/tutorial/classes.html") as a pretty exhaustive explanation on classes and it's own implementation.

As for Multithreading, leave this for later and read some of the theory behind it. Unfortunately, I don't have any good link to share.

---

### Post by Godd on 2009-07-13
So the program I'm creating has to run a child process.

The child process constantly generates a list of massive length. (literally billions of strings, adding up to more than 10gigs of information)

So my solution was to use multi-threading and never have the generator surpass a list pf 1000 strings. And when the parent program processes a new string, to pop the last used string in the queue. Allowing the child process to queue new strings to be processed.

So if I weren't to use multi threading, how could I achieve the same effect?

I guess I could write it to tag team back and forth between the generator and the processor, but the generator wouldn't be able to store what place it was in the sequence.

EDIT: Or, simply enough, give me an example of how to do this and I can reverse engineer it.

---

### Post by Godd on 2009-07-13
I did some reverse engineering from some scripts and figured out my problems with your(plural) help. Thankyou!

However I don't know where to look for how to redirect the output of my program into the input of another program after it prompts for said input.

What functionality is this called?

---

### Post by DocFox on 2009-07-13
there is a python modules called threading that i have used to monitor serial ports, through the pySerial module. i'm really no expert.

---

### Post by JordyD on 2009-07-13
> **Godd said:**
> I did some reverse engineering from some scripts and figured out my problems with your(plural) help. Thankyou!

However I don't know where to look for how to redirect the output of my program into the input of another program after it prompts for said input.

What functionality is this called?

What program is doing the prompting. Before you look for a way to send it to the program's stdin, you may want to check and see if there are any arguments you can send it so that you can call it with your information instead of send it information after it's called.

---

### Post by days_of_ruin on 2009-07-13
btw don't do:```
class Ball:
``` as it is deprecated. Use ```
class Ball(object):
``` instead.

---

### Post by JordyD on 2009-07-13
> **days_of_ruin said:**
> btw don't do:```
class Ball:
``` as it is deprecated. Use ```
class Ball(object):
``` instead.

Argh! Always deprecating things on me!

---

### Post by Godd on 2009-07-13
I got the class to work with a modified constructor.

However I can't seem to find out what the protocol is to pass argument variables to a class defined module. 

I currently have:

[PHP]
global char_select
char_select = sys.argv[1]
global pass_length
pass_length = sys.argv[2]

class gen(threading.thread)

    def _init_(self,char_select,pass_length):

        self.char_select = char_select
        self.pass_length = pass_length

    def run(self)
        pass

generator = gen()
generator.start()
[/PHP]

I looked at the __init__ definitions of other files and guessed at this. But guessing didn't get me far.

def run(self) passes information out to another thread by using a global list.

But, as I stated above, the amount of data make it bogg down to crashing without pop(0)-ing. So I limit the list down to 10 strings that are constantly cycling from new to old to gone.

But it still boggs down after a few thousand iterations(of some 30 billion iterations). So I need to look into how to solve that, but an idea is to use some different method to pass the information from the generator module to a higher level(as a global list would). 

I'm using pexpect to pass the information onto the called program. I haven't implement that yet, but I know it will work. Though I don't know if it will be the fastest solution.

---

### Post by monraaf on 2009-07-13
Dude, this code makes absolutely no sense at all. Take some time to learn the basics of the language.

---

### Post by Godd on 2009-07-14
> **monraaf said:**
> Dude, this code makes absolutely no sense at all. Take some time to learn the basics of the language.

I told you that I was new to OOP languages and one of the things that I couldn't figure out was defining classes.

I've read six tutorials on the subject including the official python tutorial and five home made tutorials. And the only friend I have that codes doesn't code in python. It's not as though I jumped straight from not knowing to asking these forums. I've searched high and low for an explanation of these things that made sense to me.

And I also said that I guessed at the format and, seeing as how it didn't work, I knew it was wrong. 

I came here for help, not for criticism.

And seeing as how a massive, at least for a guy that has been coding in python for 2 weeks, works I don't think that such harsh words are deserved.

Heres to hoping that everyone else isn't so high and mighty.

---

### Post by monraaf on 2009-07-14
No offense intended. But you're trying to deal here with classes, inheritance and multi threading when it seems to me that you don't even understand how to pass arguments to a function. If you did know you would probably see the similarities between functions and methods.

Of course you are free to disregard my criticism but the usual result of someone trying to run when he can't even walk is that he will fall flat on his face.

---

### Post by Godd on 2009-07-14
I'm sorry. A little rash on my part.

I tend to learn better by baptism by fire than taking baby steps.

I know how classes work, and for that matter I understand the basics of multi threading.

I just don't know how to override the constructor to anything useful.

---

### Post by lavinog on 2009-07-14
Don't expect alot from me, but I think you could remove the global variables:
[php]
import sys
#global char_select
#char_select = sys.argv[1]
#global pass_length
#pass_length = sys.argv[2]

class gen(threading.thread):   #need a colon here

    def _init_(self,char_select,pass_length):

        self.char_select = char_select
        self.pass_length = pass_length

    def run(self):  #need a colon here
        pass


generator = gen(sys.argv[1],sys.argv[2])
generator.run()  #this should be run
[/php]

---

