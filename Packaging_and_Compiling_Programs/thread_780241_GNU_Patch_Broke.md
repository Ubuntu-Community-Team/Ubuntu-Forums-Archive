---
title: "GNU Patch Broke"
date: 2008-05-03
forum: Packaging and Compiling Programs
---

### Post by andrew510 on 2008-05-03
Hey all, 
i have been trying to compile wine from source with the direct x patches but when i go to the terminal and cd to the wine source dictionary and type in:
patch -p1 d3d9.diff
all it does is show the flashing text prompt

I've tried everything i csn think of, i uninstalled patch on synpatic and reinstalled it, no joy and tried compiling patch from source myself

Any ideas?

Thanks

---

### Post by geraldm on 2008-05-05
>all it does is show the flashing text prompt
That means that it is expecting the input to be typed . ?
Do not forget to use the "-i" before the patch file.  See
man patch

patch -p1 -i d3d9.diff

Gerald

---

### Post by andrew510 on 2008-05-06
Thanks, will try this l8r

---

