---
title: "Installing tex style packages"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by browny254 on 2008-05-08
Hi, Im trying to install a new style package for Tex (specifically im using Kile) and have no idea how to do it.

the package im trying to install is here [http://web.mit.edu/texsrc/source/latex/listings/](http://web.mit.edu/texsrc/source/latex/listings/) I tried following the instructions there but the directory structure wasnt exactly the same so I did what it said in the closest looking place to where they recommend, but now I cant even compile my code.

any ideas?

---

### Post by girishv on 2008-05-08
You can set texinputs variable to point to the directory(ies) where the style files are saved. Say for example
export TEXINPUTS=~/prosper:~/aastex52:

Dont forget the colon at the end

girish

---

### Post by browny254 on 2008-05-08
um, can you explain that a little more? I have only just started using Latex so I only know how to do the real basics atm.

---

### Post by browny254 on 2008-05-08
ok dont worry...i finally found how to do it here...

[http://en.wikibooks.org/wiki/LaTeX/Packages/Installing_Extra_Packages](http://en.wikibooks.org/wiki/LaTeX/Packages/Installing_Extra_Packages)

---

