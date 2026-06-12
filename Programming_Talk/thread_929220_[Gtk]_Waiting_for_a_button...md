---
title: "[Gtk] Waiting for a button.."
date: 2008-09-24
forum: Programming Talk
---

### Post by Stratis on 2008-09-24
Hi! : )

I have a small Gtk/Glade (created) program that I'm having a problem with. 

(callbacks.c)
```

#ifdef HAVE_CONFIG_H
#  include <config.h>
#endif

#include <gtk/gtk.h>
#include <stdio.h>
#include <assert.h>
#include <string.h>
#include <unistd.h>

#include "callbacks.h"
#include "interface.h"
#include "support.h"


void
on_spinbutton1_value_changed           (GtkSpinButton   *spinbutton,
                                        gpointer         user_data)
{
	
}


void
on_spinbutton2_value_changed           (GtkSpinButton   *spinbutton,
                                        gpointer         user_data)
{
	
}


void
on_spinbutton3_value_changed           (GtkSpinButton   *spinbutton,
                                        gpointer         user_data)
{
	
}


void
on_button1_released                    (GtkButton       *button,
                                        gpointer         user_data)
{	
         int hr = 0, mn = 0, sc = 0, thr = 0, tmn = 0, tsc = 0;
         GtkWidget * ent1 = lookup_widget(GTK_WIDGET(button), "entry1");
         GtkWidget * spin1 = lookup_widget(GTK_WIDGET(button), "spinbutton1");
         GtkWidget * spin2 = lookup_widget(GTK_WIDGET(button), "spinbutton2");
         GtkWidget * spin3 = lookup_widget(GTK_WIDGET(button), "spinbutton3");
         hr = gtk_spin_button_get_value_as_int(spin1);
         mn = gtk_spin_button_get_value_as_int(spin2);
         sc = gtk_spin_button_get_value_as_int(spin3);
         thr = hr; 
         tmn = mn; 
         tsc = sc; 
         while (thr > 0 ) {
                 char str[100];
                 while (tmn > 0) {
                         while (tsc > 0) {
                                 tsc--;
                                 sprintf(str, "%dhr, %dmin, %dsec\n", thr, tmn, tsc);
                                 //fprintf(stdout, "%s", str);
                                 sleep(1);
                                 gtk_entry_set_text(ent1, str);
                         }
                 tmn--;
                 sprintf(str, "%dhr, %dmin, %dsec\n", thr, tmn, tsc); 
                 //fprintf(stdout, "%s", str);
                 sleep(60);
                 gtk_entry_set_text(ent1, str);
                }
          thr--;
          sprintf(str, "%dhr, %dmin, %dsec\n", thr, tmn, tsc);
          //fprintf(stdout, "%s", str);
          sleep(3600);
          gtk_entry_set_text(ent1, str);
         }
}

void
on_entry1_insert_text                  (GtkEditable     *editable,
                                        gchar           *new_text,
                                        gint             new_text_length,
                                        gpointer         position,
                                        gpointer         user_data)
{
	            
}

```

I want the entry box to constantly update the countdown, but it won't do that (I'm new to all this). 

It won't update the entry box until all the code in 'on_button1_released()' is done. 

Any ideas? : )

Stratis

---

### Post by bruce89 on 2008-09-24
I assume this is glade-2 generated code. Generated code is evil, and that is why glade-3 got rid of this "feature". You should use libglade, or better still, GtkBuilder.

Anyway, I can't understand what you're trying to do.

---

### Post by Stratis on 2008-09-24
> **bruce89 said:**
> I assume this is glade-2 generated code. Generated code is evil, and that is why glade-3 got rid of this "feature". You should use libglade, or better still, GtkBuilder.

Anyway, I can't understand what you're trying to do.

It is glade-2...

Why is generated code evil?

{Edit; Never mind; found info [here]("http://www.micahcarrick.com/05-30-2008/gtk-builder-libglade-faq.html"))

