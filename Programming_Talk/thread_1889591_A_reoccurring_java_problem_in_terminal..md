---
title: "A reoccurring java problem in terminal."
date: 2011-12-01
forum: Programming Talk
---

### Post by Vexiant on 2011-12-01
Please note, the source code and error are both included in the Pastebin link.

[http://pastebin.com/0w5A8Nk9](http://pastebin.com/0w5A8Nk9)

Yeah, yeah. As you can see. I'm brand new to java. Honestly, I barely have any programming experience at all. I'm currently trying to convert the .java file to a .class file and run it in terminal on Ubuntu 11.10. I would really love for someone to point out what I have done wrong; thanks in advance.

~Vexiant

---

### Post by 11jmb on 2011-12-01
You need to compile your code before you run it
```
javac HelloWorld.java
java HelloWorld
```

---

### Post by Vexiant on 2011-12-01
> **11jmb said:**
> You need to compile your code before you run it
```
javac HelloWorld.java
java HelloWorld
```

Ohh! I missed the "c" at the end of java. Assuming it means java compile, yes? Anyhow, thank you, mate!

---

### Post by 11jmb on 2011-12-01
Yep, If that does not work make sure you have JDK installed, not just JRE. An easy way to tell is by running ```
which javac
```

---

### Post by Vexiant on 2011-12-01
> **11jmb said:**
> Yep, If that does not work make sure you have JDK installed, not just JRE. An easy way to tell is by running ```
which javac
```

Yes, it worked. Thanks again.

---

