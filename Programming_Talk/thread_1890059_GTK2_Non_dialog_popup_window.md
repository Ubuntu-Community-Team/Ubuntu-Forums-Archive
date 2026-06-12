---
title: "GTK2: Non dialog popup window?"
date: 2011-12-02
forum: Programming Talk
---

### Post by Liiiim on 2011-12-02
I'm having trouble making a popup window in GTK.  It needs to have a GtkTreeView in it, and since I couldn't figure out how to put one of those in a dialog box I'm making a whole new GtkWindow.  I can get it to show up fine, but I can't figure out how to make it close when the close button (on the window decoration) is clicked.  I tried

```
g_signal_connect_swapped (window, "set-focus", G_CALLBACK (gtk_widget_destroy), window);
```where 'window' is the GtkWindow, but nothing happens when I click the close button.  Is there a better way for creating a popup window that I'm missing?

Any suggestions would be much appreciated :)

e:  Nevermind, I think I have it working now...  I am using a GtkDialog, not sure why adding the TreeView wasn't working before.

---

### Post by Petrolea on 2011-12-03
Sorry for posting in a solved thread, but weren't you supposed to bind the 'destroy' signal? That's the signal that gets emitted when you close the window.

---

