---
title: "Events in different classes."
date: 2010-05-30
forum: Programming Talk
---

### Post by Axolotl9250 on 2010-05-30
Hi, I've carried on trying to learn wxPython practically by building a text editor. I've done it successfully with just a text area and a file menu with About, Open, and Exit options, that was all in one frame class. Then I did the same with wxGlade to see how this differs in code generation and such as I'm interested in it to speed up app making as I'm a Biology student, computer literate but not an expedient programmer or linux user by any means. 

Anyway, now I'm trying out writing code for different classes i.e. with my current thing I'm taking the code from the simple text editor and organising the code differently, and I've got the TextCtrl, and a close button in a panel, organised by sizers. And then that panel is in the frame which also has the file menu. My question is, do i need to create the close button in the panel it's own event in that class? Or can I link it to the event in the frame section, that controls the 'exit' option in the filemenu of my code instead? They both do the same thing, close the program, so writing out a event in the panel class for the close button seems a waste of space and a violation of the DRY principle. 

Also I've seen code where people put buttons and sizers and everything in their own class, where with my online tutorials, they included buttons and sizers as parts of other classes i.e. with my text editor, the code for the close button is part of the panel class chunk of code. What is the difference/advantage of having every single thing in its own class this way? 

Looking forward to being enlightened :) Thanks.

---

