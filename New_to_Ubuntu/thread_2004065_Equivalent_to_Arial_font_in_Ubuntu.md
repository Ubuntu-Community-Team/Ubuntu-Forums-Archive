---
title: "Equivalent to Arial font in Ubuntu?"
date: 2012-06-15
forum: New to Ubuntu
---

### Post by Houmie on 2012-06-15
I have opened LibreOffice and can't find a good readable font on screen such as Arial.

1) Which one is the closest in Ubuntu?

2) If someone sends me an email in Arial and I don't have it, to which font would Ubuntu automatically switch instead?

Thanks,
Houman

---

### Post by Paqman on 2012-06-15
Installing the package [msttcorefonts]("apt:msttcorefonts") will give you Arial on your machine. As for alternatives, the default Ubuntu font is pretty good, as is Liberation IMO.

---

### Post by Houmie on 2012-06-15
> **Paqman said:**
> Installing the package [msttcorefonts]("apt:msttcorefonts") will give you Arial on your machine. As for alternatives, the default Ubuntu font is pretty good, as is Liberation IMO.

Thanks I will install it then.  Dejavu Sans looks also pretty good.
I just wonder if I send someone on Ms a document with Deja Sans and they don't have it, would Microsoft Word automatically pick a default Sans Serif font that is in most cases Arial?

---

### Post by Paqman on 2012-06-15
It'll default to a font they do have, yes. Exactly which one I couldn't say. Websites control this through CSS, documents should do likewise but I'm not sure exactly what fonts and in what order.

---

### Post by mastablasta on 2012-06-15
which is why they "invented" PDF that can bring the fonts with it. :-)
 
anyway.... it owuld be good to install Ubuntu restricte extras package that will install some other usefull stuff (such as codecs) besides the MS fonts.

---

### Post by Houmie on 2012-06-20
Guys,

When I went to install Microsoft fonts which were part of the restricted Ubuntu package, it said that it had to remove libavcodec=extra-53 and 51 etc.  Which I agreed to it.

Today I got some updates from Ubuntu Update manager, and it wants to reinstall those packages again.  Wouldn't that make the packages collide though?  

I thought Linux would see these dependencies...
Do I still do the update?

Thanks,

---

### Post by oldrocker99 on 2012-06-20
Yes, you should upgrade. If a program exists in an older version, it will be upgraded.;)

---

### Post by mastablasta on 2012-06-21
sometimes it removes packages as they are no longer needed (i.e. a better version is available) so they don't take up your disk space.

---

