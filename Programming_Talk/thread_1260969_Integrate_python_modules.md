---
title: "Integrate python modules"
date: 2009-09-08
forum: Programming Talk
---

### Post by nipunreddevil on 2009-09-08
In my application i wish to use VPython,PIL,Matplotlib,Pygame,Cairo,wxPython/PyGtk.How can all these be integrated

---

### Post by Tony Flury on 2009-09-08
What do you mean by integrated ?

They are libraries/bindings and you will need (i would imagine) to investigate them individual to use them together - I know for instance pyGTK has a good tutorial, and an excellent reference web site.

How you use them together is primarily up to your and what your application needs to do.

Maybe if you could be a bit clearer on what you are trying to acheive then you might get some more specific help.

---

### Post by nipunreddevil on 2009-09-08
i would basically want a multithreaded program where each module i.e.
1.main computation
2.image plotting in pil/pygame
3.3d graphics in VPython
4.Geographical Map functions using matplotlib

where 2,3,4 get their data from main computation 
All these threads must be called and the values to be used in2,3,4 be updated and new image/plot be generated according to them.
All this should occur in a GUI

---

### Post by Tony Flury on 2009-09-08
Sounds entirely possible, although I have never played with multi-threading.

I would be tempted to tackle each bit at time - get each thread to work, and then work out how to synchronise between the threads etc, and between the thread and the gui.

For something this complex - i would write out the design first -before i even touched the code. Worry about the design and not the technology that you will use to implement it.

Good luck.

---

### Post by nipunreddevil on 2009-09-08
> **Tony Flury said:**
> Sounds entirely possible, although I have never played with multi-threading.

I would be tempted to tackle each bit at time - get each thread to work, and then work out how to synchronise between the threads etc, and between the thread and the gui.

For something this complex - i would write out the design first -before i even touched the code. Worry about the design and not the technology that you will use to implement it.

Good luck.
How do you do the design writing part.All that i have done is always start with coding.Please elaborate.

---

### Post by CptPicard on 2009-09-08
Well... sounds like the sort of vague architectural problem a programmer is supposed to be able to solve himself instead of asking others how to do it. That's what writing software is all about, after all.

But, yeah, looks like you want to have some sort of separate model that then fires events to the GUI displays that are listeners to the model, MVC-style. I do feel like your hodgepodge collection of libraries is a bit too much of variable assortment for your application (I've been following your "how do I do this" threads)... I would just pick a widget set, use the canvas widget (or whatever the custom drawing surface is) for the 2D and use OpenGL for the 3D ... vpython looks like a bit of an "educational toy" for your purposes...

---

### Post by nipunreddevil on 2009-09-08
> **CptPicard said:**
> Well... sounds like the sort of vague architectural problem a programmer is supposed to be able to solve himself instead of asking others how to do it. That's what writing software is all about, after all.

But, yeah, looks like you want to have some sort of separate model that then fires events to the GUI displays that are listeners to the model, MVC-style. I do feel like your hodgepodge collection of libraries is a bit too much of variable assortment for your application (I've been following your "how do I do this" threads)... I would just pick a widget set, use the canvas widget (or whatever the custom drawing surface is) for the 2D and use OpenGL for the 3D ... vpython looks like a bit of an "educational toy" for your purposes...

Well you know that i a helpless student living in a place where not many people even know about Linux,Python,GUI designing.All this is not a part of my curriculum and i have resorted to hit and trial of late.It will be appreciated if experts like you guide newbies like me.I feel sorry for posting "stupid" threads but ubuntu forums have been my only source of help.

---

### Post by Bryantos on 2009-09-08
If you need help with designing your code beforehand, than you should hit up your local bookstore for a book on design patterns.

---

### Post by nipunreddevil on 2009-09-08
> **Bryantos said:**
> If you need help with designing your code beforehand, than you should hit up your local bookstore for a book on design patterns.

May you recommend some book.

---

### Post by CptPicard on 2009-09-09
I really feel like you'd be better served just hacking on some small things for the purpose of learning... this is exactly the kind of stuff nobody can be "told" how to do it in the general case, it comes with time, patience and learning. No royal road to mathematics and so on. You may want to start by some example where you set up some GUI to draw something, and then create a model object that has the GUI view side registered as a listener and that then just fire off events as the model side changes, possibly as a result of a separate model-manipulation thread. Look up "model-view-controller", the typical architectural solution for stuff like this.

If something is unclear, it would be helpful if you were able to identify the point of difficulty explicitly, specific questions are always much more easy to answer.

---

