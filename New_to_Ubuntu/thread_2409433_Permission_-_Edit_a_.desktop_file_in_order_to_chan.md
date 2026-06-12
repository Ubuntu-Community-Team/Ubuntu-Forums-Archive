---
title: "Permission - Edit a .desktop file in order to change icon"
date: 2019-01-02
forum: New to Ubuntu
---

### Post by kesetyan on 2019-01-02
Hi,

Having used various Puppy Linux and Windows operating systems, changing icons for files and folders was fairly straightforward but this is not the case with Lubuntu 18.04.  For example, I would like to change the icons for certain '.desktop' files but have been unable to do this because I am not able to gain permission.  I can open the file in a text editor like Leafpad and enter the filepath to the required icon in the 'icon=' line but my changes will not save. 

Related to this permission issue is the fact that I cannot add my own sub-folder of png format icons to the '/usr/share/icons' folder nor add my own '.desktop' file* (that I have created for an executable script file)* to the '/usr/share/applications' folder.  

I'm still near the bottom of a steep learning slope as far as Ubuntu and its offshoots are concerned - I know it is necessary to be careful when trying to work in system folders and that fiddling with permissions can cause severe problems if incorrect changes are made to system files but what I want to do is fairly basic stuff.  Is there a fairly simple way I can achieve what I want to do without risk.

Thanks.

---

### Post by CatKiller on 2019-01-02
You can change the icons of launchers simply by clicking on the icon in the Properties screen.

In general, you'll want to familiarise yourself with the multi-user permissions model. You can read and write to files in your Home folder. Other users can read and write to files in *their* Home folder. Some applications, like web servers and the like, are restricted in where they can read and write for security purposes.

If you want to write outside of your Home folder, you'll need to temporarily switch to a different identity to run your command, using the **sudo** (switch user, do) command. There is lots of information available about that. Use it with caution; it is possible to break things in unexpected ways by using it inappropriately.

~/.local/share/applications is the place in your Home folder where .desktop files for your user are stored, and ~/.local/share/icons for icons. You may want to use those in preference to the system-wide ones.

---

### Post by yetimon_64 on 2019-01-02
> **CatKiller said:**
> ...
~/.local/share/applications is the place in your Home folder where .desktop files for your user are stored, and ~/.local/share/icons for icons. You may want to use those in preference to the system-wide ones.
+1.

@ OP, Using these locations will avoid the permissions problems you are currently noting. Copying system desktop files to ~/.local/share/applications gives you ownership of the desktop files and will allow you to easily change any contents. Any desktop file placed at this location will be used instead of the system copy for your user profile.

---

### Post by kesetyan on 2019-01-02
Hi CatKiller and yetimon_64,

Thanks for your replies - I beginning to understand a bit more.  I've copied one '.desktop' file from '/usr/share/applications', changed the icon on the copy and placed it on the desktop.  I don't know if it's possible to put it on the application launch bar on the panel instead as, as far as I can see, applications on the panel relate to menu categories and I've yet to work out how to add my own categories there.

The other thing, as yet unresolved, is how to turn  my 'EjectDisc' executable script into a working '.desktop' file - the script is to open the cd/dvd drive tray and it does work but only indirectly.  When I double click the file's shortcut on the desktop, a message window appears showing the executable is recognized and gives 4 options ('execute', 'execute in terminal', 'Open' and 'Cancel' - I would like it to open directly and preferably from a '.desktop' link with my own icon on the desktop.

Thanks again for your advice and your patience in helping an old fogey like me.

---

### Post by CatKiller on 2019-01-02
You can drag-and-drop .desktop files onto the panel.

.desktop files in ~/.local/share/applications will be automatically added to the menu. 

The menu category is defined within the file itself, from a standardised set.

The specification is [here](https://www.freedesktop.org/wiki/Specifications/desktop-entry-spec/).

The protection against executable text files is provided by the desktop environment. Rather than turning that off, you can probably call the shell directly in your Exec line. However, there is probably a command to eject the tray that doesn't need to be included in a script; I don't have an optical drive to check.

---

### Post by kesetyan on 2019-01-03
Hi CatKiller,

Many thanks - I've now got a bit of experimenting to do; your advice has given me confidence to explore the possibilities.

Regarding ejecting the CD tray - simply typing 'eject' into the terminal and pressing <ENTER> will eject the tray but I wanted a one click option which I have now sorted with your help.

---

