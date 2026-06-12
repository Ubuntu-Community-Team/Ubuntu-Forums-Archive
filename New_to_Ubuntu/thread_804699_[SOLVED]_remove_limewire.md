---
title: "[SOLVED] remove limewire"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-05-23
Does anyone know how to remove limewire.com from ubuntu. I installed 'Limewire for linux', thinking I could always remove it. I tried the 'Add/Remove' proceedure & the system can not find the file/directory. I then tried both, the 'rm' & the 'apt-get remove' commands in the terminal format & still could not find anything either. Any Ideas? Thanks, Cal:confused:

---

### Post by bumanie on 2008-05-23
> sudo aptitude remove limewire should work. Alternatively you can go to synaptic and type limewire into the search function. There you should be able to choose 'remove' or 'completely remove'

---

### Post by CoCoKnots on 2008-05-23
Thanks,

The " [COLOR="Blue"]sudo aptitude remove limewire[/COLOR]" line didn't work for what ever reason.
However, the second part of your recommendation worked fine.

should work. Alternatively you can [COLOR="Blue"]go to synaptic and type limewire into the search function. There you should be able to choose 'remove' or 'completely remove'[/COLOR]

Thanks Again

---

### Post by fluteflute on 2008-05-23
It didn't work because the package is called 'limewire-basic' rather than just plain 'limewire'. :)

---

### Post by bumanie on 2008-05-23
Sorry, didn't know it was called limewire-basic. CoCoKnots, you should mark this as solved, so that others can read the solution.

---

