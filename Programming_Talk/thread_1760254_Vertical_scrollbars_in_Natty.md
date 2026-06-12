---
title: "Vertical scrollbars in Natty"
date: 2011-05-16
forum: Programming Talk
---

### Post by t1497f35 on 2011-05-16
Hi,
I'm doing a little (gtkmm) app which has a DrawingArea inside a ScrolledWindow.
It works fine in Ubuntu 10.10 but in 11.04 it generates a segfault which I traced down to the fact that under Ubuntu 11.04 a ScrolledWindow doesn't (automatically) have a vertical scrollbar (scrolledWindow.get_vscrollbar() returns NULL).

The app counts on the ScrolledWindow always returning a non NULL vscrollbar to add a scrolling listener to it, and since it's not the case in 11.04 - any ideas what I should do?

I'm suspecting this might have something to do with the new type of scrollbars introduced in Ubuntu 11.04..

---

### Post by wojox on 2011-05-16
Haven't made it to the scrollbars yet but [this may help.]("https://wiki.ubuntu.com/Ayatana/ScrollBars")

---

### Post by t1497f35 on 2011-05-16
> **wojox said:**
> Haven't made it to the scrollbars yet but [this may help.]("https://wiki.ubuntu.com/Ayatana/ScrollBars")
Thanks, the link describes the new scrollbars, but it doesn't seem to have any info about why the ScrolledWindow in 11.04 returns a NULL vscrollbar or any hints for gtk-based app developers regarding the new scrollbars if any needed at all.

---

### Post by t1497f35 on 2011-05-18
Ok, looks like Canonical changed something in Ubuntu 11.04 (Unity3D), cause on the screenshot one can clearly see the vertical scrollbar, yet the API reports (in the output from terminal) that it's NULL.

So the question is, how to get a grip of the new "Canonical scrollbars" and what API do they work with.

Test sample project attached (zip).

PS: Looks like it's an upstream issue, somebody mangled the bindings and/or API:
[http://old.nabble.com/ScrolledWindow-problem-tt31441828.html#a31441828](http://old.nabble.com/ScrolledWindow-problem-tt31441828.html#a31441828)
No clue if Canonical will update the libraries when the fix is delivered.

---

