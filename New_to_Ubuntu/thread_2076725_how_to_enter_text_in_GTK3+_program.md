---
title: "how to enter text in GTK3+ program"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by mark allyn on 2012-10-26
Hello everyone,
 
I am new to Ubuntu and new to GTK3+.  I am hoping that a kind soul will be willing to share some code or point me to a good example of how to write GTK3 code that will accept text inputs.  I have really been stymied.  I've looked at the GtkEntry definitions given in the GTK3 documentation and really can't figure them out. 
 
It is also possible that the dialog widget would be a better tool.  But, I don't see how to enter text into the dialog content area.
 
I'm running on 12.04 and have the most recent edition of GTK3 installed.
 
Thanks,
Mark Allyn

---

### Post by MG&amp;TL on 2012-10-26
GtkEntry really is the best way to go.

What language are you using? I can drum something up if you like. :)

---

### Post by mark allyn on 2012-10-26
Hi Mg&Tl,
 
Thank you for responding.  I am programming in plain old C.  No classes.
 
Cheers,
Mark

---

### Post by MG&amp;TL on 2012-10-27
> **mark allyn said:**
> Hi Mg&Tl,
 
Thank you for responding.  I am programming in plain old C.  No classes.
 
Cheers,
Mark

Woo, C!

Okay, here's some sample code. If you don't understand any part of it, just ask. :)

```
//include GTK+ libraries.
#include <gtk/gtk.h>

#include <stdio.h>

//callback for entry.
void print_text(GtkEntry *entry, void *optional_data) {
    //retrieve text from entry with gtk_entry_get_text()
    printf("Text in Entry: %s\n", gtk_entry_get_text(GTK_ENTRY(entry)));
} 

int main(int argc, char **argv) {
    
    //initialise GTK+ with optional arguments from argv[]
    gtk_init(&argc, &argv);

    //our window, and our entry
    GtkWidget *window, *entry;

    //make a new toplevel window
    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);

    //make a new GtkEntry.
    entry = gtk_entry_new();

    //add the entry to the window.
    gtk_container_add(GTK_CONTAINER(window), entry);
    
    //connect the return key from the entry to a callback. You could use any signal for this.
    g_signal_connect(entry, "activate", G_CALLBACK(print_text), NULL);

    //connect our window destroy signal.
    g_signal_connect(window, "destroy", gtk_main_quit, NULL);

    //show our window and sub-widgets.
    gtk_widget_show_all(window);

    //start GTK+ mainloop.
    gtk_main();
    return 0;
}

```...compile with:

```
cc source_file.c $(pkg-config --cflags --libs gtk+-3.0)
```..hope that helps. :)

---

### Post by mark allyn on 2012-10-27
Good afternoon, MG&TL
 
Thanks for your help on this little problem. I just returned from a brief trip and only now looked at your code.  
 
I will try it out shortly and get back to you.
 
I really appreciate the assistance.  There are not many good tutorials on GTK+ that I have found, and it is hard to get clear on even the most elementary functions and objects.
 
Regards,
Mark

---

### Post by mark allyn on 2012-10-27
Good afternoon, MG&TL,
 
Code ran perfectly.  Thanks for your help on this.
 
If you don't mind another question, perhaps you could pass some further guidance along.  If I wanted to put an prompt on the window and also allow the user to enter a response on the window, how would this be best achieved.  I am thinking that you would use a GtkLabel widget and put the prompt into it.  But how would you demarcate the response region on the window so it was visible to the user?
 
Thanks again for your help.
 
Regards,
Mark Allyn

---

### Post by MG&amp;TL on 2012-10-28
Hi Mark,

Pleased the code works. :)

It really depends on the sort of application. However, with the information given, one way to do it is to add a GtkLabel with your content into a packing widget such as GtkBox, then also add a GtkEntry to the packing widget.

Then add the packing widget to your window, and you're ready to roll.

I know, it is a nasty situation for those wishing to program with GTK+, especially 3.x. Reading the API reference is about the only way to make any progress. Have fun!

---

