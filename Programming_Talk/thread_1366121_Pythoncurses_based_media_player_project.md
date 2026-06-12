---
title: "Python/curses based media player project"
date: 2009-12-28
forum: Programming Talk
---

### Post by OlyPerson on 2009-12-28
It's Christmas break which means lots of time and little to do.  I made a pretty spiffy temperature monitoring program and now want to move onto something a little more complex/useful.

I want to code a simple python/curses based media player and I already have a few questions:

[LIST=1]
[*]I cannot for the life of me figure out how to get audio stuff to work!  When I use pygames for audio, it works outside of curses but not in it, and I can't figure out how to install pymedia (pyaudio gives errors when I install).
So what do you suggest for audio playing?

[*]How would I ever approach having a list of music that includes all my music?  What I mean is like the sidebar in Exaile that has all your music and it's there every time you start the program.  Or is this much beyond the scope of a one person relatively beginner project?
[/LIST]

Thanks for any help!  I would think my first question would be easy to answer.

---

### Post by OlyPerson on 2009-12-28
Well I see no responses so maybe I'll expand the subject.

Help or advice on making any python based media player?  Anyone done this as a project or have any recommendations on what I should use (eg pygame)?

---

### Post by kostkon on 2009-12-28
Use Gstreamer? (i.e. *python-gst* for the Gstreamer Python bindings)

---

