---
title: "What should I use to do this? Language/Tools"
date: 2008-06-22
forum: Programming Talk
---

### Post by solexious on 2008-06-22
Hello all,

I will try  not to invoke programming wars with this thread.
This is what I want to do, then what my background / preferred methods are:

I have a laptop I've turned into a picture frame running ubuntu. On it I will have slide shows etc. What I would like to make is a program that I can send messages to over a network, when this program receives a message a box of my design will show up on the screen with the message then fade away.

I think I could find some thing pre-made but I would love to use this to get into application programming.

My programming background for consideration of your suggested language / tools is mainly php. I quite like that way php code works, so some thing along these lines would be smoothest for me to learn, I think...

So, what do you suggest?

Any more you need to know give me a shout.

Sol

---

### Post by Wybiral on 2008-06-22
Python would be a great option for a beginner, and there are modules to make this pretty painless. For the types of fading effects you might want and to load/display the images I would recommend [PyGame]("http://www.pygame.org") (a Python module for 2d graphics and such, it will handle all the events and imagine loading headaches too) and later if you want to venture out into 3d effects on the image rotation, you can use OpenGL with PyGame to accomplish that.

For the server you may be able to just hack up a simple [socket]("http://www.python.org/doc/lib/module-socket.html") server, since it's probably not going to be handling many connections it should be easy. If you want to go with a more robust solution, [Twisted]("http://twistedmatrix.com/") is a great module for client/server development.

---

### Post by solexious on 2008-06-22
Hello,

I tested the waters with python, my main turn off so far is I can't "make the code in my style" But I will look again. Can you recommend a good beginners tutorial, my book and tutorials I have found haven't been very nub friendly.

Thank you

Sol

---

### Post by LaRoza on 2008-06-22
> **solexious said:**
> Hello,

I tested the waters with python, my main turn off so far is I can't "make the code in my style" But I will look again. Can you recommend a good beginners tutorial, my book and tutorials I have found haven't been very nub friendly.


"make the code in my style"? What does that mean? Are you referring to syntax, or a way of programming?

Check out my wiki and the sticky for learning Python.

---

### Post by solexious on 2008-06-22
I guess its the way in php I can do things quite a number of ways, but the python philosophy isn't that way? Or have I taken things I have read wrong?

Sol

---

### Post by LaRoza on 2008-06-22
> **solexious said:**
> I guess its the way in php I can do things quite a number of ways, but the python philosophy isn't that way? Or have I taken things I have read wrong?

Sol

You can do things in more than one way. If you don't like the use of indents to set off blocks, then I would take it you don't indent in PHP either, and therefore don't write readable code ;)

---

### Post by Wybiral on 2008-06-22
Have you ever tried to write PHP code without the "$" in front of variables? Or perhaps without the semicolon at the end of each statement? Tried to get away with writing everything without braces?

It's not that Python isn't as syntactically free as PHP, it's just that it has different rules than you're used to. But syntax is trivial, you learn it quickly. Learning the actual logic of the language, the semantics, is more important. If you get caught up on trivial syntax likes and dislikes, you're going to have trouble learning a ton of languages.

---

### Post by solexious on 2008-06-24
Seems my reply didn't post, here it is a few days late.

I did do all of that, but with how my code looked it was my choice to make it neat, but im sure I will get over it ;)

Can you recomend any great tutorials or books as a lot of ones I have read havent been to well writen...

Thank you all, im looking forward to learning a new language.

Sol

---

### Post by LaRoza on 2008-06-24
> **solexious said:**
> 
I did do all of that, but with how my code looked it was my choice to make it neat, but im sure I will get over it ;)

Can you recomend any great tutorials or books as a lot of ones I have read havent been to well writen...



You can indent to any depth you want (within reason) but four spaces is standard.

Sure, see my wiki and web site.

---

