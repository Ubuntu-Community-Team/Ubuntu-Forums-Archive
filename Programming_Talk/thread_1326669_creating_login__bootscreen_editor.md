---
title: "creating login / bootscreen editor"
date: 2009-11-14
forum: Programming Talk
---

### Post by MR.UNOWEN on 2009-11-14
Hello,

Does anyone know if the login screen and/ or boot screen can be done in qt3 or qt4? After seeing the new one and not being able to edit it in a non-complex way, I thought I'd make my own version of it with an editor.

Also can the current one be totally overridden, such that it'll go from the custom one to the desktop without anything of the old login showing?

---

### Post by MR.UNOWEN on 2009-11-15
No one is interested in improving the look of the login? Personally I'd like to be able to modify the appearance of things. Any one?

---

### Post by nvteighen on 2009-11-15
What login? GDM (GNOME's)? KDM (KDE's)? Console's login?

If you refer to graphical login screens, you may just design a theme (however that's done) instead of editing the code...

---

### Post by MR.UNOWEN on 2009-11-15
> **nvteighen said:**
> What login? GDM (GNOME's)? KDM (KDE's)? Console's login?

If you refer to graphical login screens, you may just design a theme (however that's done) instead of editing the code...

...  Didn't 9.10 take out GDM  based log in because it loads GDM later on?

---

### Post by nvteighen on 2009-11-16
> **MR.UNOWEN said:**
> ...  Didn't 9.10 take out GDM  based log in because it loads GDM later on?
Huh? I don't think so... if no Display Manager is available, X will default to XDM... which is pretty ugly.

---

