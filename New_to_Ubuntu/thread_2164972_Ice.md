---
title: "Ice"
date: 2013-08-02
forum: New to Ubuntu
---

### Post by misswham2 on 2013-08-02
I was looking at different  distros on youtube and saw the ICE app and I thought it was in ZORIN but  it was in Peppermint 3.  Its an app where you can take any webpage and  turn it into a shortcut.  You just put in the url, where u want the icon  to appear on the desktop ie. menu or desktop and u choose the icon of  your choice or use the websites icon.  I assumed it was on the Zorin  ULTIMATE video but I was Peppermint.  Is there any app in Zorin that  will do that?I went to the Zorin website and no one knows what im speaking of so i decided to come here because i figured since Zorin was a part of Ubuntu, someone here might know.
 				[[IMG]http://www.zoringroup.com/forum/download/file.php?avatar=g2_1305566241.jpg[/IMG]]("http://www.zoringroup.com/forum/memberlist.php?mode=viewprofile&u=124443")
				[misswham]("http://www.zoringroup.com/forum/memberlist.php?mode=viewprofile&u=124443") 			 **Posts:** 2**Joined:** Wed Jul 31, 2013 10:14 pm 				
[LIST]
[*]
[/LIST]

---

### Post by SweetAurora on 2013-08-02
[http://askubuntu.com/questions/85253/how-do-i-place-shortcuts-from-bookmarks-onto-desktop](http://askubuntu.com/questions/85253/how-do-i-place-shortcuts-from-bookmarks-onto-desktop)

Here, all you do is use Firefox Bookmark Manager to drag and drop bookmarks to the desktop.

Oh yeah, after dropping to the deskop, right click the link and open properties and click on the icon in the corner to chose a new icon other than the default.

---

### Post by SweetAurora on 2013-08-02
Another option is to create a desktop file.
Open a text editor and paste this in it:
```

[Desktop Entry]
Version=1.0
Name=Website Name
Comment=This is my comment
Exec=firefox "Put URL address here without quotes"
Icon=Location of your icon
Terminal=false
Type=Application
Categories=Internet;Link;
```

Then save it as webpagename.desktop and put it in the Desktop folder in Home Folder.

edit: I forgot something. After you save the text as whatever.desktop, right click it and check the "Allow executing file as program" box in the permissions tab. Otherwise it won't run.

---

