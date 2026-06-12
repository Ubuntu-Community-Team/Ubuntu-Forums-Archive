---
title: "Glade &amp; GTK+ Incompatibility"
date: 2009-01-22
forum: Programming Talk
---

### Post by rich1939 on 2009-01-22
I have a top-level window that is opened by a signal from the primary top-level window. Both were designed by Glade.

I specifed for the secondary window that it should be **Decorated**, but **not** be **Deletable** (the tooltip for Deletable indicates that there will be no close box for the window in that case). However, the window manager **does** provide a close-box, which when clicked deletes the window...and then it can't be reopened.

I changed the Glade description to remove the **Decorated** property but also kept the **Deletable** property, then I added the following code just before showing the window:

```

    gtk_window_set_has_frame(GTK_WINDOW(cwin), TRUE);


```

This works, somewhat and though there is a close button in the frame, it does not destroy the window when clicked ... but in the debugging console window I see the following failed assertion:

```

    Gdk-CRITICAL **: gdk_window_set_icon: assertion: 'GDK_WINDOW_TYPE(window) != GDK_WINDOW_CHILD' failed

```

I can't seem to find how to create a top-level window that doesn't have a close-box, or escape from the failed assertion when I create the frame myself.

If there is a way to specify what buttons are present in a window's frame, either programmatically, or via Glade, I'd sure like to know how to do so. My application is going to have quite a few of these top-level windows that need to operate in the same way (i.e., not have close boxes).

What's the solution?

---

### Post by bruce89 on 2009-01-22
> **rich1939 said:**
> I specifed for the secondary window that it should be **Decorated**, but **not** be **Deletable** (the tooltip for Deletable indicates that there will be no close box for the window in that case). However, the window manager **does** provide a close-box, which when clicked deletes the window...and then it can't be reopened.

The deleteable property is a hint, so some window managers override it. I can't think of any case where having no close button is a good idea.

> **rich1939 said:**
> 
What's the solution?

Don't have windows without close buttons. If you want to have a secondary window, use a GTK_WINDOW_POPUP one.

---

### Post by rich1939 on 2009-01-22
> **bruce89 said:**
> The deleteable property is a hint, so some window managers override it. I can't think of any case where having no close button is a good idea.

Don't have windows without close buttons. If you want to have a secondary window, use a GTK_WINDOW_POPUP one.

Okay...I'll give it a try. My main problem was that when the close box was clicked, the window (and presumably the objects that GBuilder created) was/were destroyed. Trying to recreate it caused only the frame, minus all of its contents, to be displayed.

I'll give the POPUP variety a try...but I believe that I had tried that and it had no frame.

---

### Post by bruce89 on 2009-01-22
Why do you want to use a window with no close button. If I knew what it was for, I could better find a solution to it.

---

### Post by rich1939 on 2009-01-22
> **bruce89 said:**
> Why do you want to use a window with no close button. If I knew what it was for, I could better find a solution to it.

I'm creating a PostgreSQL database-based application that has many different data entry windows, report windows, etc. I've built a toolbar for the data entry windows that lets the user post entries, look at previous, next, first, last, etc. entries...and the windows also include data fields into which they can view, enter, and edit entries.

I've created the user interface for two of the windows (a primary window that contains Icon buttons that when clicked open the secondary windows) and one secondary window at this point. The secondary window is the problem.

I'm using GBuilder (gtk_builder_get_object()) to access the window definition(s) created when GBuilder read the XML file (produced by Glade, and then converted to GBuilder format), and then call gtk_widget_show_all() to show the window.

When the secondary window is opened, everything is fine. I can enter data and post it into the PostgreSQL database. However, when the close box is clicked, apparently the entire set of window objects is deleted and any attempt to reopen the secondary window results in just the frame and an entirely grey interior, with no child controls.

I've discovered (by adding a CLOSE button to the window) that hiding the window, rather than closing it, works just fine and I'm able to close and reopen it with no problems.

If I have to have a close box in the frame, and if I could somehow intercept the "destroy" signal and cause the window to hide rather than destroy, I think my problem would be solved.

I tried changing the Glade definition of the window to a Popup type, but although it seems to work that way, it has no frame at all.

So, in a nutshell, if I could either eliminate the close box or (ideally) intercept the destroy signal and cause the window to hide instead, that would be ideal.

Hope that explains my problem.

---

### Post by bruce89 on 2009-01-22
> **rich1939 said:**
> If I have to have a close box in the frame, and if I could somehow intercept the "destroy" signal and cause the window to hide rather than destroy, I think my problem would be solved.

