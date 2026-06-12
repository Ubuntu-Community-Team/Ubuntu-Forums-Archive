---
title: "Wine Menu"
date: 2011-10-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by zerubbabel on 2011-10-03
I did a fresh install of Oneiric, switched to the Gnome 3 desktop, and for the most part all is well. However, I don't know how to gain access to the few Windows applications I still occasionally need to use. They were accessible under my old Gnome 2 desktop via the Wine section of the applications menu, and presumably they are all still there under ".wine/drive-c", since I restored my old ".wine" directory tree before installing Wine under 11.10, but that didn't lead to the previously installed Windows applications becoming accessible.

---

### Post by crdlb on 2011-10-03
Wine installs .desktop files for Windows applications in ~/.local/share/applications/wine/ . You need those to have the wine entries in the menu.

---

