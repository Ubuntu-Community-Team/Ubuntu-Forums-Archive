---
title: "help customizing emacs"
date: 2008-07-05
forum: Programming Talk
---

### Post by japhyr on 2008-07-05
I am just getting started using emacs.  I installed version 22 through Synaptic.  I want to have line numbers displayed, and I hope by getting this to work I will understand better how to continue customizing emacs.

I copied [linum.el]("http://stud4.tuwien.ac.at/~e0225855/linum/linum.el") to a folder in my home directory, /home/username/Emacs Customizations, and saved it through gedit as "linum.el".

There was no .emacs file that I could find, so I created a file called .emacs in my /home/username directory.  This file now reads:
```
(add-to-list 'load-path "/home/username/Emacs Customizations/")
(require 'linum)
(global-linum-mode 1)
```

Now when I open a file in emacs, I do not see any line numbers.  When I type M-x linum-mode, it says [No match].  If it matters, I am using php-mode and looking at an index.php file.  Also, when emacs first starts, I see a page with information about attempts to load something, but it is replaced by a splash screen too quickly to read what it says.  Any thoughts?

---

### Post by shifty2 on 2008-07-05
You are going to have to "escape" the space in Emacs Customization. Instead of
```
(add-to-list 'load-path "/home/username/Emacs Customizations/")

```

have

```
(add-to-list 'load-path "/home/username/Emacs\ Customization/"
```

I think thats your problem anyway. 

As a side note the convention is to store your extensions in an "elisp" directory ie ~/elisp, and you will see most tutorials refer to this instead of ~/Emacs Customization as you have.

EDIT:
The messages you say that flash up before the splash screen can be found in the "messages" buffer - C-x right/left a few times to find it.

Finally welcome to emacs, you won't go back :)

---

### Post by japhyr on 2008-07-06
Thank you very much, I had missed a directory in the path as well as not escaping the space in the filename.  I made an elisp folder as you suggested, and I was also able to see the error screen as you described.  Line numbers are displaying, and programming is fun again!

---

