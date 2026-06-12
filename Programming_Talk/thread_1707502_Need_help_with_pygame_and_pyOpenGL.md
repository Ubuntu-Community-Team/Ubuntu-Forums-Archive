---
title: "Need help with pygame and pyOpenGL"
date: 2011-03-15
forum: Programming Talk
---

### Post by PicardsTea on 2011-03-15
Hi, I'm new around here and I need help with these problems.

First, I've been using ubuntu for quite some time. Resantly upgraded to 10.10. Have a lot of exp in c++ programming and non in python.

What should I do to get a proper version of python, pygame and pyopenGL? In case I want them by terminal, by sudo apt-get?
As I can see on the "Internets", there are a lot of problems in that field. Different versions won't work together, etc.. And what about tutorials?

Thx for the answers, I'll really appreciate them.;)

---

### Post by Tony Flury on 2011-03-16
Not sure about pyOpenGL - but : 

Python should already by installed - if not a large chunk of your Ubuntu applications simply would not work

pygame- i think you can get that by : 

```

sudo apt-get install pygame

```
And that will get you a version which is comptable with your installed python version.

---

### Post by PicardsTea on 2011-03-16
Yes, somehow I did manage to download all I need.

What about tutorials?

---

### Post by PicardsTea on 2011-03-18
Noone? :(

---

### Post by LemursDontExist on 2011-03-18
I found [this tutorial]("http://pygame.org/docs/tut/chimp/ChimpLineByLine.html") somewhat useful just for getting started in pygame.  It introduces all the tools you need to at least make a basic program.  After that, I would just check the [API]("http://www.pygame.org/docs/ref/index.html").

I was eventually forced to abandon pygame though, due to performance shortcomings, so if you're planning a large or complicated program, you might want to consider another library.

---

### Post by AbhiJais on 2011-03-19
For the python start up you can try this link.

[http://docs.python.org/tutorial/](http://docs.python.org/tutorial/)

It would give you a nice startup. :)

---

### Post by PicardsTea on 2011-03-25
Ok, thx for the help. 

Now, can anyone tell me, how can I rotate around the cube using pygame with pyOpenGL? It confuses me :S

edit: I manage to rotate the object with glRotatef() function. Now how can I zoom in or zoom out from the object?

---

