---
title: "Showing new window Gtk+/C++"
date: 2012-05-01
forum: Programming Talk
---

### Post by Markanbl on 2012-05-01
Hi, I've seen that some people already asked similar questions but not about Gtk for C++.
What I want to do is to open a new window after clicking on a button in main window. So far I've not found any solution for this. Here's my code so I would like to have a totally new window after clicking on Start button. Thanks in advance...

```
#include "GraphicalInterface.h"
#include <stdlib.h>
#include <iostream>
#include <string>
using namespace std;

enum {
    COL_NAME = 0,
    COL_CONSOM,
    COL_DURATION,
    COL_START,
    COL_END,
    COL_PLANNED,
    NUM_COLS
};

GraphicalInterface::GraphicalInterface(int argc, char** argv) {

      gtk_init(&argc, &argv);

      GtkWidget *window;
      GtkWidget *start;
      GtkWidget *quit;
      GtkWidget *frame;
      GtkWidget *label;
      GtkWidget *description;
      GtkWidget *vbox;
      GtkWidget *hbox;
      GtkWidget *halign;
      GtkWidget *valign;

      gtk_init(&argc, &argv);

      window = gtk_window_new(GTK_WINDOW_TOPLEVEL);                    // creating a new window
      gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
      gtk_window_set_default_size(GTK_WINDOW(window), 500, 300);
      gtk_window_set_title(GTK_WINDOW(window), "Power Consumption");
      gtk_container_set_border_width(GTK_CONTAINER(window), 10);

      vbox = gtk_vbox_new(FALSE, 5); // creating a vertical box
      frame  = gtk_frame_new("Description"); // creating a frame where a short description will be
      label = gtk_label_new("For starting the program click on Start. This will open a new window \n\
              where you will be able to create or load a household with devices.\n\
          If you wish   to terminate the program click on Quit. Thank you!");
      gtk_label_set_justify(GTK_LABEL(label), GTK_JUSTIFY_CENTER);
      gtk_container_add(GTK_CONTAINER(frame), label); // putting description in frame
      gtk_container_add(GTK_CONTAINER(vbox), frame); // puting frame in vertical box
      valign = gtk_alignment_new(0, 1, 0, 0); // creating a new widget with alignment, not sure what are really (0,1,0,0)..i just copied it from the tutorial
      gtk_container_add(GTK_CONTAINER(vbox), valign); // adding valing to vertical box
      gtk_container_add(GTK_CONTAINER(window), vbox); // putting verctical box in our window

      hbox = gtk_hbox_new(TRUE, 3); // creating a horizontal box...for putting start and quit button

      start = gtk_button_new_with_label("Start");
      gtk_widget_set_size_request(start, 100, 50);
      g_signal_connect(start, "clicked", G_CALLBACK(newWindow), NULL); // here we will change this callback to opening a new window in which we will have load function
      gtk_container_add(GTK_CONTAINER(hbox), start); // adding start button...the rest is the same with quit button
      quit = gtk_button_new_with_label("Quit");
      g_signal_connect(quit, "clicked", G_CALLBACK(gtk_main_quit), NULL);
      gtk_container_add(GTK_CONTAINER(hbox), quit);

      halign = gtk_alignment_new(1, 0, 0, 0); // aligning horizontal box..
      gtk_container_add(GTK_CONTAINER(halign), hbox);

      gtk_box_pack_start(GTK_BOX(vbox), halign, FALSE, FALSE, 0); // adding the aligned horizontal box

      g_signal_connect_swapped(G_OBJECT(window), "destroy", // closing the window with X
            G_CALLBACK(gtk_main_quit), G_OBJECT(window));

      

      gtk_widget_show_all(window);
}
```

---

### Post by r-senior on 2012-05-01
Welcome to the forum :)

In essence, you need to replicate you have already done, i.e. create a new class that encapsulates a window, then create an instance of that window in your button handler and show it.

