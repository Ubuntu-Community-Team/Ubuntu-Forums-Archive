---
title: "Glade: Setting icons for Toolpalette?"
date: 2012-05-12
forum: Programming Talk
---

### Post by fallenshadow on 2012-05-12
Hi guys/gals,

I have a toolpalette which was constructed with code. This was done before Glade had the support for a Toolpalette.

Can an image be set on the button inside Glade? At the moment if I set an image it will show the missing icon symbol.

The option seems to be there for a custom image to be set.

[IMG]http://ubuntuone.com/04cxgEn4UAxSpQ20KPadqp[/IMG]

Any ideas folks?

---

### Post by pbrane on 2012-05-12
It looks like glade is not setting the path to the image. Go to the project properties in glade and change the image loading to the toolpalette_icons directory in your project.

---

### Post by fallenshadow on 2012-05-15
Yes that is exactly it! Glade thinks you will have the .glade file in the same location as your images.

So even though I was selecting the directory through Glade to **toolpalette_icons/Pointer.png**, Glade would just set it to **Pointer.png**.

Manually setting the file path worked! Thanks for coding the toolpalette initially for me but as a result of this bug ( [http://ubuntuforums.org/showthread.php?t=1978705](http://ubuntuforums.org/showthread.php?t=1978705) ) I wanted to rework it to use Glade if possible. (less code, more control)

That bug no longer affects my project. :)

---

