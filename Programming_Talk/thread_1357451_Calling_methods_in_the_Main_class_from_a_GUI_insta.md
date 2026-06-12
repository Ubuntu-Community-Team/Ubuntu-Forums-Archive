---
title: "Calling methods in the Main class from a GUI instance in Java"
date: 2009-12-17
forum: Programming Talk
---

### Post by JCoster on 2009-12-17
Hey guys, just a quick question.

Say that I have the following main class:

```
public class Main {
    private GUI myGUI;    
   
    public Main() {
        myGUI = new GUI();
    }

    public int someCalculation(int x, int y) {
        return (x+y);
    }
}
```

From the GUI instance, how can I call *someCalulation(x,y)* in the parenting Main class?

Cheers guys,
JC

---

### Post by Zugzwang on 2009-12-17
> **JCoster said:**
> From the GUI instance, how can I call *someCalulation(x,y)* in the parenting Main class?


Change the GUI constructor to have a parameter: The instance of the Main that is instantiating the GUI. Then, the GUI class can store a reference to this instance and use it for calling the someCalculation method.

---

### Post by JCoster on 2009-12-17
Thanks for your quick response.  This was what I was thinking of doing but didn't know whether there is a better way?

---

### Post by Can+~ on 2009-12-17
Well, aside from what Zugzwang, someCalculation could be static if you don't intend to override it later.

---

### Post by Some Penguin on 2009-12-18
You could define myGUI as an inner class.  See [http://java.sun.com/docs/books/tutorial/java/javaOO/nested.html](http://java.sun.com/docs/books/tutorial/java/javaOO/nested.html) -- an instance of a non-static inner class has direct access to the (unambiguous) containing instance's methods and fields.

---

