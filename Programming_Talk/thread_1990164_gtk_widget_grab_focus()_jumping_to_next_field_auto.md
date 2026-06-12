---
title: "gtk_widget_grab_focus() jumping to next field automatically !"
date: 2012-05-29
forum: Programming Talk
---

### Post by etdsbastar on 2012-05-29
Hello there, 

I am creating a 'C' project with glade and gtk. I want a focus on a gtkentry field naming txt_demandno and so I called the function:

```
gtk_widget_grab_focus (txt_demandno);
```There is another gtkentry widget just after txt_demandno widget naming txt_def.

My problem is instead of getting focus on txt_demandno widget, the cursor is automatically being focused on txt_def widget, when I am running the application.

One more thing, when I am setting the focus at txt_def widget by calling the code: ```
gtk_widget_grab_focus (txt_def);
``` the control is again being focused on the next widget on the window, i.e. txt_name.

I want the focus exactly on the widget I am setting the grab signal.

How to resolve this problem.

---

### Post by PaulM1985 on 2012-05-29
Once you have called gtk_widget_grab_focus(), call gtk_widget_is_focus() to check if the focus has been set on the widget.  

If gtk_widget_is_focus() is returning TRUE and it appears that the next widget has the focus then it is possible that something odd has gone on with your assigning of widgets.   Are you able to create a very small, simple program reproducing this issue?

Paul

---

### Post by etdsbastar on 2012-05-29
Here is the function which I am using as per your instructions:

```
void
on_notebook_switch_page (GtkNotebook *notebook, GtkWidget *page, guint page_num, gpointer data)
{
    switch (page_num)
    {
        case 1:
            gtk_widget_grab_focus (Application.txt_demandno);
            if (gtk_widget_is_focus (Application.txt_demandno) == true)
                g_message ("Got a focus true event.");
            break;
        default:
            break;
    }
}
```

This code is returning the message:
```
"Got a focus true event."
```

But, the focus is still on the txt_def field, I mean to the second field, I want the focus on txt_demandno field.

---

