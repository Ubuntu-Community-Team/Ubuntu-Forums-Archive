---
title: "Nano help"
date: 2013-09-19
forum: Programming Talk
---

### Post by twsLeGR on 2013-09-19
I have started learning Shell Scripting and so i also began using the Nano text editor. Now i know how to change the background and Foreground colours in nano so i made the background black and the foreground (text) white but when i want to edit a webpage, for example ~/football/lge-page.html the text appears in blue?

---

### Post by TheFu on 2013-09-19
Nano is an extremely basic editor.  I purge it from all my systems, so I can't look up the man page for it, which probably explains how to setup all the color options.

Not to start an editor war, but there are 20-200 other options.  Gedit, geany, are more like Notepad++ on Windows. As you learn those, you might want more power, like vim or emacs. If you have 16G of RAM and the fastest Core i7 CPU, then Eclipse might be a nice IDE (though mostly used by Android and Java devs).

An editor is a very personal decision. Others will be quick to offer their recommendations.  I can't think of any that do not support bash syntax highlighting at this point. Geany and vim are cross-platform - don't know about the others.

So, if I'm reading your question, you just want links to be a different color? Found this via google [https://github.com/aziz/dotfiles/blob/master/nano/bash.nanorc](https://github.com/aziz/dotfiles/blob/master/nano/bash.nanorc) - I probably asked a different question than you did. Anyway, it is full of examples.

---

### Post by twsLeGR on 2013-09-19
I am still at the beginning of my Programming adventure and is why i choose Nano. I hope given time that i may be knowledgable enough to upgrade to the likes of Emacs or Vi. Until then i shall stick with Nano. Thanks for the help. Cheers

---

### Post by Lars Noodén on 2013-09-19
nano is a convenient and easy to use editor.  It's a good choice but vi is on all systems so eventually you might want to look at that, too.  The documentation for  nano  is pretty good too.  The foreground and background colors are described in the documentation for the configuration file.

```

man nanorc

```

You can then set the colors there.  I didn't see any mention of setting alternate config files with runtime options though.

---

