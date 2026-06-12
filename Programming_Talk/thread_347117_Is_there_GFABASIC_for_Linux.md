---
title: "Is there GFABASIC for Linux ?"
date: 2007-01-26
forum: Programming Talk
---

### Post by burek on 2007-01-26
it exists for windows, so, why not for linux ?

---

### Post by lnostdal on 2007-01-26
> **burek said:**
> it exists for windows, so, why not for linux ?

lol - are you asking a question with a lead or what? No technical reason whatsoever of course.

Well, from another perspective my first guess would be because the authors released binaries for only Windows and kept the source for themselves. Sucks, eh?

It seems GFABASIC has been dead regardless of OS for some time. If your business or whatever depends on GFABASIC in some way you might be somewhat stuck now. This is a problem with proprietary/closed software in general. You as a user tend to be stuck and left behind when authors/businesses you're depending on move along. Want to fix some annoying bug you've recently discovered? Forget it. Want to add some cool feature you've recently thought of? Forget it.

The [wikipedia-page](http://en.wikipedia.org/wiki/GFA_BASIC) does however mention [http://x11-basic.sourceforge.net/](http://x11-basic.sourceforge.net/) They have an .rpm which you might run via `alien' to later install using APT, and they also distribute the source for you to compile. Maybe you can use that?

There are also other options like the excellent (considering the task they are up against) Wine-project which might enable you to run the Windows-version of some specific binary or version of GFABASIC you might require for some (I assume) old software that might not work with the x11-basic dialect.

..if however you want to program under Linux in general there are _way_ better options like Python, Ruby and Lisp available. I'd seriously consider any of those worth the investment in time it takes learning them.

---

### Post by burek on 2007-02-03
Oh loooot of informations !!

Thank you !

apt-get install clisp 
I read that LISP exists for linux. That's cool !
I just installed Clisp and this is a bit like with Atari

I found tkl for gui for lisp programing ... 

... 
thx

---

### Post by lnostdal on 2007-02-03
great :) 

also take a look at emacs and slime (slime should be downloaded from CVS at the moment) .. combined they work great as an interface to your lisp-implementation .. 

let me know if you need help with setting any of this up and i'll try to assist

---

