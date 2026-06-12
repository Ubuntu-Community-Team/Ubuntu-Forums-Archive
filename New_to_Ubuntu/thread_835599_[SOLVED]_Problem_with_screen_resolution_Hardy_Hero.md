---
title: "[SOLVED] Problem with screen resolution Hardy Heron 8.04 LTS"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by yizuman on 2008-06-20
I upgraded to 8.04 and I cannot get my screen resolution to be at 1024x724 with my Nec Multisync A500.

It used to be whereas I could find it under system/administration/screen something, I forget what it was, but it allowed me to find my monitor brand and set the resolution from there.

Now it's gone so, the system/preference/screen resolution doesn't work and there's no selection for a resolution higher than 800x600. I tried clicking on "detect displays" button, but nothing happens.

How do I fix this?

Thanks in advance!

---

### Post by avtolle on 2008-06-20
Right click Applications; select Edit Menus. When this opens, scroll down to "Other"; in right hand panel, click on "Screens and Graphics"; close. Open Applications menu; scroll to "Other"; Screens and Graphics should appear to the right; click on it to start; OR

From terminal (assuming you are using Gnome)```
gksudo displayconfig-gtk
```

---

### Post by bred on 2008-06-20
[COLOR="Blue"]what kind of videocard do u have ?
ATI, geforce etc..[/COLOR]

---

### Post by yizuman on 2008-06-20
> **bred said:**
> [COLOR="Blue"]what kind of videocard do u have ?
ATI, geforce etc..[/COLOR]

geforce 2

I got it to work from the 1st reply, so it's working like a charm.

---

### Post by avtolle on 2008-06-20
Please mark it "solved", using the thread tools in the left top. Thank you.

---

### Post by yizuman on 2009-01-14
Hi guys,

Well, I got 8.10 installed and lost my settings with my screen resolution and the post about right clicking to add the systems & screen thing is not working since the icon is no longer there in 8.10 versus what was for 8.04.

So how do I find it again or how do I find a way to locate my monitor type and then change my screen resolution? It won't go higher than 800x600.

*sighs*

---

