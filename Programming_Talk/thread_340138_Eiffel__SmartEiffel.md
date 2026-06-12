---
title: "Eiffel / SmartEiffel"
date: 2007-01-16
forum: Programming Talk
---

### Post by Frothy on 2007-01-16
I have a class project that requires I learn Eiffel. Has anyone else done any Eiffel programming in (K)ubuntu? I searched through the repos and came across the compiler SmartEiffel, but I haven't been able to get it to work. When I go to compile it gives the following error
```
/usr/bin/smarteiffel.sh: line 111: se-compile: command not found
```
I'm going to try getting the source from SmartEiffel's website and compiling myself. However, if anyone else has run into this before or has any suggestions I'd be happy to hear them.

---

### Post by Frothy on 2007-01-17
Ah-ha! If anyone else runs into the problem above, here's the solution:

Open ~/.bashrc

add the following lines to the end of the file
```

# smarteiffel
export PATH=/usr/lib/smarteiffel/bin:$PATH

```

reload .bashrc (I just typed **bash** at the command line, although there may be other ways to do it)

Voila!

---

### Post by &lt;mawe&gt; on 2007-01-17
[quote="Frothy"]reload .bashrc (I just typed bash at the command line, although there may be other ways to do it)[/quote]
Yep, that's what the *source* command is for ;)
```
source ~/.bashrc
```

Regards, mawe

---

