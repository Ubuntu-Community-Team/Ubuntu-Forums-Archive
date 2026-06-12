---
title: "Project to make common emacs keys work in everything using global key hooking"
date: 2009-07-21
forum: Programming Talk
---

### Post by Azim.Palmer on 2009-07-21
Hi,

Bit of background, I'm a student programmer who's happily making the switch from Windows to the Linux world ^_^

One thing I've found straight away is that (after a period of adjustment) I find a number of the emacs shortcuts really useful, at the moment it's mainly simple text manipulation things such as ctrl a (move to start of line), ctrl n (move to next line) etc.

What I'd really like to do is have a small app that I can configure to globally hook a list of key combinations, when one is pressed "eat it" so the window it should be sent to never sees it but instead sees a key that would produce the same behaviour, for example if I press "ctrl a" it sends "home".

This could later be extended to support macros and custom actions depending on what application is in focus, but at first I want to get a basic version up and running.

Problem is, despite being a "not too terrible" programmer I'm very new to linux development. While this is something I could whip up in an evening on windows I have no idea where to start on Linux. I've been looking at a few keyloggers in python and c, but they don't seem to be extendable to support keybinding, for example they sniff an input log, which (it seems) is too late to re-map anything.

I wanted this to be my first project to help me get to grips with Linux dev and finding stuff out on my own but everything feels so fragmented and my google-fu is failing me. This is a humble request for help, oh and if I get it working I promise to open source it !

Thanks,
Az

---

### Post by Dejai on 2009-07-21
Knowi9ng Emacs its probably already been done but your probably using Gnome so start by googling GTK.

---

### Post by soltanis on 2009-07-21
There already exists a project for capturing keystrokes sent in the X windowing environment. I use it for setting volume up/down/mute, locking my screen, blanking my screen, and reading out the time/date to me with espeak.

It's called xbindkeys.

You can probably adapt this (it understands multi-key combinations) to produce the effect you desired, although some things (like changing the keystroke sent to a program) you might need to go write yourself.

This looks like mostly an X11 job, though, so I would start at those docs.

---

