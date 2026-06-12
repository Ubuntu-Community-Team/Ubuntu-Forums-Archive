---
title: "[JAVA] Gui-building class"
date: 2009-06-17
forum: Programming Talk
---

### Post by spupy on 2009-06-17
Hello, fellow coders.
I'm writing in Java a simple graphical interface. However simple there is lots of code that does the actual construction - panels, borders, padding, etc. For this reason I've decided to move the gui building code to a new class, to unclutter a bit. So, if the class containing the gui logic is called Gui.java, the class that builds the gui at start up is called GuiBuilder.java.
Now, the gui has a lots of components but only a fraction of them is used in Gui.java - button's call-backs, text areas for printing, jtables for lists, etc. So I entered these important components as fields in Gui.java with the **default modifier**. Default modifier gives access to objects from the same package. The GuiBuilder.java is in the same package.
The GuiBuilder is doing its work, builds the gui; when it adds one of the important gui components, it passes the reference to the Gui.java. Pseudo-code example:
```
 GuiBuilder.java
public static buildGui(Gui gui){
   // gui building...
   JButton importantButton = new JButton("qwerty");
   somePanel.add(importantButton);
   gui.importantButton = importantButton; // give the reference to the real gui
   // gui building...
}
```
I hope I managed to explain how this design works.

**But, is there a better way to write such a gui building class?**

---

### Post by froggyswamp on 2009-06-17
If you really have such a lot of widgets, then "creating" them all inside a single Java class and dispatching them to the corresponding classes isn't the way I usually take.

Say you have 3 major containers in your app: a toolbar, a menubar and a panel with other components. In such a case every container should take care of its own widgets (all creation done inside container's constructor) and provide getter methods to those components that you might need from outer classes. There are slight variations to this approach but the logic behind is the same.
This lets you look for the widget inside the container where it belongs, rather then holding a huge huge all-knowing class - it's (always) better to have 10 classes each 50KB rather than 1 class of 500KB.

If your project isn't too big you could post it here see what I/we can do.

A static helper "factory" class to create basic widgets (i.e. buttons) will also be welcome.

---

### Post by spupy on 2009-06-17
Well, the important components are less than 15. What I have right now is that the Gui class holds them, while the builder uses the setters of the Gui class to pass the displayed components to Gui. I didn't want to have bajillion setters, so instead I used the default modifier (which is what's bugging me).
So what your proposition is: instead of the builder(s) using the setters of the Gui, the Gui uses the getters of the builder(s). (Instead of the builder "giving", the Gui is "getting".) Did I understand you correctly? I didn't think of this approach, but it seems nice.

---

### Post by froggyswamp on 2009-06-17
I f you post your project I could recreate it the way I mean, better see the actual code I guess.

---

### Post by spupy on 2009-06-17
> **froggyswamp said:**
> I f you post your project I could recreate it the way I mean, better see the actual code I guess.

Unfortunately, I can't post the code. :/
But I think I get your idea. Thank you for it.

---