```

g_signal_connect (window, "destroy",
		   G_CALLBACK (gtk_widget_hide_all), NULL);

```

I suppose destroying a window as opposed to hiding it frees the memory it uses, so it won't exist unless you recreate it.

---

### Post by rich1939 on 2009-01-22
> **bruce89 said:**
> ```

g_signal_connect (window, "destroy",
		   G_CALLBACK (gtk_widget_hide_all), NULL);

```

Thanks, I'll give it a try.:D

---

### Post by rich1939 on 2009-01-22
> **rich1939 said:**
> Thanks, I'll give it a try.:D

> **bruce89 said:**
> ```

g_signal_connect (window, "destroy",
		   G_CALLBACK (gtk_widget_hide_all), NULL);

```

I suppose destroying a window as opposed to hiding it frees the memory it uses, so it won't exist unless you recreate it.

Apparently, although I didn't get any errors when adding that code, it apparently doesn't take precedence over the window manager's signal when the close box is clicked.

I do believe that the window and its children are destroyed when the close box is clicked, which apparently deletes all of the objects created by GBuilder when the XML file was parsed.

Maybe "destroy" isn't the correct signal-name...but I really don't know how to proceed without finding a solution to this problem.

---

### Post by bruce89 on 2009-01-23
> **rich1939 said:**
> Maybe "destroy" isn't the correct signal-name...but I really don't know how to proceed without finding a solution to this problem.

Indeed, it should be "delete-event".

---

### Post by rich1939 on 2009-01-24
> **bruce89 said:**
> Indeed, it should be "delete-event".

Unfortunately this doesn't work either...it doesn't seem to take precedence over the Window Manager's **delete/destroy** signal/event.

Although the secondary window disappears when the close box is clicked, when I attempt to reopen the window, only the frame appears, with its title. The contents area of the window is now blank (uniformly grey) and doesn't contain any of the child controls.

Is it possible that the gtk_builder_get_object(dbBuilder, "company_data") function isn't also retrieving the child controls...and only the window that contains them? On the first opening of the secondary window (company_data), everything shows up.

Here's the code that gets executed each time the primary window tries to open the secondary window:

```

void dbProcessCompanyData()
{
    cwin = GTK_WIDGET(gtk_builder_get_object (dbBuilder, "company_data"));
    g_signal_connect(GTK_WINDOW(cwin), "delete-event",
        G_CALLBACK(gtk_widget_hide_all), NULL);
	gtk_widget_show_all (cwin);
    ...
}

```

Again, **cwin** is a global variable defined as follows:

```

GtkWidget *cwin;    // company window pointer

```

Any more suggestions?

---

### Post by rich1939 on 2009-01-24
Okay...after doing some more research about "events", I discovered that the callback function should be written as follows:

```

gboolean cwClose_window(GtkWidget *window, GdkEvent *event, gpointer user_data)

```

And that the callback routine (in this case, cwClose_window) has the opportunity to return TRUE if the event has been entirely handled, and FALSE if not.

I'm calling the gtk_widget_hide function inside my callback routine and then returning a result of TRUE. This seems to completely fix the problem. Being somewhat of a newbie, I didn't understand the difference between **signals** and **events**.

Handling the delete-event this way solved my problem. Thanks very much for putting me on the right track by mentioning the word "event".

---

### Post by Julius123321 on 2010-02-24
I dont know if it solves your problem. I use glade 2.0. in Property window of  my top level window, ("window1" in my case) I select the way this window will be used, as splash screen or dialog, you can see it creates a windows without no buttons.
if you use splashscreen it looks like this:
 gtk_window_set_type_hint (GTK_WINDOW (window1), GDK_WINDOW_TYPE_HINT_SPLASHSCREEN);
  gtk_window_set_urgency_hint (GTK_WINDOW (window1), TRUE);

hope this helps

BUT

it is better to use delete_event and connect it to your function
    glade_xml_signal_connect (gxml, "on_window1_delete_event",G_CALLBACK (MY_FUNCTION));

and you dont need to use destroy  anywere, just manually do whatever you want and finally destroy widget window1 and call gtk_main_quit

---

### Post by kknd on 2010-02-24
To prevent the window deletion, you can connect the "delete-event" signal to a callback that returns TRUE, indicating the event was fully handled there and shouldn't be propagated further.

Example (in Lua + lgob.gtk):

[PHP]
win = gtk.Window.new()
win:connect('delete-event', function() return true end)
win:show()
gtk.main()
[/PHP]

---

