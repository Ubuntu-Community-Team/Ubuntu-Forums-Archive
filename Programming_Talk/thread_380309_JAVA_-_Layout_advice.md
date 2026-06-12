---
title: "JAVA - Layout advice"
date: 2007-03-09
forum: Programming Talk
---

### Post by serlex on 2007-03-09
I'm trying to layout labels with text field in a panel. Java layout-managers are making me very angry

Any advice on how I should do this. Screenshot below

---

### Post by Ragazzo on 2007-03-09
Here's an overview of the different layouts: [http://java.sun.com/docs/books/tutorial/uiswing/layout/visual.html](http://java.sun.com/docs/books/tutorial/uiswing/layout/visual.html)

I would use SpringLayout with the help of [SpringUtilities.java]("http://java.sun.com/docs/books/tutorial/uiswing/layout/examples/SpringUtilities.java") that is used in the examples.

---

### Post by Engnome on 2007-03-09
What layout type are you using now? FlowLayout?

Try Grid or spring layout.

[http://java.sun.com/docs/books/tutorial/uiswing/layout/visual.html](http://java.sun.com/docs/books/tutorial/uiswing/layout/visual.html)

Edit: too slow :/

---

### Post by serlex on 2007-03-09
EDIT: at that screenshot i was not using a layout,

OK, grid seem to be the easier option. Did a simple ```
setLayout(new GridLayout(0,2,30,30));
```

that gay me occured gaps :( . Spring looks very complicated, im gona have a go now

---

### Post by phossal on 2007-03-09
For all but the most *basic* GUI's, I recommend netbeans. It's a pain to switch back and forth (as I do) between eclipse and netbeans, but GUI building is so much easier that it's a net improvement.

---

### Post by serlex on 2007-03-09
ahh not netbeans :( thanks anyways

---

