---
title: "Good Python IDE (not just a syntax highlighter)"
date: 2005-10-19
forum: Programming Talk
---

### Post by bytter on 2005-10-19
Heya there!

I'm a C++ guy. Actually, in the past 2 years, I've been more of a C# guy. MonoDevelop is starting to get to the usability point of VisualStudio. With the integration of stetic, better code completion and debugging facilities, it will SIMPLY rock!

Boo is also cool... Very, very powerfull engine. Good for quick prototyping!

But... Linux desktop seems to be centered around Python. I see python everywere... I would prefer to see C#/Boo and Mono, but Python seems to be here to stay (at least, for now). It has a huge collection of libraries, small footprint, and support in almost every single desktop linux distribution (This coming from a guy whose experience in python have been about 2/3 hours :P) Moreover, lots of stuff are being done with Python and if u want to give an hand to the several tools of the community... Well... In Rome...

Unfortunately, every IDE I've looken upon isn't quite up to what I expect from an IDE. Maybe I've not looked enough (quite possible), or I've understimated the power of VIM (joke here guys :)): I've just glanced at epic3 (ugly, though probably powerfull) and pida (nice but lacking love). 

Of course that the *ideal* IDE would be something in the line of Eclipse (and its amazing Java infrastructure). But I would be very happy to find a Python IDE that has:

[LIST]
[*]Project Support (basic.. the notion of scripts that belong to the same project);
[*]Library crawler (what classes, methods, overloads, arguments is in a library.. documentation here would also be usefull, if available);
[*]Syntax Highlighting (easy and already done);
[*]Smart identation (could be a concept problem due to the nature of Python. How do the current IDEs handle this?);
[*]Code completion (code, not keyword... If I write a dot after "object", it should display a list of methods. If I go through each method, it shuld display a quick summary of its signature and, hopefully, some documentation snip).
[*]Debugging capabilities (Breakpoint, trace, step into, step out, watch, etc, etc...)
[/LIST]

And of couse, if you want to go wild, several other cool features like Refactoring, SVN/CVS integration, collaboration support (thinking of gobby), etc, etc, etc....

My question is (forgetting the last paragraph where I started dreaming out aloud) is there a Python IDE like this? Is there any intent to produce an IDE like this? From scratch? Based on another IDE? Maybe a Plug-In for Eclipse, or MonoDevelop, or, whatever?... Would it be welcomed by the community? Does it even make sense to exist? Are the IDEs available (epic3, pida, others I don't know) working towards this? Have I been blind and ALL of this is implemented and I'm just a noob that can't see them (probably true also :))? Where the hell is my bastard sword +5 with 1d8 fire damage, haste and keen?

Cheers!

---

### Post by ltmon on 2005-10-19
Hi,

It's only really Ubuntu that makes a big thing of Python... if Mono is more your thing you might try out OpenSuSE, as Novell is putting a lot of work into Mono.

As for a good Python IDE, I'd have to recommend Eric3... it's my favourite anyway.  It's in the repos.

L.

---

### Post by bytter on 2005-10-19
[QUOTE=ltmon]It's only really Ubuntu that makes a big thing of Python... if Mono is more your thing you might try out OpenSuSE, as Novell is putting a lot of work into Mono.[/QUOTE]

Yeah, but I use Ubuntu, like Ubuntu, and I'm far more willing to put my time contributing to Ubuntu than SuSE. :D Thx by the tip, though!

---

### Post by amohanty on 2005-10-19
boa-constructor.sf.net

---

### Post by UbuWu on 2005-10-20
SPE (stani's Python Editor). Great IDE. I think it has most features you describe, but it can be a little bit buggy from time to time. Easily installable from the repositories.

You might also like Wing IDE. More advanced, seems more stable, has lots of features. It is not open source, but free for non-commercial open source developers. [http://wingware.com/](http://wingware.com/)

Also there is a plugin for eclipse, never tried that one though.

---

### Post by bytter on 2005-10-20
Thx for the tips guys. I'll have a look to those!

Cheers!

---

### Post by David Marrs on 2005-10-20
I suspect that mono will become more popular with time. It's still quite a new platform and perhaps has to shed its M$-stigma. I really like it as a developer environment myself.

---

### Post by jrbj on 2005-10-20
[QUOTE=bytter]...
Of course that the *ideal* IDE would be something in the line of Eclipse (and its amazing Java infrastructure). ..
[/QUOTE]

As mentioned earlier in the thread, these is a plugin for Eclipse: PyDev:
[http://pydev.sourceforge.net/](http://pydev.sourceforge.net/)

I've been using it for about a month now, and it should be fairly usable to someone who's familiar to Eclipse. It supports Python (CPython) and Jython right now and there's been talk of supporting IronPython later. IronPython is implemented in .NET, but I don't know how compatible it is with Mono.

---

### Post by ember on 2005-10-20
Mhmm ... if I look at it, PyDev seems actually something I could need - how good is code completion with that one?

Best,
ember

---

### Post by jrbj on 2005-10-21
[QUOTE=ember]Mhmm ... if I look at it, PyDev seems actually something I could need - how good is code completion with that one?

Best,
ember[/QUOTE]

Code completion in PyDev is pretty good. In dynamic languages where you can create and define new Classes at runtime, code completion gets kinda tricky. PyDev does ok in most cases, and it can be heavily configured to do what you want.

You need to remember to set the path to your Python interpreter, though:
(Menu): Window->Preferences->Pydev->Interpreter - Python

There's more information on that here:
[http://pydev.sourceforge.net/codecompletion.html](http://pydev.sourceforge.net/codecompletion.html)
[http://pydev.sourceforge.net/faq.html](http://pydev.sourceforge.net/faq.html)

For a list of PyDev features, read the Features page:
[http://pydev.sourceforge.net/features.html](http://pydev.sourceforge.net/features.html)

---

### Post by Quest-Master on 2005-10-21
There's also Dr. Python.. give it a shot. [http://drpython.sourceforge.net/](http://drpython.sourceforge.net/)

---

### Post by fng on 2005-10-21
I would also recommand SPE.

---

