---
title: "URGENT Java swing/awt help"
date: 2008-12-03
forum: Programming Talk
---

### Post by Luke has no name on 2008-12-03
I have a final due TODAY on a similar project, and I'm getting runtime errors. Put in text for first and last name, and a number between 40 and 50 for the hours worked.

This is legal, you aren't helping me cheat in a class, I promise. But My issue with the final is giving a similar issue.

My email is [email]lukehasnoname@gmail.com[/email] if you do not have a UF account.

---

### Post by jdong on 2008-12-03
Sigh, homework help is really not encouraged here. It's a homework assignment for you to do, and the process helps you learn. I will reluctantly keep the thread open here, but please don't have someone else give you an obvious answer.


If you can provide a helpful hint towards the correct answer, that's somewhat more appropriate, but I suggest the OP to consult his course help resources if this really isn't cheating.

---

### Post by Luke has no name on 2008-12-03
The assignment I posted is something I've already turned in. A current assignment also contains editing a JTextArea, and my professor didn't even know exactly what the problem was. 

I'm getting a NullPointerException when appending a String to a JTextArea. Anyone know how that can happen?

---

### Post by jdong on 2008-12-03
Sorry, that hint was a bit mean.

Here's a better hint:

Have you tried using a debugger to follow the code path?

---

### Post by Luke has no name on 2008-12-03
Ya, but the path is a bit obscure, and my experience with swing and the java debugger are both not up to par...

My current plan is to continue programming the new project and hope to God I don't run into obscure exceptions. Maybe this code will be better than the old stuff.

---

### Post by jdong on 2008-12-03
Ah, but the debugger REALLY is your friend. Let's learn how to use it.

For reference, here is the stacktrace:
```

Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
	at lab65804.MyGui$ButtonHandler.actionPerformed(**MyGui.java:124**)
	at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:2012)
	at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2335)
	at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:404)
	at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:259)
	at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(BasicButtonListener.java:253)
	at java.awt.Component.processMouseEvent(Component.java:6108)
	at javax.swing.JComponent.processMouseEvent(JComponent.java:3276)
	at java.awt.Component.processEvent(Component.java:5873)
	at java.awt.Container.processEvent(Container.java:2105)
	at java.awt.Component.dispatchEventImpl(Component.java:4469)
	at java.awt.Container.dispatchEventImpl(Container.java:2163)
	at java.awt.Component.dispatchEvent(Component.java:4295)
	at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4461)
	at java.awt.LightweightDispatcher.processMouseEvent(Container.java:4125)
	at java.awt.LightweightDispatcher.dispatchEvent(Container.java:4055)
	at java.awt.Container.dispatchEventImpl(Container.java:2149)
	at java.awt.Window.dispatchEventImpl(Window.java:2478)
	at java.awt.Component.dispatchEvent(Component.java:4295)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:604)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)

```


I bolded the only part you should pay attention to. Now, do you want to pick a good place to set a breakpoint and take a closer look?


(NOTE: I may have been mean enough to change your code so that my stack trace looks different from yours. But use your head.)

---

### Post by jdong on 2008-12-05
So, have you had a chance to figure it out yet? :)

---

### Post by geirha on 2008-12-06
If you can spot the problem in this code, you'll be able to spot the problem in your own code.
```

public class Test
{
    private String a;

    public Test()
    {
        String a= "Hello, World!";
    }
    public String toString()
    {
        return a;
    }

    public static void main(String args[])
    {
        Test t= new Test();
        System.out.println(t);
    }
}

```

---

### Post by Reiger on 2008-12-06
Ooh I love those. Usually it's the other way around for me. (Complaining about duplicate variable names, preferably of different types.) :p

---

### Post by jdong on 2008-12-06
> **geirha said:**
> If you can spot the problem in this code, you'll be able to spot the problem in your own code.
```

public class Test
{
    private String a;

    public Test()
    {
        String a= "Hello, World!";
    }
    public String toString()
    {
        return a**.toString()**;
    }

    public static void main(String args[])
    {
        Test t= new Test();
        System.out.println(t);
    }
}

```


Now it even throws the same exception in the same fashion :)

---

### Post by drubin on 2008-12-07
> **geirha said:**
> If you can spot the problem in this code, you'll be able to spot the problem in your own code.
[code]


Nice example, But seriously these types of errors can be stared at for ages with out seeing it ;p.

/me <3 netbeans's informational messages for this

---

### Post by jdong on 2008-12-07
> **drubin said:**
> Nice example, But seriously these types of errors can be stared at for ages with out seeing it ;p.

/me <3 netbeans's informational messages for this

Back to Luke, setting a breakpoint at the beginning of the event handler and mousing over jtaOutput would've told you it was null. When you know *how* to look for it, it's really apparent. The problem IMO is a lot of people really don't know how to debug... reading your code like proofreading an English paper is an extremely ineffective form of troubleshooting, but that's what most people tend to do!

---

