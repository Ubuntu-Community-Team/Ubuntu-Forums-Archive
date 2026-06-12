---
title: "Glade Interface Designer rendering problems"
date: 2010-08-20
forum: Programming Talk
---

### Post by machinogodzilla on 2010-08-20
Hi,


I am using Ubuntu 10.04.1 and just started my adventure with Glade 3.6.7. It was all fine until suddenly and for no obvious reason Glade started displaying misshaped GUIs.

From then on any file I save and then open again in Glade looks similar to what is in the attachment. If you go through the properties of widgets in Glade and start refreshing them by unchecking and checking boxes again, modifying text content etc. the widgets and they content will start reappearing.

Is it a known problem? Does anyone know a solution to it?


EDIT: It also froze another time today while adding items to a vertical box (and also when changing the position of an element), which meant that I had to go through that 'refreshing' process yet again. But what I have just found out was that adding a parent container to the second outside most element refreshes all children within that element.

.

---