sudo apt-get GtkBuilder ? 

I guess I have to trash what I have then. 

I have three spin buttons, an entry box, and a button. 

You set a value for each spin button (hour, min, sec), and it sets a timer. 

The eye-candy is having the minutes/hours/seconds tick down in the entry box.

The problem is I can't get the value of 'str' (or any value) to display. 

If I just toss in a 'gtk_entry_set_text(ent1, "Hello!");' at the top and comment out the while loops it works. 

I think the entry box is waiting on the button if that makes sense...

Thanks for the reply.


8 )

---

### Post by Tony Flury on 2008-09-25
Deleted

---

### Post by Tony Flury on 2008-09-25
Yes - it will wait - the event model in GTK is almost certainly single threaded, and the updates you request are queued as events to be completed (i.e. after the on_button_released1 event finishes).

In this case it is not the generated code that is the problem - it is the manually added code - specifically that while loop with a sleep in it.

All the code for the on_button1_released event should do is to set some initial values, start a timer (for maybe 500 micro secs) and then exit.

When the timer fires - the code should work out if the displayed value needs to be updated, update the text control if neccessary and then return.

The reason for having a 500 micro sec timer is that it allows for drifting timer, slow systems etc - and you will still get at least one timer event per 1 millisecond - if not two.

Look at setitimer - (and don't use sleep, especially not in an event handler). 
As an example [http://www.codeguru.com/forum/showthread.php?t=356101]("http://www.codeguru.com/forum/showthread.php?t=356101")

If you don't get what i mean above : just think about what would happen to your code if you need to implement a stop button - that stops the count down. How would you implement it ? The on_stop_button_clicked event would not get fired (until after the count down finishes) and even if it did - how would you stop that while loop ?

---

### Post by gomputor on 2008-09-25
I know almost nothing about C, but I had a similar problem in a program I was writing in Python.
I had a time.sleep(2) after a command to display something in a textview. But nothing was happening, no display, until the sleep() function reached to the end.
The work around for me was to put:
```
while gtk.events_pending():
    gtk.main_iteration(False)
time.sleep(2)
```
just before the sleep() function and I had my display working as I was expected.

You can do something similar and see if that works.

---

### Post by Stratis on 2008-09-25
> **Tony Flury said:**
> Yes - it will wait - the event model in GTK is almost certainly single threaded, and the updates you request are queued as events to be completed (i.e. after the on_button_released1 event finishes).

In this case it is not the generated code that is the problem - it is the manually added code - specifically that while loop with a sleep in it.

All the code for the on_button1_released event should do is to set some initial values, start a timer (for maybe 500 micro secs) and then exit.

When the timer fires - the code should work out if the displayed value needs to be updated, update the text control if neccessary and then return.

The reason for having a 500 micro sec timer is that it allows for drifting timer, slow systems etc - and you will still get at least one timer event per 1 millisecond - if not two.

Look at setitimer - (and don't use sleep, especially not in an event handler). 
As an example [http://www.codeguru.com/forum/showthread.php?t=356101]("http://www.codeguru.com/forum/showthread.php?t=356101")

If you don't get what i mean above : just think about what would happen to your code if you need to implement a stop button - that stops the count down. How would you implement it ? The on_stop_button_clicked event would not get fired (until after the count down finishes) and even if it did - how would you stop that while loop ?

Great information! 

Thanks so much!

: )

> **gomputor said:**
> I know almost nothing about C, but I had a similar problem in a program I was writing in Python.
I had a time.sleep(2) after a command to display something in a textview. But nothing was happening, no display, until the sleep() function reached to the end.
The work around for me was to put:
```
while gtk.events_pending():
    gtk.main_iteration(False)
time.sleep(2)
```
just before the sleep() function and I had my display working as I was expected.

You can do something similar and see if that works.

I also give this a try! 

Thanks!

---

