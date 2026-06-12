---
title: "Choosing Python  2.5/2.6 or 3.0?"
date: 2009-06-12
forum: Programming Talk
---

### Post by Krijk on 2009-06-12
I'm learning Python at the moment. The project I work on is starting to evolve into more code than I imagined at first and is written in 2.5.
Before it gets too big to change I think I have to make a choice between 2.5/2.6 or 3.0.
  
Obviously Python 3.0 is the future but it isn't used as much as the earlier versions. I'm a bit concerned about the backward-portability and the lack of reference-material (internet or books) that I rely on a lot when learning.

I would like to hear some opinions about using Python 2.5/2.6 or Python 3.0?

---

### Post by Tony Flury on 2009-06-12
The normal reply is to continue with Python 2.5/2.6 at least for the time being. It is still installed as default in ubuntu and other linux distributions.

Python 3.0 will become the default I am sure at some point, but with plenty of warning and the conversion is not that difficult from what i know.

---

### Post by myle on 2009-06-12
If you are not in hurry to release your application, or you can ensure that its users will have Python 3.0, I would recommend you the use of version 3.0.

Someday you will have to do it. For the most stuff in Python 3.0, you don't have to worry about the manuals. Most python 2.x will do the job. Just keep in mind that there are some differences.

---

### Post by ricegf on 2009-06-12
Python 2.6 is the "bridge version" between 2.5 and 3.0 - it backports all of the great new 3.0 features that don't break 2.5 compatibility. Consider coding in 2.6, using as many 3.0 features as practical. This will make your eventual transition to 3.0 (with this code and your brain) much simpler.

You can use 2to3 ([http://docs.python.org/library/2to3.html](http://docs.python.org/library/2to3.html)) periodically to check how much manual effort will be required for the transition. And kudos for thinking long-term about your project!

---

### Post by pokerbirch on 2009-06-12
I've been considering this recently as well. From what i have read, the difference between Python 2.5 and 3.0 is quite significant. I like Python, but it has a few annoyances regarding performance (on CPU intensive stuff) and it's not much use for commercial apps or programs for which you don't want the source code *easily* read/decompiled. I guess the language is still evolving, so changes are inevitable...

I keep looking at C because it never changes, but i always end up using Python again. :)

---

### Post by ricegf on 2009-06-12
> **pokerbirch said:**
> ...it has a few annoyances regarding performance (on CPU intensive stuff)...

Yes, Python isn't optimized for performance, but you can address this in several ways. Use built-ins such as generators judiciously. Use libraries such as numpy extensively, as they are already performance-enhanced. Use Psycho as needed. Anticipate Google's "Unladen Swallow". ;-)

> **pokerbirch said:**
> I keep looking at C because it never changes...

Neither does Latin, but I wouldn't want to *speak* it!  ;-)

But seriously, on the performance topic, profile your Python and rewrite the few (and it's almost always just a few) critical methods in C for that extra burst of speed.

C has some advantages - fast, bare-metal speed and control, potential greater portability - but the disadvantages of low-level fixed data structures, much more verbose and detailed code, and lack of object / functional / aspect programming features makes it much less appealing to me nowadays that Python for most projects. (Since my projects are open source, of course, distributing source for the JIT compiler is a *feature*. ;-)

---

### Post by benj1 on 2009-06-12
i would recommend 2.5, most books will be based on 2.5, most people here will be more experienced in 2.5, you will find it easier to get help for 2.5.
from what ive read the differences aren't huge, and 2.6 will include a conversion tool, py2to3 that some one linked above, that will fairly reliably convert code. 
stick with 2.x it'll be around for quite some years.

---

### Post by BackwardsDown on 2009-06-12
You can just use any 2.5 tutorial and use the python 2.6 interpreter. 2.6 is backwards compatible with 2.5 and has some nice things to make the transition to 3.0 more easy.

There are many 2.5/2.6 python tutorials/books around so use them. When there are more libraries for 3.x you can use that. If you know 2.5 well you can learn almost all of the stuff that's new in 3.x within a few hours.

---

### Post by soltanis on 2009-06-12
2.6 is the bridge between 2.5 and 3.0; use that one, since it is reasonable to expect your users to be running an up-to-date version of python such as 2.6, and it will make the future porting to 3.0 a breeze (3.0 isn't really that much different from 2.5 anyway).

---

### Post by jimi_hendrix on 2009-06-13
2.6...but if you dont have it 2.5

even #python on freenode recommends 2.x because its faster and less buggy

---

### Post by Greyed on 2009-06-13
> **pokerbirch said:**
> I've been considering this recently as well. From what i have read, the difference between Python 2.5 and 3.0 is quite significant.

Actually, it isn't.  In fact one of the largest changes, print "foo" to print("foo"), doesn't even effect me since I have always used the latter form which was just as valid in 1.5.2 as it is required in 3.0!  Beyond that change most differences are not something people will run into in day-to-day development.

I may sound like a crusty old fart but believe-you-me, compared to the Perl 4 to Perl 5 conversion the compatiblity breaks here are hardly worth mentioning!

> I like Python, but it has a few annoyances regarding performance (on CPU intensive stuff) and it's not much use for commercial apps or programs for which you don't want the source code *easily* read/decompiled. I guess the language is still evolving, so changes are inevitable...

Why is it every Python thread that comes up this tired, old and completely wrong canard comes out to play?  Go decompile EVE Online or tell me that it isn't a commercial, CPU intensive app.  I hate raising EVE Online as the response but until people get it through their heads that Python is not just some quaint little toy language that ain't up to the heavy lifting of the big boys there's little chance of that to percilate into other highly visible and visually stunning projects which can be used as an example.

> I keep looking at C because it never changes, but i always end up using Python again. :)

I keep looking at C and wondering why I need to spend a few hours building a decent data structure when I can use Python and just do it with 2 characters.  {}.  The machine have cycles to burn.  I, as a mere human, do not.

---

### Post by maximinus_uk on 2009-06-13
> **Greyed said:**
> 
I keep looking at C and wondering why I need to spend a few hours building a decent data structure when I can use Python and just do it with 2 characters.  {}.  The machine have cycles to burn.  I, as a mere human, do not.

I do the same, except, as an old Lisp programmer, my characters are [] ;)

---

### Post by Sinkingships7 on 2009-06-13
> **greyed said:**
> 
i keep looking at c and wondering why i need to spend a few hours building a decent data structure when i can use python and just do it with 2 characters.  {}.  The machine have cycles to burn.  I, as a mere human, do not.

*Slowly begins clapping*

---

### Post by soltanis on 2009-06-14
> **maximinus_uk said:**
> I do the same, except, as an old Lisp programmer, my characters are [] ;)

Damn, what epoch is your Lisp from, early '50s?

---

### Post by The-ITu on 2009-06-14
use eather 2.5 or 2.6.
don't use 3 coz it has different syntax.

---

### Post by openuniverse on 2009-12-06
.

---

### Post by Greyed on 2009-12-06
> **openuniverse said:**
> python is the new basic

Ouch, can't tell if you love or hate Python with that statement in your sig.  :-k

---

### Post by openuniverse on 2009-12-06
.

---

