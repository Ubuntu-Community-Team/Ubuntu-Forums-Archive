---
title: "Pythøn Definitions"
date: 2010-08-16
forum: Programming Talk
---

### Post by Sailor5 on 2010-08-16
Ahoy Sailors!

Maybe my head is too clouded to program in Python today, But how can I get this to work?```
class alpha():
  def omega(self):
     print "Is working"
  omega()
```Which of course won't work due to you having to supply omega() with the self argument, Which isn't defined.

Anyone know how to fix this?

See Ya!

---

### Post by -grubby on 2010-08-16
You will either have to call the method inside another method in the class, or instiate the class and call the method.

---

### Post by -grubby on 2010-08-16
You will either have to call the method inside another method in the class, or instiate the class and call the method.

---

### Post by Bachstelze on 2010-08-16
What is it that you want to do? Whatever it is, this is probably not the right way to go about it.

---

### Post by StephenF on 2010-08-16
FWIW
```

class alpha():
  def omega():
    print "Is Working"
  omega()
  omega = staticmethod(omega)  # Or del omega.
  
alpha().omega()
alpha.omega()

```

---

