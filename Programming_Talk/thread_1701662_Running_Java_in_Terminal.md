---
title: "Running Java in Terminal"
date: 2011-03-06
forum: Programming Talk
---

### Post by Pengi-FlyGirl26 on 2011-03-06
For my CSC 330 class, we're supposed to be using notepad to develop and write the code and the command prompt environment to run the actual programs. There's even step-by-step powerpoints with print-screens showing how we're supposed to do this...in Windows. I've managed to write the code, set up all the permissions, save in the right directory, and access the directory, but still haven't yet managed to get anything to show up. I feel like a complete idiot. I went to my professor and he told me to use one of the school computers (which wouldn't really work b/c only one lab will has the permissions set up right, and it usually has a class in it) b/c the school does not support Linux. Therefore I am on my own. ](*,)
Here's some of what I've tried/gotten:
kelsey@Wubi:/usr/lib/jvm/java-6-openjdk/bin$ javac Ballworld.java
Note: Ballworld.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
Ideas?

---

### Post by Reiger on 2011-03-06
It's a warning. Not an error, a hint of what you might want to fix. So if you run javac -Xlint:deprecation Ballworld.java it will print the precise line and bits of code where you are using the deprecated API. Or you can ignore it for now and get on with your assignment until you feel more comfortable tackling extra problems.

---

### Post by myrtle1908 on 2011-03-06
As Regier says, it's just a warning.  Don't worry about it for now.  *javac* should still have produced a class file.  So try run it and see what happens.

```
java Ballworld
```

Good Luck

---

### Post by Pengi-FlyGirl26 on 2011-03-06
Thanks! I knew it was something simple I was overlooking. Didn't exactly know what the warning was, though.

---

