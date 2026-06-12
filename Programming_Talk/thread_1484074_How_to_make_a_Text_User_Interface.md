---
title: "How to make a Text User Interface?"
date: 2010-05-15
forum: Programming Talk
---

### Post by rbaleksandar on 2010-05-15
Hi, guys. :)


  Yesterday I was doing something with my files using [Midnight Commander]("http://www.midnight-commander.org/") (really awesome file manager :guitar: ). I often use [eLinks]("http://elinks.or.cz/") (a text-based internet browser) too. And I asked myself - how can I make such cool text user interfaces? It's not the first time I asked myself such a question and using these two programs just 'turned on the light bulb inside my head'. So I decided to ask you. Where can I find documentation on how to write a TUI and which tools do I have to use to accomplish that? Using Qt one can create GUI and console applications. Is it possible to use it for TUI-development? I googled quite a bit but I couldn't find anything regarding this matter.


Cheers,
rba

---

### Post by januzi on 2010-05-15
You could use curses or ncurses.

---

### Post by rbaleksandar on 2010-05-15
That was one express reply. :P Thanks.

  Now the main question - can I use these libraries with C/C++? Or do I have to use another programming language?


EDIT: Dull question. :D Of course I can. ;) Thanks a lot again. :)

---

### Post by nvteighen on 2010-05-15
And better, there are ncurses bindings for other languages as well :D

---

### Post by januzi on 2010-05-15
Be prepared, 'cause You will be (as name says) cursing a lot.

---

### Post by rbaleksandar on 2010-05-15
> **nvteighen said:**
> And better, there are ncurses bindings for other languages as well :D
  Well, I'm actually interested in C/C++ therefor it doesn't really matter to me if there are. ;) As for the cursing that januzi mentioned...Well, I curse a lot even without a reason. :P

  I'd appreciate if someone can point some good tutorials/literature/etc. on this topic. One can find tons of GUI-books/tutorials/etc., but almost none concerning TUI development.

---

### Post by rnerwein on 2010-05-16
hi
it's interesting that there are people around who want to use curses.
there are many reasons to use this stuff. i use it since about 25 years ( only C - language ) and there are a lot of reasons where you must 
use curses ( low resources, monitoring on huge sever systems without GUI etc. .... )
a quiet good documentation  will be found here: [http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/)
but you must get your own experience because it's "curses" and this will take some time.
have fun with curses  :-)
ciao

---

### Post by DangerOnTheRanger on 2010-05-16
C is ncurses's main language, but I think there is a binding for Python as well. Be warned though, there is no GLADE equivalent.

---

