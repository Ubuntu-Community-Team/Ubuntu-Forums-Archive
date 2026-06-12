---
title: "Seeking a text editor..."
date: 2007-09-14
forum: Programming Talk
---

### Post by Vadi on 2007-09-14
... that can search with regex, indent C/C++ code nicely, find matching brackets, highlight C/C++ and XML code, can have multiple files open at once, and do macros.

Anyone know any?

Thinking of switching from Notepad++. It's a great open-source app, albeit _very_ heavily coded for windows, and it's developer doesn't want want to port it. There's a whole bunch of people like me who want it on Linux, but nobody really knows how to port it properly.

Npp has a ton of features, but I just need these. Could anyone recommend a text editor?

(Notepad++ is derives from Scintilla, or the Scite, and I tried it - but it doesn't have all of the functions :/)

Edit: Oh and it works okay in Wine, but I'm hoping for a native alternative.

---

### Post by vambo on 2007-09-14
In a word   emacs

---

### Post by Vadi on 2007-09-14
Okay, it can search regex, I couldn't find the indenting option (and I can't read the manual for some reason), it can match brackets, ... and I can't seem to open a file in it. At the bottom it's just stuck at the /tmp directory :|.

---

### Post by vambo on 2007-09-14
Have a look at this - [http://www.lepp.cornell.edu/~bxin/computer/emacs/emacs24/index.htm]("http://www.lepp.cornell.edu/~bxin/computer/emacs/emacs24/index.htm")

Also, once it's up and running look through the help and tutorial pages

---

### Post by tpg on 2007-09-14
Also consider VIM - it is a very nice text editor with lots more features than you'll ever need - albeit command-line oriented with a rather steep learning curve. Otherwise, I'd recommend KATE (K Advanced Text Editor) from KDE.

---

### Post by psusi on 2007-09-14
Emacs has more features than you can throw a kitchen sink at, and you can easily add more because it is mostly written in a dialect of lisp.  You can throw it a quick lisp expression if you want to perform almost any kind of text editing you can imagine, but unless you need intelligent things like automatic re sequencing of numbers found in the text, it's often easier just to use the find and replace with regular expressions function ( ctrl-alt-% ).  

It takes a good deal of time to learn, but if you do much text editing, it is well worth it.  Start with the tutorial ( ctrl-h t ) and then try to spend a little time each day reading the info page ( ctrl-h i ).

---

### Post by Vadi on 2007-09-14
Okay, thanks for the input people.

---

### Post by std on 2007-09-14
At first sight I'd recommend emacs too (I've been using it happily for a few years now), but you're reading the post of someone who has ran UltraEdit with wine during his early Linux days.

I've had a quick (and fun) experience with a small GTK-based editor called Tea, but I don't know if it has the features you mentioned (although as far as I remember, it does).

Jedit may also be able to do what you are after (again, I can't tell for sure, since I haven't bothered trying to search for an alternative to emacs).

Bottom-line though (and although it's a personal preference), I'd recommend emacs, if you can refrain from smashing keyboards and punching monitors in the first few days.

---

