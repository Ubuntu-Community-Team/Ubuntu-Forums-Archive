---
title: "Linux HDD not getting detected"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by hunter2000+ on 2008-09-26
When I start my system it detects like,
**[COLOR="DimGray"]Second Master HDD: SATA1 160 GB[/COLOR]**            *(Windows only)*
and straight away boots into Windows.

If I insert Ubuntu or openSUSE CD and start the system it detects
**[COLOR="DimGray"]Second Master HDD: SATA1 160 GB[/COLOR]**
and CD menu is displayed and when I select Boot from first HDD it boots into Windows.

Now from this point if I restart the system (from windows) it detects,

**[COLOR="DimGray"]First Master HDD: SATA2 500 GB[/COLOR]**              *(Ubuntu and OpenSUSE)*
**[COLOR="DimGray"]Second Master HDD: SATA1 160 GB[/COLOR]**
and CD menu is displayed and when I select Boot from first HDD it boots into ubuntu.

In effect I need to boot from a CD to windows first, and from there I need to restart and boot from CD and choose boot from HDisk from menu, if I need to get into ubuntu.

I don&#8217;t understand this, something wrong with my 500GB HDD?

---

### Post by bangmalley on 2008-09-26
go into BIOS, and check your SATA configuration.

---

### Post by hunter2000+ on 2008-09-26
Tried that, and at the first boot 500GB HDD is not detected in BIOS and during restart as I explained in my question it is getting detected.

---

