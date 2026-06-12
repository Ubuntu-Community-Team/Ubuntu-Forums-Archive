---
title: "how could reinstall gtk2.0 in ubuntu12.04"
date: 2014-01-16
forum: Packaging and Compiling Programs
---

### Post by goog2 on 2014-01-16
hi, all! after i installed gtk+3.6.4 in the ubuntu12.04 for installing nautilus-3.5.5 , the UI is broken and becomes abnormal , so i want to restore gtk back.
[ATTACH=CONFIG]249542[/ATTACH]

> sudo apt-get install --reinstall   libgtk2.0

the command doesnt work , how could i do it ?

---

### Post by mikewhatever on 2014-01-17
The correct package name is **libgtk2.0-0**. Try reinstalling and post the output.

---

### Post by goog2 on 2014-01-17
yes, reinstall well , thx.   but the desktop UI is the same, how could i restore to use the gtk2.0 as the default gtk library  .

---

### Post by vasa1 on 2014-01-17
> **goog2 said:**
> hi, all! after i installed gtk+3.6.4 in the ubuntu12.04, ...
Please could you explain how and why you installed "gtk+3.6.4"?

---

### Post by Toz on 2014-01-17
How exactly is your UI broken? Its difficult to tell from the image you posted.

Secondly, how did you install GTK3? 

GTK2 and GTK3 are separate components, re-installing GTK2 will not remove or overwrite GTK3. You'll need to uninstall the GTK3 version you installed first then re-install the repo GTK3 version.

EDIT: beaten to the punch by vasa1 :)

---

### Post by goog2 on 2014-01-17
> **vasa1 said:**
> Please could you explain how and why you installed "gtk+3.6.4"?

compile gtk3.6.4 from the source for installing newer nautilus , because default nautilus3.4.2 make cpu high for kernel3.10.18

---

### Post by goog2 on 2014-01-17
> **Toz said:**
> How exactly is your UI broken? Its difficult to tell from the image you posted.

Secondly, how did you install GTK3? 

GTK2 and GTK3 are separate components, re-installing GTK2 will not remove or overwrite GTK3. You'll need to uninstall the GTK3 version you installed first then re-install the repo GTK3 version.

EDIT: beaten to the punch by vasa1 :)

Toz, thanks! i got it  :)

---

### Post by goog2 on 2014-01-17
I have check that there is not a libgtk3.6.4-common in synaptic ,  some library changes the UI style . my gedit becomes
[ATTACH=CONFIG]249547[/ATTACH]
and the bash didn't work well, typed command doesn't show on the screen . how to solve this problem

---

### Post by Toz on 2014-01-17
> **goog2 said:**
> I have check that there is not a libgtk3.6.4-common in synaptic ,  some library changes the UI style . my gedit becomes
[ATTACH=CONFIG]249547[/ATTACH]
and the bash didn't work well, typed command doesn't show on the screen . how to solve this problem
Are you perhaps looking for libgtk-3-common? Running:
```
apt-cache policy libgtk-3-common
```
...will show you versioning information of the package that is available in the repositories.

---

