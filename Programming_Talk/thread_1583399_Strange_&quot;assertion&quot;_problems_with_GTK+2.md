---
title: "Strange &quot;assertion&quot; problems with GTK+2"
date: 2010-09-27
forum: Programming Talk
---

### Post by bcz on 2010-09-27
I probably have a problem in my code, but if others have similar problems, then it could be a GTK issue.  So I summarise the symptoms

I have a set of"wrapper routines" interfacing GTK to pascal.  All was working fine.  A week ago, on a new bit of application code, I suddenly got GTK assertion problem freeing widgets.  Printing pointer addresses at runtime shows me the widgets should exist, but GTK says no.

A very similar program is compiling and running fine, which makes me think the problem is linked to the new code;  it just seems essentially the same as the other.

Valgrind does not find any bad memory accesses.  GDB tells me I die in GTK adding data to a non-existant widget which my program thinks still exists

An overview of what is happening:

A window opens a scrolled window in a notebook
The scrolled window vbox contains stacked fixed fields in this case containing labels
To clear the scrolled window the  labels are GtkWidgetDdestroyed, but this fails as they are not widgets.  Adding new data to the fixed field fails as it is not a widget and GTK exits (gracefully)

So the application thinks the widgets exist but GTK doesnt

I reworked the wrapper routines, and get the same problem.
Where do I go from here

Running 9.04 with latest updates

Any thoughts appreciated - Rgds Bill

---

### Post by worksofcraft on 2010-09-27
Well labels are actually GtkWidgets:
```

  GObject
   +----GInitiallyUnowned
         +----GtkObject
               +----GtkWidget
                     +----GtkMisc
                           **+----GtkLabel**
                                 +----GtkAccelLabel
                                 +----GtkTipsQuery

```

Thus it should not be assertion failing IMO. However, Gtk automatically disposes of Widgets that it thinks are not used anymore and this is based on reference counting. I have only done very simple applications so far where the top level window persists for the entire duration of the program and thus all the widgets it contains are quite safe.
I'm sort of studying how to make proper use of the smart pointers in Gtk but don't know yet how to tell if that would be what the problem is for you.

---

### Post by bcz on 2010-09-27
Thanks WorksofCraft.

I should add that the logic works fine in other cases  -- several programs using the wrapper routines.

However with the most recent program I am porting, I get what appears to be spurious assertion failures.   It would be explained if I had accidentally destroyed the widgets previously, but this does not seem to be the case.. I have reworked the wrapper routines  to examine this possibility

> However, Gtk automatically disposes of Widgets 


Assume that if you destroy a widget, then its children are destroyed by GTK automatically.  More than this will cause trouble, and if this is what is happening, then IMO it is a bug

Not sure what you mean by "smart pointers"

Tanks Bill C

---

### Post by worksofcraft on 2010-09-27
> **bcz said:**
> 
Not sure what you mean by "smart pointers"


I only recently started exploring the lower level operation of Gtk and apparently they use a system of reference counting to know when an object can be destroyed. The way this works is though a kind of "smart pointer" that keeps track of how many references are outstanding to each object: Only when that goes to zero will the object actually be deleted! 

In theory this should allow your program to hang on to widgets even after their parent container is disposed of, but it's all supposed to be handled transparently by the interface wrapper of your programming language. In C++ it is a library called gtkmm that does it for us, and presumably this is what you creating for Pascal?

Also I don't think Gtk actually frees the memory. Has own internal store of memory blocks it can recycle because there is a separate g_free() function. That might explain why nothing shows up on Valgrind, but alas I just don't know enough about it yet.

---

### Post by bcz on 2010-09-28
Thanks to All

Problem resolved.  Somehow deleted a line of code in application, which error was not picked up by my wrapper, resulting in bad data being sent to Gtk which correctly detected an assertion failure...  Fix wrapper to correct for this error and it will be easier to debug next time it happens.  Correct application code.  All done

Believe "smart pointers" are Gobject reference counts.  As I understand it, Widget addresses are fixed until destroyed (by application/wrapper or by GTK) and can be saved and used as appropriate..  Sometimes the documentation/coded examples make mention of this and it is good to follow such direction as given by those who know best

Rgds BillC

---

