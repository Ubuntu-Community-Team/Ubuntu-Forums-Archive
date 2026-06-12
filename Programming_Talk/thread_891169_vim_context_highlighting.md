---
title: "vim context highlighting"
date: 2008-08-15
forum: Programming Talk
---

### Post by Tyke91 on 2008-08-15
I'm doing a directed study course in high school where my friend and I have to teach ourselves some C++ programming. Everything's going very well, but I'd like to use a real text editor (one with advanced commands that I can use later on to make programming more efficient). I've settled on vim (please don't turn this into a vi vs emacs flamefest :( ).

The one thing that I'm missing in vim is context highlighting (similar to what gedit has) is there a way I can get this in vim?

---

### Post by ConMan318 on 2008-08-15
If you add the line "syntax on" to your vimrc, it will turn on highlighting for any file with a programming language's extension.

This is my vimrc (minus the stuff after the # signs):
```

syntax on      # turns on programming highlighting
set number      # turns on line numbering
set tabstop=4      # sets tab stop to 4 spaces rather than the default 8
set shiftwidth=4      # controls indentation
set expandtab      # inserts 4 spaces for a tab rather than a tab block
set softtabstop=4    # allows backspace to recognize the tabs being spaces
colorscheme darkblue      # my fav color scheme (for gvim at least) :p

```

This works very well for my programming needs.

Just save any settings you want to be applied every time you start vim to
```

~/.vimrc

```

You will have to make the file, but after making it vim will automatically get your settings from it.

---

### Post by dwhitney67 on 2008-08-15
Edit/create a file in your home directory called .vimrc, and insert the following statement into it:
```
syntax on
```
Then save the file, and try vim again.

P.S.  I believe Ubuntu still ships with a less-than-worthy vim editor.  If you have not done it already, you may have to install the "full" vim (via synaptic or other means) to get syntax highlighting.

---

### Post by LaRoza on 2008-08-15
vim-tiny, the default Ubuntu and Debian package doesn't do syntax highlighting.

Run this command:

```

sudo aptitude install vim

```

Here is my .vimrc:
```

set showmatch
set expandtab
set tabstop=4
set shiftwidth=4
set nocompatible
set number
syntax on

```

---

### Post by mssever on 2008-08-15
Three other options I find useful, in addition to what's already been mentioned:
```
set mouse=a
set set scrolloff=5
set hlsearch
```mouse=a makes it possible to use the mouse in vim. Sometimes that's handy, especially if you use a ThinkPad like I do where you can use the trackpoint without moving your hand off the keyboard.

scrolloff is also essential, IMHO, because it's annoying to have the cursor at the bottom of the screen without being able to see the full context.

---

### Post by Tyke91 on 2008-08-16
Thank you everybody for your help :guitar:

---

