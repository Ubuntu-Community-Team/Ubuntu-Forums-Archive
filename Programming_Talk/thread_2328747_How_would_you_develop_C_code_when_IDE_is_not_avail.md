---
title: "How would you develop C code when IDE is not available?"
date: 2016-06-24
forum: Programming Talk
---

### Post by DaviesX on 2016-06-24
Sometimes it's just too hard to reverse engineer the Makefile to reproduce the project in an IDE. I would then have to use CScape + VIM to edit to source file. But the problem is how will you debug the program? It seems there is no good GDB frontend at the moment. I tried nemiver. It crashes often. I also tried DDD but wasn't able to figure out what that was. I wonder what debugging tools would you recommend?

---

### Post by TheFu on 2016-06-24
Many, many, many years ago, we used xxgdb - not that fancy and it would crash about once every other day, but better than typing commands.
There's always emacs, if you are truly desperate. 

I prefer makefiles. To each his own.

---

### Post by DaviesX on 2016-06-24
Hmm... I haven't tried emacs yet. Could you please tell me how emacs helps in this situation? Thanks.

---

### Post by TheFu on 2016-06-24
> **DaviesX said:**
> Hmm... I haven't tried emacs yet. Could you please tell me how emacs helps in this situation? Thanks.

No need for me to write a book: [https://tuhdo.github.io/c-ide.html](https://tuhdo.github.io/c-ide.html)
This is how we did it in the old days - still a highly efficient environment in the hands of someone used to it. I'd put the old-ways up against the new GUI IDEs any day.  Plus, has huge and bloated as emacs is/was, it is still 10000000x less than Eclipse. (Ok, I jest, but you get the point).

Since I'm already excellent at vim, I'd probably do something there, if I still wrote in compiled languages. Pretty comfortable with 3 terminals - that works for every language I've come across from Ada to ZPL with stops for bash, C/C++, IDL, Perl, Ruby, SQL and lots of other smaller languages in between.  OTOH, if you learn the _old ways_, you'll be better prepared when a full IDE isn't available for whatever reason. 

Again, to each their own. Maybe the way I've been doing it all these years is _the hard way_. I dunno.

---

