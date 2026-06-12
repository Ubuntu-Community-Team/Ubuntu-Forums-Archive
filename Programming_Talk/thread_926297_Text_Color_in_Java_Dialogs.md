---
title: "Text Color in Java Dialogs"
date: 2008-09-21
forum: Programming Talk
---

### Post by DBQ on 2008-09-21
Hi Everybody,

Does anybody know how to change the color of the text in the standard java dialog boxes?

I am referring to: JOptionPane


Can this even be done?

Thank You.

---

### Post by patrickballeux on 2008-09-21
For all components of Swing, the obj.setForeground(Color c); will select the color to be shown.  Some classes are using also obj.setColor(Color c);

An easy way is :

mycomponent.setForeground(java.awt.Color.BLUE);


Hope it helped!

Patrick

---

### Post by DBQ on 2008-09-21
What if I wanted to change only a part of the text of the JOPTIONPANE?

---

### Post by patrickballeux on 2008-09-26
What do you mean part of it?

If you want different colors, you will have to put different components (Labels, text box, ...)

Is that what you mean?

You cannot have several color for one component.

---

### Post by Zugzwang on 2008-09-26
> **DBQ said:**
> What if I wanted to change only a part of the text of the JOPTIONPANE?

If it is not supported, then you will need to write your own specialised JOptionPane class. Have a look at the licence of the respective class, maybe you can tweak the original source code.

---

### Post by Reiger on 2008-09-26
One of the key features of JOptionPane is that it takes *any* object for message argument. That means, you could write, for this specific purpose, a generic component (say, an JPanel extension) which deals with all you could possibly wish for; and pass such an object to the JOptionPane.

---

