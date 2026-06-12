---
title: "shell script to get current system font?"
date: 2011-04-12
forum: Programming Talk
---

### Post by rg4w on 2011-04-12
I'm making a Linux app and want it to conform to the user's current appearance settings.  What shell script should I use to find the current system font and size?  And will this work on KDE as well as Gnome-based systems, or do I need a different script fot KDE?

Thanks in advance -

---

### Post by hakermania on 2011-04-12
But, you didn't specify which of all these you need:
[IMG]http://uppix.net/7/b/8/b0b07e7a9b880cfd6605ec908f65b.png[/IMG]

---

### Post by bashologist on 2011-04-12
```
% gconftool-2 --get /desktop/gnome/interface/font_name
Verdana 10
% 

```
Use gconf-editor and ctrl+f to find other values you're interested in if that's not what you're looking for. Good luck.

---

### Post by rg4w on 2011-04-13
> **hakermania said:**
> But, you didn't specify which of all these you need:
[IMG]http://uppix.net/7/b/8/b0b07e7a9b880cfd6605ec908f65b.png[/IMG]
That's a good question.  I'll review the Gnome HIG for details on the proper use o the Application and Document fonts, but it looks like those are the ones I'll need.

---

