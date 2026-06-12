---
title: "I Need some ideas , leads etc."
date: 2008-04-23
forum: Programming Talk
---

### Post by StOoZ on 2008-04-23
hello my fellow ubuntuers & programmers ,how are you?.

ok, the reason I opened this thread is to get some directions,leads for something to learn and stick up with it.
I have a fairly basic knowledge of C++ , and I learning the language fundamentals more and more each day.
I would like to extend my knowledge to new fields (aka sockets programming etc...), with this language, so Im here to ask for any suggestions, that may or may not interest me, any good interesting fields out there?
I know there a lot, but nothing that comes to my mind at the moment. 
thanks in advance

---

### Post by LaRoza on 2008-04-23
> **StOoZ said:**
> hello my fellow ubuntuers & programmers ,how are you?.

ok, the reason I opened this thread is to get some directions,leads for something to learn and stick up with it.
I have a fairly basic knowledge of C++ , and I learning the language fundamentals more and more each day.
I would like to extend my knowledge to new fields (aka sockets programming etc...), with this language, so Im here to ask for any suggestions, that may or may not interest me, any good interesting fields out there?
I know there a lot, but nothing that comes to my mind at the moment. 
thanks in advance

Is C++ all you know? Perhaps it will help you to learn a new language, a higher level language, or another paradigm.

You could look up some resources on data structures and algorithms as well.

---

### Post by lnostdal on 2008-04-23
google for beej .. install man pages .. check out man 7 socket

---

### Post by StOoZ on 2008-04-23
Is I know only C++.
actually I would like to stick with C++ at the moment,

---

### Post by LaRoza on 2008-04-23
> **StOoZ said:**
> Is I know only C++.
actually I would like to stick with C++ at the moment,

Have you tried GUI programming? You might find that to be interesting. (My wiki has links for GUI toolkits for C++)

---

### Post by StOoZ on 2008-04-23
actually about GUI programming , I thought about going for QT, but the issue is, its not that wide spread, and popular , and its interesting indeed.
about GUI, actually im wondering why should someone learn to program GUI, while you can actually "draw" it using the QT designer?

---

### Post by LaRoza on 2008-04-23
> **StOoZ said:**
> actually about GUI programming , I thought about going for QT, but the issue is, its not that wide spread, and popular , and its interesting indeed.
about GUI, actually im wondering why should someone learn to program GUI, while you can actually "draw" it using the QT designer?

There is more to it than that ;)

---

### Post by StOoZ on 2008-04-23
I know that the QT Designer basically deals only with the QtGui part of the overall QT libraries (I guess), there are also sockets etc threads etc in qt...
but about the GUI ,what else there is?
you can draw anything isnt it?

---

### Post by LaRoza on 2008-04-23
> **StOoZ said:**
> I know that the QT Designer basically deals only with the QtGui part of the overall QT libraries (I guess), there are also sockets etc threads etc in qt...
but about the GUI ,what else there is?
you can draw anything isnt it?

Besides the technical part, there is the design of GUI's.

---

### Post by StOoZ on 2008-04-23
I dont get it...
you mean the design pattern of GUI's?

---

