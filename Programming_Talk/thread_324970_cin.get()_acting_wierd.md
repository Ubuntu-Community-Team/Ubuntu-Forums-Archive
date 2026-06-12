---
title: "cin.get() acting wierd"
date: 2006-12-24
forum: Programming Talk
---

### Post by HokeyFry on 2006-12-24
i like to jump back and forth between Anjuta and command line when im programming, depending on the size of what it is im doing. yet i have one simple question about cin.get() for C++.

i use cin.get() to pause program execution. how come when i use it in anjuta it pauses like it should, but when i use it outside of anjuta (i.e. command line) it doesnt pause?

---

### Post by samjh on 2006-12-24
Try cin.ignore() before cin.get().  Perhaps there is a EOL or CR character that cin.get() is reading from a previous input.
```
// existing code using cin

cin.ignore();
cin.get();

// following code
```

---

### Post by HokeyFry on 2006-12-25
yep that works. thanks!

---

