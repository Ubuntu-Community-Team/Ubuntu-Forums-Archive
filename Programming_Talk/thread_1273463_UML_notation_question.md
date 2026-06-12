---
title: "UML notation question"
date: 2009-09-23
forum: Programming Talk
---

### Post by the_real_fourthdimension on 2009-09-23
Hey All

I'm drawing a uml diagram for a java system in which ClassA creates an object of ClassB then calls methods in it.  What kind of arrow would I use for this?  Thanks.

---

### Post by dwhitney67 on 2009-09-23
Look thru this site... maybe something will inspire you.

[http://www.holub.com/goodies/uml/](http://www.holub.com/goodies/uml/)

---

### Post by PaulM1985 on 2009-09-23
I think you would use a solid arrow for invoking methods and a dashed arrow for message responses ie if a method returns a value.

When classA create classB, you need to do a solid arrow from the activation rectangle in classA to the object box classB with a label saying "new".

Hope this helps

Paul

---

### Post by the_real_fourthdimension on 2009-09-23
> **PaulM1985 said:**
> I think you would use a solid arrow for invoking methods and a dashed arrow for message responses ie if a method returns a value.

When classA create classB, you need to do a solid arrow from the activation rectangle in classA to the object box classB with a label saying "new".

Hope this helps

Paul

Thanks.  Yeah, that's correct for a sequence diagram, but I'm working on a class diagram at the moment that just shows the program structure.
I'll check out the above link.

---

