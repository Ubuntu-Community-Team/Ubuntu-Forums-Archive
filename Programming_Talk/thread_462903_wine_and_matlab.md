---
title: "wine and matlab"
date: 2007-06-03
forum: Programming Talk
---

### Post by Zacharias on 2007-06-03
hi guys, 

how can install matlab using wine? 

if you may help me i will be very glad.

---

### Post by Zacharias on 2007-06-03
any idea ?

---

### Post by xtacocorex on 2007-06-03
Matlab does have a Linux version.  I've always just used that when I installed it, never tried it with wine.

---

### Post by Zacharias on 2007-06-04
how can i install that is there a deb package ?

---

### Post by rich.bradshaw on 2007-06-04
matlab is expensive, your university/company should be able to provide you with a copy. I didn't even realise there was a Windows version!

---

### Post by xadder on 2007-06-04
Do you need the real matlab? Octave or Pylab are free and make very good substitutes.

---

### Post by xtacocorex on 2007-06-04
> **Zacharias said:**
> how can i install that is there a deb package ?
There should just be an installer on the installation disk.  Of course I have an old student version of Matlab and don't know how the new disks are laid out.

You could also try Scilab, which is an open source clone of Matlab.

---

### Post by FryerFox on 2007-06-04
I would go with octave. I have tried several opensource alternatives to Matlab myself, and found octave to be the easiest to port code to. Most code ports over without change - the more obscure tricks like pause(0) to allow Matlab to flush disp() data to screen won't work (you can use flush() instead). The only major stumbling block is object orientation works differently (not a problem is you're talking about <= Matlab 5 IIRC)

Octave is command line only, but I use Kate and have a hotkey bound to:

```
cd "%directory" && gnome-terminal --execute octave --silent
```

for instantly launching octave in a terminal in the correct directory (I could add '%filename' to the end of that to run the opened file if I wanted)

Also, Kate, GEdit, and tools that use them (eg. KDevelop) will recognize Matlab syntax highlighting.

---

