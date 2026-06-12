---
title: "Project architecture"
date: 2009-06-25
forum: Programming Talk
---

### Post by psld on 2009-06-25
Hi!
I want to develop some for me pretty advanced and complex projects, like with python, sockets, sdl, gtk etc in C but I have no idea how to structure the project. 

Are there any good articles on this subject? Like how to organize and structure projects or so..

---

### Post by nvteighen on 2009-06-26
> **psld said:**
> Hi!
I want to develop some for me pretty advanced and complex projects, like with python, sockets, sdl, gtk etc in C but I have no idea how to structure the project. 

Are there any good articles on this subject? Like how to organize and structure projects or so..

Develop with Python in C? What do you mean by that?

Let's see. The basic idea is to split functionality into independent modules. That's it and use your common sense to keep it as clearest as possible.

Of course, looking at other projects will help you. Also bear in mind that you'll have to learn project management tools, for instance, Makefiles and, probably, some revision control system to keep track of the changes (bazaar is the best option for beginners, IMO) and help you to revert things when something goes wrong.

---

### Post by psld on 2009-06-26
Thanks for the answer, do you know any ideal and small project that I could take a look at?

> **nvteighen said:**
> Develop with Python in C?
I meant something like [http://docs.python.org/c-api/](http://docs.python.org/c-api/)

---

### Post by nvteighen on 2009-06-26
> **psld said:**
> Thanks for the answer, do you know any ideal and small project that I could take a look at?

Look at Launchpad... You'll find a lot. My projects at my sig are not quite orthodox in project structuring :p

Another idea would be to take a look on some simpler sources like nano's. Do:

```

mkdir nano-src && cd nano-src
apt-get source nano # No sudo, please!

```

> I meant something like [http://docs.python.org/c-api/](http://docs.python.org/c-api/)

Ah, ok :p

---

