---
title: "[SOLVED] [Java] Random Amount of Objects?"
date: 2008-04-13
forum: Programming Talk
---

### Post by TreeFinger on 2008-04-13
Is there a way to create a random amount of objects??

I ask this because I have a project asking to create a random amount of bars on a bar graph. I am thinking that there is no way to initiate a random amount of objects but instead just display a random amount??

I do not think our instructor is anticipating any of us to create a 'Bar' class but I would like to. Anyone wanna throw me an idea?

---

### Post by Zugzwang on 2008-04-13
You mean something like this?

[PHP]
  Vector<Whatever> foo = new Vector<Whatever>();
  while (Math.random()>0.1) {
    foo.add(new Whatever());
  }
[/PHP]

Then the vector foo contains a (geometrically distributed) random number of Objects of type Whatever.

---

### Post by TreeFinger on 2008-04-13
Well these objects I am going to create will be graphics on the screen. I am going to do some coding then I will be back!

---

### Post by TreeFinger on 2008-04-13
OK, I've created a class called 'Bar' and I need to be able to create / display a random amount of 'Bars'.

I'm not sure how to do this.. how can I 
[php]
bar.draw(page)
bar1.draw(page)
bar2.draw(page)
...
barN.draw(page)
[/php]

do that??


hmm.. I'm guessing a few If statements??

Create a random number  and If randNum = X .. display ahhhhah!

---

### Post by Zugzwang on 2008-04-13
It is better to store all the objects into an array (or Vector in my example). This way you can handle an arbitrary number of objects.

---

### Post by Quikee on 2008-04-13
As Zugzwang said but don't use Vector directly - use List interface (to be implementation neutral) with Vector or ArrayList (which is a faster thread unsafe implementation of Vector actually).

[PHP]List<Whatever> foo = new Vector<Whatever>();
  while (Math.random()>0.1) {
    foo.add(new Whatever());
  }  [/PHP]

[PHP]List<Whatever> foo = new ArrayList<Whatever>();
  while (Math.random()>0.1) {
    foo.add(new Whatever());
  }  [/PHP]

This is the preferred way of using Collections / Lists in Java nowadays.

---

### Post by TreeFinger on 2008-04-13
Well, something is wrong. haha!

I get the program to compile but when it runs I have a lot of errors thrown at me.

```

$ java BarGraph
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
        at BarPanel.paintComponent(BarPanel.java:36)
        at javax.swing.JComponent.paint(JComponent.java:1022)
        at javax.swing.JComponent.paintChildren(JComponent.java:859)
        at javax.swing.JComponent.paint(JComponent.java:1031)
        at javax.swing.JComponent.paintChildren(JComponent.java:859)
        at javax.swing.JComponent.paint(JComponent.java:1031)
        at javax.swing.JLayeredPane.paint(JLayeredPane.java:564)
        at javax.swing.JComponent.paintChildren(JComponent.java:859)
        at javax.swing.JComponent.paintToOffscreen(JComponent.java:5111)
        at javax.swing.BufferStrategyPaintManager.paint(BufferStrategyPaintManager.java:285)
        at javax.swing.RepaintManager.paint(RepaintManager.java:1132)
        at javax.swing.JComponent.paint(JComponent.java:1008)
        at java.awt.GraphicsCallback$PaintCallback.run(GraphicsCallback.java:21)
        at sun.awt.SunGraphicsCallback.runOneComponent(SunGraphicsCallback.java:60)
        at sun.awt.SunGraphicsCallback.runComponents(SunGraphicsCallback.java:97)
        at java.awt.Container.paint(Container.java:1797)
        at javax.swing.RepaintManager.paintDirtyRegions(RepaintManager.java:738)
        at javax.swing.RepaintManager.paintDirtyRegions(RepaintManager.java:683)
        at javax.swing.RepaintManager.seqPaintDirtyRegions(RepaintManager.java:663)
        at javax.swing.SystemEventQueueUtilities$ComponentWorkRequest.run(SystemEventQueueUtilities.java:128)
        at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
        at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
        at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
        at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
        at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)

```

Something going on with the If statements I created.. When I remove the inititalization of the variable for the if statement all runs peachy..

--edit

heh, i'm an idiot. never constructed the Random object..

---

