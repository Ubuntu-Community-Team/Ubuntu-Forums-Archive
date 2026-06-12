---
title: "[SOLVED] How do I change the font on the splash screen"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by the8thstar on 2008-05-28
Hello all,

The title sums it all: how do I change the font on the Gnome splash screen (the one where you log in)?

Thanks in advance!

---

### Post by philinux on 2008-05-28
Well, System>Admin>Login window allows you to change the look. I've installed a theme from [http://www.gnome-look.org](http://www.gnome-look.org)

It's a GDM theme for gnome.

---

### Post by sayakb on 2008-05-28
> **the8thstar said:**
> Hello all,

The title sums it all: how do I change the font on the Gnome splash screen (the one where you log in)?

Thanks in advance!

I'm not sure that even you can even change the font. The GDM configuration file is: /etc/gdm/PreSession/Default and it does not have any font preferences.
Though you might apply GDM themes as the previous post suggests.

---

### Post by the8thstar on 2008-05-28
Well, if GDM themes can change the font used, then there MUST be a way to at least edit it manually. I'm growing sick and tired of *Sans*.

---

### Post by the8thstar on 2008-06-01
[size="7"]bump[/size]

---

### Post by nick_h on 2008-06-01
Have a look at the [Gnome Display Manager Reference Manual](http://library.gnome.org/admin/gdm/stable/index.html.en).  Read the configuration and greeter sections.

Some of the text may be part of a bitmap.

---

### Post by the8thstar on 2008-06-08
Thanks **nick_h**, I think we've struck oil on that one. :)

---

