---
title: "GUI logic design"
date: 2009-07-01
forum: Programming Talk
---

### Post by Dbugger on 2009-07-01
Lately I've been programming in Windows Forms and an issue has come to my mind that I think is encountered in all the tools to design GUIs.

Let's say I have a Parent Form that has 2 containers. Each container has components that interact with the components of his own container and with components of the other container.

Where would you locate the code to do this?

The way I've been doing is using a lot of "this.Parent.Parent.form["whatever"].Textbox ...." but seems kinda messy to me.

What do you guys do for this?

---

### Post by simeon87 on 2009-07-01
How about having a class in between, where the components of both containers can read and write from? Effectively, this would create a model and the containers would be the view/controller (can be separated further I guess), see: [http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller](http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller)

---

### Post by Dbugger on 2009-07-01
I dont mean to separate the "business logic" from the UI; that's already clear. The thing the UI has some logic by itself.

Let me put you a "for instance":

> I hace a "mainPanel" that contains another 2 panels "panel1" and "panel2". In "panel1" there are 2 buttons. If the first button is pressed, in "panel2" appear a Label. If the second button is pressed, in "panel2" appear a TextBox.

Now I usually put the event handling of each button inside the code of "panel2", but the I have to use this annoying "this.parent.parent.child[2].child[1]... blabla" way of comunicating between components which seems kinda messy to me.

How do you guys do it?

---

