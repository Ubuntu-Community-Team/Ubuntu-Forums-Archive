---
title: "colour coded vim"
date: 2007-04-19
forum: Programming Talk
---

### Post by Ne0z on 2007-04-19
hi, 

i was wondering how u get a colour coded vim in ubuntu ?

its like "vim file.c" and it opens up and everything is colour coded. 

thanks !

---

### Post by bihe on 2007-04-19
:syn on

---

### Post by Ne0z on 2007-04-19
hmm i tried doing ":syn on" in vim . it says 
"Sorry, the command is not available in this version :(

---

### Post by Jucato on 2007-04-19
You have to install vim-full to get syntax highlighting

---

### Post by wdk on 2007-04-19
If you don't already have a .vimrc in your home directory, create one and add the line

:syntax enable

if you don't like the default colors, you can select a different color scheme using:

:colorscheme NameOfColorScheme

You should be able to find a list of available schemes in /usr/share/vim/vimcurrent/colors/ (at least that's where they are on my setup--Ubuntu Edgy). You can also edit those files and create your own custom color scheme.

happy hacking!

---

### Post by timondy on 2008-03-17
> **bihe said:**
> :syn on

much appreciate  but seems i hv to type :syn on each time vim is opened

---

### Post by LaRoza on 2008-03-17
You have to install vim-full on Ubuntu for that. (vim-tiny is there)

```

sudo aptitude install vim-full

```

---

### Post by mssever on 2008-03-17
> **timondy said:**
> much appreciate  but seems i hv to type :syn on each time vim is opened

Put this in your ~/.vimrc:
```
syntax on
```

---

### Post by RedSquirrel on 2008-03-19
> **Jucato said:**
> You have to install vim-full to get syntax highlighting

> **LaRoza said:**
> You have to install vim-full on Ubuntu for that. (vim-tiny is there)

```

sudo aptitude install vim-full

```

Other options include:

```
sudo aptitude install vim
```or for gvim (with a GTK+ gui):

```
sudo aptitude install vim-gtk
```The "vim-full" package pulls in a number of GNOME libraries, which may or may not be desirable. ;)

---

