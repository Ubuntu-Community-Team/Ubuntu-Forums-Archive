---
title: "game language"
date: 2008-01-24
forum: Programming Talk
---

### Post by pavel989 on 2008-01-24
hey everyone. after long hours of research, i have a few questions.

unfortunately, ruby, my favorite language (bc of syntax) isn't that famous in the game world so i decided not to go with it. secondly, i've moved onto python for distributed programming since ruby needs an interpreter. but from what i understand, the industry is ruled by directx and opengl, c++ and java. 

ive considered learning either or, but that doesn't sound too efficient. and ive seen some awesome games written with python. so like, if i use a binding (methinks thats what its called) for python to have cpp stuff(¿), would it be still like fully functional and efficient. ive been reading that java's garbage collection is apparently slow????? but its cross platform bc of jvm. cpp is crazy but difficult to lean.

can python be cross platform? are there java bindings? are bindings good? i wanna start devel'ing games for linux, but ti would be awesome if i start making mmorpg's for xp and mac to be able to use. but thats not really important. its mostly, how can I make pretty 3d games that run fast and not too difficult to make?

I'd want any input.

---

### Post by LaRoza on 2008-01-24
> **pavel989 said:**
> 
can python be cross platform? are there java bindings? are bindings good? i wanna start devel'ing games for linux, but ti would be awesome if i start making mmorpg's for xp and mac to be able to use. but thats not really important. its mostly, how can I make pretty 3d games that run fast and not too difficult to make?

I'd want any input.

PyGame, and there are game engines for Python, which work in any OS. Look into Jython.

Try some of the game engines available, and look into PyGame.

---

### Post by c174 on 2008-01-24
Python is designed to integrate C++ code easily. So "yes" to Python is not "no" to C++ or the many different packages written in C++. In fact a lot of stuff available in Python is wrapped code from other languages.

---

### Post by pmasiar on 2008-01-24
> **pavel989 said:**
>  if i use a binding (methinks thats what its called) for python to have cpp stuff(¿), would it be still like fully functional and efficient.

Python links to C libraries nicely and is cross-platform.

> ive been reading that java's garbage collection is apparently slow????? but its cross platform bc of jvm.

It is not slow, but might decide to go GC when it is not convenient for you (deep in some interaction) and it is out of your control. This is why C or C++ is used: it is harder, but you are in the control where GC happens. Python has reference-counted GC, so it kinda happens all the time, in small increments, so you will not notice.

> cpp is crazy but difficult to lean.

With great power comes great responsibility :-)

> can python be cross platform?

yes, very.

> are there java bindings? are bindings good? 

Python for JVM is called Jython. Was neglected by Sun for 10 years, but recently (when MSFT hired main Jython developer for IronPython.NET) was revived. Jython 2.2 was released last year (2007), 2.5 is due this year.

> start making mmorpg's for xp and mac 

[MMORPG are big projects](http://www.devmaster.net/articles/building-mmorpg/) (10 man-years for a team), I would strongly recommend trying something simpler first. See wiki in my sig for training tasks. [alone is possible for expert](http://www.rampantgames.com/blog/2006/11/how-to-develop-mmorpg-with-no-team-and.html)

> its mostly, how can I make pretty 3d games that run fast and not too difficult to make?

You have your priorities backwards. Your first priority should be: how long it will take you to write something usable. If it will require decent PC and will not run on old slow PC, too bad, you can improve it later. BTW, you can rewrite any part of Python in C and link it as library - but only AFTER you profiled and measured that you need it :-)

Pygame is considered good game library, there are many more.

Edit:

And you want to read [So you want to make your own MMORPG..](http://sol.gfxile.net/mmorpg.html) and thread about [Writing a game engine](http://ubuntuforums.org/showthread.php?t=674173)

Maybe this should be added to new FAQ? LaRoza, wanna write it up?

---

### Post by slavik on 2008-01-24
as far as I know, Ruby has bindings to SDL and OpenGL and that is all you need in order to start writing a game.

Python also needs an interpreter.

Ruby, Python and Perl all get compiled to bytecode for their respective virtual machines before being executed, so the interpretation does not happen during run time. :)

---

### Post by pavel989 on 2008-01-24
well i know full well that i wont be able to write an mmorpg. but im just setting it an extreme.

slavik: yes however python is much more wdily used than ruby.

---

### Post by slavik on 2008-01-24
> **pavel989 said:**
> well i know full well that i wont be able to write an mmorpg. but im just setting it an extreme.

slavik: yes however python is much more wdily used than ruby.
just because a language is more widely used doesn't mean that it is somehow better. might as well use Windows since it is more widely used :-\ (not knocking Python, just saying)

---

### Post by LaRoza on 2008-01-24
> **slavik said:**
> just because a language is more widely used doesn't mean that it is somehow better. might as well use Windows since it is more widely used :-\ (not knocking Python, just saying)

Actually, a language needs users to be good. Turing looked like a good language, but I never met a programmer who used it.

---

### Post by pavel989 on 2008-01-24
not knocking anything. i mean its just like if you look at it. since im learning, im more likely to get more support with python rather then ruby since there are more ppl using it.

---

### Post by slavik on 2008-01-24
agreed. If you ever happen to look into perl, check out perlmonks.com :)

@LaRoza, yes, but can python do things like: 5.times print "hello"; ? (would be fun if Perl could do this)

---

### Post by LaRoza on 2008-01-24
> **slavik said:**
> 
@LaRoza, yes, but can python do things like: 5.times print "hello"; ? (would be fun if Perl could do this)

No, Python can't do that.

---

### Post by pavel989 on 2008-01-24
print "hello"*5

---

### Post by pmasiar on 2008-01-25
> **slavik said:**
>  can python do things like: 5.times print "hello"; ? 

print 'hello' * 5

Edit: OOps, Pavel beat me.

---

### Post by LaRoza on 2008-01-25
> **pmasiar said:**
> print 'hello' * 5

Edit: OOps, Pavel beat me.

By an hour...

(I know, you probably didn't see this page. Happens to me all the time)

---

