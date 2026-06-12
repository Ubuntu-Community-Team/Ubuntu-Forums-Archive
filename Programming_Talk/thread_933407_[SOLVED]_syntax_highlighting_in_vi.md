---
title: "[SOLVED] syntax highlighting in vi"
date: 2008-09-29
forum: Programming Talk
---

### Post by kcode on 2008-09-29
To enable syntax highlighting in vi i typed 
syntax enable as command. But it is not permanently enabling highlighting. How to permanently achieve this.

thanks

---

### Post by LaRoza on 2008-09-29
Debian/Ubuntu comes with "vim-tiny", you want "vim" (vim-full has a lot of extra junk, only install if you want gvim).

```

sudo aptitude install vim

```

It will probably have syntax highlighting by default and detect files, however, if you need more help after, let me know.

---

### Post by rnodal on 2008-09-29
Anything that you want to be on or off when you run vim should be placed in your .vimrc file under your home directory.

-r

---

### Post by kcode on 2008-09-29
laroza:

i am using vim only. But it is not providing me with permanent syntax highlighting, only temporarily.

rnodal:

i cannot find .vimrc in ~. Even locate .vimrc didnt show up anything.

---

### Post by Kadrus on 2008-09-29
you can try:
:so $VIMRUNTIME/syntax/language.vim

---

### Post by LaRoza on 2008-09-29
> **kcode said:**
> laroza:

i am using vim only. But it is not providing me with permanent syntax highlighting, only temporarily.

rnodal:

i cannot find .vimrc in ~. Even locate .vimrc didnt show up anything.

You know vim, obviously?

```

touch .vimrc
vim .vimrc

```

Here's mine, you want the last one, but the others may be of interest:

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

### Post by rnodal on 2008-09-29
LaRoza has the answer for you. :D

-r

---

### Post by kcode on 2008-09-29
> **Kadrus said:**
> you can try:
:so $VIMRUNTIME/syntax/language.vim

on this command i'm getting(also tried it with root):
cant open file language.vim

LaRoza:

got .vimrc (empty), && added your settings.
with success.

thanks all.

---

### Post by LaRoza on 2008-09-29
> **kcode said:**
> on this command i'm getting(also tried it with root):
cant open file language.vim

LaRoza:

got .vimrc (empty), && added your settings.
with success.

thanks all.

In case you don't know:

set showmatch == Highlight matching braces
set expandtab == Uses spaces when you press the tab key
set tabstop=4 == Sets tab to four spaces (the above command turns them into actual spaces)
set shiftwidth=4 == Not really sure, but I knew at the time :-)
set nocompatible == Vi incompatible, Vim features enabled
set number == Line numbers
syntax on == Obvious

---

### Post by Kadrus on 2008-09-29
You type this command in Vi,where language.vim is the language you wish to highlight.

---

