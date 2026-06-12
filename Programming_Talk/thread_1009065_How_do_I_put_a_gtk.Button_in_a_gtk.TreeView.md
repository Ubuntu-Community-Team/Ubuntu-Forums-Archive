---
title: "How do I put a gtk.Button in a gtk.TreeView?"
date: 2008-12-12
forum: Programming Talk
---

### Post by derrick81787 on 2008-12-12
Hello everyone,

I'm working on a little program using PyGtk, and I need to put a button in a treeview object.  I've managed to put text and images in the treeview, but I cannot seem to figure out how to display just a regular button.  I'm sure this has been done many times, so can someone please help me out?

Thanks,
Derrick

---

### Post by Tony Flury on 2008-12-12
I think you need to use a CellRendered - there is an example - i think in the pyGTK tutorial that shows how to do this.

---

### Post by derrick81787 on 2008-12-12
> **Tony Flury said:**
> I think you need to use a CellRendered - there is an example - i think in the pyGTK tutorial that shows how to do this.

I've been looking there and various other places, but I just can't find it.  The closest thing I can find is a checkbox, but I want to have just a regular button.  I figured that there would just be a way to just display a generic widget, but I can't seem to find it anywhere.

---

### Post by Tony Flury on 2008-12-12
Ok - i think you might need to ask your self why do you need a button ?

Why not use an image - and use of the signals (i think activated signal) to determin and act on which row has ben chosen ... ?

---

### Post by derrick81787 on 2008-12-12
> **Tony Flury said:**
> Ok - i think you might need to ask your self why do you need a button ?

Why not use an image - and use of the signals (i think activated signal) to determin and act on which row has ben chosen ... ?

Well, the TreeView is acting as a queue of jobs to be done, and each row has some information in it.  I want to have a cancel button on each row so that when the button is clicked, a dialog pops up asking if the user would like to cancel the job that is represented by that row of data in the TreeView.  I can use an image, but I want the user to have to click on that image for the dialog to pop up.  Just clicking anywhere else on the row shouldn't cause that to happen.  Does this sound possible?

---

### Post by slavik on 2008-12-12
I would just list the jobs and have a cancel button outside of the treeview, this way, the user could select multiple jobs (ctrl+click or shift+click) and calcel them all in 1 go.

---

### Post by derrick81787 on 2008-12-14
> **slavik said:**
> I would just list the jobs and have a cancel button outside of the treeview, this way, the user could select multiple jobs (ctrl+click or shift+click) and calcel them all in 1 go.

Yeah, I'll just do that.  I didn't think about the multiple cancellation scenario.

---

### Post by nhale25 on 2009-02-22
Hi,

I've got the same problem of trying to put a button in a treview.  Is there a way of doing this?  Unlike the post above, I think this is the best way to go for my app.

Why isn't it possible to just add any widget to a treeview?

Thanks
Nick

---

### Post by derrick81787 on 2009-02-22
> **nhale25 said:**
> Hi,

I've got the same problem of trying to put a button in a treview.  Is there a way of doing this?  Unlike the post above, I think this is the best way to go for my app.

Why isn't it possible to just add any widget to a treeview?

Thanks
Nick

I don't know. I never did figure out how to do it, but I'd still be interested in knowing how.

- Derrick

---

### Post by spupy on 2009-02-22
> **nhale25 said:**
> Hi,

I've got the same problem of trying to put a button in a treview.  Is there a way of doing this?  Unlike the post above, I think this is the best way to go for my app.

Why isn't it possible to just add any widget to a treeview?

Thanks
Nick

I just started working with TreeView few days ago. As far as I understand it, you have to define you own custom CellRenderer to display Buttons. The supplied renderers work only for text and images, don't they?

EDIT: I just remembered that Transmission has a TreeView in the files list. At the end of each row there is a combo box (in a separate column). Transmission is written in C, but I think looking at that code might be helpful.

---

