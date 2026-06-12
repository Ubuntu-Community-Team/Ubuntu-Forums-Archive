---
title: "Wanting to learn Python"
date: 2007-11-10
forum: Programming Talk
---

### Post by enchance on 2007-11-10
Where do I start to learn python? I want to develop small apps for my Ubuntu customization. If not Python, what would you suggest?

---

### Post by LaRoza on 2007-11-10
Python is very good, don't stray...

My wiki and the wiki it links to are very good for learning Python. 

If you have any questions, post them here and we'll try to help.

Happy coding!

---

### Post by chris.m.ball on 2007-11-10
Python is definitely a powerful language.  I highly recommend learning by example.  Read lots and lots of other scripts and it will sink in very quickly.  I have a number of python examples on my blog (link is in my signature below) if you're interested.  They start off pretty simple and gradually become more complex.

I'm actually still in the process of learning the language myself - I'm a C# guy at work :popcorn:

---

### Post by Martin Witte on 2007-11-11
this site has a very useful tutorial: [http://diveintopython.org](http://diveintopython.org), for other beginner docs see [http://wiki.python.org/moin/BeginnersGuide](http://wiki.python.org/moin/BeginnersGuide)

---

### Post by Kadrus on 2007-11-11
[http://www.python.org/doc/current/tut/node2.html](http://www.python.org/doc/current/tut/node2.html)

[http://www.sthurlow.com/python/](http://www.sthurlow.com/python/)

The second link is a good basic tutorial for Python...Enjoy :)

---

### Post by pmasiar on 2007-11-11
Again and again forum members recommend "Dive into Python" for beginners. Author itself says it is NOT for beginners: it is for ppl who already mastered other language and want just dive into Python. Seriously people, do you think you are smarter than the author?

There are better books for beginners, see wiki in my sig

---

### Post by dgeorge on 2007-11-11
What can be developed with python?

What do you guys think of plone and zope ?

Is this combo the future of web development?

---

### Post by pmasiar on 2007-11-11
plone and zope are monoliths for really big projects. It is more past than future.

For beginner web app, Django is highly recommended (and "pronounced" by Guido). For more advanced, Turbogears or even Pylons if you really know what you are doing.

Anything can be developed in Python, Python is turing-complete.

---

### Post by Kadrus on 2007-11-11
> **dgeorge said:**
> What can be developed with python?

What do you guys think of plone and zope ?

Is this combo the future of web development?
Yep...like  pmasiar said..anything can be developed in Python..very strong..

---

### Post by enchance on 2007-11-11
How about an editor? I read about VIM and other programs. I don't know which one to get. Also if you can give instructions on how to install them it'd be great. I want to get into Python since I heard it's great--and after all your comments now I'm sure it is and can't wait to begin!

---

### Post by LaRoza on 2007-11-11
Any editor will do, Gedit (default on Ubuntu) is fine. Kwrite, and Kate are also good. Vim is very good, but it may be difficult to use at first.

---

### Post by pmasiar on 2007-11-12
IDLE - Python's IDE - is simple editor integrated with shell and debugger. Most ppl starts learning Python with IDLE. See wiki in my sig. You need to install it on Ubuntu: Python is there, IDLE is not. Couple of clicks with Synaptic...

---

### Post by ThinkBuntu on 2007-11-12
TextMate is superb if you're on a Mac.

---

### Post by enchance on 2007-11-12
> **ThinkBuntu said:**
> TextMate is superb if you're on a Mac.
I'm using Gutsy.

---

### Post by Smygis on 2007-11-12
Stay away from IDLE. It sucks realy hard.
Use Gedit or Kate. [/opinion]

---

### Post by pmasiar on 2007-11-12
Well, I am not sure, why IDLE is so much worse? It is not pretty, I agree (Windows version is nicer), but is very simple and it works right out of the box, and integration with Python shell is better than Kate etc. has.

For pretty IDE, SPE is my favorite (but more complex), or Eric.

> **Smygis said:**
> Stay away from IDLE. It sucks realy hard.
Use Gedit or Kate. [/opinion]

BTW "it sucks" without explaining why not only means I discard **this** comment - it also means (for me) that I will mark you as a person whose opinion can be safely ignored - as just a noise. IMHO, YMMV. You may safely ignore my opinion about you, i don't care, I just wanted to mention it to you, in case you do care about impression you do on other posters.

---

### Post by enchance on 2007-11-12
How about VIM? It any good? I'm gonna be programming in python for the first time tomorrow right after I finish my work tonight!:)

---

### Post by Kadrus on 2007-11-12
> **enchance said:**
> How about VIM? It any good? I'm gonna be programming in python for the first time tomorrow right after I finish my work tonight!:)

VIM is alright in my opinion..

---

### Post by LaRoza on 2007-11-12
Vim is the ultimate editor. I use it on Windows and Linux. It takes a while to learn, but will stay with you the rest of your life.

```

sudo aptitude install vim-full

```

---

### Post by Smygis on 2007-11-12
> **pmasiar said:**
> Well, I am not sure, why IDLE is so much worse? It is not pretty, I agree (Windows version is nicer), but is very simple and it works right out of the box, and integration with Python shell is better than Kate etc. has.

For pretty IDE, SPE is my favorite (but more complex), or Eric.



BTW "it sucks" without explaining why not only means I discard **this** comment - it also means (for me) that I will mark you as a person whose opinion can be safely ignored - as just a noise. IMHO, YMMV. You may safely ignore my opinion about you, i don't care, I just wanted to mention it to you, in case you do care about impression you do on other posters.


1: It does not work as you wuld expect all the time.
Often when i use IDLE scripts ive written wont run thrue IDLE. But runing them normaly works fine.

2: I hate the UI.
I dont give a rats *** about the fact that it looks ****. Ive run apps looking worse and been completley pleased with them. But i cant find anything when i want to find it whenever im forced to use IDLE. 

3: Abstraction obstructs learning.
I think its bad to learn the IDLE way first. Mostly becouse its worse than doing it yourself. you dont gain anything on using it.

And its buggy.

My conclusion of this is that using Gedit with the terminal/python plugin is way better than IDLE. And it looks a lot nicer.
Im not saying that IDLE dont work, Im saying that everything else is better.

And Gedit is installed by default.

IDLE may serve a purpuse on windows where notpad is the default texteditor and the cli is slightly broken but with tools like Gedit available, You dont need it.

---

### Post by pmasiar on 2007-11-12
Re 1: never happened to me. What was it? maybe your expectation are formed using some other program?

Re 2: I use it daily for simple edits, have no problem with it.

Re 3: "Abstraction obstructs learning." ? Not sure how. Good abstractions simplify the learning. What bugs? Did you reported them?

> **Smygis said:**
> 
My conclusion of this is that using Gedit with the terminal/python plugin is way better than IDLE. And it looks a lot nicer.

... but but but... you just said you don't care how it looks, no?

IDLE has nice shell with syntax highlighting - this feature alone beats plain shell in terminal.

My experience with beginning programmers is, they like colorized syntax in IDLE shell very much - it helps them better to see what Python "thinks" about what they typed. Even before they start writing code in py files.

---

### Post by enchance on 2007-11-12
> **pmasiar said:**
> 

My experience with beginning programmers is, they like colorized syntax in IDLE shell very much - it helps them better to see what Python "thinks" about what they typed. Even before they start writing code in py files.

I want to use IDLE shell. How do I install it?

---

### Post by LaRoza on 2007-11-12
Applications->Add/Remove

System->Administration->Synaptic Package Manager

```

sudo aptitude install idle

```

Take your pick...

---

### Post by stimpack on 2007-11-13
I really would just use Kate or gEdit, as boring as it sounds. You need to learn the language, you don't want to waste time learning an IDE.

Once you got the language down, sure look into IDE's that can speed up your development, you will also have a much better idea of what you want the IDE to provide as well. For now, an IDE is just an extra barrier.

---

### Post by pmasiar on 2007-11-13
> **stimpack said:**
> you don't want to waste time learning an IDE.

I am not sure if you know IDLE at all. Learning it - maybe all 5 minutes?

---

### Post by Rich78 on 2007-11-28
Just dragging this back up as I'm in a similar situation.

I'm just wondering if someone could have a quick look at my situation below and offer some advice?

I'm a c# developer as my day job but I've got a project planned that I want to be native to linux but the potential for one component to be windows based (this component may need to be written separately though if my assumptions are correct)

Currently I'm in two minds about whether it's going to be open or closed as I wish it to be a business project which would be an off the shelf product for sale.  But depending on which business model I decide to adopt decides whether I go open or closed.

The project is intended to be a web based system which will require client level access to pieces of hardware.

I'm considering developing the web app in a python based framework but can't decide which so any recommendations would be welcome.  I've had some collegues go down the Django route but it looks a little bit bloggy and wordpressy for my liking, a little restrictive but perhaps my perceptions are wrong?

The other important aspect of the project is to provide client based hardware access.  In windows I would do this by building a windows service, however as the os will be Linux I'm assuming a daemon would be the component to build?  If I build a daemon, would I be right in thinking I'd have to rewrite to component to be a windows service to provide windows support?

Am I also right in thinking, if I go the open source route it would be better to use python to write the daemon (maybe personal choice?)?

But develop it in C++ if it's to be closed?

Thanks and sorry if my questions are a little inaccurate as I'm still fairly new to Linux.

Any advice would be most appreciated.

---

### Post by pmasiar on 2007-11-29
> **Rich78 said:**
>  I've got a project planned that I want to be native to linux but the potential for one component to be windows based ...
The project is intended to be a web based system which will require client level access to pieces of hardware.

This is tricky. If the client is browser, it has only as much access to local hardware as browser has - not much, for security reasons.

So maybe you want to create classical desktop GUI client, talking to remote server over http or something?

> I'm considering developing the web app in a python based framework...Django route but it looks a little bit bloggy and wordpressy for my liking,

You are correct, Django origins in newspaper publishing are there. Turbogears is web app focused on flexible application approach, beyond Django.

> The other important aspect of the project is to provide client based hardware access.  In windows I would do this by building a windows service, however as the os will be Linux I'm assuming a daemon would be the component to build?  If I build a daemon, would I be right in thinking I'd have to rewrite to component to be a windows service to provide windows support?

This does not smell like run-of-the-mill standard web app.

If you need access to local client hardware beyond what Firefox does, you have two routes: ActiveX client (with strong vendor lock-in to Win/Internet Exploder platform, and upgrade treadmill), or cross-platform GUI desktop client.

IIUC, you have no control on client platform, it might be Windows, Linux or Mac. Can you at least settle on platform for server (and settle for Linux :-) )?

Twisted is Python framework to create really flexible server-side apps. Disclosure: I used it only once, I inherited app using Twisted as plain CGI web server. It is independent from client development, but I would assume twisted has client-side python libraries to communicate with the twisted server.

There are many ways to create cross-platform desktop app with Python (wxPython, PyQt, PyGTK and more).

> Am I also right in thinking, if I go the open source route it would be better to use python to write the daemon (maybe personal choice?)?

But develop it in C++ if it's to be closed?


You can develop in Python closed source, license allows it. Python has BSD-like license including core libraries, check license of non-core libraries tho, some might be GPL.

It is not exactly clear to me what you want, but anyway... and you might have more luck soliciting more help by starting your own specific thread with better title.

HTH, and good luck!

---

### Post by Rich78 on 2007-11-29
Thanks for the reply.  

The access to the hardware I plan to do from the client side separate from the browser (hence my mentioning writing a Daemon).

I've written similar apps which use a windows service to poll a database, the site updates the database and the windows service works with the record from there.

My difficulty is switching to the Linux environment to understand developing Daemons.

The server platform will be Linux, no doubt about that, and the primary client base will also be Linux but I would like to support Windows to as not to be too restrictive, from a potential business perspective.

As Python is a scripting language, although I can use a closed source license, I assume the product source can still be accessed and so abused and modified.  This is my concern so far as charging license fees would be concerned.  

As much as I love the idea of Open Source and collaboration, I can't see the business model from a small software business perspective.

Thanks again for your help.  If anyone has any more comments/suggestions I'd appreciate it.

I've come from a strictly Windows and c# background so the learning curve is a little steep at the minute.

---

### Post by pmasiar on 2007-11-29
> **Rich78 said:**
> The access to the hardware I plan to do from the client side separate from the browser (hence my mentioning writing a Daemon).

I've written similar apps which use a windows service to poll a database, the site updates the database and the windows service works with the record from there.

In this case, client talks to server. In web application, browser talks to server, I am not sure what plugin you can make to access local hardware but if you know how, all power to you.

I would hope that security in browser would restricts plugins to go too deep to local hardware but I admit I have no expert info about it.

> My difficulty is switching to the Linux environment to understand developing Daemons.

from 30K feet, daemon is just program which runs without terminal, responds to input on some port, and responds to the port and log files.

> As Python is a scripting language, although I can use a closed source license, I assume the product source can still be accessed and so abused and modified.  This is my concern so far as charging license fees would be concerned.  

There are pyc code obfuscators. Yoy may want to look at Eve Online, IIRC they have client in Python, and it is MMORPG, no lack of smart hackers poking in.

> As much as I love the idea of Open Source and collaboration, I can't see the business model from a small software business perspective.

configuration and support services? customizations?

of course it depends what you want to do, but companies do not want responsibility for understanding their systems, and love to have a throat to choke if something is wrong.

giving sources for free lets them try your package, so you save on marketing.

---

