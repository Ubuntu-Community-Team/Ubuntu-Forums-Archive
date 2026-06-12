---
title: "C/C++ IDE for large projects ?"
date: 2008-02-03
forum: Programming Talk
---

### Post by norapinephrine on 2008-02-03
Can anyone recommend an IDE for developing large C/C++ programs ?  I would prefer one that has VI extensions, but it's more important 
that the IDE can build large projects.  Which C/C++ IDE's are  popular
for large projects ?
Thanks!

---

### Post by LaRoza on 2008-02-03
See the IDE thread, links in the stickies.

Any editor / IDE can be used for large projects. If it is a large project, I guess you should use what is standard for the members of that project.

---

### Post by neonum6 on 2008-02-03
you could try Eclipse C/C++ Development Tooling and use Eclipse! 
Eclipse is the most important ide for linux OS

---

### Post by raul_ on 2008-02-03
I guess Eclipse or Geany. Eclipse has the advantage of having good integration with CVS and SVN.

---

### Post by neonum6 on 2008-02-03
I don't know Geany...but with Eclipse i'm feeling fine

---

### Post by bobrocks on 2008-02-03
Eclipse CDT with the viPlugin, sadly that vi plugin is not free cost about 10 pound ([http://www.satokar.com/viplugin/](http://www.satokar.com/viplugin/)) has a few issues but the guy does fix them if you raise the bugs.  I use it full time at work with eclipse java prespective.

Can't live without my vi

---

### Post by thornmastr on 2008-02-04
Have you looked at NetBeans IDE 6.0.

---

### Post by lnostdal on 2008-02-04
nono, in the open source world projects are not bound to any particular IDE in the way you might be thinking

building and editing is not tightly bound together by ways of automatically generated "project files" (usually gruesome, huge, bugprone and unmaintainable things) that only work with that particular editor

people use whatever editor they prefer and configure them until they become their IDE by ways of shortcut keys and scripts that execute the building process automatically, compiles, executes the debugger .. or whatever

..i use emacs .. some use vi .. others use other editors -- it doesn't matter, in this world

for building we use portable tools that are not hard coded or integrated into (only one) editor or environment .. take a look at cmake or scons .. they are great and trivial to use from any decent editor

edit:
there are of course exceptions, and many projects out there .. but imho the ones who follow a approach similar to Visual Studio etc are short sighted -- do you really expect others to use the exact same setup and environment you are using? .. doesn't sound very user friendly and "open source"'ish to me .. or, hm, maybe i should start forcing emacs and elisp (elisp scripts could handle the building etc.) down peoples throats  :)

---

### Post by etdsbastar on 2011-02-20
Eclipse is a good startup for large projects...

---

