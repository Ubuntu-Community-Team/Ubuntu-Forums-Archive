---
title: "HOWTO: Create &amp; populate Sub-Menus in the Applications Menu"
date: 2005-05-23
forum: Outdated Tutorials &amp; Tips
---

### Post by kassetra on 2005-05-23
[i]Note:
This HOWTO assumes general Gnome familiarity along with experience using the command line and changing permissions.[/i]

**In Gnome, the Menuing system works like this:**

[list]
[*]There is an XML file (applications.menu) that sets up the structure of the Menu. *This is located in /etc/xdg/menus. You will need write permissions to this file.
[*]There are .desktop files that correspond to the icons / launchers in your Menu.  **These files are contained in possibly multiple directories on your system, including: "/usr/share/applications," "/usr/share/gnome/apps," and "/etc/X11/applnk." In order to better control your Menu, you will need to have all of your .desktop files in /usr/share/applications.*
[*]There are .directory files that correspond to the Sections in your Menu (Accessories, Games, Graphics, etc.) *These files are located in /usr/share/desktop-directories. You will need write permissions to this directory.
[/list]**Note: This HOWTO shows you how to edit the standard menu for all users on your system - if you would like to change only your own menu, the directories you will be using are: ~/.config/menus, ~/.local/share/applications, and ~/.local/share/desktop-directories, respectively. These local versions of the menuing system can be trickier to work, simply because the local menu merges with the standard menu - possibly causing duplicate entries, etc.*

In order to actually create the submenus, you will be editing an XML file on your system, as well as creating a special file called a ".directory" file.
[b]
In preparation for editing your menu, please have the following applications open:[/b]
**gedit** - with the file /etc/xdg/menus/applications.menu open for editing, plus a new blank document open.  [i]Note: you will need an icon to use for your submenus - you can reuse the same icon/file, or you can create a new .directory file with a different icon for every submenu you wish to create. 
Here is the icon I use: [img]http://www.linuxpeach.com/more-menu.png[/img][/i]
**nautilus** - open to the directory /usr/share/applications
**nautilus **- open to the directory /usr/share/desktop-directories

**To create the Submenu .directory file (which you will need first):**
1. In the blank document - type the following code:
 ```
[Desktop Entry]
Name=More
Comment=More Applications
Icon=more-menu
Type=Directory
``` 
Save the file as "more.directory" into /usr/share/desktop-directories.
Close the file. (The Icon=more-menu is how you would change the icon for the directory, you can put in an absolute path, such as /usr/share/pixmaps/my-special-icon.png or you can use the shorthand notation which I use here, if your icon is in either your theme or the pixmaps directory on your system. "more-menu.png" is in both my theme and my pixmaps directory.)
2. In the nautilus window that is open to the directory /usr/share/desktop-directories, you should see your icon labelled "More."

**As an example of how to create & populate submenus, we will be working with the "System Tools" section of the Applications Menu:**
In the applications.menu file, scroll down to the section that begins, <!-- System Tools -->
In order to have a populated submenu without duplicate icons appearing, we need to specify that our launcher/icon not be shown in the main section of the System Tools menu, and also be shown in the submenu. Let's start with creating the submenu to be populated. 
1. Create a blank line under the </Include> and before </Menu> of the System Tools section of the applications.menu file.
2. Add in the following code to that blank line:    
 ```
	<Menu>
	  <Name>More</Name>
	  <Directory>more.directory</Directory>
	  <Include>
	  </Include>
	</Menu>
``` - This code creates the submenu structure.

