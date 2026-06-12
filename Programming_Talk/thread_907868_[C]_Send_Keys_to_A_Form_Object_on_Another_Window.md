---
title: "[C] Send Keys to A Form Object on Another Window"
date: 2008-09-01
forum: Programming Talk
---

### Post by loganwm on 2008-09-01
In my quest to "automate" my redundant tasks through my knowledge of C, I was wondering if there's a method to "send" keystrokes to a form object in a separate window.

Here's the setup:
I want to automatically send a sequence of keys or a full string to another application that's running, most likely into a text box on a form, but possibly into another location.

Is there a way to do this and if so, what are the prerequisites (such as Xlib, GTK, KDE, etc)

I'm in C, and I would PREFER to stay in C, but if I had to move into C++, I suppose I could.

---

### Post by CptPicard on 2008-09-02
That's a fairly complex piece of inter-process communication you're looking at there, and the receiving application would have to be coded for it.

There's no general way to do it, but specific desktop environments have their own mechanisms to communicate to running applications, for example KDE has DCOP, which is a means of sending messages to apps from all kinds of languages -- it's a particularly powerful mechanism if you're automating stuff from a higher-level language such as Python.

---

### Post by mssever on 2008-09-02
When I was a kid, my family had a Mac running System 7.1 (1992-era OS). I found a program at some point--likely a number of years later--that would allow you to type abbreviations into any text field (even in modal dialogs which in System 7.1 were globally modal) and hit an expansion key such as tab, and it would replace that abbreviation with whatever text had been pre-defined. Are you saying that something like that isn't possible in X?

I have very little experience with GUI programming, but it wouldn't surprise me if this was impossible in a cross-toolkit manner, unless you could do it with raw Xlib calls.

---

