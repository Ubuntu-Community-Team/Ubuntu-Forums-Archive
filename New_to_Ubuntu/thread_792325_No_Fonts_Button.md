---
title: "No Fonts Button?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by BTJustice on 2008-05-12
What happened to the FONTS button?  It use to be in SYSTEM > PREFERENCES > APPEARANCE.  You would click the FONTS tab then click the DETAILS button and there would be the FONTS button right?

---

### Post by unutbu on 2008-05-12
Are you talking about the "Go to fonts folder" button?
I don't know why yours might be missing, but you could create a launcher to do the same thing:

Right click on the root window. Create Launcher.
The command is: 

```
nautilus fonts:
```

---

### Post by BTJustice on 2008-05-12
Yes that is the button I meant.  I am using Ubuntu with Wubi if that matters.

I am not sure how to do this launcher thing as I am a noob with Linux, lol.

---

### Post by unutbu on 2008-05-12
Oh, okay, no prob. Move your mouse to a clear section of your screen not covered by a window. (That's what I meant by root window). Right-click the mouse. A menu should appear. The second option is "Create Launcher...". Left-click to select this menu item.

A window will appear. Go to the second line, asking for a Name. You can say "Fonts", for example. Anything you like.

On the third line, Command, you need to type

```
nautilus fonts: 
```

This is a command-line program which will open a window with the little font icons that you can browse.

The third line says Comment. I have no idea what that's for. 

Click OK. You'll be left with a little nautilus icon on your desktop with the word "Fonts" under it. When you double-click the icon, you'll get the same window that you would get by pressing the "Go to fonts folder" button.

---

### Post by BTJustice on 2008-05-12
[FONT="Tahoma"]I followed your directions but it doesn't seem to work.  When I double-click the icon, I get an error window that says...

**Couldn't display "fonts:///"**

I did figure out a way to install fonts easily though...

[LIST=1]
[*]Click PLACES > HOME FOLDER.
[*]Click on VIEW > SHOW HIDDEN FILES.
[*]Click on FILE > CREATE FOLDER and call the new folder **.fonts** (BE SURE NOT TO FORGET THE PERIOD IN FRONT OF THE FOLDER NAME).
[*]Double-click on the .fonts folder to open it.
[*]Now click on PLACES > COMPUTER to open a new File Browser window and go to the Windows Fonts folder.  If you are using Ubuntu with Wubi, it is in FILESYSTEM > HOST > WINDOWS > FONTS.
[*]When the Windows Fonts appear, click the button that says VIEW AS ICONS and change it to VIEW AS LIST.  Then click on the TYPE header so the files are arranged by type.
[*]Scroll down the list and left-click once on the very first TRUETYPE FONT listed so it is highlighted.  Then scroll down to the last TRUETYPE FONT listed.  Hold down the SHIFT key on your keyboard and left-click once on the last TRUETYPE FONT.  This should highlight all your Windows TrueType Fonts.
[*]Right-click once on any of the highlighted fonts and then left-click once on COPY.
[*]Now left-click once on the **.fonts - File Browser** window on your taskbar.  When the window opens, right-click once then left-click once on PASTE.
[*]This will copy all your Windows TrueType Fonts to the .fonts folder you created.
[*]You can close all the File Browser windows.
[*]Now click on APPLICATIONS > ACCESSORIES > TERMINAL to open the terminal window.
[*]In the TERMINAL window, type in the following command then press ENTER...
**sudo fc-cache -f -v**
[*]Now either log out of Ubuntu and log back in or reboot your computer so the new fonts are loaded.
[/LIST]
If you have more custom fonts saved somewhere, you can go back to the .fonts folder and paste them there then do Steps 11-14 above.

Hopefully Helpful,
BTJustice[/FONT]

---

### Post by SunnyRabbiera on 2008-05-12
there was a change in gnome that is behind all your issues, unfortunately there is no easy way to remedy this other then opening up a terminal and typing in sudo nautilus and going to the usr/share/fonts folder...
they made a entry about it on the gnome homepage:
[http://library.gnome.org/misc/release-notes/2.22/#sect:gvfs-regressions]("http://library.gnome.org/misc/release-notes/2.22/#sect:gvfs-regressions")

---

