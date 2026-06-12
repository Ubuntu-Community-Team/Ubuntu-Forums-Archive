---
title: "problem with xfce menu"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by Daverobb on 2008-08-29
does anyone know why the menu list at the top left corner of xubuntu would change name from ?? (can't remember) to xfce menu and now it has no menu items but a few minutes ago it had the standard menu items?  

This is a brand new install of xubuntu (7.10) but something similar happened on the previous install too.

---

### Post by phidia on 2008-08-29
If I'm thinking clearly xfce doesn't have a menu icon or spot there but gnome does.
Are you using a seperate home partition and if so was that once part of a ubuntu or gnome based install?

Normally with xfce you access your computer (applications & system) from the dock applet or by right clicking the desktop.

---

### Post by Daverobb on 2008-08-29
yeah it's weird - when you first install xfce it does give you a gnome like icon in the top left but in my last install this changed after a boot up to the right click on desktop.  However, this time, I get this strange Xfce Menu  icon up there which has no programs listed below and the right click on desktop doesn't work either?!  There is nothing when I right click on the desktop.

It's brutal - I can't get at any of my apps except for firefox which is in that top menu bar.

---

### Post by phidia on 2008-08-29
What about your home directory is it from a previous install-on a separate partition?

I'm thinking this could be caused by preference files in your user directory.

If it's not that then you might have a bad install. Check the md5sum of the iso you downloaded and burn the image at a slow speed.

---

### Post by denham2010 on 2008-08-30
Hi,

It could be that your default menu file is corrupted.

Follow these steps to re-instate the default.

1. press ALT+F2 and type xfce4-terminal

2. enter the following code in the terninal to backup your old menu file:
```
 cp ~/.config/xfce4/desktop/menu.xml ~/.config/xfce4/desktop/menu.xml.old
```

3. enter the following in the terminal to open mousepad:
```
mousepad
```

4. copy and paste the following into your mousepad window:
```
<?xml version="1.0" encoding="UTF-8"?>
<xfdesktop-menu>
	<menu name="Settings" icon="gnome-settings">
		<app name="Settings Manager" cmd="xfce-setting-show" icon="gnome-settings" snotify="true"/>
	</menu>
	<separator/>
	<include type="system" style="simple" unique="true" legacy="true"/>
	<separator/>
	<app name="Help" cmd="xfbrowser4 /usr/share/xubuntu-docs/desktopguide/C/index.html" icon="gnome-help"/>
	<app name="About Xfce" cmd="xfce4-about"/>
	<builtin name="Quit" cmd="quit" icon="gnome-logout"/>
</xfdesktop-menu>
```

5. save the file as "menu.xml" in ~/.config/xfce4/desktop

6. close mousepad and enter the following code in the terminal:
```
xfce4-menueditor
```

7. Click on File - Open default menu.

8. Close the menu editor and terminal.

Right clicking on the desktop should now produce the default Xfce menu. If this now works, try deleting the menu applet from your panel and rebooting, then add the applet back.

If you still have issues, it could be as others have previously mentioned, either a permissions problem or a corupt install.

To see if it is a permissions problem, ALT+F2 and type xfce4-terminal.

In the terminal enter:
```
xfdesktop --menu
```

This should open the Xfce menu. If it is having any problems, paste the terminal output here.

Cheers.

---

### Post by Daverobb on 2008-09-06
How do I find the file:
```

~/.config/xfce4/desktop
```

Think I figured out this - just typed in the save as file as ~/.config/xfce4/desktop/menu.xml and saved.

Then tried as you advised but all I get is a window with a few selections like Create Launcher, Create URL Link, etc... it doesn't contain any icons with the associate programs, as it did before.  

If I upgraded to 8.04 would this solve the problem?

---

### Post by RaisedFist on 2008-09-13
I have the same problem. Just installed Ubuntu the other day and the xfce desktop menu is the gnome desktop menu. I want to have the xfce menu when I right click the desktop.

Does anyone else have this issue?

---