Now that we have the submenu created, we need to populate it. In this example, we will first populate the submenu with the "Floppy Formatter" launcher/icon, and then remove the "Floppy Formatter" launcher/icon from the main System Tools section.
1. In your nautilus window open to /usr/share/applications, locate the icon named "Floppy Formatter."
2. Drag this icon to the toolbar of gedit.
3. gedit will open the .desktop file and show you what it's exact name is - in my case, it's "gfloppy.desktop" ... you need to know this name in order to move this launcher/icon around in your menu file.
4. Close the "gfloppy.desktop" tab.
5. In the applications.menu file, scroll down to the new code you just entered that created the "More" area.
6. Between the <Include></Include>, enter the following code:
 ```
<Filename>gfloppy.desktop</Filename>
``` 
7. Move up to the area right above the "More" - to where it says <Category>System</Category>
8. Add a blank line after <Category>System</Category>
9. Enter the following code:
 ```
<Not>
<Filename>gfloppy.desktop</Filename>
</Not>
``` 
10. Save the applications.menu file.  In order to see your changes, you may need to do a "killall gnome-panel."

In your Applications menu, down at System Tools - if you hover your mouse over the section name, you should see a new icon at the top, "More" - with an arrow which if you follow, you should see a second menu with the Floppy Formatter launcher/icon inside.

The key point is that you had to tell the menu <Not><Filename>gfloppy.desktop</Filename></Not> for the regular section, at the same time telling it <Filename>gfloppy.desktop</Filename> in the new "More" menu. Using these processes, it is now possible for you to create many submenus, and move around your launchers/icons. :)  (At least until the next version of gnome...)
[i]
*Note if you move a launcher/icon in this manner, and find that there are duplicates in your menu, this can be caused by either .desktop files in other directories, or your local copy of applications.menu has the .desktop file specified. You may need to remove duplicate .desktop files and / or your local applications.menu.[/i]  

**Happy Menuing!**

---

### Post by keffo on 2005-05-23
Great!

By the way, may you post a screenie of this?

---

### Post by sapo on 2005-05-23
[QUOTE=keffo]Great!

By the way, may you post a screenie of this?[/QUOTE]

A Screenshot talks more than words  :-#

---

### Post by kassetra on 2005-05-23
Here you go!

[Submenus Screenshot]("http://ubuntuforums.org/gallery/showimage.php?i=297&c=4")

---

### Post by sapo on 2005-05-23
[QUOTE=kassetra]Here you go!

[Submenus Screenshot]("http://ubuntuforums.org/gallery/showimage.php?i=297&c=4")[/QUOTE]


Nice, very organized :D

And nice desktop too ;)

---

### Post by kassetra on 2005-05-23
[QUOTE=sapo]Nice, very organized :D

And nice desktop too ;)[/QUOTE]

Ha!  I knew someone would comment about my fudgey bunny.

---

### Post by sapo on 2005-05-23
[QUOTE=kassetra]Ha!  I knew someone would comment about my fudgey bunny.[/QUOTE]


Hehe but i really liked your desktop, very clean.. 

I m ashamed of mine.. i cant organize stuff.. i have a lot of files over my desktop, my top bar is FULL, i cant even add a shortcut there... and my 4 desktops always have a lot of random windows open

Btw... whats the icon theme you are using?  :-#

---

### Post by kassetra on 2005-05-23
[QUOTE=sapo]Hehe but i really liked your desktop, very clean.. 

I m ashamed of mine.. i cant organize stuff.. i have a lot of files over my desktop, my top bar is FULL, i cant even add a shortcut there... and my 4 desktops always have a lot of random windows open

Btw... whats the icon theme you are using?  :-#[/QUOTE]

Well, I organize everything - especially my menus / bookmarks so that I can find things I use very often (which is how I got onto the kick about submenus) ... and I use 7-10 desktops, which also helps things out a bit, because I "group" things together, like say my web work - bluefish on one desktop, nautilus / terminals on another... right next to each other.

As for my icon theme... well... it's mainly just icons I liked put together into my own theme... some from gartoon, jimmac, suse, novell, lila, and some hand-created.  :)  I kind of had the standard that any icon I wanted to add to my theme had to have a nice strong outline, but that's really the only basis other than "I like it."  :)

---

### Post by Ali_Baba on 2005-05-24
Nice desktop kassetra,looks very girlish,I think :) That kind of submenus could be a nice idea. Like you said those virtual desktops are great to use.You got nice space for all your applications.Also good HOWTO.

---

