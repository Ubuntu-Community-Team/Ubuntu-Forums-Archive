---
title: "[SOLVED] Tried to delete several files, but have serious problems."
date: 2008-06-02
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-06-02
In synaptic I have 5 files listed as:
> Installed (local or obsolete)
The files names are:
> libnss3-1d
libpng12-0
libpng12-dev
xulrunner-1.9
xulrunner-1.9-gnome-support
I have tried removing these files, but a message comes up telling me that half the files on my system will also be deleted.  How can I get rid of these files without loosing everything else on my ubuntu install.
PS- I am running Hardy 8.04 LTS

---

### Post by EXCiD3 on 2008-06-02
If other packages depend on them you wont be able to use the other programs after removing these. Why is it that you want to get rid of these?

---

### Post by unutbu on 2008-06-02
"local or obsolete" does not necessarily mean obsolete. Most likely it just means that those are packages you installed from .deb files, instead of through Synaptic or apt-get.

---

### Post by alienexplorers on 2008-06-03
Don't remember how these files were installed.  Just figured if they were listed as local or obsolete I could get rid of them.  Tried using aptitude and apt-get to remove them and it tells me that a lot of other files have to also be deleted.  Does it hurt to leave these files on the system.

---

### Post by EXCiD3 on 2008-06-03
Shouldnt hurt a thing, in fact you probably **need** them. These packages would have been installed by hand through the command line with dpkg like mentioned earlier. They just get filed away in a different section, but that doesnt make them any less important! ;) If you want to get rid of extra packages just run "sudo apt-get autoremove" and it will take care of remove stranded packages that nothing is using anymore.

---

