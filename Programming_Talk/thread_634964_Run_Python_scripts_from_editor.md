---
title: "Run Python scripts from editor?"
date: 2007-12-08
forum: Programming Talk
---

### Post by ThinkBuntu on 2007-12-08
In TextMate, the shortcut Command + R when in Python mode runs the script in a window called PyMate. It doesn't show any sort of return values as would and IDLE prompt, but is very complete and useful based on my limited experience.

**My question:** Can GEdit, Emacs, Eclipse, or Vim do this (or other editor)? Ideally, it would work just like this: A window opens, runs the script, and closing this window takes you right back to the editor.

---

### Post by xtacocorex on 2007-12-08
There is a plugin for GEdit: [http://live.gnome.org/Gedit/Plugins](http://live.gnome.org/Gedit/Plugins)

---

### Post by ThinkBuntu on 2007-12-08
Have you used the Run In Python plugin? Any surprises? Just curiosity, as I'm on a Mac (Gedit is the only editor I listed that I can't take advantage of, although I doubt it has anything that TextMate lacks, as opposed to Emacs and Vim).

---

### Post by LaRoza on 2007-12-08
Vim has the :sh command, which brings you to a shell. exit gets you back to Vim.

There is probably more, but I never explored it.

---

### Post by tyoc on 2007-12-08
mm, that dont work??, at less for me only work without the "command"

> 
$ vi [enter]
:!python[enter]


that is something like exec... I mean, if you do :!ls you will not see the colours, because normally the shell pass an extra arg for say to ls to output colors. doing :!ls only print the list without colors (because there is no shell).

---

### Post by xtacocorex on 2007-12-08
> **ThinkBuntu said:**
> Have you used the Run In Python plugin? Any surprises? Just curiosity, as I'm on a Mac (Gedit is the only editor I listed that I can't take advantage of, although I doubt it has anything that TextMate lacks, as opposed to Emacs and Vim).
I do am on a Mac and I do all my Python from the terminal window and occasionally IDLE.  I do all my visual editing in Smultron and for quick changes in the terminal, VI.
Smultron does have the ability to run external commands: [http://smultron.sourceforge.net/features.html](http://smultron.sourceforge.net/features.html) (It's also a free program)

---

### Post by LaRoza on 2007-12-08
> **tyoc said:**
> mm, that dont work??, at less for me only work without the "command"



that is something like exec... I mean, if you do :!ls you will not see the colours, because normally the shell pass an extra arg for say to ls to output colors. doing :!ls only print the list without colors (because there is no shell).

You have to specify the script name, to run the script.

```

:!python p.py

```

---

### Post by engla on 2007-12-08
Use % with vim if you want to run the current file. Try and see what "!echo %" outputs
```
!python %
```

It's completely unrelated to editors, but [reinteract]("http://fishsoup.net/software/reinteract/") is a cool way to try out python snippets -- useful for those who experiment with typing in class defs or functions defs in the prompt normally

Edit:
I found out how to map that to a key sequence:
```
:map <F2> :!python %<cr>
```
(everything should written literally - <cr> means that the newline is part of the command, else you will have to type F2 then return to run it)

---

### Post by wolfbone on 2007-12-08
[QUOTE=ThinkBuntu]Can GEdit, Emacs, Eclipse, or Vim do this (or other editor)? Ideally, it would work just like this: A window opens, runs the script, and closing this window takes you right back to the editor.[/QUOTE]

Yes - but in Emacs, you don't open and close windows like that exactly. Emacs initially opens in what it calls a "frame" which you can then subdivide into as many independent subwindows as you like. Typically you'll be editing your Python code "buffer" in one window (which may be the whole frame) and then when you type 'C-M-x', the definition or whatever "at point" gets sent to the interpreter. The interpreter will be running in another buffer and whether it's in a whole new frame or in an already visible subwindow (or a non-visible buffer you need to switch in to a window), is entirely up to you.

---

### Post by pmasiar on 2007-12-08
IDLE (default Python IDE) lets you run current source by hitting F5.

---

### Post by ssam on 2007-12-08
geany is a good editor for python. it can run the script you are working on

---

