---
title: "Howto Implement Copy/Cut/Paste"
date: 2009-02-01
forum: Programming Talk
---

### Post by dmendizabal on 2009-02-01
I'm new programming in Gtkmm and I almost finished my first software. But I still can't figure out how to implement the Copy/Cut/Paste features.

1. When I don't include these Actions in the ActionGroup for the menus, I can use Ctrl-C/X/V normally in my application and copy-paste any text from one Entry to another.
2. When I include the Actions in Edit (EditCopy, EditCut and EditPaste) using the accelerators and icons from the Stock, I can't have the funtionality of Ctrl-C/X/V anymore. Instead of working as copy-paste it call my slot funtion. 

It must be an easy way to sort this out. I don't thing that I will need to implement the copy-paste funtion from scratch when it is already there. Do I?

---

### Post by PC-XT on 2009-02-14
I think the default clipboard functions are just for text, so when you make your own, it uses them, as it assumes they are better suited to your application. Perhaps you could identify the actions differently to avoid this, but it would tend to complicate things.

---

