---
title: "Wrong LibreOffice icons in the menu"
date: 2014-10-10
forum: New to Ubuntu
---

### Post by Seventh_Magpie on 2014-10-10
Hello everybody

I have installed Xubuntu yesterday and rather like it so far. However, there is an issue that bugs me. 

The system had preinstalled word processor AbiWord and a spreadsheet application which name I don't remember. I uninstalled them and installed trusted LibreOffice instead. However, the links that have appeared in the menu are not that of LibreOffice, but something very-very old from OoO, I think. Only Math and main LibreOffice Launcher have correct icons.

The correct icons are safely in /usr/share/icons/hicolor folder, I checked. However the system doesn't use them for some reason and uses something else from somewhere else. 

The file type LibreOffice icons are also wrong, but that doesn't bug me much. However, these old icons are plain ugly. Besides, I use LibreOffice across all my computers and have already gotten seriously used to what the app icons look like. :)

Is there a way to make Xubuntu use correct icons?
[ATTACH=CONFIG]257103[/ATTACH]

---

### Post by Toz on 2014-10-10
Hello and welcome.
Assuming that you are using the default settings, then you are using the elementary-xfce icon theme. Those icons come packaged with that theme.

You can override those icons by right-clicking the menu and choosing "Edit Applications". In the application that displays (menulibre), find and select the program that you want to change on the left side of the window and on the right side, click on the picture of the icon. This will give you the opportunity to change it. Select the "Image file" option and navigate to and select the icon that you want to use.

---

### Post by Dennis N on 2014-10-10
The icon used for any application is normally determined by the icon theme that is being used. The icon theme is selected in Settings > Appearance > Icons.

But, you can choose a different icon for any application from it's panel launcher: right-click on the icon, select properties, click on the 'edit' button on the right side > in the edit window, click on the icon and then browse to the one you prefer.

---

### Post by Seventh_Magpie on 2014-10-10
> **Toz said:**
> Hello and welcome.
 Assuming that you are using the default settings, then you are using the elementary-xfce icon theme. Those icons come packaged with that theme.

Thank you Toz and Dennis N for the welcome and the answers. However, there is a question. How come Xubuntu uses two icons that are not in its default set (LibreOffice main launch window and Math)? Can it be because there are no such icons in its default set and it falls back to where it was supposed to take them from the start? Where does it take icons from if there are no icons for an application in the default set? 

I'm rather new to all this Ubuntu/Xubuntu thing, so I my question might sound stupid or ignorant. :) Can I somehow delete the wrong icons from the default set? Will Xubuntu start using the correct LibreOffice icons? Or will it achieve nothing? I don't want to break anything in the process, however it is logical to assume the icon sets should be editable.

Thank you again!

---

### Post by Dennis N on 2014-10-10
> **Seventh_Magpie said:**
> How come Xubuntu uses two icons that are not in its default set (LibreOffice main launch window and Math)? Can it be because there are no such icons in its default set and it falls back to where it was supposed to take them from the start? Where does it take icons from if there are no icons for an application in the default set?

Correct. There is a specific search order for locating a specified icon. I think the selected theme would be used first if possible. I have read that hi-color icon theme is actually a "fallback" choice for any needed icon that has no match.

> Can I somehow delete the wrong icons from the default set? Will Xubuntu start using the correct LibreOffice icons? Or will it achieve nothing? I don't want to break anything in the process, however it is logical to assume the icon sets should be editable.

I've never tried it. But I wouldn't delete them. Just rename the icons so you can restore them - I would rename with an extension: rename xxxx to xxxx.orig for example. If you are going to experiment, I strongly suggest you copy the entire icon theme folder from /usr/share/icons to ~/.icons so you don't need root privileges to work with them and you don't mess with the original icons. Any changes you make in ~/.icons actually have a higher priority. If you delete this folder, the originals will again be used. Also, there are icons of various sizes (16 px, 22 px, 24 px, etc) for the same thing - you would have to rename them all.

icons can be located in several locations: 
~/.icons
~/.local/share/icons  
/usr/share/icons
/usr/share/pixmaps

