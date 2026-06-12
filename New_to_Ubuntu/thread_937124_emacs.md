---
title: "emacs"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by paper_bridge on 2008-10-03
I do most of my text editing in emacs. I am very fond of the Carbon emacs package that I have on the Mac that I use at home. In particular, I like that when I am editing a file with a ".tex" extension, it recognizes this, and color codes the various commands, etc. I am running Ubuntu on my machine at work, and the basic version of emacs21 isn't sensitive to any of these details. Is there a package for Ubuntu that will allow me to change the displayed text in a way that is sensitive to LaTeX commands?

Thanks.

---

### Post by bhadotia on 2008-10-03
Never used emacs but a suggestion :You try searching synaptic (System>Administration>Synaptic Package Manager). Press ctrl+f and start typing what you are searching for. You can also try to see if there are any packages available on the net (e.g. [look hare]("http://packages.ubuntu.com/")).

---

### Post by osx424242 on 2008-10-03
It should just be a setting within emacs (i.e. not anything Ubuntu-specific). Try playing around with the Options?  Maybe make sure Syntax Highlighting is turned on?  Look at this page, maybe, too: [http://www.stat.umn.edu/~charlie/fl.html](http://www.stat.umn.edu/~charlie/fl.html).  Sorry I'm not of more help :(

---

### Post by jamesrl on 2008-10-03
I run emacs in linux and it has a LaTeX environment that was loaded by default (see screenshot).  The emacs packages I have installed are (dpkg -l *emacs* | grep ii): 

```

ii  emacs-snapshot                             1:20080504-1~hardy                                   The GNU Emacs editor (development snapshot)
ii  emacs-snapshot-bin-common                  1:20080504-1~hardy                                   The GNU Emacs editor's shared, architecture 
ii  emacs-snapshot-common                      1:20080504-1~hardy                                   The GNU Emacs editor's common infrastructure
ii  emacs-snapshot-el                          1:20080504-1~hardy                                   GNU Emacs LISP (.el) files[ATTACH]87184[/ATTACH]
ii  emacsen-common                             1.4.17                                               Common facilities for all emacsen
ii  xemacs21                                   21.4.21-1ubuntu3.1                                   highly customizable text editor
ii  xemacs21-basesupport                       2007.04.27-1                                         Editor and kitchen sink -- compiled elisp su
ii  xemacs21-bin                               21.4.21-1ubuntu3.1                                   highly customizable text editor -- support b
ii  xemacs21-mule                              21.4.21-1ubuntu3.1                                   highly customizable text editor -- Mule bina
ii  xemacs21-mulesupport                       2007.04.27-1                                         Editor and kitchen sink -- Mule elisp suppor
ii  xemacs21-support                           21.4.21-1ubuntu3.1                                   highly customizable text editor -- architect

```

I do use emacs-snapshot (add to /etc/apt/sources.list):
```

deb     http://ppa.launchpad.net/avassalotti/ubuntu hardy main
deb-src http://ppa.launchpad.net/avassalotti/ubuntu hardy main

``` as it allows prettier fonts in emacs if you add 
```

(if (>= emacs-major-version 23)
    (set-default-font "Monospace-9"))

``` to your .emacs file.  However, I would guess either emacsen-common or xemacs21-mule or mulesupport contains the package for LaTeX recognition.

However, personally I find its easier to TeX a document up in a LaTeX environment like kile.

---

