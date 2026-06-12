---
title: "Python, my thing?"
date: 2008-10-31
forum: Programming Talk
---

### Post by linkmaster03 on 2008-10-31
I've been learning and writing in Python. It seems unorganized with all these libraries, and it has odd and incomplete web functions. The lack of documentation for some of the only libs that do a certain function doesn't help either. The community is lacking as well, and the freenode channel isn't very helpful for me.

I am looking for advice; should I switch to something else? I'm not deeply involved with Python. I'd like a language that has good web functions+interaction available. It can be scriptable or compilable. Cross platform is not an issue for me, and I use Ubuntu. Good CLI and GUI interfaces would be cool. 

I'm looking forward to your opinions and suggested. They are all appreciated. :)

---

### Post by LaRoza on 2008-10-31
> **linkmaster03 said:**
> I've been learning and writing in Python. It seems unorganized with all these libraries, and it has odd and incomplete web functions. The lack of documentation for some of the only libs that do a certain function doesn't help either. The community is lacking as well, and the freenode channel isn't very helpful for me.

What do you mean? The standard library is very well organised (although big). [http://www.python.org/doc/](http://www.python.org/doc/)

> 
I am looking for advice; should I switch to something else?
You'll be hard pressed to find something as well documented as Python...

> 
Good CLI and GUI interfaces would be cool. 


Not sure what you want, but Python has support for CLI and GUI interfaces...

---

### Post by HotCupOfJava on 2008-10-31
Well, I'm not familiar enough w/ python to know if I should agree with your analysis, but I am partial to Java. It has extensive documentation and libraries, is cross-platform, and has many advantages for developing web applications. The swing library has just about anything you could want in GUI, and if you want to develop in a GUI (with an IDE of some sort) Netbeans and Eclipse are both very handy (although you'll learn the ins and outs of the language faster using the command line and a plain text editor). I still wouldn't go so far as to say that it is a "perfect" language, though.

---

### Post by pmasiar on 2008-10-31
> **linkmaster03 said:**
> I am looking for advice; should I switch to something else? 

Seems like Python is your first language? 

Yes, please do switch: try to read and make sense from 60+ classes for different variants of input and output in Java. Then you will crawl back to Python singing hossanas ;-)

---

### Post by HotCupOfJava on 2008-10-31
> **pmasiar said:**
> Seems like Python is your first language? 

Yes, please do switch: try to read and make sense from 60+ classes for different variants of input and putput in Java. Then you will crawl back to Python singing hossanas ;-)

As I said - it ain't perfect.........I remember wading through the I/O classes myself, scratching my head and saying "why is this so complicated?"

---

### Post by LaRoza on 2008-10-31
> **HotCupOfJava said:**
> As I said - it ain't perfect.........I remember wading through the I/O classes myself, scratching my head and saying "why is this so complicated?"

Static typing.

---

