---
title: "Marking images with LibreOffice I suppose ?"
date: 2024-09-01
forum: New to Ubuntu
---

### Post by Innernet on 2024-09-01
Hello.
I get an image on email.  To highlight an area, or to circle something in the image, or to superimpose/add a pencil-handdrawn sketch on the image.  How to do it ?   Tried on LibreOffice Draw,   imported the image to the program and that was it.  Gave up.  How is it done?

---

### Post by Dennis N on 2024-09-02
> **Innernet said:**
> Hello.
I get an image on email.  To highlight an area, or to circle something in the image, or to superimpose/add a pencil-handdrawn sketch on the image.  How to do it ?   Tried on LibreOffice Draw,   imported the image to the program and that was it.  Gave up.  How is it done?

If the image was attached to the email, you open it in the appropriate application to do the job. To add arrows, boxes, etc. or text on the image, I use KSnip. It does screenshots too, if you are using Xorg session. To superimpose one image onto another, I have used Inkscape.

If its not attached, you may have to do a screenshot of the image first.

---

### Post by Innernet on 2024-09-02
Thank you, Dennis.
So I need some application capable of such;  LibreOfficeDraw is not capable of marking an image imported to its work area.  Finally clear !

---

### Post by Holger_Gehrke on 2024-09-02
It actually is possible in LibreOffice Draw, but since it is a vector-oriented program - like Adobe illustrator or Inkscape - you need to know how to use it. Since it's internally treating everything as mathematical descriptions of the drawn elements it has the advantage that everything drawn with its tools can be scaled / moved / rotated / ... without any loss of quality (a circle stays a circle, no matter how much you zoom in). LibreOffice does have a rather nice set of Help files, but accessing them is difficult if you're using a browser in a snap-package (the help is in HTML files in /usr/share/libreoffice/help/, which a snap can't access ...). A work-around is to use the online version [https://help.libreoffice.org](https://help.libreoffice.org) or to get the manual(s) from [https://documentation.libreoffice.org](https://documentation.libreoffice.org).
I've attached a screenshot of your last post that I did a few simple things with in Draw.

Holger

---

