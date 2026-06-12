---
title: "Gtk3 on Windows"
date: 2011-10-31
forum: Programming Talk
---

### Post by Liiiim on 2011-10-31
I wasn't really thinking and took Gtk3 at its word that it would work on Windows.  Now that I've gotten to the stage where I'd like to port my program to Windows, this is looking to be not so true.  So, I have a few questions - 

All of the posts I can find regarding getting Gtk3 on Windows (about how it's not really possible and rather buggy) are from a few months ago.  Does anyone know if there's been any updates or progress made?  Or is it still just as difficult and unfeasible?

Assuming I won't be getting Gtk3 to run in Windows, how difficult would it be to redo the program in Gtk2?  I did most of the UI in Glade, and it looks like there is a version of that for Gtk2.  It would be pretty easy to just redo the UI in Glade, but would there be much else I have to change?

Thanks for any advice :)

---

### Post by crdlb on 2011-10-31
I don't know anything about the quality of Gtk3's Windows port, but I do know that many of the changes in Gtk3 should actually improve portability. I think it's just a problem of manpower.

As far as the UI goes, you'll need to replace GtkGrid with GtkTable, and GtkBox with GtkVBox and GtkHBox. It seems that Glade 3.10 [has dropped Gtk2 support]("https://bugs.launchpad.net/ubuntu/+source/glade/+bug/822861"), but you can install 3.8 [from a PPA]("https://launchpad.net/~hramrach/+archive/ppa") You'll need to install the packages manually or do something like pinning the repository. If you want to salvage your UI file, you can edit it and change each GtkBox, but changing GtkGrid to GtkTable would be more difficult.

The amount of porting you'll have to do depends on how "custom" your UI is. If it is just a collection of standard widgets, it shouldn't be too bad.

What language are you writing in? C?

---

### Post by Liiiim on 2011-10-31
It's in standard C.  That's what most of the posts I've seen have said - that eventually the port will ready it's just so close to the release of Gtk3 that there's a lot that needs to be done still.  The problem is I can't really wait too long to port it, so I think I'll just switch over to Gtk2.

Thanks for the reply.

---

### Post by Simian Man on 2011-11-01
Even getting GTK2 going on Windows is a PITA and it's been out for nearly ten years.  Windows support is always an afterthought to that crowd.  If you will be working on this project long-term, something like QT would be much better.

---

### Post by nicoge on 2012-10-25
Me too I'm waiting for a gtk3 port on windows. You can try to cross-compile your application using mingw on linux.

---

