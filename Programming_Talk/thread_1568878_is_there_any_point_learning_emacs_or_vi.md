---
title: "is there any point learning emacs or vi?"
date: 2010-09-06
forum: Programming Talk
---

### Post by Søren on 2010-09-06
ive been trying to learn emacs because all these really great older programmers seem to use it and i though because its is so advanced there must be something really rewarding about knowing it. but so far i find it all very painful and unenjoyability. in this day and age is there any reason to use these complex editors from the old days of would i just be better off embracing visual studio and eclipse?

---

### Post by schauerlich on 2010-09-06
Yes.

---

### Post by msrinath80 on 2010-09-06
Yes, again. Please learn both. Learn emacs to run an OS within another. And learn vi to spite emacs users :)

---

### Post by d3v1150m471c on 2010-09-06
i learn the command-line tools because a gui isn't always going to be there to get me out of a bind. if you are prod and poke around in your system as much as me you may want to consider it.

---

### Post by alenis on 2010-09-06
They can be useful when you can't use a GUI editor, but you can consider simpler alternatives, like Nano, for example

---

### Post by matthew.ball on 2010-09-06
I would recommend GNU Emacs personally (though I have never tried vi/m).

There are a few sites which are really good for GNU Emacs, in particular: [emacswiki.org]("http://www.emacswiki.org/") - there's a lot that GNU Emacs has to offer which is very advantageous to programmers, in particular check out the "Programming" section on the aforementioned site.

Really, just have a run through the included tutorial, but remember it is an *interactive* tutorial and to get the most out of it you really have to play along.

Just remember a few key-combinations (save buffers, exit GNU Emacs, and open a new buffer), almost everything can be accessed through the M-x controls (which has support for the tab auto-completion), so it's relatively intuitive after a while. If you find yourself repeating the same commands often - there's probably already a key-binding available for it, if not you can always set one yourself (or you can re-bind a command if you would prefer it at a different key-combination).

---

### Post by eeperson on 2010-09-06
I think both are worth learning if you spend a lot of time in the terminal or spend a lot editing text (such for programming). Each one has its advantages.  Many people tend to be polarized by the two but I think each one has different advantages. 

Emacs is basically the most flexible IDE in existence.  This is in large part due to its Lisp nature (if you haven't learned a Lisp yet I highly recommend it).  Lisp programs allow you to modify them at runtime.  Emacs maps key bindings to Lisp functions (elisp to be exact).  This means that if you want to add features to lisp you can easily do it by calling the functions behind the key bindings.  Also, you can add key bindings for any operation the Emacs is capable of.

Vi(m) is probably the most efficient text editor out there.  This is because it is a [structured editor]("http://en.wikipedia.org/wiki/Structure_editor").  Basically this means that instead having to edit text one character at a time you can edit words or sentences or some other unit of text.

Emacs has better keyboard driven text editing features than most IDEs.  Vim has more IDE features than most text editors.  As a result they tend to be compared to each other even though their emphasis is slightly different.  Vim emphasizes the Unix style 'do one thing and do it well'.  Emacs tends to emphasize including everything in one place (as a result it contains things such as email clients, web browsers)

Since Vi vs. Emacs can be such a polarizing issue I will make my biases clear.  I prefer Emacs + vimpulse (Vim reimplemented in Emacs) as a GUI IDE.  I prefer Vim as a command line text editor.

---

### Post by juancarlospaco on 2010-09-06
ED PWN both

---

### Post by MadCow108 on 2010-09-06
when you are forced to work a lot remotely without nx or X they are tremendously useful.

But for local mid to large project editing it is not very useful.
In that case you are far more productive with an IDE.
Most IDE's (even the simple ones like geany) incorporate the most important emacs/vim editing features nowadays (e.g. duplicate/delete line, block editing, split views, multiple buffers, snippets, ...)
Of course vim/emacs provide a lot more, but the project management features of IDE's outweigh the better editing features of vim/emacs by far.

And turning emacs/vim into an IDE equivalent is a lot of frustrating work for negligible gain.

---

### Post by nvteighen on 2010-09-06
I think Emacs and/or Vi are worth because they do what they are meant to do and do it perfectly. They're text editors optimized for programming; ok, the difference is what they consider "optimized for programming" means, but both do it in different, but useful ways that appeal to different people (I'm an Emacs guy). IDEs have the problem that they want to replace the compiler and other stuff by default and be "not just text editors" (and therefore add a lot of stuff that just make things more confusing)... Sure, you can turn Emacs or Vi into something like an IDE... but you can control them much better and build your environment to your tastes.

---

### Post by matthew.ball on 2010-09-06
To be honest, I rarely do any programming these days. But I still use GNU Emacs heavily; AUCTeX is amazing.

Anyone who uses LaTeX should seriously consider using GNU Emacs + AUCTeX.

---

### Post by worseisworser on 2010-09-06
Emacs and Slime when doing Common Lisp is *very* good.

[http://common-lisp.net/project/slime/doc/html/](http://common-lisp.net/project/slime/doc/html/)

It's actually split in two; a server and client part; this is so one can do remote development. ...but yeah, it has a ton of other features too.

I've got the impression that even people using proprietary Lisps, which come with their own IDEs built in, prefer Emacs+Slime instead of those IDEs.

---

### Post by eeperson on 2010-09-06
> **worseisworser said:**
> Emacs and Slime when doing Common Lisp is *very* good.

[http://common-lisp.net/project/slime/doc/html/](http://common-lisp.net/project/slime/doc/html/)

It's actually split in two; a server and client part; this is so one can do remote development. ...but yeah, it has a ton of other features too.

I've got the impression that even people using proprietary Lisps, which come with their own IDEs built in, prefer Emacs+Slime instead of those IDEs.

+1

Slime is the best development environment I have ever seen.

---

### Post by Reddoug on 2010-09-06
I am just starting a Unix/Linux programming class and we have to learn how to use vi editor.

---

### Post by Athas on 2010-09-06
I have basic vi knowledge. And yeah there is a point in it.  Unfortunatly its vi not vim which I gotta say I prefer to vi.

The point in vi is so that I can just get an ssh shell and edit files. Emacs never learnt I don't think its installed by default on [SIZE=1]solaris[/SIZE] which we use at work.

---

### Post by maximinus_uk on 2010-09-07
I was forced to use VI for a year at college but never really liked it.

EMACS, on the other hand - well, I didn't like that either at the start, to be honest. But EMACS is the one editor that you can ultimately setup exactly the way you like, and turn into the perfect editor for you.

Drawbacks are a very sharp learning curve at the start, and the fact that you might not be certain what really IS your ultimate setup without a lot of playing about. I'd say it was a year or so before I really got EMACS doing exactly what I liked, and I still tweak occasionally now.

But is worth it, if you use a text editor or IDE on a regular basis.

---

### Post by Simian Man on 2010-09-07
If you are a casual programmer, then you likely won't find the time you invest to be worth it.  If you spend most of your time editing text files, however, it is definitely worth it.  If you just learn how to open, save, close, edit etc...then you are just using the functions of any text editor and there is no point.  It's when you go beyond that that it becomes useful.

I have been using vim for six years and still learn new things about it that increase my productivity from time to time.

---

