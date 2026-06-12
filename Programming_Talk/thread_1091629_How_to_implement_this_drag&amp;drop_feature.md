---
title: "How to implement this drag&amp;drop feature?"
date: 2009-03-09
forum: Programming Talk
---

### Post by tneva82 on 2009-03-09
Here's the thing. I have program X. It deals with certain classes that gets drawn to screen. User can drag some of these(which I can determine with class method) around with mouse. So far things are working allright.

The classes are stored in list<GUIObject*> in order that last dragged/clicked/whatever is in front.

Certain classes which inherit from GUIObject can contain new GUIObjects which are then moved around when parent object gets moved around. This also works ATM.

What I now need to figure out is how to implement drag&drop so that when object is dropped to object that accepts child objects pushes object to front of list and child is removed from parent objects list(if it had parent). If object is dropped into object that doesn't accept childs object should return to where it was(original position is stored when drag begins). Finally if dragged object has no parent it doesn't care if target doesn't accept childs(but is added if it does).

Thought it should be easy but so far every attempt has resulted in non-working system with segmentation faults added to mix. Doh.

Any suggestions?

---

### Post by cabalas on 2009-03-09
Off the top of my head the first way I would try is to keep a list containing pointers to all of the GUIObjects that support being dropped into, irregardless of who their parent is, then when something is moved all you have to do is iterate through the list and check whether it was dragged onto any of the items in the list.

---

### Post by tneva82 on 2009-03-09
> **cabalas said:**
> Off the top of my head the first way I would try is to keep a list containing pointers to all of the GUIObjects that support being dropped into, irregardless of who their parent is, then when something is moved all you have to do is iterate through the list and check whether it was dragged onto any of the items in the list.

Hum. This has just nasty side effect of adding yet another list of pointers I need to keep track of :-/ Chance of error probably grows the more I have pointers pointing to same thing essentially.

Atleast now I don't seem to be getting seg.faults. Just not working properly(though atleast not as dramatically incorrectly as it used to...).

Edit: Actually getting VERY close. Just one very odd behaviour. Alas very hard to explain what's the odd error :( But atleast I'm getting somewhere...

Edit: Basicly what happens is that I have 2 windows each with subwindow inside them. I can move windows nicely. I drag one sub window into other window. Second window can be moved and the both subwindows move just fine. Then when I try to move the other sub window it don't move. Note that if I restart program and move that one it moves but then freezes. If I then move the original one it goes all haywire. If I moved it to empty window it moves same pace as the window I'm moving. If I kept it inside that window moves become exaggerated. Move bit upward, the subwindow moves WAY up.

Hum hum. Somewhere something goes wrong but what...

Edit: If you don't understand a word of what above means and wish to know I can provide executable.

Edit: Found it. So much to do I forgot one piece of code and that was swapping parent to new one. Whoops! Now it works. Next up: Buttons!

---

