---
title: "Glade 3 ID crashing on combo box entry - anyone else see this?"
date: 2008-05-02
forum: Programming Talk
---

### Post by Gordon Bennett on 2008-05-02
Hi, I have just started Linux development, love the tools, but have been wedged into a corner when adding items to a combobox using Glade Interface Designer (3.4.2) - it crashes, even within Anjuta.

As a test, I tried an older version of Glade Interface Designer (2.12.2) and also Gazpacho - they do not crash doing the same thing.

I am wondering - is this due to a system library - I've checked and everything seems as fresh as it can be - or is it a bug in Glade Interface Designer 3.x?

---

### Post by RIchard James13 on 2008-05-05
Yes just making a Window, Adding a Vbox then Adding a Combo and then trying to add items to the combo crashes it.

I have an old Glade file from before the upgrade to 8.04 and in that I was able to add items to a Combo Box. Now however when I click on the ... button next to the list of items the dialog box comes up with no items.

It looks like this problem occurred during the upgrade from 7.10 to 8.04 since there have been no updates to GLADE since I added those items two or three weeks ago.

---

### Post by Gordon Bennett on 2008-05-08
Hi, thanks for the feedback - after I read your reply I checked Bugzilla and there is a report, so I added a comment to confirm.

---

