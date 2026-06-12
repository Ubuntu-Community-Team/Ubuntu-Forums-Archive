---
title: "Shortcuts on the desktop and the bottom panel?"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by hamstermoon on 2012-05-07
Hi there,

I am experimenting on an  ancient and battered laptop with rather crappy graphics.

Lubuntu certainly gives me a better screen than Xubuntu (it wouldn't play at all with Ubuntu and Unity) but I have a couple of questions.

I have seen screen caps of people who have shortcuts to their home drive on their desktop and to things like firefox on their bottom panel. Have I got a dodgy install, or am I mssing some training in terminal commands to get them there?

---

### Post by Rex Bouwense on 2012-05-07
To put applications such as Firefox , Thunderbird, etc in the quick launch potion of your panel, right click at open potion of the panel and choose Add/Remove Panel Items.  Double click Application Launch Bar and then select any application you want to move to the Launch Bar.

---

### Post by Dennis N on 2012-05-07
**Shortcuts on the Desktop**

In addition to adding to the panel (post above) it's possible to make a shortcut to open a folder with the pcmanfm file manager. You have to decide if this has any advantages over just making a bookmark in the file manager.

Example:

```
[Desktop Entry]
Name=Go to Project
Type=Application
Exec=pcmanfm /home/user-name/Project
Icon=folder-new

```

will open the folder named Project that is in your home directory. The desktop icon will be labeled 'Go to Project'

Create in text editor, and save in Desktop folder with extension .desktop

I might save it as go-project.desktop

Method can also be used to make application shortcuts.

---

### Post by Rodney9 on 2012-05-07
For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by hamstermoon on 2012-05-08
> **Rex Bouwense said:**
> To put applications such as Firefox , Thunderbird, etc in the quick launch potion of your panel, right click at open potion of the panel and choose Add/Remove Panel Items. Double click Application Launch Bar and then select any application you want to move to the Launch Bar.
 
Right, in that case I DEFINITELY have a dodgy install. I tried that and nothing happened. Will reinstall and try again.

---

