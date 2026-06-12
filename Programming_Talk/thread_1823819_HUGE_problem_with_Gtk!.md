---
title: "HUGE problem with Gtk!"
date: 2011-08-12
forum: Programming Talk
---

### Post by nickos on 2011-08-12
Hey everybody!


I am having a HUGE problem with GTK+ on GNOME.

at first i setted as child a menu to the window.Then wanted to place onother vbox but failed because as the error stated window can only have one child at a time.I tried creating a vbox as child of window that will contain as child the vboxes of the menu and the main shell.However when adding a toolbar i noticed a huge gap between the toolbar and the menu.Then i tried adding scrollbars to the box.It completely failed.

So what do i have to do so that nothing is messed up?Is there any special technique?


Huge thanks to anyone who answers ! :)

---

### Post by bouncingwilf on 2011-08-12
It's all a little tricksy to start with but you'll get the hang of it. I suggest you try and work from one of the tutorials. The gtk+ one is ok but you might find it easier to follow this one.
[http://zetcode.com/tutorials/gtktutorial/](http://zetcode.com/tutorials/gtktutorial/)


Bouncingwilf

---

### Post by JupiterV2 on 2011-08-12
What you need to understand is that there are two ways to attach widgets, via a container and via a packing widget. vboxes, hboxes and tables are examples of packing widgets. Windows and frames are examples of container widgets. A container can only contain a single widget whereas a packing widget can have multiple widgets packed within it. So, you would normally **add** a packing widget into a container first then **pack** additional widgets into the box.

As already stated, look into a tutorial. Using the API will help too.

---

### Post by nickos on 2011-08-13
i have been using the api for 2 months, but i still cant understand how i can have many widgets in the wind ow.Do i have to create a package window and add the others into it?I already made a vbox and added the other widgets but still nothing.

---

### Post by JupiterV2 on 2011-08-13
Then I strongly suggest you follow a tutorial. [This one]("http://developer.gnome.org/gtk-tutorial/2.90/") is from the GTK team themselves and there are others out there. You are clearly missing some key concepts of writing an interface from scratch. You could also look at this [glade tutorial]("http://tadeboro.blogspot.com/2009/09/glade3-tutorial-1-introduction.html") which has been recommended by the GTK/Gnome team.

---

### Post by nickos on 2011-08-13
I DO appreciate your help,however you are making things more messy for me,so i decided to experiment.

The plan is a menubar,toolbar and an image.
Since window can only hold one child i created a vertical box as a window child.
Then i box_pack_started the vertical boxes of the menubar,toolbar and image on their parent vbox,the window's child obviously.Since you seem to be more skilled, id appreciate a reply if that is valid or not.

---

### Post by JupiterV2 on 2011-08-13
> **nickos said:**
> I DO appreciate your help,however you are making things more messy for me,so i decided to experiment.

The plan is a menubar,toolbar and an image.
Since window can only hold one child i created a vertical box as a window child.
Then i box_pack_started the vertical boxes of the menubar,toolbar and image on their parent vbox,the window's child obviously.Since you seem to be more skilled, id appreciate a reply if that is valid or not.

Thank you for your appreciation of my assistance, I just wish you'd follow it. =) I'll answer your question with a question of my own: Did it work?

---

### Post by nickos on 2011-08-13
> **JupiterV2 said:**
> Thank you for your appreciation of my assistance, I just wish you'd follow it. =) I'll answer your question with a question of my own: Did it work?

yes that time it did work,i also took a quick look at the second link you showed me which did make things a little more clear.Despite it worked i would ask if its a correct method or im making thigs more complicated (:

---

### Post by JupiterV2 on 2011-08-14
It is the only method:

```
Window (container)
  `- vbox (packing widget)
       `- menubar
       `- toolbar
       `- scrolled window (container)
             `- image
```
As you can see, only a single widget may be added to a container but multiple widgets may be packed into a box.

To create an interface in GTK+, especially if you are doing it within the source code, you should work out a widget hierarchy. You must figure out before hand what your widget tree is going to look like otherwise you're going to have a difficult time placing widgets properly.

I'll also warn you, menubars and toolbars are not the easiest widgets to work with if you don't first understand how to use basic widgets, like the window, vbox, label and button, first.

---

### Post by nickos on 2011-08-14
you didnt reply to me with a yes or no,but i will take this as a yes ;)

---

