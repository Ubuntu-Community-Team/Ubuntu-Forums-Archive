---
title: "Synaptic Refuses to Start"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by Samulus on 2008-10-12
Hello,

About a week ago Synaptic just stopped working.
When i started through the applications menu it i type in my authentication and shows up in the icon box applet. But it will not open when i click it or tell it to maximize. But when i start in the terminal just typing synaptic without sudoing it opens it correctly but it does not let me install anything because i haven't given it proper authorization. When i type sudo the command, it does the same thing as when i start via the applications menu. When i started it via the terminal i got this error message in the terminal

(synaptic:7065): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

Update manager, add and remove, and apt-get all work but synaptic is the only one that will not.

Any help would much be appreciated.

-Sam

---

### Post by oldos2er on 2008-10-12
What happens if you type "gksu synaptic" in a terminal?

---

### Post by Samulus on 2008-10-12
Synaptic shows up in the icon box and doesn't run.
Just like what happened when ran it with sudo

---

### Post by Samulus on 2008-10-12
Umm.. Bump!

---

### Post by seshomaru samma on 2008-10-12
did you google that error?
alternatively you can try reinstalling synaptic

---

### Post by Samulus on 2008-10-12
I googled it already no results.
When i renistall synaptic i would type

sudo apt-get remove synaptic

and then

sudo apt-get install synaptic

Right?

Because i already did that no luck :(.

EDIT: I reinstalled it via sudo apt-get install --reinstall synaptic and it still does not work.

---

