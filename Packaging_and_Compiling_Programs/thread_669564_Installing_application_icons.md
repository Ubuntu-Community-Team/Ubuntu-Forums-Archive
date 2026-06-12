---
title: "Installing application icons"
date: 2008-01-16
forum: Packaging and Compiling Programs
---

### Post by kevykev on 2008-01-16
Hi all,

I'm creating a binary deb file for an application i'm developing. According to the [freedeskop.org icon theme spec]("http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html") (Section: "Installing Application Icons") I installed various sized icons in 

/usr/share/icons/hicolor/apps/48x48
/usr/share/icons/hicolor/apps/32x32
/usr/share/icons/hicolor/apps/24x24
/usr/share/icons/hicolor/apps/16x16

The icon is called ist.png and my desktop entry file contains

```
[Desktop Entry]
...
Icon=ist
...
```

However, the icon doesn't display in the GNOME menu. It works when I use the full path in the .desktop file, but this doesn't allow different icon sizes. Any idea what i'm doing wrong?

Thanks,
Kevin

---

### Post by dholbach on 2008-01-17
Do you run dh_icons and dh_desktop in debian/rules?

---

### Post by kevykev on 2008-01-17
> **dholbach said:**
> Do you run dh_icons and dh_desktop in debian/rules?

Thanks! I had not being using debhelper (I just had a shell script build the package instead), so I used update-desktop-database and gtk-update-icon-cache in my postinst and postrm file instead.

Perhaps I should use debhelper instead though, do you know any good tutorial on using it?

---

### Post by dholbach on 2008-01-18
Try [https://wiki.ubuntu.com/PackagingGuide/Lists/ReferencePackages](https://wiki.ubuntu.com/PackagingGuide/Lists/ReferencePackages) and [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete) generally.

---

### Post by Flimm on 2009-06-22
I get this error message when using dh_desktop:```
dh_desktop: This program is deprecated, and does nothing anymore.
```
Any idea what's supposed to have replaced it?

---

