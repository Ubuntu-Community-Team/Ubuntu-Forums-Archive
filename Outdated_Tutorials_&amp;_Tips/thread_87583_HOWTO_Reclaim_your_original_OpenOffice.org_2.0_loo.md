---
title: "HOWTO: Reclaim your original OpenOffice.org 2.0 look!"
date: 2005-11-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Omer on 2005-11-08
After [installing the latest OpenOffice.org 2.0]("http://ubuntuforums.org/showthread.php?t=80392"), by default, it uses the original icon theme, and not the one installed with (K)Ubuntu (Industrial or Crystal).

Lets restore that icon theme, and reclaim our good old consistant looking desktop!

*So, how do we do it?*

First, [install latest OO.o 2.0]("http://ubuntuforums.org/showthread.php?t=80392").
Second, back up the latest install icon theme:
```
sudo mv /opt/openoffice.org2.0/share/config/images.zip /opt/openoffice.org2.0/share/config/images.zip.old
```
And last, copy the icon theme you would like to use:
```
sudo cp /usr/lib/openoffice.org2/share/config/**images_industrial.zip **/opt/openoffice.org2.0/share/config/images.zip
```
[SIZE="1"]* **images_crystal.zip** (for Kubuntu) or **images_hicontrast.zip** (for users with sight disabilities).[/SIZE]

Restart OpenOffice, and voila!

---

### Post by PiTT on 2005-11-08
I would like to know how to do the opposite (kinda): how to use the default icons (the ones that come with OOo) with the "normal" OOo2 (i.e., the v1.9.129 that comes with Ubuntu).

Any ideas?

---

### Post by benplaut on 2005-11-08
[QUOTE=PiTT]I would like to know how to do the opposite (kinda): how to use the default icons (the ones that come with OOo) with the "normal" OOo2 (i.e., the v1.9.129 that comes with Ubuntu).

Any ideas?[/QUOTE]

ditto! i really like the new ones :mad:

---

### Post by thechitowncubs on 2005-11-08
Tools>Options>View

Change Icon style to Default

---

### Post by Sionide on 2005-11-08
How do you change the icons to the ones used in the Windows version of OpenOffice2??

Is there a place to download new icon themes for Ooo2?

---

### Post by benplaut on 2005-11-09
there are some nice icons at 
[http://www.wincustomize.com/ViewSkin.aspx?SID=1&SkinID=428&LibID=39](http://www.wincustomize.com/ViewSkin.aspx?SID=1&SkinID=428&LibID=39)

---

### Post by Sionide on 2005-11-09
[QUOTE=benplaut]there are some nice icons at 
[http://www.wincustomize.com/ViewSkin.aspx?SID=1&SkinID=428&LibID=39](http://www.wincustomize.com/ViewSkin.aspx?SID=1&SkinID=428&LibID=39)[/QUOTE]

Was more thinking along the lines of icon themes for the IN-application icons, such as New File, Open, Save etc etc etc..

---

### Post by benplaut on 2005-11-09
[QUOTE=Sionide]Was more thinking along the lines of icon themes for the IN-application icons, such as New File, Open, Save etc etc etc..[/QUOTE]

dunno about that...

---

