---
title: "Better fonts for emacs22-gtk?"
date: 2009-06-04
forum: Programming Talk
---

### Post by mfearby on 2009-06-04
Is there some way I can get more, and better, fonts into emacs22-gtk? Of the various emacs versions, the -gtk seems nicer overall (I'm an emacs newb, so correct me if this version is evil or something)... But the fonts on offer are not that easy on the eyes. My googling hasn't turned up much, either...

---

### Post by alternatealias on 2009-06-04
This is how I've configured my emacs.

Edit ~/.Xresources and enter the following lines:

emacs.background: Black
emacs.foreground: DarkGray
emacs.pointerColor: Orchid
emacs.cursorColor: Orchid
emacs.bitmapIcon: on
emacs.GlobalFontLock: on
emacs.font: lucidasanstypewriter-bold-18


you can enter basically any font there, but I find lucidasanstypewriter-bold-18 to be perfect.

---

### Post by crush304 on 2009-06-04
use emacs-snapshot-gtk

---

### Post by mfearby on 2009-06-06
Thanks. I ended up using the following in my .Xresources:

Emacs.font: Bitstream Vera Sans Mono-14

I've got my colours saving to my custom-file

---

### Post by mfearby on 2009-06-06
Dayum, that emacs-snapshot gives good font! Thanks very much :-)

---

