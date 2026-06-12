---
title: "Colour highlighting problem in Vim for c++ programs in Ubuntu 8.10 version"
date: 2008-12-01
forum: Programming Talk
---

### Post by praveen_frakes on 2008-12-01
Hi,
   I am using latest release Ubuntu 8.10 version. I am satisfied with all new features :) . But , in programming i want color highlighting in vim , to practice c++ programs and shell programs :confused: My exams are near ! :( anyone help me please... [-o< :cry:

---

### Post by hessiess on 2008-12-01
In the GUI version you can go:

syntax-> show file types in menu.
syntax-> C -> C++

(if it still dosent work)
syntax -> on/off for this file.

---

### Post by dwhitney67 on 2008-12-01
OP, if you haven't sorted out the colour issue with vim, it is possible that you need to install the full-version of vim, not the "half-full"-version that is provided on the Ubuntu installation CD.

It's been awhile since I installed vim-full, but I believe that is the correct package name.  Thus...
```

sudo apt-get install vim-full

```

P.S.  In the file ~/.vimrc, you should insert the following statement
```

syntax on

```

---

### Post by Sydius on 2008-12-01
And if it's a new file, typing ":set filetype=cpp" might help.

---

### Post by samjh on 2008-12-01
> **dwhitney67 said:**
> OP, if you haven't sorted out the colour issue with vim, it is possible that you need to install the full-version of vim, not the "half-full"-version that is provided on the Ubuntu installation CD.

The default vim in Ubuntu/Debian is not even "half-full", it's "minimal".

I prefer to sudo apt-get install vim, which installs the full-featured command-line vim (unlike vim-full, which also installs gvim).

Then create a .vimrc file in ~/, and put:
```
:set nu
:set ts=4
:set sw=4
:syntax on
:filetype plugin indent on
```
nu = line numbers on
ts = number of spaces for tabs
sw = amount of indentation for indents
syntax on = turn on syntax highlighting
filetype plugin indent on = enable plugins and indentation schemes by file type

:)

---

