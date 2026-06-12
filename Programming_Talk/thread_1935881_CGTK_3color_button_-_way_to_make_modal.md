---
title: "C/GTK 3/color button - way to make modal?"
date: 2012-03-05
forum: Programming Talk
---

### Post by anewguy on 2012-03-05
This may seem like a basic question, but I've looked online and in the DEVHelp and have found nothing.

I have a few different color selections that can be made in my application.  I used gtk_color_button_new for each of these and they all pop up a color selection dialog and work as they are supposed to, as does my code that handles them.  

However, I have found nothing that says you can set a color button as modal, and right now the user can do anything they want with the "calling" screen while the color selection dialog is displayed.  I really need this to be modal, so that only the color selection box can have focus until it completes.

So, lacking some kind of "gtk_set_modal" or "gtk_color_button_set_modal" or something along those lines, I can't find anything that would seem to do this for me.  Since the button handling, in terms of popping up the color selection dialog until close of that popup) is controlled by GTK, it would seem I need to do something to signal GTK somehow to do this modal.

Any help would be GREATLY appreciated!

Thanks in advance!

Dave ;)

---

### Post by r-senior on 2012-03-05
The color selection dialog inherits from Dialog, so you can make it modal according to the general instructions for Dialog:

[http://developer.gnome.org/gtk3/stable/GtkDialog.html](http://developer.gnome.org/gtk3/stable/GtkDialog.html)

Specifically, you have the function:

```
gtk_window_set_modal(GtkWindow *window, gboolean modal);
```

Not sure what you mean by modal button. It's the dialog window that would be modal, not the button.

---

### Post by anewguy on 2012-03-05
Well, I'm not sure how to do this yet.  I have a gtk_color_button on the screen.  Obviously when the button is pushed it does the color selection window, then goes to my callback.  Here's the relevant pieces of the code:

```
     panel_bg_gradient_end_color = gtk_color_button_new_with_color(&bggradend);
     gtk_color_button_set_title(panel_bg_gradient_end_color,
                                "Select Panel Background Gradient End Color");
     gtk_color_button_set_use_alpha (panel_bg_gradient_end_color, TRUE);
     gtk_color_button_set_alpha(panel_bg_gradient_end_color, css_panel_bg_gradient_end_alpha);

```

using the following to define the signal handler

```
     g_signal_connect (G_OBJECT (panel_bg_gradient_end_color), "color-set",
                       G_CALLBACK (update_css_panel_bg_gradient_end_color),
                       NULL);

```

and using the following to add to the screen definition

```
     gtk_table_attach (GTK_TABLE(table1), panel_bg_gradient_end_color,3,4,3,4,
                       GTK_EXPAND, GTK_SHRINK, 0, 0);

```


EDIT:  TRIED THE SET MODAL ON THE WINDOW THE BUTTON WAS IN AND IT WORKS GREAT!!  THANKS!!!! ;)


Thanks!
Dave ;)

---

