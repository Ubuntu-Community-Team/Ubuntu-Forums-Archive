---
title: "[ANN]: SymbolicWeb: AJAX/Comet library for Common Lisp"
date: 2008-03-14
forum: Programming Talk
---

### Post by lnostdal on 2008-03-14
a project page is up: [http://code.google.com/p/symbolicweb/](http://code.google.com/p/symbolicweb/)


ok, i'm just gonna post a link to a "demo" that i threw together just now .. it has some bugs.. but still, here it is:

edit: *snip* .. removed because these aren't up and running now .. see posts below instead

..i'll post the source later as it still needs work 

.. more to come later ..

---

### Post by lnostdal on 2008-03-26
some early results/tests ..  this is a quick hack .. here it is: [http://swchat.nostdal.org/](http://swchat.nostdal.org/)

sbcl, hunchentoot and jquery .. the code for the app is here: 
  [http://paste.lisp.org/display/58068](http://paste.lisp.org/display/58068)

..i'm working on some higher level widget-type api for the library .. if 
it works out and doesn't suck too much i'll post the code for that 
also .. :}

..wonder if it still runs when i wake up..

---

### Post by lnostdal on 2008-03-27
ok, it survived the first 24 hours .. i had to do some live-patching, but it's written in lisp so no problem ^^

seems Hunchentoot does not GC sessions unless i call START-SESSION .. so, things grinded to an almost complete halt after a while 

i also got burned by IE(#1) .. it does not (always) remove already bound events on DOM elements when i refresh the browser which lead to interesting results

it's still using long polling for the comet part .. but there should be less network chatter than before, and the performance should be better

it would be interesting to see if it is possible to implement this using a continuous stream of JS directly to the client instead of using long polling

Hunchentoot is starting to feel a bit heavy for this though .. maybe something running on IOLib could handle the comet/ajax requests .. but there is still a lot of room for improvement regardless of what HTTP server is used

..i'll post some more code soon.. =)

PS: any lispers on this forum still alive?


#1: or maybe it was a Wine bug .. i run IE under Wine .. but i think i saw at least one other case where this happened and i don't think he was running IE under Wine

---

### Post by lnostdal on 2008-03-29
edit: a project page is up: [http://code.google.com/p/symbolicweb/](http://code.google.com/p/symbolicweb/)

..any students out there? i just got accepted as a SoC mentor(#1) for this project

more info about SoC here: [http://code.google.com/soc/2008/](http://code.google.com/soc/2008/) .. basically google pays you (read: summer job) to work on cool open source projects

contact me if you're interested in this

again; the idea is to create an ajax/comet/widget library for common lisp(#2)


#1: via the LispNYC organization: [http://lispnyc.org/](http://lispnyc.org/)

#2:  .. there has also been some interest in making it work with other languages like python (python library <--> SW) .. need to do this a bit later though

---

### Post by WW on 2008-03-29
> **lnostdal said:**
> ..any students out there? i just got accepted as a SoC mentor(#1) for this project
Congratulations!

---

### Post by lnostdal on 2008-04-24
thank you WW .. =)

SymbolicWeb came through btw. .. we now have a student aboard for the summer .. *whoho!* time to hack ..... =)

---

