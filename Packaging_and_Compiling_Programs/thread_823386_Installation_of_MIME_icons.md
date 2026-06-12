---
title: "Installation of MIME icons"
date: 2008-06-09
forum: Packaging and Compiling Programs
---

### Post by Lantash on 2008-06-09
I'm currently working on the distribution mechanisms of the Python application LottaNZB I contribute to. Both the setup.py and the deb package installation work almost perfectly now, but there's one thing I don't figure out:

The installation of the MIME icon. Currently our MIME icons are installed into /usr/share/icons/hicolor/*/mimetypes/application-x-nzb.png. ```
gtk-update-icon-cache -q -f -t /usr/share/icons/hicolor
``` is run after the installation. Now the problem: All applications &#65279;(such as Firefox and the file browser of LottaNZB) except Nautilus seem to use this icon for NZB files. Installling the icon to &#65279;/usr/share/icons/gnome did the trick but I guess this isn't the correct approach. Does anyone know how to get things working, to make Nautilus use the mime icon in 'hicolor'?

Thanks in advance! :)

-- Lantash

---

