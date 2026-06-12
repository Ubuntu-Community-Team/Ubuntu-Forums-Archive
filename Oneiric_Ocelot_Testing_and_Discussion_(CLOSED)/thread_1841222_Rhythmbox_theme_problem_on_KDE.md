---
title: "Rhythmbox theme problem on KDE"
date: 2011-09-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sleepitoff on 2011-09-09
In System Settings under 'GTK+ appearance' I have it set to display the QTcurve theme in GTK apps. While this changes the theme in all other GTK apps I use, it doesn't for Rhythmbox. How could I correct this?

---

### Post by sumski on 2011-09-09
Try this:
GTK2_RC_FILES=/usr/share/themes/QtCurve/gtk-2.0/gtkrc [FONT=Verdana]rhythmbox
EDIT:
That won't do it, you will need oxygen-gtk3
[/FONT]

---

### Post by sleepitoff on 2011-09-09
is there a debian package for oxygen-gtk3?

---

### Post by sumski on 2011-09-10
I filed a wishlist bug for packaging it but haven't got any response for some time. You can compile it yourself

---

### Post by sleepitoff on 2011-09-29
Bringing this back up... 

Were you able to compile it with proper results, sumski? This is kind of a downfall for me, since I prefer Rhythmbox over all the other music library players out there... and it's the only one that reads my tags correctly.

---

### Post by sumski on 2011-09-29
Uploaded it just now:
[https://launchpad.net/~hrvojes/+archive/kde-goodies]("https://launchpad.net/%7Ehrvojes/+archive/kde-goodies")

---

### Post by sleepitoff on 2011-10-02
Thank you!

---

