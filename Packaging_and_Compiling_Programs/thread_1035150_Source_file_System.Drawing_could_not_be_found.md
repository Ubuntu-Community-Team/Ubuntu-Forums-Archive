---
title: "Source file System.Drawing could not be found"
date: 2009-01-09
forum: Packaging and Compiling Programs
---

### Post by thale on 2009-01-09
Hey guys, I'm compiling a mono app with winforms in it and I "believe" I have everything installed correctly but I'm still getting errors. The command I'm using is:
```

gmcs -out:bin/Debug/Windows/Test.exe -debug -r:System, System.Drawing, System.Windows.Forms Test.cs WinFormMain.cs 
```

The out put:

```
error CS2001: Source file `System.Drawing,' could not be found
error CS2001: Source file `System.Windows.Forms' could not be found
Compilation failed: 2 error(s), 0 warnings
```

I can obviously include System just fine and I verified that the dll's do exist in the system :( am I missing something?

---

### Post by directhex on 2009-01-09
Close, but no cigar. Use 
```
-r:System -r:System.Drawing -r:System.Windows.Forms
```
not 
```
-r:System, System.Drawing, System.Windows.Forms
```

---

### Post by thale on 2009-01-09
Yup, haha, that did do it. I must have read the man page wrong. Thanks!

---

