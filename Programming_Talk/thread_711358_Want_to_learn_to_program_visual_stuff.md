---
title: "Want to learn to program visual stuff"
date: 2008-02-29
forum: Programming Talk
---

### Post by Melhisedek on 2008-02-29
Visual like in Visual Basic. You know have window and boxes and buttons and stuff, not just console output :)

I'm such a newb when it comes to programing so I don't even know what language I'm after. But for now I would like to build some simple calculators, like calories burned after such and such workout. Simple stuff with formulas behind buttons.

Where do I start? What language and/or IDE?

Later on I would like to program some bigger things like bloodsugar "database" for my mother. Where she can put in her daily blood sugar levels and get some smart graphs and replies back. 
Have a lot of ideas but so little time and lack of programing knowledge :)

Thank you for your time!

---

### Post by aks44 on 2008-02-29
You being a self-admitted beginner, I'd say: Python + Glade. I have no experience with that, but it looks quite easy to use.

Other people here will hopefully give more details about that.


When it comes to database stuff: SQLite is what you want. Easy to use & deploy, and has good integration with Python (from what I heard).

---

### Post by LaRoza on 2008-02-29
> **Melhisedek said:**
> Visual like in Visual Basic. You know have window and boxes and buttons and stuff, not just console output :)

I'm such a newb when it comes to programing so I don't even know what language I'm after. But for now I would like to build some simple calculators, like calories burned after such and such workout. Simple stuff with formulas behind buttons.

Where do I start? What language and/or IDE?

Later on I would like to program some bigger things like bloodsugar "database" for my mother. Where she can put in her daily blood sugar levels and get some smart graphs and replies back. 
Have a lot of ideas but so little time and lack of programing knowledge :)

Thank you for your time!

The sticky has this information.

If you want to program GUI's from the start, you will be disappointed.

---

### Post by EXCiD3 on 2008-02-29
I have always liked using C++ and Qt or you can use Python and Qt. I have found that Qt is much easier to me than GTK.

---

### Post by kish on 2008-02-29
Go with python and glade

This may help;

[http://hantslug.org.uk/cgi-bin/wiki.pl?TechTalks/2ndDecember2006](http://hantslug.org.uk/cgi-bin/wiki.pl?TechTalks/2ndDecember2006)

Good luck

---

### Post by pmasiar on 2008-02-29
You did not mentioned what kind of experience you have, if any.

For your mom: plain spreadsheet might be a start. MS Office or OpenOffice, your pick.

Linux developers are not as obsessed about newbie-friendly GUI IDE: because after you get some experience, that same IDE stays in the way to accomplish something you need but IDE designers did not foresee. Which is frustrating. Also, most of free software are done by experts programmers for expert programmers, so obviously server needs of expert programmers :-) Instead of frustration with limited "user friendly" beginner's languages like VB, flexible, productive and easy to learn languages (like Python) are used.

Try links in wiki in my sig. Sticky FAQ has even more info. Be ready to dedicate couple years of study before you become competent programmer, and 10 years of more to be expert.

If you are complete beginner, avoid GUI and learn text programing first.

---

### Post by y-lee on 2008-02-29
C++ might be a hard language to start with but [JUCE ]("http://www.rawmaterialsoftware.com/juce/index.php") looks promising :)

---

### Post by mike_g on 2008-02-29
I wouldent advise starting with C++; imho its pretty hardcore ;)

Out of all the programming languages I know (which is not a lot) I would recommend Java. OOP is great for GUI stuff. Netbeans has an excellent form designer to experiment with when you are starting out. I would also recommend reading 'Objects First' with Java as out of all the programming books I have read (again which is not many) its the only one that hasent bored me to tears, covers a lot of stuff and it introduces using Swing.  Also learning Java should help if you want to move on to C++ later.

---

### Post by stevescripts on 2008-02-29
Melhisedek,

Learning to program is going to take some time (much more than you realize...) and effort.

Learning to use a GUI toolkit is going to take even more time.

