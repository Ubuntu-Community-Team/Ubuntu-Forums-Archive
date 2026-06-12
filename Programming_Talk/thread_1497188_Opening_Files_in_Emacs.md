---
title: "Opening Files in Emacs"
date: 2010-05-30
forum: Programming Talk
---

### Post by andypi on 2010-05-30
I'm just getting used to emacs, and using it for all my programming/LaTeX.

I was wondering if there's an easy way to open a new file in a different buffer, but the same window. Like, from the eshell or something? All the stuff I've read about opening new buffers seems to only work for creating blank buffers, and whenever I try and open a new file from either the command line or the eshell I get a new emacs window, which results in loads of windows, which aren't as easy to switch between as multiple buffers in the same window.

Anyone know what I should be doing?

Andy

PS Sorry this isn't strictly a programming question. Please let me know if you think I should have posted it elsewhere.

---

### Post by Barrucadu on 2010-05-30
```
C-x C-f
Type path (tab completion works)
Press enter
```

You now have a new buffer with your file open.

---

### Post by andypi on 2010-05-30
Thanks!

I knew it would be something simple, I'm just not that proficient at finding the shortcuts I want yet.

---

### Post by diesch on 2010-05-30
I guess by "window" you mean what Emacs calls "frame", and by "buffer" what Emacs calls "window" :-)

In your shell set ALTERNATE_EDITOR="" and use ```
emacsclient -c some_file
``` to open *some_file* in a new frame, ```
emacsclient some_file
``` to open it in the current frame and ```
emacsclient -t some_file
``` to use a text mode emacs. 

This starts an Emacs server the first time you use it, and reuses this for every other call. You can kill this server by [I]M-x kill-emacs
[/I] from inside Emacs or by *emacsclient -e '(kill-emacs)'* from the command line.

To switch frames [framemove]("http://www.emacswiki.org/emacs-en/FrameMove") may help (but I prefer to use the window manager for this).

---

### Post by nvteighen on 2010-05-30
Er... isn't opening into a new window Emacs default behaivor? Then you just call the new window by using C-x b or C-x C-b...

---

### Post by andypi on 2010-05-30
Barrucadu's reply gives me the behaviour I was hoping for.

I've got used to switching between buffers using C-x C-<arrow>, but since the file I open is the one that's displayed when I've used C-x C-f, I only actually need to switch when I want to go back to what I was working on before.

I still find the buffer/window/frame nomenclature a bit confusing though!

---