Did you know about gtkmm, which provides GTK bindings for C++? Saves all that casting and is more OOP:

[http://developer.gnome.org/gtkmm-tutorial/stable/](http://developer.gnome.org/gtkmm-tutorial/stable/)

Will your main window eventually contain something? I wonder if your start button would be more elegant as a menu option (File -> New Window) and toolbar button?

Have you also considered using Glade?

---

### Post by Markanbl on 2012-05-01
Actually, I've come to a solution, I've just used the same pointer to window in another function called new window but now I have a different problem. I want to create a menu in the new window and for that the functions that create have to be declared "static" but one of my functions contains "this" pointer and it doesn't work with static function.

---

### Post by Markanbl on 2012-05-01
I've done as you said, I created a new class with functions I had earlier, now they're member functions of that other class so there shouldn't be a problem with static "thingy". But, when I try to call the constructor with G_CALLBACK option in the button I get this error:

GraphicalInterface.cpp:69: error: invalid cast from type ‘GraphicalInterface2’ to type ‘void (*)()’

This is the new part of my code...
```
GraphicalInterface2 gr(argc, argv);
...
...
...
g_signal_connect(start, "clicked", G_CALLBACK(gr), NULL);
```

---

### Post by r-senior on 2012-05-01
You are writing object-oriented code using a non-object-oriented library, which is a mismatch. IMO you would be better off considering:

C with GTK3
C++ with gtkmm3

[http://developer.gnome.org/gtkmm-tutorial/stable/sec-gtkmm.html.en](http://developer.gnome.org/gtkmm-tutorial/stable/sec-gtkmm.html.en)

---

### Post by Markanbl on 2012-05-01
Actually I am not supposed to use gtkmm. This is a part of a school project and we were given GTK+ to work with. It is not forbidden of course but I am not sure how much time will it take me to get used to gtkmm. Thanks a lot...

---

### Post by Markanbl on 2012-05-08
Hi again, the more my program develops the more I encounter new problems, so here's one. How can I pass a row from one treeview to another? I have a treeview in one window and I want to pass it to the first window's treeview but with some new data. Actually the two treeviews only have 3 columns in common...

---

### Post by r-senior on 2012-05-10
You can't pass rows as such. You would extract data from the treestore that backs the first treeview and use that to derive the data that you want to add to the treestore for the second treeview.

[http://developer.gnome.org/gtk3/3.1/TreeWidget.html](http://developer.gnome.org/gtk3/3.1/TreeWidget.html)

---

### Post by Markanbl on 2012-05-10
Yeah, that is want I want to do, I want to extract the data from one window and show them in another. This can't be done?

---

### Post by Markanbl on 2012-05-10
Actually what I've done is that I used the function for getting the data, I got the the data from a row and form a spin button, I created an object I need, it's all great but it's just that the function gtk_tree_selection_get_selected is a boolean, so I can't have my object... :S

---

### Post by r-senior on 2012-05-10
See: [http://developer.gnome.org/gtk3/3.1/GtkTreeSelection.html#gtk-tree-selection-get-selected](http://developer.gnome.org/gtk3/3.1/GtkTreeSelection.html#gtk-tree-selection-get-selected)

You pass a GtkTreeIter as the third parameter and gtk_tree_selection_get_selected sets it to the iterator for the selected row (if any). Then you can use that iterator with gtk_tree_model_get(...)

[http://developer.gnome.org/gtk3/3.1/GtkTreeModel.html#gtk-tree-model-get](http://developer.gnome.org/gtk3/3.1/GtkTreeModel.html#gtk-tree-model-get)

You have to think of this as a model-view pattern. The treestore provides the data (model) for the tree(view) to render. You are responsible for putting the data in the treestore and GTK is responsible for making it look pretty, scrolling it, etc. That's the deal between you and GTK.

Try to think less about moving things from window to window and control to control. Think more about how on-screen controls present your data model for you.

---

