---
title: "HOWTO: File associations in Opera on Xubuntu"
date: 2007-02-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Copter on 2007-02-12
Opera is designed to run with KDE. When using Xubuntu, or Xfce in general there is a problem with file associations. Opera wants to open saved files (from Transfers) with **kfmclient exec**, but this program in not present so nothing happens. Another thing is that Opera wants to run every media file with gxine. If someone, like me, uses (g)mplayer instead, than this trick also will help to change this.

Tested on:
**Xubuntu** 6.10 Edgy Eft with default Xfce
**Opera** Version 9.10 Build 521
**Kernel** i686, 2.6.17-11-generic
**Qt library** 3.3.6

The trick is quite simple.
1) run **Opera** :)
2) go to **Tools** -> **Preferences** -> **Advanced** tab -> select **Downloads**
3) click there on a button **Handlers for saved files**
4) select **Files (fallback)**, click **Change** and type **[COLOR="Red"]thunar[/COLOR]** instead of **kfmclient exec**
5) do the same thing with **Folders**

Thats it. Now every time when you open directly from the web or save and than open some file, it will be opened with application that is set as default in **Thunar**. To set **Thunar** default applications (file associations) right click on a file, choose open with other application, choose the one you want, 'set as default for this file type' and click OK.

good luck,
copter :]

---

### Post by lnxnubie on 2007-03-05
thanks . that really helped.:)

---

### Post by Copter on 2007-09-19
Ive found another thing that can help solving KDE / Qt applications' file associations issues. Ive installed and run KDE's Konqueror. Then configure all you need in Settings -> Configure: Konqueror -> File associations. By doing this KDE will create a new file ~/.kde/share/config/profilerc with all associations saved. Now, hopefully, all KDE / Qt apps will open files properly.

I know that using this method we have to set all file associations twice, once for Xubuntu and once for KDE, but at the moment I cant figure out anything better.

copter :]

---

