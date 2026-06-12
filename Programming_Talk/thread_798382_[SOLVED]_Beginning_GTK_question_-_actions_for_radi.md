---
title: "[SOLVED] Beginning GTK question - actions for radio buttons"
date: 2008-05-18
forum: Programming Talk
---

### Post by anewguy on 2008-05-18
Please bear with a beginner here  :)

I have successfully defined a series of radio buttons and they show when the program is run and I can click them.  My only problem is I have no idea how to set up callbacks when they are clicked.

I searched the net, and it seemed to say I needed to use gtk_signal_connect.  I have it just on the first 2 buttons to test.  For the first button, it is as follows:

    gtk_signal_connect (GTK_OBJECT (find_button), "clicked",
                        GTK_SIGNAL_FUNC (do_init), (gpointer *) find_button);

  where the button name is find_button


The callback is:

extern int CAM_TYPE;

void do_init()
{
    do_logmsg("In do_init");
    return;
}


For the 2nd button, where the button name is open_button, it is as follows:

    gtk_signal_connect (GTK_OBJECT (open_button), "clicked",
                        GTK_SIGNAL_FUNC (do_open), (gpointer *) open_button);


The callback is:

extern int CAM_TYPE;

void do_open()
{
    do_logmsg("In do_open");
    return;
}

When I click the find_button, it does indeed issue a message saying "In do_init.  But when I then click the open_button, instead of saying "In do_open" it issues the message "In do_init" again, as if it is either ignoring the open_button, or perhaps it processes an "unclick" (forgive me) of the find_button as a click event and then skips the open_button.

Or, more than likey, I am simply doing something stupid.  It's my first try at a set of radio buttons (they all belong to the same button group but each is individually named).

Help!!??  :):):)

Thanks in advance!


EDIT:  More digging and playing around showed I need to use "pressed" instead of "clicked", since with that changed everything seems to work.

---

