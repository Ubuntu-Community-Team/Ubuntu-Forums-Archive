---
title: "Learning to write for GNOME"
date: 2009-01-04
forum: Programming Talk
---

### Post by Coder543 on 2009-01-04
Greetings, Let it be known that I am not a newb to programming. I know about 7 different programming languages (mostly C influenced, like C++ etc.). What I don't know, is where the magic all-in-one reference for GUI design with Gnome is. Any tips? Also, I would appreciate any examples that are not overly complex (as in, full programs. Learning by example is most effective when a single task is completed, not lots of tasks being completed.)

I am able to do GUI in Mac and Windows, but as of yet I haven't been able to do GUI in Gnome Ubuntu (except for monodevelop... but that doesn't count, that is windows in essence).

I would greatly appreciate links to good tutorials and amazon books (or free online books :D).

oh, almost forgot, the *preferred* langauge would be C++ or C... but I guess I could use python or something else too.

---

### Post by fiddler616 on 2009-01-04
I'm quite shaky on my GUI skills, but AFAIK:
-There are several GUI tookits for Ubuntu. GTK (Gnome-biased), Qt (KDE-biased), WxWidgets, and Tk.
-You can use whichever one you fancy. Google is your friend. As are these forums--somebody should come up with a link soon.

---

### Post by mali2297 on 2009-01-05
You can find some information about GTK+ at [http://www.gtk.org/documentation.html](http://www.gtk.org/documentation.html) (including links to two tutorials).

---

### Post by Coder543 on 2009-01-05
Ok I'll look at that documentation link, also, I think Qt would be cool to know because not only does it look great, but it looks good in gnome (where as gtk, looks almost despicable [by default] in kde). Additional links are welcome!

---

### Post by jespdj on 2009-01-05
GTK+ is the toolkit used in the GNOME desktop. If you want to make your application look like a standard GNOME application, use GTK+.

Qt is the toolkit used in the KDE desktop. Your app will look like a native KDE application if you use that. It might look pretty to you, but GNOME users will generally prefer GTK+ applications.

---

### Post by Coder543 on 2009-01-05
Ok, it has been noted.

---

### Post by fiddler616 on 2009-01-05
> **Coder543 said:**
> I think Qt would be cool to know because not only does it look great, but it looks good in gnome (where as gtk, looks almost despicable [by default] in kde).
Most GNOME people will get a little bit grouchy about having to load the Qt libraries just to run one app. For example, I think Kolourpaint is the best simple paint program out there, but don't have it installed in the name of speed and purity.

---

