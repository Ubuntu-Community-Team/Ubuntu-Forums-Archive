---
title: "Gnome Theme to contrast alternate rows in GUI"
date: 2010-09-09
forum: Programming Talk
---

### Post by bcz on 2010-09-09
I am trying to use GtkTreeView, and notice a reference in the documentation that some OS configurations automatically change backround colour on alternate lines to improve the user interface.  It seems the latest MS products, and 3rd party applications, use this feature 

Anyone know of a theme that does this in Gnome desktop, or an (efficient) way of doing it in GTK

Rgds Bill C

---

### Post by SledgeHammer_999 on 2010-09-09
I think you're looking for [gtk_tree_view_set_rules_hint()](http://library.gnome.org/devel/gtk/stable/GtkTreeView.html#gtk-tree-view-set-rules-hint). But note the warning on the docs.

---

### Post by bcz on 2010-09-09
Thanks sledgeHammer..  I used this and I guess the warning applies..  Hence my question about a theme that does it

I dont see any difference between rows.  Apparently with MS2007 apps onwards, this feature is available and dramatically improves the GUI IMHO, and I am an MSphobe.  An MS programmer tells me how much better VB is now this feature is available, and as a Linux programmer, I need to match or beat the MS competition

On Ubuntu 9.04, I have to click the row to highlight it across the page and check it is what I want; then doubleclick to select it.

Would 10.04 have anything ?  Anyone out there know?

Rgds Bill C

---

### Post by SledgeHammer_999 on 2010-09-09
> **bcz said:**
> 
On Ubuntu 9.04, I have to click the row to highlight it across the page and check it is what I want; then doubleclick to select it.

I am not answering, again, your original question.
But you can make gtk to highlight each row the cursor hovers over. Use [gtk_tree_view_set_hover_selection()](http://library.gnome.org/devel/gtk/stable/GtkTreeView.html#gtk-tree-view-set-hover-selection). I find it pretty neat this way.

---

### Post by bcz on 2010-09-10
Thanks Sledgehammer

Hover selection sounds just what I want

Will check out on 10.04 on a different PC with latest upgrades as again it is not working as expected..  Also setup trivial example to try and find my error

Thanks again Bill C

---

### Post by bcz on 2010-09-11
Thanks Sledgehammer

Hover selection works great....

Nothing as confusing as having 2 versions of a source file and updating the old one

Rgds Bill

---

### Post by bcz on 2010-09-13
I now think the standard Ubuntu Gnome themes actually give a contrast between alternate rows, but the contrast is so slight as to be difficult to notice.  IMHO there should be more contrast, but the "hover feature" is excellent and does the job, so why worry.

Guess the status should go to "solved"

Thanks to all -- Bill C

---

