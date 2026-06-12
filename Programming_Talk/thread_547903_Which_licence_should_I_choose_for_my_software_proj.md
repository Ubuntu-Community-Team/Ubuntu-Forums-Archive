---
title: "Which licence should I choose for my software project?"
date: 2007-09-10
forum: Programming Talk
---

### Post by thetor on 2007-09-10
I am working on a smallish multi-platform software project, and I'm having trouble finding out which software license I can use.

I am programming in Java, and use SWT/JFace for GUI features. I also use Apache Derby and a few LGPL libraries.

So far, I've found out that SWT is released under the Eclipse Public License (which is incompatible with GPL) and that Derby uses the Apache Public License 2.0 (which is compaitible with GPL v3).

If possible, I would like to release my project with the GPL license, but I am worried that this might be illegal seeing as I use SWT. I'm not modifying SWT or any of the other libraries I use, but I have to include them all in the installer package (at least in the windows version)

I did a quick search in SourceForge and found several other GPL-licensed projects that use SWT. Are they using some kind of legal loophole, or have I completely misunderstood how open source licenses work?

---

### Post by pmasiar on 2007-09-10
Sun promised to release Java under GPL3, so just do the same. GPL3 is newest and greates, cutting edge license! Of course you want to use it, exactly as most recent library! :-)

Most programmers don't dive into legal trickery, use spirit of the law and not the literal meaning. Let Sun and FSF figure it out for you.

---

