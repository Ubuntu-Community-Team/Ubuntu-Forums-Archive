---
title: "Emacs wouldn't display special characters"
date: 2006-11-04
forum: Programming Talk
---

### Post by derwisch on 2006-11-04
I have the following packages installed: 
Package: emacs21-bin-common
Package: emacs-goodies-el
Package: emacsen-common
Package: emacs21
Package: emacs21-common

When using emacs, umlauts and other characters are not properly 
displayed. When I use emacs with X, they are displayed in a 
smaller (= barely recognizable) size. When my wife uses emacs,
they are displayed as empty rectangles. They are saved as 
umlauts all right, only the optical represenation is inappropriate.

When I use emacs in the shell (tested with gnome-terminal and
xterm, the keystrokes are not mapped as expected. For example,
pressing the ü key leads to the execution of 
shell-command-on-region.

Does anybody have a hint how to amend this behavior? 
Hiding .emacs does not help.

Greetings


Johannes

---

### Post by shining on 2006-11-04
Maybe you need to use a font that support these characters.

---

### Post by derwisch on 2006-11-05
> **shining said:**
> Maybe you need to use a font that support these characters.

My .Xresources file contains the entry "emacs.Font  : fixed".
When I inspect the font with xfontsel, it displays the 
characters with diacritical marks I am looking for in the
appropriate size.

My wife has nothing regarding emacs in her .Xresources file.

Neither of our .Xdefaults files contains an entry on Emacs.

---

### Post by toojays on 2006-11-05
I'm not sure about the keyboard mapping issue, but it's possible it's related to a combination of your LANG and TERM environment variables.

On the font issue, try installing the package xfonts-intl-european. Also, maybe try using emacs-snapshot instead of emacs21. The emacs-snapshot package is an out of date snapshot of emacs 22, but it is still much newer than emacs21.

---

### Post by derwisch on 2006-11-07
Thanks for directing me to emacs-snapshot. I'd love to 
have it installed, yet Ubuntu uninstalls all packages
related to openoffice.org version 2 whenever I try to
install emacs-snapshot.

I already thought about it being an issue of installed
fonts, and will try to install the related X fonts.

---

### Post by derwisch on 2006-11-07
yep, package xfonts-intl-european was missing. Many thanks!

(Plea to Ubuntu packagers: This should be a strong recommendation
as soon as the language is set to any European using latin 
characters.)

---

