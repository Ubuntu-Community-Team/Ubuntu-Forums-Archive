---
title: "GtkBuilder/Glade to pure PyGTK"
date: 2009-07-16
forum: Programming Talk
---

### Post by Nevon on 2009-07-16
I'm currently in need of a preferences window/dialogue for an application that I'm working on. However, I have very little experience dealing with PyGTK (and even less with libglade and GtkBuilder). I've made a glade mockup of what I want (see the attached screenshot and glade file), but I don't know how to replicate this using pure PyGTK. 

Eventually we might migrate the entire application to use GtkBuilder, but for now I figure it would be simplest to keep it all pure PyGTK.

So my question to you is the following: is there a relatively simple way of somehow converting this glade mockup to just pure PyGTK, or is there a Pythonista with GUI programming experience, and an insatiable hunger for Python FOSS projects to help out with, out there?

If you want to know more about the project, visit our Launchpad page: [https://launchpad.net/caffeine](https://launchpad.net/caffeine)

(Here's the glade file, as I couldn't upload it to the forums [http://www.speedyshare.com/599391182.html](http://www.speedyshare.com/599391182.html))

---

### Post by Vadi on 2009-07-16
Hrm. Looking at it from the HIG point of view, there is nothing worthy to be converted.

There may be outdated glade programs that I remember that dump C/Python/Perl code

---

