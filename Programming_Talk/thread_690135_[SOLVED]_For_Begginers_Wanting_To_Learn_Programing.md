---
title: "[SOLVED] For Begginers Wanting To Learn Programing"
date: 2008-02-07
forum: Programming Talk
---

### Post by stooshbunutu on 2008-02-07
So I asked earlier to very mixed results so after investigation here is my begginers introduction

***Please note to experienced programmers this is an oppinion based on personal experience so don't just gun me down for the sake of it***

I found that Python seemed to be the easiest and nicest looking language to begin with, also the python console is installed on Ubuntu from the bootup CD.

Here are a few links to nice wats of starting to lear python from an absolute novice level.

[Creating a Game in Python using PyGame Part 1]("http://www.learningpython.com/2006/03/12/creating-a-game-in-python-using-pygame-part-one/")
[Creating a Game in Python using PyGame Part 2]("http://www.learningpython.com/2006/03/19/creating-a-game-in-python-using-pygame-part-two-creating-a-level/")
[Creating a Game in Python using PyGame Part 3]("http://www.learningpython.com/2006/04/16/creating-a-game-in-python-using-pygame-part-3-adding-the-bad-guys/")
[Creating a Game with PyGlet and Python]("http://www.learningpython.com/2007/11/10/creating-a-game-with-pyglet-and-python/")
[Google Learn Python Tutorial]("http://www.google.co.uk/search?hl=en&q=learn+python+tutorial&meta=")

As you can probable tell I decided that a simple game would be the way to go about starting. I am also looking at some different reference books and will edit this later to show my recomendations.

Here are some package requirement links:
[PyGame]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=PyGame&searchon=names&subword=1&version=all&release=all")
[PyGlet]("http://pyglet.org/download.html")

As Regard to Books:
[Free Online Book: Dive into Python]("http://diveintopython.org/")
[How To Think Like A Computer Scientist: Learning With Python (as recomended by erginemr)]("http://openbookproject.net//thinkCSpy/")

Hope this helps someone out there :)

---

### Post by pmasiar on 2008-02-07
Good. I agree that Python is best language for beginners.

But "Dive Into Python" is not a book for beginners: It is for experienced programmers learning Python as yet another language.

There are better books for complete beginners: see wiki in my sig.

---

### Post by ghostdog74 on 2008-02-07
> **stooshbunutu said:**
> So I asked earlier to very mixed results so after investigation here is my begginers introduction

***Please note to experienced programmers this is an oppinion based on personal experience so don't just gun me down for the sake of it***

I found that Python seemed to be the easiest and nicest looking language to begin with, also the python console is installed on Ubuntu from the bootup CD.

Here are a few links to nice wats of starting to lear python from an absolute novice level.

[Creating a Game in Python using PyGame Part 1]("http://www.learningpython.com/2006/03/12/creating-a-game-in-python-using-pygame-part-one/")
[Creating a Game in Python using PyGame Part 2]("http://www.learningpython.com/2006/03/19/creating-a-game-in-python-using-pygame-part-two-creating-a-level/")
[Creating a Game in Python using PyGame Part 3]("http://www.learningpython.com/2006/04/16/creating-a-game-in-python-using-pygame-part-3-adding-the-bad-guys/")
[Creating a Game with PyGlet and Python]("http://www.learningpython.com/2007/11/10/creating-a-game-with-pyglet-and-python/")
[Google Learn Python Tutorial]("http://www.google.co.uk/search?hl=en&q=learn+python+tutorial&meta=")

As you can probable tell I decided that a simple game would be the way to go about starting. I am also looking at some different reference books and will edit this later to show my recomendations.

Here are some package requirement links:
[PyGame]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=PyGame&searchon=names&subword=1&version=all&release=all")
[PyGlet]("http://pyglet.org/download.html")

As Regard to Books:
[Free Online Book: Dive into Python]("http://diveintopython.org/")

Hope this helps someone out there :)
what's your experience in programming like? Is Python your first language? Do you know how many programming languages are out there? Have you tried the others? How do you reach the conclusion that Python is the one for you , without playing with the rest?  How do you know that making a game in Pygame is easier than doing the same in other languages?

---

### Post by pmasiar on 2008-02-07
OP: And why you feel you need to write all new tutorial, instead of adding to existing, and IMHO better, more complete than yours?