### Post by samjh on 2008-10-31
Python is actually well-documented (although they are a bit terse, like most tech docs) and has a big community.  Try the Python newsgroup such as [comp.lang.python](http://groups.google.com/group/comp.lang.python/topics).  A lot of posters on this forum know Python well, so feel free to fire away with questions here.

If you're looking for alternatives for web programming, try PHP or Ruby.  It's not my area of interest, so I can't offer more suggestions, but lots of people go gaga over PHP and Ruby for web programming.

---

### Post by HotCupOfJava on 2008-10-31
> **LaRoza said:**
> Static typing.

LOL :lol: I've seen those other threads.....

---

### Post by LaRoza on 2008-10-31
> **HotCupOfJava said:**
> LOL :lol: I've seen those other threads.....

Well, it is the truth. Java has so many functions and objects (Ravioli code) that you need a smart IDE to shuffle through it.

---

### Post by HotCupOfJava on 2008-10-31
> **LaRoza said:**
> Well, it is the truth. Java has so many functions and objects (Ravioli code) that you need a smart IDE to shuffle through it.

Oh, I totally agree! I still find it amusing though (does that mean I'm code-masochistic?)

---

### Post by LaRoza on 2008-10-31
> **HotCupOfJava said:**
> Oh, I totally agree! I still find it amusing though (does that mean I'm code-masochistic?)

Or maybe just used to it :-)

One can be used to anything.

---

### Post by jdonnell on 2008-10-31
ruby has a larger web dev community and a lot more tutorials/books than the python equivalents. Give it a look, it might work for you.

[ruby]("http://www.ruby-lang.org/en/")
[ruby on rails]("http://www.rubyonrails.org/") (for web development)

---

### Post by slavik on 2008-11-01
only you can decide whether a language is for you or not ...

---

### Post by sheto on 2008-11-01
What are you saying?

Python has a huge library and you can always download more. 

And BTW, there's Django for web development.

---

### Post by Greyed on 2008-11-01
Or [Zope](http://www.zope.org/).

Getting back to what the OP said, specifically the documentation.  Personally I have not found the documentation sorely lacking in Python.  I started learning it almost 10 years ago.  The main strength that Python has is how simple it is to putter around with things in the interpreter itself.  For example I just could not get the notion of slices in my head so any time I used them (uniform input, for example) I would take a sample, open up the interpreter and literally do something like this:

```

>>> a = 'Some long string I want to capture this and that from'
>>> a[20:30]
'ant to cap'
>>> a[50:60]
'rom'
>>> a[40:53]
'and that from'
>>> a[35:53]
'this and that from'
>>> a[35:49]
'this and that '
>>> a[35:48]
'this and that'

```

So if there is something you're not grasping open up the interpreter and play with it until it gels in your mind.

---

### Post by ankursethi on 2008-11-01
I *specifically* chose to learn Python 2 years ago because of the great documentation. IMHO, Python probably has the best documentation of any of the major programming languages in use today. Of course, I'm talking about the "official" documentation that comes with the language, not extra docs like books and screencasts. Counting the extra stuff, Java wins hands down.

BTW, Ruby has a horrible library reference, but both the Pickaxe book and *The Ruby Programming Language* are great books both for learning the language and for reference. Wait a few months for the new Pickaxe book, which will cover the newly released Ruby 1.9.1. *The Ruby Programming Language* already covers it.

I partly agree with the fact that the standard library is a bit of mess. But then again, Python's stdlib is so extensive and is written by so many different people that getting people to follow a certain standard would be very difficult. Moreover, some of the modules, like ElementTree, appeared as add-ons you could install separately, but were later integrated into the stdlib. If the Python devs had insisted on strict coding standards, we probably wouldn't have all these great modules from so many different authors.

Go take a look at the Ruby libraries and then tell me how you like them :). Even I used to hate the way the Python libs are organized, but I've been using it for 2 years now and I've learned to love them.

EDIT : Whoa! I need to do something about my horrible English.

---

### Post by pmasiar on 2008-11-01
> **jdonnell said:**
> ruby has a larger web dev community and a lot more tutorials/books than the python equivalents.

Rails might be valid advice - back in spring of 2005 (at the time of PyCon 2005). Since summer of 2005, Python has two Rails-inspired web frameworks, Django (better for beginners) and excellent Turbogears. Especially Django has excellent library of ready-made solutions, with substantially bigger comunity of developers and excellent docs.

Python is also more popular than Ruby overall, especially in scientific (non-web) computing (it's primary audience), and is one of three main languages for Google (and main production languages for everything but deep infrastructure).

---

### Post by pmasiar on 2008-11-01
> **ankursethi said:**
> Of course, I'm talking about the "official" documentation that comes with the language, not extra docs like books and screencasts. Counting the extra stuff, Java wins hands down.

One could argue that Java is so complex and over-engineered (60+ I/O classes? WTF?) that it need all that additional docs and books, while Python is so intuitive that the limited amount of docs available is enough. If Python, with no marketing money (only word of mouth) can compete as almost equal with Java, heavily promoted by formerly rich company (Sun), it certainly tell you something about the quality of the language?

Book publishers certainly do prefer Java (because they sell more books for it), but why programmers should prefer language which is more expensive to master? ;-)

---

### Post by DevilzDriv3r on 2008-11-01
> **linkmaster03 said:**
> I've been learning and writing in Python. It seems unorganized with all these libraries, and it has odd and incomplete web functions. The lack of documentation for some of the only libs that do a certain function doesn't help either. The community is lacking as well, and the freenode channel isn't very helpful for me.

I am looking for advice; should I switch to something else? I'm not deeply involved with Python. I'd like a language that has good web functions+interaction available. It can be scriptable or compilable. Cross platform is not an issue for me, and I use Ubuntu. Good CLI and GUI interfaces would be cool. 

I'm looking forward to your opinions and suggested. They are all appreciated. :)

if you ask me these are not good excuses to give-up, stop programming in python and trying a new programming language. because, the same problems you're experiencing in python now can happen in other programming languages. it's like you're running away instead of facing the problems and enjoying programming. 

what i suggest is that first you won't give-up. secondly, this forum has many experts that would like to help you, so please ask anything you like. in addition, the best and the most ultimate way to know what a function does is to see its code-lines - simple, isn't it? 

anywayz, good luck!

---

### Post by linkmaster03 on 2008-11-01
The documentation is good for official Python stuff, but things like web libraries and threading... not so much. I guess I'll check out the others and see what I like.

---

### Post by CptPicard on 2008-11-01
What do you mean by "web libraries" exactly? One might be able to suggest an alternative library if the one you're using is something marginal...

The threading stuff on the other hand is documented just fine. I have a feeling that you just need to learn about concurrent programming in general...

---

### Post by jdonnell on 2008-11-01
> **CptPicard said:**
> I have a feeling that you just need to learn about concurrent programming in general...

This is a great point and I think it highlights some of the flaws with communities like python and ruby. Both have fine documentation if you already understand the underlying concepts of the library be it threading, sockets, or whatever. But what if you don't? I learned most of the underlying concepts from learning about C and linux programming or java texts (usually in college). It's an interesting issue.

---

### Post by CptPicard on 2008-11-01
On the other hand I really don't want to turn something like a threading library API documentation into a general concurrency textbook, which can be 500+ pages thick. And learning about those kinds of general concepts is what you go to school for :)

---

### Post by Greyed on 2008-11-01
> **jdonnell said:**
> But what if you don't? I learned most of the underlying concepts from learning about C and linux programming or java texts (usually in college). It's an interesting issue.  I poked at it with Python.  Ahhh, creating and recovering from thread-bombs that push the computer to a load of 50.  Good times, good times.  :D

---

### Post by jdonnell on 2008-11-01
> **CptPicard said:**
>  And learning about those kinds of general concepts is what you go to school for :)

And if you don't go to school or if you don't learn it all in school? When someone says things like "python is a great language to learn to program in" what do they mean? Just the basics; looping, branching, variables, OO, etc? Then they switch to java to learn about concurrency because there are books on concurrency in java?

---

### Post by CptPicard on 2008-11-01
The point is that API docs really shouldn't cover the "how to really use this in real programs" stuff, they just need to describe how you call the library. Otherwise it becomes really hard to quickly find the technical details you are looking for.

The general concepts are learned, if not in school, then somewhere else. They are not language-dependent, and I am somewhat sceptical of the "concurrency in language X" type books, there is generally too much code per units of actual information. Concurrency for example is, in my opinion, best learned from a source that takes a more abstract look at the whole issue, perhaps using some kind of easy pseudocode (Python is of course pretty close to "easy pseudocode" already..)

---

### Post by jdonnell on 2008-11-02
> **CptPicard said:**
> The point is that API docs really shouldn't cover the "how to really use this in real programs" stuff, they just need to describe how you call the library.

I completely agree. I was talking about the larger issue of learning programming with python or ruby as your first language. 

> Concurrency for example is, in my opinion, best learned from a source that takes a more abstract look at the whole issue, perhaps using some kind of easy pseudocode (Python is of course pretty close to "easy pseudocode" already..)

Exactly, python or ruby are essentially easy psuedocode :) But I recall looking at some ruby code recently that was basically a thin wrapper around C's socket libraries. Calls to select() and stuff like that. There isn't really an explanation of that sort of stuff in ruby (i'm guessing it's true of python too) and I'd have no idea why things were done that way if I didn't already learn it doing C directly. Things like non-blocking IO, buffering, etc.

---

### Post by linkmaster03 on 2008-11-02
Thanks guys, I might try C to learn some of the "theory" (for lack of a better word) of programming.

---

### Post by jdonnell on 2008-11-02
Hey linkmaster, I just wanted to say that I woudln't worry too much about the low level theory stuff until you are comfortable making sites/apps do what you want them to do. 

Ruby or python are both great choices for starting out and doing websites. I'm a rubyist and most of the people here are pythonistas. The differences between ruby and python are more cultural than anything else.

Regarding the low level, here's where it will affect you. The site I do for work uses SOLR for the search. SOLR is written in java but you talk to it via a REST interface (i.e. through network calls). My site works perfectly, but I noticed that talking to the network was slower than it should have been. When I dug into it I realized why it was slow because I understand the low level socket stuff. Not knowing this wouldn't have prevented my site from working exactly how it should, it would have just been slower than necessary.

If you want to check out ruby for the web then check out [ruby on rails]("http://www.rubyonrails.org/")

---

### Post by CptPicard on 2008-11-02
For a good theory language, see Scheme... C teaches you about the "facts of life" with the computer, but programming itself is not really that machine-bound...

---

