---
title: "C++ Tray Icon"
date: 2008-05-09
forum: Programming Talk
---

### Post by solarwind on 2008-05-09
Hey all, I want to make an app that sits and runs in the system tray. The language is C++. Is there a library that will let me put an icon in the tray? Can this be done with GTKMM?

---

### Post by imdano on 2008-05-09
I think what you want is [gtk.StatusIcon](http://www.gtkmm.org/docs/gtkmm-2.4/docs/reference/html/classGtk_1_1StatusIcon.html)

---

### Post by solarwind on 2008-05-09
> **ExpertAnalysis said:**
> I think the problem you're encountering goes beyond looking for a specific library.  What you really need is a fresh, clean install and conduct a system update in your Windows partition.  Good luck!

I'm sorry but I really have no idea what you're saying.

I may not have phrased my question properly, so here it is again:

I'm making a program in C++. It will live in the system tray. I need a way to make it live in the system tray. Therefore I need a library which will let me stick a nice little icon in the system tray. Which library is best suited for this job? Will GTKMM work? I want it to be cross platform (work with winbloze too), but if not, not a big deal.

---

### Post by solarwind on 2008-05-09
> **imdano said:**
> I think what you want is [gtk.StatusIcon](http://www.gtkmm.org/docs/gtkmm-2.4/docs/reference/html/classGtk_1_1StatusIcon.html)

Thank you! That's exactly what I'm looking for. Do you think I can use it with libnotify to pop up notifications?

---

### Post by imdano on 2008-05-09
Yes, you can.  I've messed around doing it with pygtk and pynotify and got it working.  And ignore ExpertAnalysis, he's a troll.

---

### Post by Can+~ on 2008-05-09
Who the hell is ExpertAnalysis? I looked for his posts:

[http://ubuntuforums.org/search.php?searchid=40912612](http://ubuntuforums.org/search.php?searchid=40912612)

He says things like reporting to the RIAA, clogging the tubes; he's like a living parody of all the nonsense the media/politicians speak?

---

### Post by solarwind on 2008-05-09
> **Can+~ said:**
> Who the hell is ExpertAnalysis? I looked for his posts:

[http://ubuntuforums.org/search.php?searchid=40912612](http://ubuntuforums.org/search.php?searchid=40912612)

He says things like reporting to the RIAA, clogging the tubes; he's like a living parody of all the nonsense the media/politicians speak?

He has been deleted :)

---

### Post by solarwind on 2008-05-10
> **imdano said:**
> Yes, you can.  I've messed around doing it with pygtk and pynotify and got it working.  And ignore ExpertAnalysis, he's a troll.

Is is possible to add a label to the trayicon? I mean, not just an icon but other widgets as well, such as a label.

---

### Post by imdano on 2008-05-10
I'm not sure what you mean by a label.  You can add a tooltip, if that's what you mean.

---

### Post by solarwind on 2008-05-10
> **imdano said:**
> I'm not sure what you mean by a label.  You can add a tooltip, if that's what you mean.

Not a tooltip, but an actual widget such as a label or a button. I really need to put a label in there so I can show the user some text quickly and easily so there is no need to interact with the icon itself.

Edit: I know it's possible because I've done it with my gmail checker. It's written in python and uses pytrayicon.so as the tray library. I can just add(widget) to the tray. However, I do not know how to do this with c++.

---

