---
title: "personal programming tasks"
date: 2008-01-17
forum: Programming Talk
---

### Post by thepopasmurf on 2008-01-17
I've learned Python and now I'm trying to now learn C++ and lisp (and others, don't know which ones I like)

However, I'm finding it hard to motivate myself since I don't have a goal in mind.

Does anyone have any ideas for goals or programs which I could do to motivate myself?

---

### Post by FunkyJack on 2008-01-17
I recommend you C++ VTC form 3DBuzz.
They are easy to watch :)

[http://isohunt.com/download/16605687/3dbuzz](http://isohunt.com/download/16605687/3dbuzz)

---

### Post by naugiedoggie on 2008-01-17
> **thepopasmurf said:**
> I've learned Python and now I'm trying to now learn C++ and lisp (and others, don't know which ones I like)

However, I'm finding it hard to motivate myself since I don't have a goal in mind.

Does anyone have any ideas for goals or programs which I could do to motivate myself?

"Scratch the itch."  What application are you using that bugs you or what application would you like to have that is missing?

You don't have to rewrite Word.  It could be something as simple as a log book for your running, a searchable database for your email or a time logger.  When I started learning Java, the object of my desire was an application to record and track my travel expenses.  I'd already written a CGI web app in perl to do it.  But, I wanted an actual application to do it.  I never did finish that project, but it got me started.

I think my first "application" was a checkbook balancer written in bash using bc.  About that same time, I wrote a shell script that computed my net pay based on hours worked, overtime, taxes deducted &c.  You might deduce that I was living from paycheck to paycheck at the time.  ;-)  And, they weren't very big.

Maybe there's something you do at work that could be automated with a new tool that you write yourself.  It could be a macro in Excel -- "macro" can be misleading, since you can write 1000-line code modules to do all kinds of fancy tricks.  I've written an Excel "macro" that provides calendar forms for selecting dates and entering search terms and pulls data from databases through an ODBC driver connection, based on the form data provided by the user.

And, it's less important to know a language than it is *how to program*.  If you know *how* to program, you can write in any language.  (That said, I wouldn't use C++ if you beat me with a stick.  ;-) But, that's another thread.)

Have fun!

Thanks.

mp

---

### Post by EXCiD3 on 2008-01-17
Yeah, just find something you wish you had and start making it. If you need to do some GUI stuff with C++ I highly recommend using Qt ;)

---

### Post by pmasiar on 2008-01-17
wiki in my sig has many training task for learner of programming. One of my most recommended is PythonChallenge, 32 puzzles in increasing difficulty, and with forums where you can discuss (and get hints) each level.

---

### Post by thepopasmurf on 2008-01-18
The main problem is that there is really nothing that I need, I just need ideas for things to do.

---

### Post by Mr.popo on 2008-01-18
- Create an advanced GUI calculator.
- Create a simple text editor.
- Create a webpage in python.
- Create a simple game using the pygame module

There you go.

---

### Post by naugiedoggie on 2008-01-19
> **thepopasmurf said:**
> The main problem is that there is really nothing that I need, I just need ideas for things to do.

Indeed, it is difficult to motivate oneself to do anything, without a goal in mind. Well, people have given you some prospective tasks.  

Here is one that scratches one of my itches, sort of.  Something that I don't have, and you can write, is a commandline tool that displays disk usage by directory.  The perl cookbook has an example tool called dutree, which actually does the parsing and display, but the display is horrible and hard to read.

So, your mission is to write (in python) a directory listing tool that will show the user the number of blocks/bytes/Mbytes used in each directory.  It should format the output for use at the *commandline*, either in an Xterm or in a virtual terminal.  Another gtk frontend is useless.  There are various libraries available for doing basic color/drawing at that level -- [ncurses]("http://invisible-island.net/ncurses/announce.html"),  [slang]("http://www.s-lang.org"), or [svgalib]("http://www.svgalib.org").  

Aren't you always trying to figure out where all your disk space went?  I am.  This tool is the answer.

Have fun.

Thanks.

mp

---

### Post by cprofitt on 2008-01-20
> **thepopasmurf said:**
> The main problem is that there is really nothing that I need, I just need ideas for things to do.

Write a program to determine if a number is a [Lychrel number]("http://users.tmok.com/~pla/lychrel/lychrel.shtml").

That is all for now.

---

### Post by pedro_orange on 2008-01-21
Work through a relevant programming book, doing the exercises as you go. 
Then you get the theory and practical knowledge. 

Accelerated C++ is pretty good for this. Has some pretty interesting exercises to get your teeth into, and doesn't mince about with variables in the first chapter, ifs in the second. Gets right into the STL around chapter 2 (if memory serves) and you start using some funky library commands right off the bat.

The real key is finding something that interests you. Then you can try and rewrite your own version of it, or write add ons to it. 

Goodluck, and more importantly have fun!

---

### Post by mathisdermaler on 2008-01-21
If you want to be a better programmer, I suggest joining an open source community that develops some open source application that you admire, even if you don't personally  use it.  

An example for me is PostgreSQL; subscribe to [email]pgsql-hackers@postgresql.org[/email] ([http://www.postgresql.org](http://www.postgresql.org)) and you'll learn a *lot* about programming and databases even if you never write a line of code.  And when you have some time to program you can try to fix a bug or try to add a new feature to PostgreSQL.

---

### Post by pmasiar on 2008-01-21
... or even better, join project you use daily and want to add some features - and then do it!

---

### Post by bobbocanfly on 2008-01-21
Simple ones:

- Rot13 cipher (and try and optimise it)
- Portscanner (basic sockets)
- Pseudo Random Password Generator (Another one to optimise, my record is 1million in 20 seconds using C++)

---

### Post by moephan on 2008-01-22
A plugin for gedit to do something unique and useful for your work or programming.

---

