---
title: "VB.net programs in Ubuntu with mono"
date: 2009-12-02
forum: Programming Talk
---

### Post by CoreyB. on 2009-12-02
When I try to run programs written in VB.net in Windows in Visual Studio 2008.  But when I run the exe from the Debug folder under Ubuntu in the terminal like, mono MyProgram.exe, none of the text shows up.

What am I missing?

---

### Post by Zugzwang on 2009-12-03
Ok, so you try running
```

mono MyProgram.exe

```
from the terminal. What error message do you get? Please copy&paste here.

---

### Post by CoreyB. on 2009-12-03
I'm not getting any error messages, the program runs, but there is no text at all.  No text in list boxes, text boxes, no text on buttons, no labels.

Am I missing a package or something?

---

### Post by -grubby on 2009-12-03
Maybe, though it should be noted that Mono isn't exactly a perfect reproduction.

---

### Post by doas777 on 2009-12-03
I don't think you can run win32 user interfaces with mono, since it uses gtk for its gui stuff. never tried it.

---

### Post by CoreyB. on 2009-12-03
For example here is how it looks when run in Ubuntu, and here is how it looks when run in Windows Vista.

---

### Post by doas777 on 2009-12-03
mono is much more about open sourcing C# rather than providing a crossplatform runtime for executing .net apps.

---