@ghostdog74: Why you felt you need to quote whole post, and then comment on it in general, nothing specific?

(Yes, today is the "trim the quote" national day again :-) )

---

### Post by ghostdog74 on 2008-02-07
> **pmasiar said:**
> 
@ghostdog74: Why you felt you need to quote whole post, and then comment on it in general, nothing specific?


yes, i need to. I am quoting his opinion. and all the questions asked are pertaining to his opinion. :). and it doesn't really matter does it, i mean , trim the quotes? there are so many "opinionated" posts everywhere like those "which this and this do you prefer" type and those of the "flaming" type. if its for saving bandwidth and space, why don't we trim those? :)

---

### Post by BuffaloX on 2008-02-11
Hmm DiveintoPython

First example gives me this result!

> bill@logic1:~/Desktop/diveintopython-5.4/py$ ./odbchelper.py 
./odbchelper.py: line 3: odbchelper.py sample script

This program is part of Dive: command not found
./odbchelper.py: line 11: __author__: command not found
./odbchelper.py: line 12: __version__: command not found
./odbchelper.py: line 13: __date__: command not found
./odbchelper.py: line 14: __copyright__: command not found
./odbchelper.py: line 15: __license__: command not found
./odbchelper.py: line 17: syntax error near unexpected token `('
./odbchelper.py: line 17: `def buildConnectionString(params):'


---

### Post by LaRoza on 2008-02-11
Add this line to to the top:

```

#! /usr/bin/python

```

Or run it with:

```

python odbchelper.py

```

---

### Post by ghostdog74 on 2008-02-11
Forget about Dive into Python for now. Go to the first link in my sig and learn from the creator himself.

---

### Post by erginemr on 2008-02-11
Could you please list the contents of this file: odbchelper.py?

I can also advise a secondary beginner book / tutorial ***"How to Think Like a Computer Scientist: Learning with Python"***, which has a more basic approach than ***"Dive into Python"***:

[http://openbookproject.net//thinkCSpy/](http://openbookproject.net//thinkCSpy/)

---

### Post by LaRoza on 2008-02-11
> **erginemr said:**
> Could you please list the contents of this file: odbchelper.py?

I can also advise a secondary beginner book / tutorial ***"How to Think Like a Computer Scientist: Learning with Python"***, which has a more basic approach than ***"Dive into Python"***:

[http://openbookproject.net//thinkCSpy/](http://openbookproject.net//thinkCSpy/)

I already listed the solutions.

(The script doesn't have a shebang)

I also recommend another source for beginners.

---

### Post by erginemr on 2008-02-11
> **ghostdog74 said:**
> Forget about Dive into Python for now. Go to the first link in my sig and learn from the creator himself.

Although Guido van Rossum's tutorial is absolutely noteworthy (it has been written by the developer of the Python language after all), I have read it thoroughly before and resultingly, find it too advanced for a newbie to computer languages. 

It seems to me as if this document has been written rather to explain the semantics / syntax of Python to people who already know how to program in other languages such as C, Java or Pascal.

In this respect, I still recommend ***"How to Think Like a Computer Scientist: Learning with Python"*** to an absolute newbie.

---

### Post by erginemr on 2008-02-11
> **LaRoza said:**
> I already listed the solutions.

(The script doesn't have a shebang)

I also recommend another source for beginners.

Sorry, I didn't see your post. I also suspected the same, that's why, wanted the OP to post the contents of the program.

---

### Post by LaRoza on 2008-02-11
> **erginemr said:**
> Sorry, I didn't see your post. I also suspected the same, that's why, wanted the OP to post the contents of the program.

I have a lot of time on my hands, and I downloaded the source. :-)

---

### Post by BuffaloX on 2008-02-11
> **LaRoza said:**
> Add this line to to the top:

```

#! /usr/bin/python

```

Or run it with:

```

python odbchelper.py

```

Silly me
Thank you worked like a charm,
I wonder why the examples doesn't have correct headers, probably another windows bug. :lolflag:

---

### Post by pmasiar on 2008-02-11
> **BuffaloX said:**
> I wonder why the examples doesn't have correct headers, probably another windows bug. :lolflag:

Windows does not recognize shebang - file association is done in registry, which is proprietary binary structure. So in that sense, using proprietary binary structure for something better done by shebang line **is** a bug :-)

---

