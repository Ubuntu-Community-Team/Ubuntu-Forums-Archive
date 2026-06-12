---
title: "My first GUI in C"
date: 2012-02-20
forum: Programming Talk
---

### Post by Hydrathe on 2012-02-20
Hi, newbie programmer here, I'm making a program for one of my subjects at college, the program itself is about inter process communication(pipes, message queues, signals, etc.) and although a GUI is not a must, it gives extra points. But, as the title says, its the first time I have to manage a GUI, so I'm a bit lost, basically I would like to know which is the best option to start, knowing that we are limited to C, and that we don't have administrative privileges, so it has to run out of the box in the lab's pcs(Ubuntu 10.04 LTS). 


Thanks a lot for your time!

---

### Post by doobrie on 2012-02-20
Your choices are probably Qt or GTK.  You can write C gui's in both of these.

---

### Post by Hydrathe on 2012-02-20
> **doobrie said:**
> Your choices are probably Qt or GTK.  You can write C gui's in both of these.

Hi, I followed your advice and started to read about GTK, it may sound stupid, but its the first time I have to leave the Standard C libraries and I have some doubts... 

As far as I know, I need the gtk+2.0-dev package to compile any program, it was not installed in my system by default so it wont in the labs either, I should know this already but I don't :sad: will it run without problems if I can't compile it in the machine it's gonna be tested? 


Thx a lot :)

---

### Post by CivilizationII on 2012-02-20
> **Hydrathe said:**
> Hi, newbie programmer here, I'm making a program for one of my subjects at college, the program itself is about inter process communication(pipes, message queues, signals, etc.) and although a GUI is not a must, it gives extra points. But, as the title says, its the first time I have to manage a GUI, so I'm a bit lost, basically I would like to know which is the best option to start, knowing that we are limited to C, and that we don't have administrative privileges, so it has to run out of the box in the lab's pcs(Ubuntu 10.04 LTS). 


Thanks a lot for your time!


It seams incredible that a college can give such requirement, even optional, without pointing out what framework or library to use.

Anyway, GTK is directly linked to C while QT is linked to C++, so you will need a additional wrapper to use it with C = far too much over-sophisticated. But i think that a framework is too much sophisticated for a first project.