These are the ones that come to mind right now.

---

### Post by Seventh_Magpie on 2014-10-10
Oh, thank you, Dennis! Making a user copy of icon set would definitely be the easiest choice for experimenting, especially since it's a netbook and I'm the only user. :)

Could you please walk me through the process of creating  ~/.local/share/icon folder? Should it be in my home directory? Is that what ~ means? From .htaccess experience I can guess that .local is the hidden folder, is that right?

---

### Post by Seventh_Magpie on 2014-10-11
Local icon set didn't solve the problem, even despite the fact that I replaced all "libreoffice" icons with original LibreOffice ones. 

Seeing how this system is about two days old and I'm not really risking anything yet, I went and renamed all the "libreoffice" icons in the original elementary-xfce folder and then refreshed icon cache by running gtk-icon-update for elementary-xfce folder in Terminal. And only then I saw correct LibreOffice icons on the menu.

How bad is what I have done? Is it dangerous? Could it potentially break something?

---

### Post by Dennis N on 2014-10-11
Sorry -  
~/.local/share/icons is not correct. It should be **~/.icons** 
No harm done. To fix, just move the theme folder you edited from **~/.local/share/icons** into **~/.icons** where it belongs.
I fixed the original post. The other locations are correct.

Edit: Turns out **~/.local/share/icons** works too as a location for icon theme folders! See next post.

---

### Post by Dennis N on 2014-10-11
Well, I just discovered something I hadn't realized. I made a test and ~/.local/share/icons is another possible location for an icon theme folder. I put an icon folder in there and it registered in the Settings dialog. So what I thought was a mistake, really isn't. I have been using ~/.icons on my system.

Added that location back to the original post as a possible location.

---

### Post by Dennis N on 2014-10-11
> **Seventh_Magpie said:**
> Local icon set didn't solve the problem, even despite the fact that I replaced all "libreoffice" icons with original LibreOffice ones. 

Seeing how this system is about two days old and I'm not really risking anything yet, I went and renamed all the "libreoffice" icons in the original elementary-xfce folder and then refreshed icon cache by running gtk-icon-update for elementary-xfce folder in Terminal. And only then I saw correct LibreOffice icons on the menu.

How bad is what I have done? Is it dangerous? Could it potentially break something?

I can't see that you could "break" anything or cause any harm in this case. Sounds like you got the result you wanted in the end. Glad that worked for you.

---

### Post by Seventh_Magpie on 2014-10-11
> **Dennis N said:**
> Well, I just discovered something I hadn't realized. I made a test and ~/.local/share/icons is another possible location for an icon theme folder. I put an icon folder in there and it registered in the Settings dialog. So what I thought was a mistake, really isn't. I have been using ~/.icons on my system.

Yes, it worked as a possible location. When I experimentally renamed the folder with icons I copied there I got a second "elementary-xfce" icon set in the relevant settings window. :) However, it didn't work for my purpose and I can't even imagine why. So in the end I had to mess a bit with the default system icon set. Now I can quickly recognise the LibreOffice apps at a glance by their icon colour. :)

Xubuntu looks like a a nice system so far. I didn't think I'd like it at all, but somehow I'm starting to fall in love. :)

Thank you Dennis again for all your help! I really appreciate it.

---

### Post by Dennis N on 2014-10-11
> **Seventh_Magpie said:**
> Yes, it worked as a possible location. When I experimentally renamed the folder with icons I copied there I got a second "elementary-xfce" icon set in the relevant settings window. :)

There is an explanation: the name used in the Settings dialog is not taken from the folder, but from the **index.theme** file inside. If you change the value of **Name=** in that file, you would get that new value used as the name in Settings.

---

### Post by Seventh_Magpie on 2014-10-11
Yes, I realised this. It works pretty much like a Wordpress theme. :) Wonder why it didn't replace the icons with the correct ones, though. I suspect it had something to do with icon cache, because I copied the entire folder including the original cache. I suppose it doesn't refresh automatically when you change locations? Too bad I didn't think of it sooner, could've checked while I was at it.

---

