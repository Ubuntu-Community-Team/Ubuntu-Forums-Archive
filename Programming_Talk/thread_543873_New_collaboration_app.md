---
title: "New collaboration app?"
date: 2007-09-05
forum: Programming Talk
---

### Post by kripkenstein on 2007-09-05
I really want an app to help me with collaborating with people on writing articles.  So far I can't find such a thing, so I thought I might work on coding one myself.

Basically the goal is simple: I write a document (a LaTeX file, which is really just a text file), and I want to be able to work on it with other people at the same time. That is, when they change their copy I want mine to be affected, and vice versa. Currently we are doing this by emailing the file back and forth, but that is really inconvenient.

It seems that Novell's iFolder app might be just what I want - sort of a P2P system for sharing files among a few users. However, from reading on these forums it seems it is quite hard to get it to work on Ubuntu.

Another idea is to do this as a plugin of sorts to Gaim/Pidgin: simply use the file transfer to shuttle the file over when necessary, something like that.

Another direction is to use subversion, which can act as a server on one of our computers. This would also have the benefit of version tracking. GUIs for the clients already exist, what is left to do would be a GUI for the server part, if one doesn't already exist.

So, do any apps exist that already do this sort of thing? If not, any ideas on how to start working on this? Thanks in advance :)

---

### Post by b1g4L on 2007-09-05
Try Google Docs. I believe you can upload docs and invite people to collaborate.

