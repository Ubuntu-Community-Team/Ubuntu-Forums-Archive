---
title: "language suggestion"
date: 2011-04-06
forum: Programming Talk
---

### Post by vortmax on 2011-04-06
I'm developing a program to interface with a piece of hardware over serial ports.  I just spent all day writing an interface in labview only to figure out I can't use it due to version mismatch (and I'm not buying a $$$$ license to fix it).   Since I have to code the serial port conversation by hand in labview, the only thing that program is giving me is a nice GUI.  This is making me seriously consider ditching labview and rolling my own code...I'm just not sure what language to choose.

I need it to have solid GUI capabilities and be able to be compiled into a static windows executable (I want to avoid extraneous dependencies).  Java might be an option but I don't know Java at all.

Any suggestions?

---

### Post by VernonA on 2011-04-08
Java's support for serial ports is poor at best. Sun used to provide a javax.comm package but I don't think it is available any more. There may be a 3rd party lib available, but I don't know of one.
The best language for controlling hardware is C, and you will find a ton of code examples and libraries available for serial comms. When you want to add a GUI to C, that complicates things. You need to find a good library to help you out, and I suggest you start Googling. You can also search in these threads since "what's the best way to get a GUI" is a popular point of debate. To get you started have a look at Qt, wxWidgets and GTK+.

---

### Post by v1ad on 2011-04-08
C is very good on the hardware layer.

---

### Post by youbuntu on 2011-04-08
> **v1ad said:**
> C is very good on the hardware layer.

+1, as almost every other language is based on C (apart from ASM, of course)

---

### Post by myrtle1908 on 2011-04-08
> **VernonA said:**
> Java's support for serial ports is poor at best. Sun used to provide a javax.comm package but I don't think it is available any more. There may be a 3rd party lib available, but I don't know of one.

It's still available ... 

[http://www.oracle.com/technetwork/java/index-jsp-141752.html](http://www.oracle.com/technetwork/java/index-jsp-141752.html)

[http://en.wikibooks.org/wiki/Serial_Programming/Serial_Java](http://en.wikibooks.org/wiki/Serial_Programming/Serial_Java)

---

### Post by CptPicard on 2011-04-09
> **glossywhite said:**
> +1, as almost every other language is based on C (apart from ASM, of course)

These kinds of statements need closer inspection. Conceptually speaking, yes, a lot of imperative programming languages have borrowed C's syntax for their basic constructs, but that's pretty trivial.

I guess what you're after is the idea that other languages somehow "run on" C, because, say, a lot of language interpreters are written in C. Whether this makes the language itself in any way "based on C" is IMO a questionable proposition... any Turing-complete language can be implemented on top of any other Turing-complete language. Higher-level languages are not "coupled" to C or "hosted on it" in the way that this seems to suggest.

---

### Post by Jonas thomas on 2011-04-09
> **vortmax said:**
> I'm developing a program to interface with a piece of hardware over serial ports.  I just spent all day writing an interface in labview only to figure out I can't use it due to version mismatch (and I'm not buying a $$$$ license to fix it).   Since I have to code the serial port conversation by hand in labview, the only thing that program is giving me is a nice GUI.  This is making me seriously consider ditching labview and rolling my own code...I'm just not sure what language to choose.

I need it to have solid GUI capabilities and be able to be compiled into a static windows executable (I want to avoid extraneous dependencies).  Java might be an option but I don't know Java at all.

Any suggestions?

What kind of hardware???

---

### Post by Jonas thomas on 2011-04-10
I was curious to see if there where open source alternatives to labview and I ran across this little gem of a thread..
Very interesting reading. Original post in 2007 and still going strong.
[http://jshoer.wordpress.com/2007/08/03/why-i-hate-despise-detest-and-loathe-labview/]("http://jshoer.wordpress.com/2007/08/03/why-i-hate-despise-detest-and-loathe-labview/")

---

### Post by slavik on 2011-04-10
write it in C and make it a library. :)

---

