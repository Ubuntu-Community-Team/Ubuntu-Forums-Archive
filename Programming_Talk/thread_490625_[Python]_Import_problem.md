---
title: "[Python] Import problem"
date: 2007-07-02
forum: Programming Talk
---

### Post by Laterix on 2007-07-02
Hi,

I have a problem on importing source files in Python. The files look like this:
```

from mycode.class_a import ClassA

class ClassB:
    # Stuff here

```
And the other one
```

from mycode.class_b import ClassB

class ClassA:
    # Stuff here

```
These are imported in another file. I would like to keep one class per file, but I get import error when I have this kind of situation that both classes A and B needs to know each other. What am I missing here?

---

### Post by avik on 2007-07-02
mycode.class_b is importing mycode.class_a which is importing mycode.class_b which is...

You get the idea.  It's a cycle.

My suggestion?  Don't separate classes into different files just because they're different classes.  Each file should have everything required related to a certain concept.

---

### Post by skeeterbug on 2007-07-02
Try and remember that the file is a module, you created two seperate modules. If you named them by their class, then you probably had something like this:

ClassA.ClassA.Method()

Do what the first reply suggested, move them to the same file (module).

---

### Post by Laterix on 2007-07-03
Thank you for your replies. I find it better to write only one class per file, but if there is no way to do this that way, then I just have to join those classes to the same source file. Thanks.

---

### Post by avik on 2007-07-03
Remember, it's not that you can't have one class per file, it's just that if both classes depend on *each other*, you have to put them in the same file.  The most important thing is that Python is *not* Java.  It has its own preferences and best practices, and once you go with the grain, you'll find so much more power in the language.

Happy coding!

---

### Post by Laterix on 2007-07-04
Well, now it works as it should, but I still find it better to organize object-oriented code one class per file. :) But I can live with this. Thanks to all.

---

### Post by dwblas on 2007-07-06
> I still find it better to organize object-oriented code one class per fileIf you want to keep 2 files, then you will have to use a third program/file that will import the other 2 and run everything from the 3rd file.  This may or may not work, and may even be worse depending on how things are set up.  The objective is to have something that works well however it runs.

---

