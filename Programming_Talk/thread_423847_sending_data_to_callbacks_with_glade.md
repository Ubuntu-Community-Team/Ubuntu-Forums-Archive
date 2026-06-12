---
title: "sending data to callbacks with glade"
date: 2007-04-26
forum: Programming Talk
---

### Post by PointSource on 2007-04-26
I'm having trouble sending data to callbacks in GTK. In the properties window in glade, signals tab, it shows no text entry for placing data in. In a couple of screen shots in tutorials on the web I've seen this box, but its nowhere to be seen in my version. The code glade outputs looks like this:
g_signal_connect ((gpointer) button1, "clicked",
                               G_CALLBACK (name_clicked),
                               NULL);
The "NULL" ought to have something in it's place, but there doesn't seem to be any option in glade to modify it, and if I modify the code glade will overwrite it next time I make a change. What do I do?

TIA

---

### Post by PointSource on 2007-04-27
bump?

---

