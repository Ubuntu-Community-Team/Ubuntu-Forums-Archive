---
title: "gtk+ Delayed Output"
date: 2010-02-19
forum: Programming Talk
---

### Post by Milliways on 2010-02-19
I have a gtk+ program which performs a slow function (disk logging) in response to a key press.

I wanted to output a message, in a GtkLabel to warn the user of possible delay.

Unfortunately the label is not displayed until the function finishes.

Is it possible to force this to be displayed immediately?

I am trying to put the function in a thread, but am finding this a challenge.
I thought threads were complicated in Windows, but gtk+ documentation is confusing.

---

### Post by nvteighen on 2010-02-20
> **Milliways said:**
> I have a gtk+ program which performs a slow function (disk logging) in response to a key press.

I wanted to output a message, in a GtkLabel to warn the user of possible delay.

Unfortunately the label is not displayed until the function finishes.

Is it possible to force this to be displayed immediately?

I am trying to put the function in a thread, but am finding this a challenge.
I thought threads were complicated in Windows, but gtk+ documentation is confusing.

Hm... why not print it always before calling the disk logging? If it's a warning of possible delay, whether there is or not any delay is irrelevant... you're just talking about possible behaivor :)

---

### Post by pbrane on 2010-02-20
This is what I do, in C++
```

void classname::updateGUI()
{
  while (Gtk::Main::events_pending()) // update the GUI
    Gtk::Main::iteration();
}

```
call the function immediately after you set the label text

for C GTK,
```

void updateGUI()
{
  while (gtk_events_pending()) // update the GUI
    gtk_main_iteration();
}

```

This is the way you should update the GUI before or during long computations. You don't need to create a function, you can place the *while* loop inline.

---