### Post by JupiterV2 on 2008-04-23
GUI programming in Linux isn't limited to Qt either. There is wxWidgets and Gtk+ (or Gtkmm for the GTK C++ bindings, which I use). Using GTKmm can lead you into XML too if you're wanting to branch out (XML is used for menu's/toolbar development).

I agree with LaRoza, presenting and designing a GUI with accompanying code is a learning experience in-of itself. Learning C++ is one thing, learning all the different libraries you can use and how to implement them properly/effectively is something altogether different.

---

### Post by StOoZ on 2008-04-23
I see, well I was sniffing for gtkmm for the last hour, its seems pretty good thing , which I guess I'll start to learn.
few more questions :does gtkmm (GTK) can be ported to win32 somehow?

any suggestions on books for that subject? (gtkmm) <<< IGNORE, FOUND FREE ONE ON THE  GTKMM SITE

---

### Post by LaRoza on 2008-04-23
> **StOoZ said:**
> I see, well I was sniffing for gtkmm for the last hour, its seems pretty good thing , which I guess I'll start to learn.
few more questions :does gtkmm (GTK) can be ported to win32 somehow?

any suggestions on books for that subject? (gtkmm) <<< IGNORE, FOUND FREE ONE ON THE  GTKMM SITE

You might like wxWidgets, as it is designed to be cross platform (it uses GTK for Linux).

---

### Post by RIchard James13 on 2008-04-23
GTK can run on Windows see the GIMP. You can also use GTK yourself. The last time I used it one Windows I had a pyGTK installer and Glade. There is a difference between the Development version of GTK and the Run Time version.
Here is one link [http://gladewin32.sourceforge.net/]("http://gladewin32.sourceforge.net/")
I think if you use [Dev-C++]("http://www.bloodshed.net/") as your compiler you can install GTK dev stuff with that.

---

### Post by happysmileman on 2008-04-23
Qt, GTK and wxWidgets are all cross-platform, so there shouldn't really be a problem there. I much prefer Qt to either of the other two (though to be honest I never really used GTK), however on a Gnome desktop Qt programs might look a bit out of place, and on a KDE desktop, GTK programs might look out of place, but as far as I know their performance is usually about similar no matter which desktop you use.

---

### Post by StOoZ on 2008-04-24
> **RIchard James13 said:**
> GTK can run on Windows see the GIMP. You can also use GTK yourself. The last time I used it one Windows I had a pyGTK installer and Glade. There is a difference between the Development version of GTK and the Run Time version.
Here is one link [http://gladewin32.sourceforge.net/]("http://gladewin32.sourceforge.net/")
I think if you use [Dev-C++]("http://www.bloodshed.net/") as your compiler you can install GTK dev stuff with that.

But what if I want to stick to my FAV IDE and keep using netbeans in linux to develop it?
can I then run this GUI on windows?

---

### Post by StOoZ on 2008-04-24
Oh and another question that popped to my mind, In order to program a GUI, shouldn't I know threads first?

---

### Post by pmasiar on 2008-04-24
> **StOoZ said:**
> Oh and another question that popped to my mind, In order to program a GUI, shouldn't I know threads first?

No. But you need to be comfortable with event handling, because GUI is not sequential run of your code.

---

### Post by Tomosaur on 2008-04-24
> **StOoZ said:**
> Oh and another question that popped to my mind, In order to program a GUI, shouldn't I know threads first?

It certainly helps, but generally only from an 'aesthetic' point of view. It's not absolutely necessary. Depending on how your program works, if there is an intensive section of computation, you may find that the GUI locks up, say after you click the 'ok' button to do whatever. However, more often than not you'll find that you don't want the user using the GUI while this extensive computation goes on anyway, so it doesn't really matter. In these cases, it pays to disable / 'grey-out' the GUI before you do all the computation, just to make things look a bit more professional.

For those cases where the user should be able to use some other part of the program while the software does something, then yes, you should learn threads. Threads themselves aren't particularly troubling, it's only when several threads share common access to some resource that you'll run into problems. Let's say you have two threads which both output a string to the command line. Unless you only give one thread access to the command line at any one time, you'll find the two threads get their output mixed up, which isn't very useful!

---

### Post by RIchard James13 on 2008-04-25
> **StOoZ said:**
> But what if I want to stick to my FAV IDE and keep using netbeans in linux to develop it?
can I then run this GUI on windows?

Although you can cross-compile from Linux to Windows, it requires a lot of work and patience to set up. You can probably use netbeans under Windows instead. I have never used it to develop C/C++ code though so I don't know what compiler it uses nor how it accesses libraries.

See some results on google about cross compiling
[http://www.google.com.au/search?q=Linux+to+Windows+cross+compile]("http://www.google.com.au/search?q=Linux+to+Windows+cross+compile")

---

### Post by Can+~ on 2008-04-25
Another interesting thing is Cairo, a library for vector graphics, I've trying it on python, and it's pretty "fun".

---

