---
title: "Web Indexer in Python"
date: 2007-10-28
forum: Programming Talk
---

### Post by ankursethi on 2007-10-28
I'm writing a simple web indexer in Python that can :
1. Download entire websites.
2. Do simple keyword searches through them.

Currently I'm writing a module which simply downloads and caches the website locally, i.e., no parsing is done. I'll then implement the module to parse the documents for keywords etc. and put it all in a database. The last module will search this database on the basis of input provided by the user. All these will work independently and will be usable as standalone modules.

A "main" module binds them all together. I'm thinking of adding a Tkinter GUI for this as well, so we can have two interfaces, text based and GUI based.

I need to know a couple of things :
1. What variable contains the path to the directory in which the current script resides?
2. I need to browse the element tree of the HTML documents. There seem to be two modules for doing this : HTMLParser and htmllib. Which one should I use? Although I can figure out the usage from the module docs, my work would become easier if anybody could give me a link to a tutorial or something.
3. How do I pause for a couple of seconds before downloading the next page? I want my program to play nice with websites, and not suck their bandwidth.

Any hints, suggestions etc. will be welcome. Since I'm doing this for a school project (a science fair, sort of), I won't be using third party modules. Everything has to be done from scratch.

---

### Post by Compyx on 2007-10-28
1. Use the getcwd() function in the os module.
2. Never used either, so I can't help with this one.
3. Use the sleep() function in the time module.

Hope this helps.

---

### Post by Quikee on 2007-10-28
1. 
```

import os

print os.path.dirname(os.path.realpath(__file__))
print os.path.dirname(os.path.realpath(os.__file__))

```

Interesting project ;)

---

### Post by ankursethi on 2007-10-28
@Compyx
Thanks, that works.

@Quickee
It works, too. I just have to append the name of my module before '__file__' (in case I import it).

Thanks guys :)

---

### Post by evymetal on 2007-10-28
Just finished building a python indexer (closed source) for an IR task at work ([team Rubber]("http://teamrubber.com/")). (you can access the resulting search interface, for viral online media, at [viralsauce.com]("http://www.viralsauce.com/"))


**1. What variable contains the path to the directory in which the current script resides?**
- see answer above

**2. I need to browse the element tree of the HTML documents. There seem to be two modules for doing this : HTMLParser and htmllib. Which one should I use? Although I can figure out the usage from the module docs, my work would become easier if anybody could give me a link to a tutorial or something.**
- I would strongly recommend using your own regular expressions via the re module, as this will allow you to index pages that don't conform perfectly to the specs (most web pages don't). If you need more complexity in your indexing algorithms

**3. How do I pause for a couple of seconds before downloading the next page? I want my program to play nice with websites, and not suck their bandwidth.**
- You're going to have to wait for a while for the socket on each request (unless you're using a thread pool). I would suggest using threads and your own code to launch a new thread every n seconds. You could also set this so that you can only download a page from a specific site every n seconds.



Don't forget to obey robots.txt. There are a couple of good modules out there to do this.


There may also be a few tips on the developer blog for the project I was on ([http://www.viralcontentnetwork.blogspot.com/]("http://www.viralcontentnetwork.blogspot.com/")) . Hope they help.


Other hints would be to definitely use some other modules, they will help a lot. For example you could use BaseHTTPServer to serve a web page from a local server to search...

---

### Post by pmasiar on 2007-10-29
Python is good choice for this kind of project for two reasons:
1) simple to learn, but extremely flexible 
2) comes with all kinds of libraries as standard, so you will not be breaking the rules. :-)

ElementTree is excellent XML parser (far best that any competition IMHO), comes with Py 2.5. See recipes in ActiveState Python cookbook, lots of useful tricks.

---

### Post by slavik on 2007-10-29
> **pmasiar said:**
> Python is good choice for this kind of project for two reasons:
1) simple to learn, but extremely flexible 
2) comes with all kinds of libraries as standard, so you will not be breaking the rules. :-)

ElementTree is excellent XML parser (far best that any competition IMHO), comes with Py 2.5. See recipes in ActiveState Python cookbook, lots of useful tricks.
Sorry, but I think Perl is better. :)

1. use wget to download the site
2. use Perl for the text processing :)

---

### Post by ankursethi on 2007-10-29
@slavik
I already know Python, and I don't want to (re) learn Perl. I keep forgetting everything I learn about Perl. The guys in my computer lab have heard good things about Python ; from where, I cannot imagine. They live under rocks. They haven't even heard of Perl (even though Perl is older).

@pmasiar
I'll look at ElementTree. I've seen projects using this module, so I have a rough idea what it can do. No doubt about Python being great for this. Moreover, the guy who's working with me on this doesn't know anything about Python. After looking over my shoulder for 15 minutes, he grasped the basic idea of modules, functions, the basic data structures and basic I/O. And remember, this is a high-school student speaking :)

@evymetal
Thanks for the valueable suggestions. I'll have to read up on threads, though. By the way, the interface *might* not be web based since I don't need to serve my search engine to several computers. I just have one computer on which I'll demo this. Then again, I'll think of it. First I'll complete the downloader and indexer, though. I'll be looking at your blog, too.

By the way, is there any way to declare constants (apart from sticking variables into tuples)?

---

### Post by pmasiar on 2007-10-29
> **slavik said:**
> Sorry, but I think Perl is better. :)

Oh absolutely I would not expect anything different from you. :-) It is great it there is something reliable what does not change.

Trick is, to use Perl without using full power of Perl (which is CPAN) would be foolish - and 3rd party libraries are not allowed.

---

### Post by ankursethi on 2007-10-29
Erm, actually I said I won't be using them. I'm actually allowed to do anything I please. But the judges who come to inspect this stuff are usually experts, and I'm afraid they would recognize any third party libraries and wouldn't give me real credit for the work. Using Python modules won't be a problem because mosules like os, re, urllib etc. are not doing anything special like automating the indexing task, just providing some additional functionality.

I think I'll get lynched for ElementTree/htmllib though. But that's something I can't help ...

---

