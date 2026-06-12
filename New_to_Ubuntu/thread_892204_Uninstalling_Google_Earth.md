---
title: "Uninstalling Google Earth"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by kolhoznik on 2008-08-16
Could anyone offer any help for uninstalling a Google Earth?  I was directed to look in the bin file that was created to look for a way to uninstall but all that was there was this message 

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Also there was a message saying it could not open the bin file.  Also, I have two Google Earth icons under Applications > Internet  

Any help to getting these out would be helpful.

---

### Post by Yuki_Nagato on 2008-08-17
Two Google Earth icons could just mean that you accidentally created another shortcut.  No big deal.

But did you actually find an uninstaller file?  Such files could be launched using,

```
./XXX
```

XXX is the exact file name.

But then again, if you can do that, you can also double-click on the file to begin uninstallation.

Right-click on the Menubar, and click on "Edit Menus" to remove the Google Earth icons if the uninstaller does not get rid of them.

---

### Post by kolhoznik on 2008-08-17
That is my main problem that I cannot find and uninstall file.  When I click on the bin file that is on my desktop it just gave me the message that was in my first post.

---

### Post by Pro-reason on 2008-08-17
Google Earth is in the Ubuntu repositories, so there was probably no need to install it manually.  If whatever you downloaded doesn't have an uninstaller that you can find, then you'll have to remove the files manually.

Type "locate googleearth" in a terminal to see what relevant files are on your computer.  You can then delete them if you wish.  

("locate" gets instant results because it uses a database.  Type "updatedb" to update it.)

---

