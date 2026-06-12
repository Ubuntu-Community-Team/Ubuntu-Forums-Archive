---
title: "I need to use the cs1 package (keyboard class)"
date: 2009-12-02
forum: Programming Talk
---

### Post by crazychristian on 2009-12-02
Hello, I am using NetBeans 6.7.1 and I need to use the keyboard class. I have tried to get it working, but I have no idea what to do really. So can anyone guide me real quick to how to get it running? (I already have the package downloaded I just need to get NetBeans to access it somehow). 

Thanks :)

---

### Post by fiddler616 on 2009-12-02
> **crazychristian said:**
> Hello, I am using NetBeans 6.7.1 and I need to use the keyboard class. I have tried to get it working, but I have no idea what to do really. So can anyone guide me real quick to how to get it running? (I already have the package downloaded I just need to get NetBeans to access it somehow). 

Thanks :)
Could we have some more information, please? What language is this--Java? Where did you hear about a "keyboard class?" What do you want the class to accomplish?

---

### Post by crazychristian on 2009-12-02
> **fiddler616 said:**
> Could we have some more information, please? What language is this--Java? Where did you hear about a "keyboard class?" What do you want the class to accomplish?

I am writing in Java. We used this package in school... and it would read the users input.

I.e
```

import cs1.Keyboard;
public class X
{
public static void main(String [] args)
{
System.out.println("Please enter a value");
double a=Keyboard.readDouble();
}
}


```So the person would type a value, and would be stored for the double a. Does this help?

---

### Post by fiddler616 on 2009-12-02
> **crazychristian said:**
> I am writing in Java. We used this package in school... and it would read the users input.

I.e
```

import cs1.Keyboard;
public class X
{
public static void main(String [] args)
{
System.out.println("Please enter a value");
double a=Keyboard.readDouble();
}
}


```So the person would type a value, and would be stored for the double a. Does this help?
Mmf, it's been a while since I had to load third-party libraries in Java, but [this]("http://faculty.ed.umuc.edu/~arnoldyl/NetBeansTutorials/Predefined-Classes.html") should help.

As a sidenote, once you get out of that class you might be interested in the [Scanner]("http://java.sun.com/j2se/1.5.0/docs/api/java/util/Scanner.html") class which does all the same stuff as Keyboard, but is built into the Java language.

---

### Post by crazychristian on 2009-12-02
Thank you :) That pointed me in the right direction.

---

### Post by fiddler616 on 2009-12-02
> **crazychristian said:**
> Thank you :) That pointed me in the right direction.
No problem, I'm glad I could help.

(PS: Don't forget to mark the thread as solved!)

---

