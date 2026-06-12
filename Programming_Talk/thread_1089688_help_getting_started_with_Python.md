---
title: "help getting started with Python"
date: 2009-03-07
forum: Programming Talk
---

### Post by Ascenti0n on 2009-03-07
Hi all,

I currently develop web apps using PHP/HTML/MySQL/Javascript/CSS and thought it would be great to learn a language the could extend out of the web.

After some searching on Ubuntu forums and some Googling, I found out more about the open source Python and the fact that it can work on web servers as well as the desktop, excellent.

But I understand a v3 of Python has been released. Can someone please advise which version I should learn on?

Ubuntu has v2.5 I think, my web host has 2.3. The obvious would be to learn v2.3 **BUT**, I am not in a rush to learn EVERYTHING, it's purely for fun ATM, and I'm not sure if take up is as with PHP ie Slooooooooow

Any advice?

---

### Post by &#956; . on 2009-03-07
Since you aren't in any rush, you're probably better off with python 3.0.1.

---

### Post by Ascenti0n on 2009-03-07
How can I run Python 3.0? in Ubuntu? and how fast does the rest of the world takeup on new versions? quicker than PHP?

---

### Post by imdano on 2009-03-07
I wouldn't try to use Python 3 yet.  It breaks backward compatibility with 2.x code, which makes it extremely disruptive to upgrade to it.  The 2.x line is going to be the norm in Linux distros for a while (i.e. several years). I'd stick with the version installed by default in Ubuntu for now.

---

### Post by pfdevil on 2009-03-07
If your into the whole web development world then give Ruby a try, and from there use Ruby on Rails.

---

### Post by Can+~ on 2009-03-07
First things first.

a) Learn python in depth
b) Then check out for things like django, cherrypy or whatever

And beginners won't notice the difference between python 2.5.2 and python 2.6/3, the most noticeable thing is that print changed from statement to function.

So start with 2.5.2 (the one that ubuntu comes with).

---

### Post by &#956; . on 2009-03-07
> **imdano said:**
> It breaks backward compatibility with 2.x code, which makes it extremely disruptive to upgrade to it.

Well, he doesn't seem to have any code at the moment so, that seems more like a reason to use 3.

---

### Post by jimi_hendrix on 2009-03-07
i would advise 2.x, because 3.0 is slower and a little worse...or thats what the python masters in ##python on irc.freenode.net told me

---

### Post by jimi_hendrix on 2009-03-07
> **pfdevil said:**
> If your into the whole web development world then give Ruby a try, and from there use Ruby on Rails.

perl is also a big CGI language that can be used alone for other things

---

### Post by &#956; . on 2009-03-07
> **jimi_hendrix said:**
> i would advise 2.x, because 3.0 is slower and a little worse...or thats what the python masters in ##python on irc.freenode.net told me

That's reasonable.

---

### Post by Can+~ on 2009-03-07
> **&#956 said:**
> Well, he doesn't seem to have any code at the moment so, that seems more like a reason to use 3.

I also jumped into Python 3, but for my disappointment, there still libraries needing to be ported, [GTK]("http://bugzilla.gnome.org/show_bug.cgi?id=566641") comes to mind.

---

### Post by Ascenti0n on 2009-03-07
so much conflicting advice....

as long as there isn't too many changes from 2.x to 3, I think I'll stick to the advice of 2.x, especially if uptake is as slow as PHP. Besides, if I really get into I can only go as far, version wide, as my web host will allow.

---

### Post by imdano on 2009-03-07
> **Ascenti0n said:**
> so much conflicting advice....The topic of the official python irc channel says:
>  Topic for #python is: NO LOL | **It's too early to use python 3.x (seriously)** | Pasting > 3 lines? Use [http://paste.pocoo.org/](http://paste.pocoo.org/) | Tutorial: [http://docs.python.org/tut/](http://docs.python.org/tut/) | FAQ: [http://effbot.org/pyfaq/](http://effbot.org/pyfaq/) | New Programmer? Read [http://tinyurl.com/6pgof8](http://tinyurl.com/6pgof8) | #python.web #wsgi #python-fr #python.de #python-es #python.tw #python.pl #python-br #python-jp | Python 2.6.1 released! [http://tinyurl.com/6ou9tl](http://tinyurl.com/6ou9tl)

---

### Post by &#956; . on 2009-03-07
> **imdano said:**
> The topic of the official python irc channel says:

Hmm, nvm then. :) This makes me wonder why they released it like that.

---

### Post by Can+~ on 2009-03-07
> **&#956 said:**
> Hmm, nvm then. :) This makes me wonder why they released it like that.

python3 is practically complete, it has all it's own libraries, [adds some libraries like multiprocessing]("http://docs.python.org/3.0/library/index.html"), etc. But gtk, cairo, pygl, pygame, all are 3rd party libraries that need to be updated yet.

---

### Post by matyasfalvi on 2009-03-08
Hello People!

Recently I also just started to work with python and I have a few very basic questions that I would like to have answered.

1. some how my help function doesn't work, as far as I understand there is a help() function, which you can use interactively from command line, right? E.g. help(file) tells you all about the object file. So this is what happens:

```

george@george-laptop:~$ python help()
bash: syntax error near unexpected token `('
george@george-laptop:~$ 

```

2. how can I check which version of python I am running?

Cheers!

---

### Post by soapytheclown on 2009-03-08
try python to get you into the interactive prompt first then help()

so :

python 
[return]
help()

---

### Post by Can+~ on 2009-03-08
```
canxp@asgard:~$ python
Python 2.5.2 (r252:60911, Oct  5 2008, 19:24:49) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
>>> help()

Welcome to Python 2.5!  This is the online help utility.

If this is your first time using Python, you should definitely check out
the tutorial on the Internet at http://www.python.org/doc/tut/.

Enter the name of any module, keyword, or topic to get help on writing
Python programs and using Python modules.  To quit this help utility and
return to the interpreter, just type "quit".

To get a list of available modules, keywords, or topics, type "modules",
"keywords", or "topics".  Each module also comes with a one-line summary
of what it does; to list the modules whose summaries contain a given word
such as "spam", type "modules spam".

help> 


```

---

### Post by matyasfalvi on 2009-05-18
soapytheclown, Can+~ thanx a lot guys!

---

