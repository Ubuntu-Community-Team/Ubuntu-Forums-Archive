---
title: "copying and pasting from emacs to firefox"
date: 2006-11-30
forum: Programming Talk
---

### Post by styracosaurus on 2006-11-30
So, I want to copy a block of code from a file that is open in emacs, and paste it into Firefox. What's the deal? When I select copy in the emacs edit menu, and paste in Firefox, I get the last thing I copied in Firefox...

I've noticed this elsewhere... the whole clipboard thing is sort of iffy? Is it just me? Am I a total noob and am missing something crucial?

---

### Post by styracosaurus on 2006-11-30
Okay, this is embarrassing!! I tried the little "clipper" tool in the KDE taskbar... it did what I want. Although it still seems a little complicated? Does it add anything you SELECT to the clipboard?

Anyway, I'm usually not this silly! Thanks for the help! ;)

---

### Post by Arndt on 2006-12-01
> **styracosaurus said:**
> So, I want to copy a block of code from a file that is open in emacs, and paste it into Firefox. What's the deal? When I select copy in the emacs edit menu, and paste in Firefox, I get the last thing I copied in Firefox...

I've noticed this elsewhere... the whole clipboard thing is sort of iffy? Is it just me? Am I a total noob and am missing something crucial?

My opinion is that the whole clipboard thing _is_ sort of iffy. It started with X (the window server) providing several mechanisms for copying/pasting between programs: clipboard, cut buffers and selections (I may be calling the same thing by two different names here - I don't remember), one of them with very complicated semantics, so it was never clear exactly where a copy operation put the text or where a paste operation fetched it. Programmers have a large scope for making mistakes or design errors here.

One program that has sometimes helped me is 'xcutsel'. Other times, it has helped to paste the text into a terminal window and then copy it again.

---

### Post by lnostdal on 2006-12-01
> **styracosaurus said:**
> Okay, this is embarrassing!! I tried the little "clipper" tool in the KDE taskbar... it did what I want. Although it still seems a little complicated? Does it add anything you SELECT to the clipboard?

Anyway, I'm usually not this silly! Thanks for the help! ;)

The way to do it in *nix is not to use the menus. You mark the text you want to copy with your left-button, then middle-click (or both left and right at the same time) at the spot you want it pasted.

```
This is from Emacs.
```

..you'll find this way better and easier than in Windows.. :)

---

### Post by ohgod on 2006-12-01
I added these lines to my .emacs file to tell emacs to always interact with the clipboard (the default is that emacs ignores the clipboard on linux I think).  Anyway, copying-and-pasting from/to emacs and any other X program works for me:

```

;; make emacs use the clipboard
(setq x-select-enable-clipboard t)
(setq interprogram-paste-function 'x-cut-buffer-or-selection-value)

```

---

### Post by dwblas on 2006-12-04
Glad you found a solution.  Also remember that you can open a file in Firefox and cut and paste within Firefox if you run into this problem with another app.

---

### Post by thomasaaron on 2006-12-04
Nice, thanks.
I've been trying to figure that one out too.

Tom

---

### Post by lukew on 2007-01-04
> **ohgod said:**
> I added these lines to my .emacs file to tell emacs to always interact with the clipboard (the default is that emacs ignores the clipboard on linux I think).  Anyway, copying-and-pasting from/to emacs and any other X program works for me:

```

;; make emacs use the clipboard
(setq x-select-enable-clipboard t)
(setq interprogram-paste-function 'x-cut-buffer-or-selection-value)

```

Thank You!!! This worked for me!!

Anyone else managed to get dragging and dropping files / text into emacs? Can this work? Should this work? Acording to GNU it should!!!

Thanks

Luke

---

