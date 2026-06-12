---
title: "GTK key_press_event"
date: 2007-01-27
forum: Programming Talk
---

### Post by code-breaker on 2007-01-27
I am working on a small app in GTK. It has a couple of text boxes (GTK_ENTRY), and is working fine. 

I am trying to have the window intercept keypresses, and then *not* pass them along to the widgets. I have a function that correctly sorts the keypress, and then performs the desired action, but the keypress is passed on no matter what I do. For example, if I hit the up or down arrow keys, the action I specify occurs, but then focus is shifted from one text box to the next. [I read]("http://www.gtk.org/tutorial1.2/gtk_tut-2.html") that returning TRUE in the callback function "indicates that the event has been handled, and that it should not propagate further". However, returning TRUE does not eliminate this behavior. Here is the code from the callback function:

```
static gint keypress( GtkWidget *widget, GdkEventKey *event, gpointer func_data)
{
  switch(event->keyval)
  {
    case GDK_Up:
    {
      printf("UP");
      return TRUE;
    }

    case GDK_Down:
    {
      printf("DOWN");
      return TRUE;
    }
  }
  return TRUE;
}

```

I am not quite sure where to put the return TRUE, so I tried various places, included after the braces of each case, but nothing helped. Any suggestions?

---

### Post by code-breaker on 2007-02-03
Upgrading from gtk 1.2 to 2 solved the problem.

---

