---
title: "gtk question.. menu behaviour"
date: 2010-02-28
forum: Programming Talk
---

### Post by dodgem on 2010-02-28
Hi all.

I'm writing an app in ruby and gtk+, and want to cause a certain behaviour, but i don't know how...

When you have a window open (nautilus for example), you can move the window by grabbing it's title bar and dragging it around.  But if you click on a menu so that it drops down, you can no longer move the window.

I want to achieve that effect when i open a popup window. The specific application is an entry widget which when clicked on opens a popup window underneath the entry widget with a calendar widget in it so that a date can be selected and then displayed in the entry widget.  The problem is that once the popup window is made visible, i can drag the main window around by the title bar and the calendar popup is staying still.

How do i achieve the same effect as i get with menus where the main window cannot be moved?  I presume this must be possible since a menu is effectively a popup window in gtk is it not?

Thanks,

Simon

---

### Post by pbrane on 2010-02-28
I haven't tried this to see if it has the effect you want, but I beleive what you are looking for is the mode of the dialog or popup. Try making your popup **Modal**. The default for *modal* is *no*.

---

### Post by dodgem on 2010-02-28
Thanks for the reply, but modal doesn't do it.  Modal stops me from interacting with the content of the parent window, but i can still move it around, minimise it etc.

---

