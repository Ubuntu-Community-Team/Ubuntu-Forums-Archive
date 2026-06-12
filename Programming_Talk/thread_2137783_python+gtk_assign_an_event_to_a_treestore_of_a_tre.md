---
title: "python+gtk: assign an event to a treestore of a tree widget?"
date: 2013-04-22
forum: Programming Talk
---

### Post by MAFoElffen on 2013-04-22
I want to dynamically assign a tree widget to represent a device controller and drives o that controller represented as treestores of that tree. From that visual representation, I want to select a drive... right click event to bring up a menu of methods to apply on that drive.

I can add an EventBox to a window and assign a widget to it, to inherit event behaviors, where it would not normally be recognized without it... So i can create a right click event on a tree... But I cannot get a treestore to inherit an event separately as an individual distinct item.

I have functions I want to do to apply individual drives and separate functions to controller devices they are members of... But having problems dividing that up within children of a widget. I've tried different ways and keep getting errors, if I try to apply an event to a treestore... Treestores don't seem to want to take a cursor map either... Then again, having problems with ID'ing a treestore as a unique identity also. Although I can apply variables and apply treestores as a dynamic array to create and display it with no problems.

Any ideas on how to do right click on a tree's treestore and have that popup menu popup be applied to that "limb" which is different different than the same evnet on the root of that tree?

I'm almost to the point of recreating that widget dynamically as an array of "label" widgets to look, act and react like a tree widget, but to where I can still break it back down into individual easily recognized pieces.

---

### Post by MAFoElffen on 2013-04-24
I figured it out. A gtk.Liststore can hold widgets. I added an eventbox that had a watched right-click event.

---

