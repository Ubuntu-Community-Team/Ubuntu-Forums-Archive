---
title: "makefile and changes in a standard header??"
date: 2008-03-26
forum: Programming Talk
---

### Post by DJTurboToJo on 2008-03-26
Ok, that should be a simple question though I couldnt find any help out there.

In a makefile you explicitly name your dependencies or sometimes called prerequisites. There you normally include just hand-made headers that are in the source code included with "". (#include "myheader.h"). That's also what I get using gcc -MM. And I never include headers like stdio.h in the prerequisites.

But what if these standard headers are changing? 
EDIT: How does make know when there is a change in libc.so or so?

Thanks
TurboToJo

---

