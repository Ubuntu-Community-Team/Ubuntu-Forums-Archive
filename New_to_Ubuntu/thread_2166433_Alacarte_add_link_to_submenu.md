---
title: "Alacarte add link to submenu"
date: 2013-08-09
forum: New to Ubuntu
---

### Post by robson22 on 2013-08-09
Hi, first thing is sorry about my english. I want add to menu link directly to website, i thing i must add item opera or mozilla witch some code but idont now what was that see.

Please give me example.

Second things is how to change icon of item in menu with alcarte or whatever?

Thanks for help.

---

### Post by Frogs Hair on 2013-08-09
I created a Firefox/Youtube Launcher via Alacarte with the following command . Just add the URL directly to the end of the launch command. I just looked at the launch command in the applications properties in the main menu.   ```
 firefox %uhttp://www.youtube.com/music
``` The icon can be changed in the launcher dialog box displayed in the screen shot . Select the icon image and navigate to the folder/directory where the image you want to use is stored.

---

### Post by robson22 on 2013-08-09
Thanks is very helpfull, but how change application menu icon i cant go to properites in alcarte.

---

### Post by Frogs Hair on 2013-08-09
First of all, are you using Unity ?  To enter launcher properties in the main menu right click or double click the line where the application is displayed . (see screen shot) If you have changed the icon you may have to log-out or restart before the image changes elsewhere.

---

### Post by Frogs Hair on 2013-08-09
I thought you just needed a command example, but if you are stating from scratch see below .

* Open the main menu. 


* Select the category where the application launcher is  to appear from the left pane. Internet , Accessories and so on.


* Select new item from the right side of the main menu to open Create Launcher dialog. 


* In the Create launcher dialog name the new item .


* Enter the command in the command box. (comments are optional)  


* Select icon picture on the left side of Create Launcher dialog. 


* Navigate to the folder / directory of the image you want to use. 


* With the image added , select OK on the Create Launcher dialog.


* The new item will now appear in the main menu.


* For Unity , locate the new item in dash and drag it to the launcher  panel if needed.

---

### Post by robson22 on 2013-08-09
I use gnome classic. I dont now we understood. I want change icon from left panel for example Internet , Accessories and launcher is not active for them. How i can do this.

Please help

---

### Post by Frogs Hair on 2013-08-09
The Icon for the categories on the left side of main menu are coming from file system usr/share/icons or home .icons depending on where the icons are installed and would have to be changed from those locations.

---

### Post by robson22 on 2013-08-09
Ok thanks, but when i add the categries to the left menu icon is folder icon when i can change this icon, add this to usr/share/icons where i can link/change my added category icon.

---

### Post by Frogs Hair on 2013-08-09
If you add a new menu/directory to the left side you can change the icon by selecting the icon picture in directory properties . From there you can navigate to any folder that has an image you want to use. If you find an icon you like on the Internet just place in a folder and use it or navigate one of the installed icon sets . I have collected some icons over time and have a folder for them.

---

### Post by robson22 on 2013-08-10
But in my alacarte properities is grey can go to them.
[IMG]http://imageshack.us/a/img842/6906/th4x.png[/IMG]

---

### Post by Frogs Hair on 2013-08-10
> [COLOR=#000000]But in my alacarte properities is grey can go to them.. [/COLOR]

Can you describe what properties  are  grayed out  ?  The icons on the left have to be changed from the Icon folder unless adding a new menu as I wrote . The properties for the applications  in the center of the main menu under " Item" can be accessed with a double click or right click.

---

