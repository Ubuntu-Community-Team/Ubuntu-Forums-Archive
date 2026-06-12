---
title: "emacs help"
date: 2008-03-20
forum: Programming Talk
---

### Post by jamescowie on 2008-03-20
Hi all,

ive got emacs installed on my ubuntu box, but when i type emacs or try to open any file with emacs it opens the gnu version. i can open the bash version using emacs -nw but this is just a pain.

is there a conf file anywhere to change this to the default?

thanks

j.

---

### Post by CptPicard on 2008-03-20
I suppose you mean you want the non-X11 text mode version? :) They're both "GNU" software... put 

```

alias emacs='emacs -nw'

```

in your .bashrc

---

### Post by jamescowie on 2008-03-20
still no joy, i added the line you said into the /home/james/.bash file and emacs still loads the gui version?

thanks for  the help.

---

### Post by ha1f on 2008-03-20
> **jamescowie said:**
> still no joy, i added the line you said into the **/home/james/.bash** file and emacs still loads the gui version?

thanks for  the help.

$HOME/.bash**rc** ...?

---

### Post by jamescowie on 2008-03-20
hi sorry type home/james/.bashrc

any sugestions.

---

### Post by ha1f on 2008-03-20
have you source'd it?

---

### Post by CptPicard on 2008-03-20
Well.. it should work... open up a new window to make sure you run a new shell that has loaded its settings from the edited file?

---

### Post by ha1f on 2008-03-20
Also, if you're trying to open files from nautilus, you'll need to make sure that nautilus knows to use emacs -nw

---

### Post by Lux Perpetua on 2008-03-21
> **jamescowie said:**
> Hi all,

ive got emacs installed on my ubuntu box, but when i type emacs or try to open any file with emacs it opens the gnu version. i can open the bash version using emacs -nw but this is just a pain.

is there a conf file anywhere to change this to the default?

thanks

j.If you don't ever use the X11 version of Emacs, you can uninstall it. The curses version of Emacs is in the package emacs-nox, which is all you would need (+ emacsen-common and other dependencies).

---

