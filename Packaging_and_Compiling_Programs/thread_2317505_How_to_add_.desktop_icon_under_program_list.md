---
title: "How to add .desktop icon under program list?"
date: 2016-03-17
forum: Packaging and Compiling Programs
---

### Post by Anes_P_A on 2016-03-17
Dear Friends,
created a deb file for ubuntu and I can add the program under Sound  & Video. But when I try to add icon for it , it show no icon image .  My dbr.desktop file content is :

```

[Desktop Entry]
Encoding=UTF-8
_Name=Insight Daisy Book Reader
_Comment=Read Daisy Talking Books
Exec=dbr
Icon=icon32x32.png
Terminal=false
Type=Application
StartupNotify=true
Categories=GNOME;GTK;AudioVideo;
```

I put the image icon32x32.png on the same level as this file .  The corresponding screenshot shown below (Insight Daisy Book Reader)
[URL="http://tinypic.com/view.php?pic=6fumpw&s=9#.Vup1iz_hVpg"]http://tinypic.com/view.php?pic=6fumpw&s=9#.Vup1iz_hVpg

[/URL]I am not included the image path not any where in configuration file. 


  Please advise how to add program icon image ..


  Thanks

Anes

---

### Post by kc1di on 2016-03-17
Is the icon image in the /usr/share/icon file?  if not  you'll need to put the full path of where the Icon is located on the H.D. 
for instance I have one in my home folder that I use.  so the path would look like this```
 /home/<user name>/icon xxx
```

In order to put the Icon image where you want it in the .deb file you may have to do a cp command to have it copied there.  or a link to the proper place.

---

