---
title: "OpenOffice Icons Gone!!"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by sayakb on 2008-05-10
Hello all
I once remember downloading an OO update which removed my toolbar icons. Today, after yet another update, I still don't see the icons. Please see attached thumbnail.
[ATTACH]69520[/ATTACH]

---

### Post by kestrel1 on 2008-05-10
You should be able to restore the icons easily, if it is what I think.
Open the application OO Writer for instance. Then go to Tools - Customize then select the Toolbars tab. Once there under OpenOffice.org Writer Toolbars you will see a drop down menu titled 'Toolbar'. If you click on that you probably have Text only selected. You can change this to Icons only or Text & Icons.
You can select the Toolbar that you want this to affect on the left of this screen.

---

### Post by sayakb on 2008-05-10
> **kestrel1 said:**
> You should be able to restore the icons easily, if it is what I think.
Open the application OO Writer for instance. Then go to Tools - Customize then select the Toolbars tab. Once there under OpenOffice.org Writer Toolbars you will see a drop down menu titled 'Toolbar'. If you click on that you probably have Text only selected. You can change this to Icons only or Text & Icons.
You can select the Toolbar that you want this to affect on the left of this screen.

Unfortunately, I don't think it is that simple :(
Check out this screenshot, it is set to "icons only". Also "Text and Icons" have no effect:
[ATTACH]69526[/ATTACH]

---

### Post by kestrel1 on 2008-05-10
Thats a shame. Have you tried re-installing OpenOffice?

---

### Post by gandaran on 2008-05-10
reinstalling won't resolve, just delete the openoffice folder in the hidden home directory, then start up oo again, should fix it.

---

### Post by sayakb on 2008-05-10
> **kestrel1 said:**
> Thats a shame. Have you tried re-installing OpenOffice?

Well, didn't I mention that I upgraded it recently. I guess it installed the newer version, so no point in re-installing.

---

### Post by sayakb on 2008-05-10
> **gandaran said:**
> reinstalling won't resolve, just delete the openoffice folder in the hidden home directory, then start up oo again, should fix it.

Tried that, but no use. The directory gets created again as soon as I launch OO (which is ofcourse, normal behavior), but I still don't have the icons..

EDIT: I found that changing the Icon theme to anything other than Tango (that I currently use) fixes it. What can I do to make it work with Tango?

---

### Post by FuturePilot on 2008-05-10
Edit:
Yes you can get it to work with Tango
```
sudo apt-get install openoffice.org-style-tango
```

---

### Post by forestpixie on 2008-05-10
try reinstalling tango - don't uninstall first - use synaptic, search for opeoffice.org-style and mark for reinstallation

---

### Post by sayakb on 2008-05-11
I think I know why this problem arose. Instead of installing tango-icon-theme, I just copied it from my friend's box to my /usr/share/icons. So it might not have installed the openoffice.org-style-tango package.
Thanks, the solution worked for me :)

---

### Post by amirman on 2008-06-14
none of these solutions worked for me, i have the same problem. i'm using the ubuntu studio icon set and a dark theme.

---

### Post by dwanders on 2009-01-08
My Icons and the text are gone. All that's left is the underscore (the one under F for the file menu). I have tried uninstalling - reinstalling deleting the .openoffice folder I even tried the tango font thing (even though my install is a default) nada it is completely unusable. Any help is greatly appreciated.

---

