---
title: "Cernlib"
date: 2005-01-27
forum: Repositories &amp; Backports
---

### Post by mirtux on 2005-01-27
Hi everybody,
   i need to install the [COLOR=Red]libkernlib[/COLOR] library. I tried to search it with synaptic but it's telling me:
```
libkernlib1:
 Depends: cernlib-base but it is not installable
``` 
In fact the package is not present in the repositories i have.
Does anybody of you has this problem or he knows how to solve it?

Regards,
MC

---

### Post by mendicant on 2005-01-28
It might be available in a multiverse, somewhere.  I thought it was GPL, so I'm not sure why it isn't in universe.  You can also try pulling it from hoary. Just put hoary in your sources.list, do:
% aptitude update
% aptitude install libkernlib1 #(or maybe libkernlib1-dev)

then revert your sources.list to what it was originally.  This, of course, is probably an unsupported operation, but it ought to work--you would then be running a mixture of warty and hoary packages, and so you might have to be careful about security notices regarding the hoary packages.

---

### Post by mirtux on 2005-01-31
Hi mendicant,
   thanks for the reply, but the problem is that libkernlib requires **cernlib-base**  which is not available. libkernlib and libkernlib-dev are present but not installable because of this problem.

Regards,
MC

---

### Post by mendicant on 2005-01-31
But it _is_ available--in hoary universe.  So you need to change from warty to hoary, and add universe in your apt sources.list, do an update, then just do:
% aptitude update
% aptitude install libkernlib1 #(or maybe libkernlib1-dev)

This will pull in the cernlib-base dependency from hoary universe (plus possibly other dependencies from hoary).  You then change your sources.list back to what it was, and you should have what you want.

---

### Post by mirtux on 2005-01-31
Oh.... 
  sorry for my reply, i didn't understand that the "universe" was from hoary. I'll have a look and i'll tell you how it goes.
  
  Thanks again,
  MC

---

