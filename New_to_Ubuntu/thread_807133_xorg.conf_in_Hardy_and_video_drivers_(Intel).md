---
title: "xorg.conf in Hardy and video drivers (Intel)"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by ingrid_ozikem on 2008-05-25
Can someone PLEASE explain why the default xorg.conf of Hardy is so empty?  For example, no driver is specified in the Device section. The monitor and screen sections just barely have the identifiers. And there is NO module section.

  I have an Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller video card and I hear that a driver is mentioned in the Device section if you have an ATI or NVidia card.  What driver is my Hardy using then and how did it know to use it??! 


  I'm a newbie and have spent the last week learning all this to set up Hardy to my liking with multiple LCDs. Answering this question will help me figure the rest out.

How did Hardy manage to slim it down? What are the implicit options and where are they given?

---

### Post by Fredo on 2008-05-28
This is the new autoconfig feature of the X server. It will configure most aspects automagically. But you can still provide the settings you want to override in your xorg.conf.

Cheers,
Fredo

---

### Post by sayakb on 2008-05-28
You do not need to configure and install a driver for the Intel i9xx series.  These cards are automatically recognized and configured.

---