[http://docs.google.com/](http://docs.google.com/)

---

### Post by kripkenstein on 2007-09-05
> **b1g4L said:**
> Try Google Docs. I believe you can upload docs and invite people to collaborate.

[http://docs.google.com/](http://docs.google.com/)

Yeah, that is the right idea, and would be good for many kinds of documents. However, as LaTeX files, I need to compile them. So this would mean constant copy&pasting from Google Docs into a local file.

Now, Google Docs has an API, so I thought I might automate this procedure. But the API only allows creation and reading of documents, not updating an existing one. So that won't work.

---

### Post by b1g4L on 2007-09-05
Why not just setup an FTP? All you would need to do is refresh / re-open each time the doc changes. This assumes you don't want a real-time collaboration session.....

---

### Post by Tomosaur on 2007-09-05
Why can't you just use subversion or something? That's what they're designed for. Software development is just one possible use for it - I see no reason why you can't just use the same technology for documents.

EDIT: Woops, I see you've already thought of this is a solution. Yes, you'll need a server, unless one of you just sets your own machine up as such a server (obviously with the downside of having to leave your computer on all the time).

A quick google search turned this up:
[https://www.bountysource.com/features/subversion](https://www.bountysource.com/features/subversion)

Not sure if it does exactly what you're after, but worth a look.

---

### Post by nanotube on 2007-09-05
you could also just use a wiki - put your file up on like a mediawiki page, and have at it. :) 

but generally, i think a cvs or subversion would probably be more featureful for what you need.

if your doc is open-source related... you could get a project on sourceforge - then you'll have access to their cvs and svn servers. :)

---

### Post by pmasiar on 2007-09-05
there is an editor for collaborative writing like you need - start edit serverm share editing edit plain text. It's name starts with G but eludes me ATM. I'll try..

Edit: Google knows:

[http://www.google.com/search?q=ubuntu+collaborative+editor](http://www.google.com/search?q=ubuntu+collaborative+editor) : [https://launchpad.net/gobby](https://launchpad.net/gobby)

---

### Post by kripkenstein on 2007-09-06
Thanks for the suggestions and ideas :)

[LIST]
[*] Regarding subversion and FTP, yes, both are possible, but I would need to write a GUI to automate things, I guess.
[*] A wiki like MediaWiki is exactly what I want, but I also need a single-click function to compile the code from LaTeX into PDF. With a web-based wiki I would need to download the source every time into a local file.
[*] Gobby is a very interesting tool, looks almost like what I want actually. All it needs is an 'external commands' button which I would use to call the compilation program. I'll check if it already has that.
[/LIST]

So, it looks like my options are either to write a little GUI for FTP/subversion, or sort of a plugin for a wiki like MediaWiki (or Plone, which I like because it is written in Python ;) ), or perhaps use Gobby if it has close-enough functionality to what I need.

I'll do some research and post back later.

---

### Post by nanotube on 2007-09-06
well, there already are guis for CVS (not sure about subversion... but CVS is just as good, for simple purposes).

i use Cervisia for my CVSing, and it works very nicely.

so... first, you'd update a file, (second step), you can compile it. not a "one step" operation, but close enough, no? :)

---

### Post by kripkenstein on 2007-09-06
> **nanotube said:**
> well, there already are guis for CVS (not sure about subversion... but CVS is just as good, for simple purposes).

i use Cervisia for my CVSing, and it works very nicely.

so... first, you'd update a file, (second step), you can compile it. not a "one step" operation, but close enough, no? :)

I guess I could try to see if GUIs for CVS are better than those for subversion, but I really like subversion so I am not sure that would be my best approach.

Meanwhile it looks like I might build on Trac. I am thinking about using the Wiki in Trac and adding a button that would compile the LaTeX document and return a PDF, hopefully that won't be too hard.

---

### Post by nanotube on 2007-09-06
> **kripkenstein said:**
> I guess I could try to see if GUIs for CVS are better than those for subversion, but I really like subversion so I am not sure that would be my best approach.


well, for keeping track of a few latex files... i don't see how it matters whether you are on svn or cvs, whatever fancy new features svn may have over cvs. :)

> 
Meanwhile it looks like I might build on Trac. I am thinking about using the Wiki in Trac and adding a button that would compile the LaTeX document and return a PDF, hopefully that won't be too hard.

seems like an interesting solution.

---

### Post by kripkenstein on 2007-09-06
> **nanotube said:**
> well, for keeping track of a few latex files... i don't see how it matters whether you are on svn or cvs, whatever fancy new features svn may have over cvs. :)

Yeah, you're almost certainly right, but I already know subversion fairly well, so I would rather not go to the effort to learn CVS ;)

---

### Post by nanotube on 2007-09-06
> **kripkenstein said:**
> Yeah, you're almost certainly right, but I already know subversion fairly well, so I would rather not go to the effort to learn CVS ;)

hehe well, afaik, svn's command syntax was deliberately made very cvs-like. not only that - but when using the gui, you don't even need to know a single cvs command, anyway! :) (honestly, if i had to suddenly use cvs on the cli, i'd have to start reading the cvs manual, cuz  i have had the gui take care of everything for me, i never really had to learn how to do cvs on the terminal. ;) )

not that i'm trying to push you to cvs - if you really want to flex your dev muscle and mod that wiki for fun, feel free. :) i personally just try to avoid rolling my own solutions when other OSS stuff already exists... but if you're out for a bit of fun, then obviously that reasoning may not apply. :)

---

### Post by kripkenstein on 2007-09-06
> **nanotube said:**
> not that i'm trying to push you to cvs - if you really want to flex your dev muscle and mod that wiki for fun, feel free. :) i

Yeah, that is just it actually, Trac is written in Python so it sounds like fun to write a plugin for it. Hopefully it will live up to the expectations :)

---

### Post by pmasiar on 2007-09-06
I wanted to suggest that route. TRAC provides for such plugins with different (non-wiki) formatting

---

### Post by nanotube on 2007-09-06
> **kripkenstein said:**
> Yeah, that is just it actually, Trac is written in Python so it sounds like fun to write a plugin for it. Hopefully it will live up to the expectations :)

cool :) let us know how that goes!
i need to collaboratively work on some latex files at times as well, so if you come up with something cool, i'd be personally interested. ;)

---

### Post by kripkenstein on 2007-09-07
Ok, it looks like indeed I will try to make a little plugin for Trac to get it to treat LaTeX nicely in its wiki.

I started a project page here:

[Trac-LaTeX]("http://code.google.com/p/trac-latex/")

---

