---
title: "c for fun?"
date: 2007-08-13
forum: Programming Talk
---

### Post by Jeek Elemental on 2007-08-13
Trying to get back into programming, mostly for fun but also to widen skills/understanding.

I used to have alot of fun with assembly on 6510 and 680x0 processors, but I realize working on that level on a modern pc is not very practical ](*,)

After a couple months looking around at various languages Im pretty much more confused than enlightened so I ask here for a little advice.

Im comfortable working with bits and bytes, I like to know exactly what Im doing and not have it abstracted away to oblivion =;

I dont have any particular goals, although games and opengl are areas of interest.

So far C looks closest to my preferences, do you agree or is it a dead end?

---

### Post by LaRoza on 2007-08-13
My wiki might help, in my sig.

C is a good language, and other will recommend many others, most noteable, Python.

My wiki also has Assembly, including NASM, which you might like. (There are Linux specific tutorials for it)

My wiki has a lot for many languages, so you might find that useful.

C is not dead, still used, and very useful. If you have no particular goals, learning it is fine. If you are looking for fun, Python can be quite surprising (easy to write and read, and very useful).

---

### Post by pmasiar on 2007-08-13
C seems good fit for you if you want to play deep in the system. Problem is, deep system is nice hobby but much more money are spent on apps development.

Python is another language which should be on your radar, for multiple reasons:
- it is OO (object-oriented), so when you decide to learn OO, try Python to learn and understand it (then you can use it in C++ - but it is much harder to learn using C++ IMHO). When you try Python you will be surprised how much work you do in C yourself Python does for you. Dynamic (latent, duck) typing should be big culture shock for you, as it was for me.
- Python is excellent for tasks which are not time critical, like simple automation, generating test data and comparing them, etc - all over scripting tasks. Because Python syntax is quite C-like and *very* intuitive, you should be able to learn it within a week, and be 10 times more productive in text processing than using C.
- Python is also popular for web-based front-end for databases - which is arguably most app development these days
- Python is great complement to C: you can develop pilot version of your app in Python, profile bottleneck, and reimplement it in C. Python works nice with C.

Programming changed a lot while you weren't looking :-D

See wiki in my sig for links. "Dive into Python" is book for experienced programmers - no fluff, just meat.

---

### Post by LaRoza on 2007-08-13
> **LaRoza said:**
> 
C is a good language, and other will recommend many others, most noteable, Python.

I must be psychic.:D

---

### Post by Wybiral on 2007-08-13
With your background (having a working knowledge of the machine and previous assembly experience) I would definitely learn C first.

But, pmasiar is right, after C you may want to look into some higher level languages like C++ and Python.

The good thing about either of those is that learning C++ will just be learning an extension of C and a new way to look at data.

Learning Python will be an extremely new way to handle program flow and development all together, but you can still use your C knowledge to extend your python programs by writing modules (or you can use Python to extend your C programs by adding scriptability).

---

### Post by Jeek Elemental on 2007-08-20
thanks all, good info.

Settled on C with Eclipse as ide, probably overkill but seems nice. :)

---

### Post by fct on 2007-08-21
If Eclipse is too much for your machine, try the nightly builds of codeblocks, it's a really nice and cross-platform IDE: [http://www.codeblocks.org](http://www.codeblocks.org)

If you are interested in games, after you get the grasp of C (pointers are critical) you might want to learn the SDL library ( [http://libsdl.org](http://libsdl.org) ) that works with OpenGL smoothly and has many other libraries based on it (SDL_mixer, SDL_net, etc.).

---