I don't mean to discourage you, by any means, but,
you are not going to choose a language and a toolkit, and crank
out the next "Tomb Raider" in the next few weeks.
(If you do, call me ASAP) ;)

Re the bloodsugar idea, as pmasiar said, a spreadsheet might
be a good place to create something useful for your mother.
(This is something I *ought* to make time for, as my wife
is diabetic).

The shortest path to where you would like to go, is, in my opinion,
a scripting language.

(Steve dons his nomex fire-retardant suit ;) )
Opinions will vary but here goes my $.02:

Scripting languages (in my order of preference - everybody
has their own ideas... and I respect them all.)

Tcl
Python (lots of help here)
Ruby
Perl (with some hesitation...)

For a GUI toolkit to begin with I (after adding another layer of nomex)
 would recommend Tk - maybe not so visually pleasing as
Glade or GTK - but (again in my opinion) much easier to grasp.

Tk is available for all of the scripting languages I mentioned above,
(as well as other languages - and easily included in C/C++ programs when you get to that level.)

Hope the helps.  Lots of folks here to support you, no matter what choices you make.

Steve
(with apologies for being long-winded)

---

### Post by mike_g on 2008-02-29
I disagree. UI coding is not all that hard. Especially with a language that has good tools and offers lots of built in functionality. Its certainly nothing when compared to producing a commercial quality game :p

I was coding simple UI stuff in Java a couple of weeks after I started to use the language. At the time I had no OO experience except a tiny bit of C++, which I completely suck at.

---

### Post by pmasiar on 2008-02-29
> **stevescripts said:**
> The shortest path to where you would like to go, is, in my opinion,
a scripting language.

(Steve dons his nomex fire-retardant suit ;)

Don't worry about suits. We discussed that issue many times, had polls about that, etc - just see sticky FAQ. Including java vs Python for beginners - no reason to start that flamewar here, let's continue in the context if so desired.

The only issue with your advice I have is: why to denigrate Python by calling it "scripting" language. It is "normal" language which might be used where traditional  "scripting" languages are used, but also way beyond that. It is dynamically typed, yes, but strongly typed, with all OOP goodies you may ever want.

---

### Post by stevescripts on 2008-02-29
pmasair -

No flame war intended - shameless attempt at humor ...

Tcl and Ruby, as well as Python, go somewhat deeper than just a scripting language.

I delineate here, by calling scripting languages, those which are normally interpreted,
rather than compiled.  (which is why I left out java, FWIW)

Lots of good folks here.

Steve

---

### Post by pmasiar on 2008-03-01
> **stevescripts said:**
> I delineate here, by calling scripting languages, those which are normally interpreted, rather than compiled. 

Difference between compiled and interpreted language is implementation detail. There is interpreted C, there is compiled Python and Lisp.

[http://en.wikipedia.org/wiki/Scripting_language](http://en.wikipedia.org/wiki/Scripting_language) was original meaning as for controlling other application (OS, game, CAD system) by manipulating objects of that application and making them interact, like in a movie script. Python was designed to be both "scripting" language (for OS Amoeba IIRC) and general programming language for solving scientific problems.

---

### Post by achelis on 2008-03-14
I think the OP don't care whether Python is technically a scripting language or not  :)

Java is fairly easy to get started with and there is some IDE's out there to help you out. As for GUI development Swing is not the easiest to learn, but quite nice once you get the hang of it.

Spreadsheets might also be a good alternative if you mainly want to make calculations - and you can do some quite powerful stuff with modern spreadsheets, and of course add graphs and stuff to it as well...

I guess it also depends on whether you have more ambitious long term goals or not.

---

### Post by Kadrus on 2008-03-15
First of all you need to learn the basics of a programming language,say Python,or C++,then start coding little programs that run from the command line,and then when you learned the essentials you can start programming with graphical user interface..it's very different from Visual Basic..if you have used it before on Windows...it's not automatic and direct...later on you can use IDE to develop GUI...like programs with QT....or GTK...

---

