---
title: "C++ or C#,  help me chose"
date: 2005-06-18
forum: Programming Talk
---

### Post by Kimm on 2005-06-18
I'm having some trubble, just a short while ago I had an idea, an idea for a program. I want the program to be graphical, preferably GTK 2 and I want the program to run on both windows and Linux with very little if any changes made to the code.
I cant pick the language I want to use.

I have more experiance with C++, but coding in GTK is more difficult in C++ then it is in C# and C# isnt all that far from C++ in general and the things that are not like C++ is more like VB and pascal, I have experiance with both. But then I dont know if I can compile my GTK program written in C# under windows and windows users will need both mono, .NET and GTK installed to run the program.

Can anyone help?

---

### Post by gil-galad on 2005-06-18
I am not really the expert on these things, but python is supposed to be a good language for writing gtk programs.

---

### Post by Kimm on 2005-06-18
Python could be good, but I know almost no Python at all so that might be a bit difficult

---

### Post by thumper on 2005-06-18
[QUOTE=Kimm]Python could be good, but I know almost no Python at all so that might be a bit difficult[/QUOTE]
Great!  Perfect choice then  :-P 

My guess that you would be more productive with python than with either C++ or C# for a cross platform GUI app.

---

### Post by Moobert on 2005-06-18
Two good articles on python gui programing:

[http://www.linuxjournal.com/article/6586](http://www.linuxjournal.com/article/6586)

[http://www.oreillynet.com/pub/wlg/6340](http://www.oreillynet.com/pub/wlg/6340)

Good example:

[http://primates.ximian.com/~sandino/python-glade/](http://primates.ximian.com/~sandino/python-glade/)

These methods can also be applied in a similar way into many other languages like perl, c. c++ and c#.

the Qt tool kit if also really worth checking out:

its python binds:
[http://www.riverbankcomputing.co.uk/pyqt/](http://www.riverbankcomputing.co.uk/pyqt/)

but again its works in a similar way with gui editors producing xml data to then be converted into normal language (perl, c, python ect) to use the toolkits binds.

---

### Post by Kimm on 2005-06-18
> 
Great! Perfect choice then


what the heck is that supose to mean? :P

I supose I might give Python a go then, I'm just afraid Python might not live up to my speed requirements, but what the hey :P

But first I would just like to know: I noticed that monodevelop compiles into a .exe files (that runns under Linux without wine), so I was woundering if this app will runn unmodified under windows if the proper libraries are installed?

---

### Post by LordHunter317 on 2005-06-18
[QUOTE=Kimm]. But then I dont know if I can compile my GTK program written in C# under windows[/quote]It should if you write it correctly (not hard).

Writing portable GTK+ in C++ is slightly more difficult, but certainly doable.  You just have to be careful.  However, what I don't know is if the gtkmm (C++ bindings) are cross-platform.  I know the core library is, however.

>  and windows users will need both mono, .NET and GTK installed to run the program.They shouldnt' need mono, just MS' .NET framework and the GTK# libraries.

---

### Post by Kimm on 2005-06-18
Sorry I wasnt thinking ompletely right, I ment if the program is compiled with monodevelop, I think I read that on their website sometime, cant seem to find it now however. Anway that does sound good, I belive most people have .NET installed now...

Anyway, about that *.exe question, can a program compiled on Linux with MonoDevelop run in Windows? I'm asking since it does run under Linux... when I tried running it in windows (with mono and .NET installed) all I got was a blank console screen, however there was one file I did not manage to include for some reason and that might have something to do with it.

---

### Post by LordHunter317 on 2005-06-18
[QUOTE=Kimm]Sorry I wasnt thinking ompletely right, I ment if the program is compiled with monodevelop, I think I read that on their website sometime, cant seem to find it now however. Anway that does sound good, I belive most people have .NET installed now...

Anyway, about that *.exe question, can a program compiled on Linux with MonoDevelop run in Windows? I'm asking since it does run under Linux... when I tried running it in windows (with mono and .NET installed) all I got was a blank console screen, however there was one file I did not manage to include for some reason and that might have something to do with it.[/QUOTE]
 It depends on the code you write, and the libraries it depends on.  If you use GTK# for example, the Windows box will need it installed.

In theory if you don't do any P/Invoke, it shouldn't need a recompile.

---

### Post by Kimm on 2005-06-18
ah, that might explain it... I installed gtk not gtk# *bangs head to table*, that sounds very interesting then, I belive C# might be the language I use in the future then ^^
I'm gona download gtk# and install it, then try to run the program and see what happens!

chears ^^

---

### Post by jdong on 2005-06-20
[QUOTE=Kimm]what the heck is that supose to mean? :P

I supose I might give Python a go then, I'm just afraid Python might not live up to my speed requirements, but what the hey :P

But first I would just like to know: I noticed that monodevelop compiles into a .exe files (that runns under Linux without wine), so I was woundering if this app will runn unmodified under windows if the proper libraries are installed?[/QUOTE]

If Python's not gonna do it, what makes you even consider C#? ;)

I highly recommend using Python. Look into the python2.4-psyco package for JIT compiling to get virtually machine code speed.

---

### Post by Kimm on 2005-06-20
Lol, good point I supose, I just figured that C# runs at pretty much equal speeds in both Linux and Windows (as apose to for example: Java)
I anyway need to rethink the way the program will be built up. it basicly needs to check and recheck lots of data in an array over and over again, untill the program stops, I was thinking an endles loop would do it... but then again that would needs lots of system resources and eventualy slow the computer down terribly (imagine that on a windows box #-o ), so that needs to be redone anyway, so Python might be a good choise after all, I'll give it a shot :)

---

### Post by jdong on 2005-06-20
Read into psyco. It can really help you out as far as performance goes.

If that's not enough, might I suggest separating the logic from the GUI? Perhaps use C++/C for the low-level, intensive array-checking logic (if it's easily implementable in C/C++), then communicate to a Python GTK (WxPython) frontend via pipes?

---

### Post by Kimm on 2005-06-20
that might be a very good idea, I did start writing the program in C++ but after realizing I might have trubble creating a GUI in it, I went here to get your opinions.
I'll have a look a psyco, it does sound very interesting ^^

---

