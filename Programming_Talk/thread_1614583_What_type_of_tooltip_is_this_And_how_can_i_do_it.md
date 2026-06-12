---
title: "What type of tooltip is this? And how can i do it?"
date: 2010-11-05
forum: Programming Talk
---

### Post by hakermania on 2010-11-05
If you set a tooltip on something ( for example a trayicon ) it will look like this:

(See first image)

But if you go on Ubuntu at the clock ( and every tooltip on ubuntu general) that will be shown:

(See second image)

So is this a different type of a tooltip or something? ( Differences: Transparency and angles )

P.s
I am setting the tooltip with this:[FONT=monospace]
[/FONT]```
ui->Button->setToolTip("Start Operation");
```

---

### Post by loell on 2010-11-05
i think it's **libnotify** or its successor if it was recently preceded.

---

### Post by hakermania on 2010-11-05
> **loell said:**
> i think it's **libnotify** or its successor if it was recently preceded.

libnotify is a notify which pops-up at the right.. it isn't that 
there must be a new type of tip on ubuntu... because setTooltip is black while everything on ubuntu is transperant ones...

---

### Post by nvteighen on 2010-11-06
It may be a tooltip of a GtkStatusIcon ([http://library.gnome.org/devel/gtk/2.14/GtkStatusIcon.html](http://library.gnome.org/devel/gtk/2.14/GtkStatusIcon.html)) or something along the way (a full-fledged GtkTooltip). Anyway, it is a regular GTK+ tooltip: it looks different because of the theme you're using: in my Debian GNU/Linux installation, they look exactly the same as every toolkit everywhere:

---

### Post by hakermania on 2010-11-06
> **nvteighen said:**
> It may be a tooltip of a GtkStatusIcon ([http://library.gnome.org/devel/gtk/2.14/GtkStatusIcon.html](http://library.gnome.org/devel/gtk/2.14/GtkStatusIcon.html)) or something along the way (a full-fledged GtkTooltip). Anyway, it is a regular GTK+ tooltip: it looks different because of the theme you're using: in my Debian GNU/Linux installation, they look exactly the same as every toolkit everywhere:

I do not think that this is it... it must be something else...

---

### Post by loell on 2010-11-07
> **hakermania said:**
> libnotify is a notify which pops-up at the right.. it isn't that 

it can pop-up anywhere. if one wants to. ;)

---

### Post by hakermania on 2010-11-07
.

---

### Post by hakermania on 2010-11-07
.

---

### Post by hakermania on 2010-11-07
Yes but this isn't what i want... I want something that does exactly what tooltip is doing but instead of having a black background to have a transparent one exactly like all the "tooltips" at ubuntu.. :confused::confused::confused:

Sorry for double-posts... my wrong..

---

### Post by loell on 2010-11-07
looking at it again closely, I think **nvteighen** is right.

it's a GtkStatusIcon widget, you might perceive them as two entirely  different widgets because the first image you posted is running on a none composited desktop while compositing is enabled on the second image, giving the widget an auto-transparency and rounded corner effects.

---