### Post by nanotube on 2007-09-10
i was curious myself so i did some cursory research. the following links may be helpful:
[http://en.wikipedia.org/wiki/Eclipse_Public_License](http://en.wikipedia.org/wiki/Eclipse_Public_License)
[http://www.eclipse.org/legal/eplfaq.php#USEINANOTHER](http://www.eclipse.org/legal/eplfaq.php#USEINANOTHER)

so... the licenses are not compatible, so it doesn't appear that you can legally distribute SWT in a GPL licensed program. what you can do, however, is distribute your code, but mention that it requires SWT - but not actually distribute SWT with your program. I think that should work.

but of course, as pmasiar says, these are all just technicalities - both licenses are open source in spirit, so it is extremely unlikely that anyone will actually give you any grief over it.

---

### Post by thetor on 2007-09-11
> **pmasiar said:**
> Sun promised to release Java under GPL3, so just do the same. GPL3 is newest and greates, cutting edge license! Of course you want to use it, exactly as most recent library! :-)

Most programmers don't dive into legal trickery, use spirit of the law and not the literal meaning. Let Sun and FSF figure it out for you.
Agreed. But SWT isn't a Sun product, it is developed by the Eclipse foundation and there are no plans to release it under GPL. Sun's Java GUI toolkit is called Swing.

> **nanotube said:**
> i was curious myself so i did some cursory research. the following links may be helpful:
[http://en.wikipedia.org/wiki/Eclipse_Public_License](http://en.wikipedia.org/wiki/Eclipse_Public_License)
[http://www.eclipse.org/legal/eplfaq.php#USEINANOTHER](http://www.eclipse.org/legal/eplfaq.php#USEINANOTHER)
so... the licenses are not compatible, so it doesn't appear that you can legally distribute SWT in a GPL licensed program. what you can do, however, is distribute your code, but mention that it requires SWT - but not actually distribute SWT with your program. I think that should work.
I have been considering something similar: The installer asks the user whether or not (s)he wants to install SWT. If the user accept, the installer would download SWT and install it automatically. In this case you might argue that SWT isn't distributed together with GPL software. 

Now, if I could only use apt-get install libswt in windows...

> **nanotube said:**
> but of course, as pmasiar says, these are all just technicalities - both licenses are open source in spirit, so it is extremely unlikely that anyone will actually give you any grief over it.
So - is this the strategy that most of the other SWT projects (like Azureus) use?

---

### Post by nanotube on 2007-09-11
> Now, if I could only use apt-get install libswt in windows...

hehe well... good luck waiting for that one. :) but at any rate, sucking it off the download url from eclipse shouldn't be too hard - or even easier, just pop up a msg box with a link :)

> 
So - is this the strategy that most of the other SWT projects (like Azureus) use?

iirc, they don't actually distribute the SWT itself - they just tell you to go and get it in their installation instructions. at least that's what they used to do, back when i used azureus.

---

### Post by thetor on 2007-09-12
Okay, GPL it is. Thanks for your input!

---

### Post by nanotube on 2007-09-12
> **thetor said:**
> Okay, GPL it is. Thanks for your input!

cool, have fun! :) 
out of curiosity, what's your project about? post a link? :)

---

### Post by thetor on 2007-09-12
It's a small hobby project of mine - a movie organizer. I'm a movie enthusiast and collector, and used to be completely dependent on a Windows-only application called moviedb. Its development has ceased and the website has been down for years. I kept using it until its IMDb-related features stopped working earlier this year. There are other alternatives out there I know, (even a couple in the Ubuntu repos) but I didn't really like any of the ones I've tried. So I'm basically making a moviedb replacement.

My project: [http://code.google.com/p/jmoviedb/](http://code.google.com/p/jmoviedb/)

I learned database and GUI design during the spring semester at the university, so I'm trying to put my new-found knowledge to use. I have to learn a lot of new stuff as I go, (like regular expressions) but I'm making good progress.

---

### Post by nanotube on 2007-09-12
> **thetor said:**
> It's a small hobby project of mine - a movie organizer. I'm a movie enthusiast and collector, and used to be completely dependent on a Windows-only application called moviedb. Its development has ceased and the website has been down for years. I kept using it until its IMDb-related features stopped working earlier this year. There are other alternatives out there I know, (even a couple in the Ubuntu repos) but I didn't really like any of the ones I've tried. So I'm basically making a moviedb replacement.

My project: [http://code.google.com/p/jmoviedb/](http://code.google.com/p/jmoviedb/)

I learned database and GUI design during the spring semester at the university, so I'm trying to put my new-found knowledge to use. I have to learn a lot of new stuff as I go, (like regular expressions) but I'm making good progress.

sounds interesting. :) good luck!
unless you already know java well, and/or you already have some substantial code, i might also suggest using python+gtk or python+wxwidgets for implementation language.

---

### Post by pmasiar on 2007-09-12
...and SQLite as database :-)

---

### Post by thetor on 2007-09-12
Hehe, thanks for the advice both of you, but you're too late...

I've been working on and off for a couple of months and have almost 10k lines of code... and besides, I'm much more familiar with Java than with Python.

The database enginge I'm using is the embedded version of Apache Derby, by the way... the only thing it's missing is a boolean datatype :p

---

### Post by pmasiar on 2007-09-12
is it desktop or web based app? 

10K lines is a lot of code to maintain.... I read somewhere that programmer's productivity should be measured not in LOC (Lines of code) **written** , but il LOC **spent** :-)

---

### Post by thetor on 2007-09-12
> **pmasiar said:**
> is it desktop or web based app?
It's supposed to be a multi-platform desktop app. It should support [all the same platforms as Eclipse]("http://download.eclipse.org/eclipse/downloads/drops/R-3.3-200706251500/index.php#swt") in *theory*... but I'll only test on Ubuntu and Windows.
> **pmasiar said:**
> 10K lines is a lot of code to maintain.... I read somewhere that programmer's productivity should be measured not in LOC (Lines of code) **written** , but il LOC **spent** :-)
No problem. I just make sure to write flawless code to begin with, and I won't have to maintain it ;)

Seriously, though.. I will make it so good that **I'm** satisfied with it - and I have fairly high standards. ...but I don't expect it to become "Debian-stable" right away (or ever)

---

### Post by nanotube on 2007-09-12
> **thetor said:**
> Hehe, thanks for the advice both of you, but you're too late...

I've been working on and off for a couple of months and have almost 10k lines of code... and besides, I'm much more familiar with Java than with Python.

The database enginge I'm using is the embedded version of Apache Derby, by the way... the only thing it's missing is a boolean datatype :p

10k lines of code? wow, that's quite a few. i didn't see any code in the cvs repository for your project... what do you use for revision control? (edit: ehrm, i mean svn - that's what code.google seems to be using).

and as an aside... i bet it could all be done in 50% that many lines in python. hehe... (just kidding - not having seen your code i have no clue if that'd be true. :) ).

---

### Post by thetor on 2007-09-12
> **nanotube said:**
> 10k lines of code? wow, that's quite a few. i didn't see any code in the cvs repository for your project... what do you use for revision control? (edit: ehrm, i mean svn - that's what code.google seems to be using).
It's a one man project so cvs/svn isn't necessary just yet. I'll upload the code when the first alpha is ready... in other words - "When it's done"

...I'm probably jinxed now.

> **nanotube said:**
> and as an aside... i bet it could all be done in 50% that many lines in python. hehe... (just kidding - not having seen your code i have no clue if that'd be true. :) ).
You may be right - though I am implementing more features than most similar applications would. It'll be the MS Office of movie organizers! J/K

---

### Post by nanotube on 2007-09-12
> **thetor said:**
> It's a one man project so cvs/svn isn't necessary just yet. I'll upload the code when the first alpha is ready... in other words - "When it's done"

...I'm probably jinxed now.


heh, well, if you have active code in cvs, that's more likely to attract other developers. if your project has no code, most people will just assume you're not serious about it. :)

and besides, even for a one-man show, revision control is very nice, in case you need to back something out, or figure out when a particular bug cropped in. so... fwiw, i recommend you use it. :)

---

### Post by thetor on 2007-09-12
> **nanotube said:**
> heh, well, if you have active code in cvs, that's more likely to attract other developers. if your project has no code, most people will just assume you're not serious about it. :)

and besides, even for a one-man show, revision control is very nice, in case you need to back something out, or figure out when a particular bug cropped in. so... fwiw, i recommend you use it. :)

I hadn't thought of that - but it sounds like a good idea. I guess I'll set up svn one of these days. Thanks again!

---

### Post by nanotube on 2007-09-12
> **thetor said:**
> I hadn't thought of that - but it sounds like a good idea. I guess I'll set up svn one of these days. Thanks agan!

good luck! :)

---

