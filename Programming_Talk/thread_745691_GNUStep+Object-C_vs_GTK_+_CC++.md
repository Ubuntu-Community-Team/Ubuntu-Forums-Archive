---
title: "GNUStep+Object-C vs GTK + C/C++"
date: 2008-04-04
forum: Programming Talk
---

### Post by dmitrijledkov on 2008-04-04
I'm slightly confused.

I switched from Windows to Mac and now to Ubuntu. And I'm confused by GNUStep.

They say that's it is cross-platform compatible. Well it is compatible with Cocoa API for Mac OS X.

But how would one go about developing for GTK or QT or Windows for that mater using GNUStep/Object C.

Cause I really like Object C it looks neat. But I also want cross-platform compatibility.

Or I'll have to go down Python + wxWidgets root to get that.

---

### Post by lnostdal on 2008-04-04
what is or where is the question or problem? ..are you looking for an obj-c compiler?

on linux:
```
sude aptitude install gobjc
```

on windows:
[http://www.mingw.org/](http://www.mingw.org/) (a port of gcc; objc is included)

for mac/apple:
i have no idea .. gcc runs there also

---

### Post by Bushfire on 2008-04-05
You can code in GTK+ with Objective C, because GTK+ uses straight C, and Objective C is a superset of the language. You'll have less luck with QT, as it uses C++. I don't know where GNUStep enters into all this however, it and Objective C are separate things.

---

### Post by dmitrijledkov on 2008-04-06
> **Bushfire said:**
> You can code in GTK+ with Objective C, because GTK+ uses straight C, and Objective C is a superset of the language. You'll have less luck with QT, as it uses C++. I don't know where GNUStep enters into all this however, it and Objective C are separate things.

I think I understand this now better. Language does not depend on widget toolkit or additional libraries and stuff you want to use.

Cause on Mac Objective C uses Cocoa libraries to do some neat stuff with graphics, audio, 2d rendering and etc. GNUStep as I know understands makes free (as in freedom) alternative to cocoa.

And since you reminded me that Object C is strict superset of C I know understand that I can always resort to C to access ANYTHING as in Cocoa, GTK, wxWidgets and etc.

Thanks a lot.

---

