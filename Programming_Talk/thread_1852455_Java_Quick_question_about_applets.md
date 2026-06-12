---
title: "Java: Quick question about applets"
date: 2011-09-30
forum: Programming Talk
---

### Post by fallenshadow on 2011-09-30
I am currently drawing on a Java applet using the 2D painting method. I heard from somewhere that drawing directly on an applet is bad... is this true?

Should I draw on an inner canvas class instead?

(Considering that other things such as buttons will be placed on this applet.)

I am grateful to anyone with an answer on this! :)

---

### Post by t1497f35 on 2011-09-30
If it works well don't bother changing anything. There's always room for improvement, even going OpenGL, the eternal question is - is it worth it?

---

### Post by PaulM1985 on 2011-09-30
I prefer to keep my drawing in a separate panel so I know that anything I do in this panel is not going to impact on any of the other ui controls.  I find it also makes my code tidier.  If I want to draw something in a panel, it is usually because it is a special type of panel and so I want a class for it.

Paul

---

### Post by jmartrican on 2011-09-30
I think creating a Panel will make it easier going forward.

---

### Post by fallenshadow on 2011-10-02
Im a bit confused about this:

> aBorderPanel.add(aComponent, BorderLayout.CENTER);

What goes in place of aComponent? Ive tried a few different things.. nothing works.

Based on info from this page: [http://download.oracle.com/javase/tutorial/uiswing/components/panel.html](http://download.oracle.com/javase/tutorial/uiswing/components/panel.html)

---

### Post by ofnuts on 2011-10-02
> **fallenshadow said:**
> Im a bit confused about this:



What goes in place of aComponent? Ive tried a few different things.. nothing works.

Based on info from this page: [http://download.oracle.com/javase/tutorial/uiswing/components/panel.html](http://download.oracle.com/javase/tutorial/uiswing/components/panel.html)Any java.awt.Component, as a guess:

[http://download.oracle.com/javase/6/docs/api/java/awt/Component.html](http://download.oracle.com/javase/6/docs/api/java/awt/Component.html)

---

### Post by fallenshadow on 2011-10-02
Ok I have another problem... when I launch my app a blank applet window opens and also another window with everything in it. Why would such a thing happen?? :confused:

---

### Post by ofnuts on 2011-10-02
> **fallenshadow said:**
> Ok I have another problem... when I launch my app a blank applet window opens and also another window with everything in it. Why would such a thing happen?? :confused:If you this is an Applet should shouldn't be lauching it, since it runs inside a browser. And an Applet is a java.awt.Panel, so you can add components to it directly. I suspect you code is creating an unnecessary window.

---

### Post by fallenshadow on 2011-10-03
Ok this should be my last question...

Is it only java.awt components are allowed in applets? or are swing components allowed too?

---

### Post by PaulM1985 on 2011-10-03
I am almost certain all Swing components are java.awt.Components.

[http://download.oracle.com/javase/1,5.0/docs/api/javax/swing/JComponent.html](http://download.oracle.com/javase/1,5.0/docs/api/javax/swing/JComponent.html)

Paul

---

### Post by fallenshadow on 2011-10-04
Problem solved folks, I wont bother ye for another while.. I hope. :D

Its amazing that starting a project again helps so much! :D

Everything is now appearing in the one applet window again. :)

---

