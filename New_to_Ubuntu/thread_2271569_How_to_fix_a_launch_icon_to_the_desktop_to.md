---
title: "How to fix a launch icon to the desktop to"
date: 2015-03-31
forum: New to Ubuntu
---

### Post by porkey10 on 2015-03-31
How can I Fix an icon to the desktop to allow me to open a web page Ie My Bank or my library etc.and also what is a "tag"  further down on this new thread page.

---

### Post by dino99 on 2015-03-31
open the link you wish, then you will see the related icon into either your taskbar or dash list: right click on it to add to favorites

---

### Post by ajgreeny on 2015-03-31
You need to make a launcher similar to the current <***browser*>.desktop** file for the browser you use, eg firefox.desktop in /usr/share/applications.

Start by copying that file to your desktop with ```
cp /usr/share/applications.firefox.desktop Desktop
``` then open the .desktop file with gedit (or your text editor) with command```
gedit Desktop/firefox.desktop
```find the line
 **Exec=firefox %u** and change it to 
**Exec=firefox [http://etc](http://etc) etc,** for the web-address you want to open.  Double clicking that launcher should now open FF to that web-page, thiough the first time you do so you may see an error saying it is untrusted.  Click on "Make executable" and the error should disappear and FF open.  You can change the icon for the launcher also by editing the line **Icon=firefox** to **Icon=/path/to/image/you/want**

Tags to threads are just a few words describing the subject of the thread, eg installation, boot, multimedia, etc etc.  They are not essential but can help browsers of the forum.

PS:
What version of Ubuntu or DE are you using, unity (Ubuntu), KDE (Kubuntu), XFCE (Xubuntu), LXDE (Lubuntu)?

I think my instructions will work for all of them, though I use XFCE (Xubuntu) so I am not able to promise for the other DEs, and unity is not really made to have icons on the desktop, though I'm pretty certain it can be done if you really want to add them.

---

### Post by CantankRus on 2015-03-31
> **ajgreeny said:**
> ```
cp /usr/share/applications[COLOR="#FF0000"]**.**[/COLOR]firefox.desktop Desktop
``` 
Hi **ajgreeny **,
Typo in your first command.
Should be 
```
cp /usr/share/applications[COLOR="#FF0000"]**/**[/COLOR]firefox.desktop Desktop
```

---

### Post by ajgreeny on 2015-04-01
Whoops! Sorry about that.

---

### Post by Dennis N on 2015-04-01
This will work too - and very easy:

Example of a shortcut to Ubuntu Forums. Create this with a text file and save in your Desktop directory as Forums.desktop (or other appropriate name followed by .desktop). Change file permission to executable. Double-click will open a new tab in browser if it's running. The **Name=** line will create the icon label. **Comment=** shows in the tooltip. **Icon=** is type of icon or path to specific icon.  

```
[Desktop Entry]
Version=1.0
Type=Link
Name=Ubuntu Forums
Comment=Visit the Ubuntu Forums
Icon=folder
URL=http://ubuntuforums.org/index.php

```

Result: Attached image. Add a cool emblem for the web!

(Tested in Xubuntu.)

---

### Post by porkey10 on 2015-04-06
thanks you all. It is good to know there are people out there (somewhere) who know the answers

---

