---
title: "Tutorials for python Gtk.TreeView + Glade Template"
date: 2013-01-15
forum: Programming Talk
---

### Post by Nebelhom on 2013-01-15
Hi Guys,

Does anyone of you know a good Tutorial, that talks in depth about Gtk.TreeView und Gtk.ListStore together with a Glade template?

I am already aware of the following ressources:

[The Python GTK +3 Tutorial](http://python-gtk-3-tutorial.readthedocs.org/en/latest/)
[GTK +3 Reference Manual](http://developer.gnome.org/gtk3/stable/)
[GTK +3 Beginner's Tutorial](http://developer.gnome.org/gnome-devel-demos/unstable/tutorial.py.html.de)
[Hari's Corner](http://harishankar.org/blog/entry.php/python-gtk-howto-cell-rendering-a-treeview-created-in-glade) (more of a use-case than a tutorial)

I've been trying for a while now to find out how to move the selected elements in the table one position up (or down). However, from there I realised that I not only wasn't able to do that, but also that I don't get what the designers of that widget had in mind when designing it.

I also have no knowledge of C or C++, so I am stuck there, too ;)

Thanks a lot for your help.

Johannes

---

### Post by Nebelhom on 2013-01-16
Really noone? ah well, too bad.

As a last resort. Could someone point me to a forum or mailing list where someone "might" be able to answer my question?

Cheers guys :)

---

### Post by r-senior on 2013-01-16
> **Nebelhom said:**
> Does anyone of you know a good Tutorial, that talks in depth about Gtk.TreeView und Gtk.ListStore together with a Glade template?
Tutorials for Python + GTK3 + Glade are pretty hard to find so I'm not surprised nobody has come up with any other than those you mention. 

When I've done it in the past there's been a lot of interpretation and sometimes guesswork based on looking at the Python GTK3 documentation and seeing how that translates to the underlying GTK3 library. It's not ideal but that's the way it is. With a bit of practice you can guess the Python equivalents of what is in the GTK3 docs. 

> I've been trying for a while now to find out how to move the selected elements in the table one position up (or down). However, from there I realised that I not only wasn't able to do that, but also that I don't get what the designers of that widget had in mind when designing it.
The tree and list widgets use a Model View Controller (MVC) pattern. You don't move elements as such, you manipulate the underlying model. So that means one of two strategies:

a. Use a sorted model based on GtkTreeModelSort and change values in the column that you are sorting on. This is the approach you'd probably take if you were using a database.

b. Use a plain list or tree store and use functions like move_before, move_after or swap to change the order. This might be a good approach if you were serializing the model somehow for persistence.

What's the scenario? Drag and drop to reorder? What's your underlying persistence mechanism?

---

### Post by Nebelhom on 2013-01-17
Hi r-senior,

thanks for taking the time to answer my question. I will try to answer yours, but I am only a hobby programmer, so I "may" use wrong terminology now and again (or so I've been told).

> What's the scenario? Drag and drop to reorder? What's your underlying persistence mechanism? 

The background:
The popular [pdf chain]("https://apps.ubuntu.com/cat/applications/precise/pdfchain/") has stopped working ever since I updated to Ubuntu 12.04 and despite valiant efforts, I couldn't get it to work.

I need it, so I am writing a python version (cos that's the language I know). Gtk.TreeView's function is simple: Assemble the files in a list. Order them if necessary and then take the files and sort them according to the order in the list (top to bottom). I modelled it on the pdf chain GUI. So, there is no persistence necessary as far as I can see it.

Does this answer your question?

> When I've done it in the past there's been a lot of interpretation and sometimes guesswork based on looking at the Python GTK3 documentation and seeing how that translates to the underlying GTK3 library. It's not ideal but that's the way it is. With a bit of practice you can guess the Python equivalents of what is in the GTK3 docs. 

Yep, this is what I've done so far, but not understanding the concept made it harder. Thanks to you, I know at least what they had in mind :) Thanks a bundle for the explanation :)

---

### Post by r-senior on 2013-01-17
> **Nebelhom said:**
> Gtk.TreeView's function is simple: Assemble the files in a list. Order them if necessary and then take the files and sort them according to the order in the list (top to bottom). I modelled it on the pdf chain GUI. So, there is no persistence necessary as far as I can see it.
OK, so you can probably just work with an unsorted list model and on those up and down arrow buttons, swap the current row with the one above or below. Then, when the user is done with reordering, get an iterator and work through the rows in order.

---

### Post by Nebelhom on 2013-01-19
> OK, so you can probably just work with an unsorted list model and on those up and down arrow buttons, swap the current row with the one above or below. Then, when the user is done with reordering, get an iterator and work through the rows in order. 

Hi r-senior,

the main issue that I am having is, that I can't get the items to "switch" the positions. I manage to get the selections that I made and so on, but I am not able to use the Gtk specific types to my advantage. Due to lack of information, I am trying to use the model like a list, which in some instances works and in others (like this one) doesn't. I attached a simplified example with no specific cases to explain the problem.

```
def on_upbutton_clicked(self, button):
    """
    Moves each selection one position up.
    """
    # get the selected rows as paths
    sel_model, sel_rows = self.merge_view.get_selection().get_selected_rows()

    # store the treeiters from paths
    iters = []
    for row in sel_rows:
        iters.append(self.merge_model.get_iter(row))
    
    for i in iters:
        if i is not None:
            # get the previous position, too
            prev_iter = self.merge_model.iter_previous(i)
            
            # Test that the items are both valid
            print "1. " + self.merge_model[prev_iter][0]                  
            print "2. " + self.merge_model[i][0]
            
            # Try to swap like in a list
            self.merge_model[prev_iter], self.merge_model[i] = self.merge_model[i], self.merge_model[prev_iter] 
            
            # This gives a Type Error as the type has changed to 'TreeModelRow'
            print "1. " + self.merge_model[prev_iter][0]                    
            print "2. " + self.merge_model[i][0]
```

What I am trying to show here is, that on "switching",I suddenly fall victim to a change in type, which I find very odd.

Using the selected rows from 'sel_model, sel_rows = self.merge_view.get_selection().get_selected_rows()' also doesn't work as they are Gtk.TreePath types. Another type where I have no clue why it exists.

I am not sure if I made sense here, if I haven't please let me know and I try to be clearer. Thanks for your help.

As a side note, this has strayed quite far from the original topic that I am considering to change the title. Is that possible... or wise?

---

### Post by Nebelhom on 2013-01-20
> b. Use a plain list or tree store and use functions like move_before, move_after or swap to change the order. This might be a good approach if you were serializing the model somehow for persistence.

Sorry dude, I entirely misread that entry ;). It works now. Thanks for your help.

I leave this article "unsolved" as I am still hoping for more tutorial entries :P

---