So maybe direct X11 coding can do the trick: xLib was the 'old' way to do this, a sample in: [http://www.paulgriffiths.net/program/c/srcs/helloxsrc.html](http://www.paulgriffiths.net/program/c/srcs/helloxsrc.html) . Or xcb, the 'modern' way in [http://xcb.freedesktop.org/DevelopersGuide/](http://xcb.freedesktop.org/DevelopersGuide/) .

Those libraries also seam to be very complicated for a first project. Eventually i would try a more modest (be aware: not something you will name easy, it is only "less worth" than X11 libraries or "far less worth" than desktop's frameworks) text/graphical mode like ncurses (you will have something like the text mode for Ubuntu installation): [http://tldp.org/HOWTO/NCURSES-Programming-HOWTO](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO)

My only advise is forget about any GUI for a first C program, especially if your subject is "inter process communication (pipes, message queues, signals)", because X11 have some access right that can be different regarding the system level or user level, unless you also want to learn how to configure a Unix/Linux X11/system during your first C programming (rather unlikely).

---

### Post by Hydrathe on 2012-02-20
> **CivilizationII said:**
> It seams incredible that a college can give such requirement, even optional, without pointing out what framework or library to use.

Anyway, GTK is directly linked to C while QT is linked to C++, so you will need a additional wrapper to use it with C = far too much over-sophisticated. But i think that a framework is too much sophisticated for a first project.

So maybe direct X11 coding can do the trick: xLib was the 'old' way to do this, a sample in: [http://www.paulgriffiths.net/program/c/srcs/helloxsrc.html](http://www.paulgriffiths.net/program/c/srcs/helloxsrc.html) . Or xcb, the 'modern' way in [http://xcb.freedesktop.org/DevelopersGuide/](http://xcb.freedesktop.org/DevelopersGuide/) .

Those libraries also seam to be very complicated for a first project. Eventually i would try a more modest (be aware: not something you will name easy, it is only "less worth" than X11 libraries or "far less worth" than desktop's frameworks) text/graphical mode like ncurses (you will have something like the text mode for Ubuntu installation): [http://tldp.org/HOWTO/NCURSES-Programming-HOWTO](http://tldp.org/HOWTO/NCURSES-Programming-HOWTO)

My only advise is forget about any GUI for a first C program, especially if your subject is "inter process communication (pipes, message queues, signals)", because X11 have some access right that can be different regarding the system level or user level, unless you also want to learn how to configure a Unix/Linux X11/system during your first C programming (rather unlikely).

Thx a lot for your advice, sadly, there is a big gap between the students, some (like me) were completely new to programming, linux and computers in general, while others compiled their own kernel despite of being in the same year, teachers know that, so they always let the best students shine. I know that I'm not at the same level, but I hate to fall behind so even if it is a bit risky I would like to aim high.

Anyway I will spend some days reading all the stuff, knowing that I can relay in easier options it's a relief, and starting projects that I can't achieve is stupid, so thx for taking me back to reality.

---

### Post by r-senior on 2012-02-20
Have a look at this, should be enough to get you going with GTK:

[http://zetcode.com/tutorials/gtktutorial/](http://zetcode.com/tutorials/gtktutorial/)

You'll need the GTK development libraries to compile your program but not to run it. You should work out whether that's going to be an issue before you get in too deep.

---

### Post by Tony Flury on 2012-02-21
What about a simpler "GUI" using ncurses - I know it wont have the flashy windows etc - but as far as I know it can still do clickable buttons etc.

---

### Post by dwhitney67 on 2012-02-21
Another GUI option is to use X/Motif (i.e. the X11 library).  Here's a [link ]("http://www.ist.co.uk/motif/books/vol6A/Title.fm.html")to a Programming Manual.

Personally, I find X/Motif easier to use than GTK.

---

### Post by nebukadnezzar on 2012-02-21
Yikes, don't use GTK. Unless you use GTKMM.

Go with Qt. Here's why Qt is clearly superior:

```

#include <QtGui>
 
int main(int argc, char *argv[])
{
    QApplication app(argc, argv);
    QLabel label("Hello, world!");
    label.show();
    return app.exec();
}

```

Compare that code with the GTK Bloat:

```

#include <gtk/gtk.h>

void hello (void)
{
    g_print ("Hello World\n");
}

void destroy (void)
{
    gtk_main_quit ();
}

int main (int argc, char *argv[])
{
    GtkWidget *window;
    GtkWidget *button;
    gtk_init (&argc, &argv);
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_signal_connect (GTK_OBJECT (window), "destroy",
              GTK_SIGNAL_FUNC (destroy), NULL);
    gtk_container_border_width (GTK_CONTAINER (window), 10);
    button = gtk_button_new_with_label ("Hello World");
    gtk_signal_connect (GTK_OBJECT (button), "clicked",
              GTK_SIGNAL_FUNC (hello), NULL);
    gtk_signal_connect_object (GTK_OBJECT (button), "clicked",
                 GTK_SIGNAL_FUNC (gtk_widget_destroy),
                 GTK_OBJECT (window));
    gtk_container_add (GTK_CONTAINER (window), button);
    gtk_widget_show (button);
    gtk_widget_show (window);
    gtk_main ();
    return 0;
}

```

Another tip: Do ***NOT*** go with raw X11/Motif. You have been warned. ;)

---

### Post by pconroy on 2012-02-21
> **Tony Flury said:**
> What about a simpler "GUI" using ncurses - I know it wont have the flashy windows etc - but as far as I know it can still do clickable buttons etc.

This was my first thought.

Since I happen to be sitting here helping my 11 year old with his homework, please take this in the spirit intended:


DON'T GET TOO WRAPPED UP IN THE GUI THAT YOU FORGET TO DO THE IPC WORK!!!!

:D



If he wants a GUI then ncurses may not cut the mustard.
If all you need is just a UI for the extra credit then ncurses might be fast.

Make sure you statically link your program - or make sure whatever UI libs you pick are part of the distribution.

---

