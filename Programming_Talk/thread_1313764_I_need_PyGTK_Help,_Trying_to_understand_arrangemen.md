---
title: "I need PyGTK Help, Trying to understand arrangement"
date: 2009-11-04
forum: Programming Talk
---

### Post by SoftwareExplorer on 2009-11-04
Hi.
I'm trying to understand [[COLOR="DeepSkyBlue"]this tutorial[/COLOR]]("http://www.zetcode.com/tutorials/pygtktutorial/layout/"), and the alignment.py example works, but I have questions.
Here's the example ```
#!/usr/bin/python

# ZetCode PyGTK tutorial 
#
# This example shows how to use
# the Alignment widget
#
# author: jan bodnar
# website: zetcode.com 
# last edited: February 2009


import gtk


class PyApp(gtk.Window):

    def __init__(self):
        super(PyApp, self).__init__()

        self.set_title("Alignment")
        self.set_size_request(260, 150)
        self.set_position(gtk.WIN_POS_CENTER)

        vbox = gtk.VBox(False, 5)
        hbox = gtk.HBox(True, 3)
        
        valign = gtk.Alignment(0, 1, 0, 0)
        vbox.pack_start(valign)
        
        ok = gtk.Button("OK")
        ok.set_size_request(70, 30)
        close = gtk.Button("Close")
        
        hbox.add(ok)
        hbox.add(close)
        
        halign = gtk.Alignment(1, 0, 0, 0)
        halign.add(hbox)
        
        vbox.pack_start(halign, False, False, 3)

        self.add(vbox)

        self.connect("destroy", gtk.main_quit)
        self.show_all()
        

PyApp()
gtk.main()

```
It accomplishes the goal of putting the buttons in the lower right corner. But it seems like Halign should be inside of Valign instead of Valign being empty but taking up the space above Halign, pushing it to the bottom. That is if I have the right idea of how gtk.Alignment works. Your supposed to put something inside of a gtk.Alignment and the gtk.Alignment thing will make it stick to what ever side you specified when you did something=gtk.Alignment(#, #, #, #) So, do I have the right idea about how that works?

I tried to edit the example to make Halign inside of Valign, but it didn't do what I thought it would. The buttons ended up on the left bottom side instead of the right bottom. Here's my version (which didn't do what I thought it would, why is that?)```

import gtk
class PyApp(gtk.Window):
    def __init__(self):
        super(PyApp, self).__init__()
        self.set_title("Alignment")
        self.set_size_request(260, 150)
        self.set_position(gtk.WIN_POS_CENTER)
        vbox = gtk.VBox(False, 5)
        hbox = gtk.HBox(True, 3)
        valign = gtk.Alignment(0, 1, 0, 0)
        ok = gtk.Button("OK")
        ok.set_size_request(70, 30)
        close = gtk.Button("Close")
        hbox.add(ok)
        hbox.add(close)
        halign = gtk.Alignment(1, 0, 0, 0)
        halign.add(hbox)
        valign.add(halign)
        vbox.pack_start(valign)
        self.add(vbox)
        self.connect("destroy", gtk.main_quit)
        self.show_all()

PyApp()
gtk.main()
```

Thanks for the help--I though I understood how it worked, but now I'm just really confused.

---

### Post by Brandon Williams on 2009-11-04
Once you add halign into the valign container, its horizontal alignment within the valign object will be controlled by the settings of valign, causing it to have no real effect, since the valign will put all empty space to the right of the halign and leave the halign no empty horizontal space to work with.

In order to get your modification to work the way that you expect, you have to change the initialization of valign, too.
```
        valign = gtk.Alignment(1, 1, 0, 0)
```

This will tell the valign to put all empty space to the top and the left. 

Once you've made this change, the halign can simply be removed, and you can add the hbox to valign instead of halign.
```
import gtk
class PyApp(gtk.Window):
    def __init__(self):
        super(PyApp, self).__init__()
        self.set_title("Alignment")
        self.set_size_request(260, 150)
        self.set_position(gtk.WIN_POS_CENTER)
        vbox = gtk.VBox(False, 5)
        hbox = gtk.HBox(True, 3)
        valign = gtk.Alignment(1, 1, 0, 0)
        ok = gtk.Button("OK")
        ok.set_size_request(70, 30)
        close = gtk.Button("Close")
        hbox.add(ok)
        hbox.add(close)
        valign.add(hbox)
        vbox.pack_start(valign)
        self.add(vbox)
        self.connect("destroy", gtk.main_quit)
        self.show_all()

PyApp()
gtk.main()
```

---

### Post by SoftwareExplorer on 2009-11-05
So do boxes and alignment containers shrink wrap down to what is inside them, or do the alignment containers make that happen? Or do the alignment containers, since they can only have one item, make whatever is inside the box which is inside the alignment container move inside the box?

Also, is there a way to see these boxes so I can see what is happening instead of guessing?

---

### Post by Brandon Williams on 2009-11-05
If I understand it correctly, alignments are greedy. They will fill up all the space they're allowed to consume. The layout of any empty space they acquire through greediness is dictated by the constructor parameters. Also, the greediness causes an alignment to give the smallest amount of space necessary to its contents (which is why putting the halign inside the valign doesn't do anything; the halign doesn't have any extra space to play with). On the other hand, boxes are not inherently greedy (I think that you can configure them to be greedy, though). By default, a box will only ask for the amount of space that it requires to display its contents.

I don't normally lay things out by hand. It's time consuming, and requires a fair bit of experimentation for me to get it right. Instead, I use glade to design the GUI part of an app. With glade, I can see precisely what the effect of a change is, and it will put a box around the currently active element. It's just a faster way to design and implement a graphical app, allowing you to focus on the internal logic, rather than where the pixels in the window are going to end up.

If you really want to learn to lay things out by hand, glade can still be helpful, since it allows you to immediately see how the various parameters work and what impact they have on your layout.

---

### Post by SoftwareExplorer on 2009-11-07
Ok, I messed around with glade, but I don't really know how to use the files it makes just yet. I guess I'll have to read up on how to do that.

---

### Post by Brandon Williams on 2009-11-07
[Here](http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/) and [here](http://www.linuxjournal.com/article/6586) are a couple of good places to start. And of course the tutorial at [pygtk.org](http://www.pygtk.org/articles/application-pygtk-glade/Building_an_Application_with_PyGTK_and_Glade.htm).

---

### Post by ukblacknight on 2009-11-07
> **Brandon Williams said:**
> [Here](http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/) and [here](http://www.linuxjournal.com/article/6586) are a couple of good places to start. And of course the tutorial at [pygtk.org](http://www.pygtk.org/articles/application-pygtk-glade/Building_an_Application_with_PyGTK_and_Glade.htm).

That pygtk website isn't working for me - is it for anyone else?

---

### Post by days_of_ruin on 2009-11-07
> **Brandon Williams said:**
> [Here](http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/) and [here](http://www.linuxjournal.com/article/6586) are a couple of good places to start. And of course the tutorial at [pygtk.org](http://www.pygtk.org/articles/application-pygtk-glade/Building_an_Application_with_PyGTK_and_Glade.htm).

Those tutorials are outdated. Check out the ones listed here: [http://live.gnome.org/Glade/Tutorials]("http://live.gnome.org/Glade/Tutorials")
> **ukblacknight said:**
> That pygtk website isn't working for me - is it for anyone else?

[Not just you.]("http://downforeveryoneorjustme.com/pygtk.org")

---

### Post by SoftwareExplorer on 2009-11-13
Thank you for all the advice. Sorry it took so long for me to reply, I just got busy with college.

---

