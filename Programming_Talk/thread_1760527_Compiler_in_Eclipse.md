---
title: "Compiler in Eclipse"
date: 2011-05-17
forum: Programming Talk
---

### Post by rdst on 2011-05-17
I heard that Eclipse uses its own compiler, doesn't use javac from Sun. Is this true ? If it's true, how could I change its compiler to javac of Sun ?
There's only sun-java6-jdk in my Ubuntu, no open-jdk, no other VMs.

Thanks a lot !

PS: I want to do that because I found there's something different between the class file from Eclipse and from javac of Sun, especially the line number of code. This seriously affects to my current project.

---

### Post by TheStroj on 2011-05-17
You can set it in preferences, search around a bit, it shouldn't be too hard.

---

### Post by GregBrannon on 2011-05-17
Your premise, what you heard, is not true.  Eclipse does not have its own compiler.  With that dispelled, if you have a working Eclipse installation, don't change anything.

---

### Post by fct on 2011-05-17
As a matter of fact, Eclipse has its own incremental Java compiler. That is why it can show errors as you type.

If you want to use javac, you must use an ant task.

[http://stackoverflow.com/questions/325498/where-eclipse-finds-javac-to-compile-the-a-project](http://stackoverflow.com/questions/325498/where-eclipse-finds-javac-to-compile-the-a-project)

But anyway... **the line number shouldn't change even if you switch compilers**. I think your problem is in some other place.

---

### Post by stchman on 2011-05-17
> **rdst said:**
> I heard that Eclipse uses its own compiler, doesn't use javac from Sun. Is this true ? If it's true, how could I change its compiler to javac of Sun ?
There's only sun-java6-jdk in my Ubuntu, no open-jdk, no other VMs.

Thanks a lot !

PS: I want to do that because I found there's something different between the class file from Eclipse and from javac of Sun, especially the line number of code. This seriously affects to my current project.

No, Eclipse uses an external compiler.

sun-java6-jdk is all you need.

---

### Post by simeon87 on 2011-05-17
> **stchman said:**
> No, Eclipse uses an external compiler.

sun-java6-jdk is all you need.

Actually, as fct said, Eclipse does use its own compiler, see [here](http://wiki.eclipse.org/FAQ_How_do_I_choose_my_own_compiler%3F) and [here](http://www.eclipse.org/jdt/overview.php).

---

