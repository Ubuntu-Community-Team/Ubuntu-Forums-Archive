---
title: "Changing the gnome icon from the ubuntu 6.0.6 icon on the menu bar"
date: 2006-09-18
forum: Outdated Tutorials &amp; Tips
---

### Post by bluefuse on 2006-09-18
[COLOR="Navy"][FONT="Century Gothic"]This is based on the same technique used to get the gnome foot back in Breezy. For Dapper, it's a little trickier but here goes:

First get the gnome-menu-logo.png no save it as 3 different files, you will want to renmae these files first thing (start here.png,gnome-main-menu.png,distributor-logo.png) store all three files in you home folder, proceed to the next step, open up at teminal and enter in the following; 

sudo mv /home/yourusername/distributor-logo.png /usr/share/icons/Human/48x48/places
sudo mv /home/yourusername/gnome-main-menu.png /usr/share/icons/Human/48x48/places
sudo mv /home/yourusername/start-here.png /usr/share/icons/Human/48x48/places
sudo rm /usr/share/icons/Human/index.theme /home/yourusername
sudo mv icon-theme.cache icon-theme.cache.bk

sudo mv /home/yourusername/distributor-logo.png /usr/share/icons/hicolor/48x48/apps

Then delete the file from your home folder and remove the menu bar and reboot your pc, the add the menu bar back, you should see the new icon in the add/remove.

With any luck, the classic Gnome foot will be back.=D>  [/FONT][/COLOR]
[COLOR="DarkOrange"]The following site has been updated on ubuntu 6.0.6 by blu [/COLOR][COLOR="Red"][http://doc.gwos.org/index.php/Gnome_Icon_Dapper](http://doc.gwos.org/index.php/Gnome_Icon_Dapper)[/COLOR]

---

### Post by bluefuse on 2006-09-19
[COLOR="Red"]This is based on the same technique used to get the gnome foot back in Breezy. For Dapper, it's a little trickier but here goes:

First get the gnome-menu-logo.png no save it as 3 different files, you will want to renmae these files first thing (start here.png,gnome-main-menu.png,distributor-logo.png) store all three files in you home folder, proceed to the next step, open up at teminal and enter in the following;
file.pngCode:

[COLOR="DarkSlateGray"]sudo mv /home/yourusername/distributor-logo.png /usr/share/icons/Human/48x48/places
sudo mv /home/yourusername/gnome-main-menu.png /usr/share/icons/Human/48x48/places
sudo mv /home/yourusername/start-here.png /usr/share/icons/Human/48x48/places
sudo rm /usr/share/icons/Human/index.theme 
sudo rm /usr/share/icons/Human/icon-theme.cache icon-theme.cache.bk

sudo mv /home/yourusername/distributor-logo.png /usr/share/icons/hicolor/48x48/apps
sudo rm /usr/share/icons/hicolor/index.theme 
sudo rm /usr/share/icons/hicolor/icon-theme.cache icon-theme.cache.bk
[/COLOR]


Remove the menu bar and reboot your pc, the add the menu bar back, you should see the new icon in the add/remove.

With any luck, the classic Gnome foot will be back. [/COLOR]

---

### Post by ArchVile on 2006-10-21
You should not do it like in those howtos. The way to go is to find the right object_n in /app/panel/objects with the "Configuration Editor" (> gconf-editor). you will be looking for one which has object_type=menu-object. Change the value custom_icon to point to the icon you want to have displayed at the menu root (e.g., the Gnome foot).

You really shouldn't move or delete (in general: mess around with) system icons.

G'luck and happy gnoming.

---

### Post by notarikon on 2006-10-21
To expand on the last post slightly :)

Run Configuration Editor (Alt-F2 then gconf-editor)

Browse to /apps/panel/default_setup/objects/menu_bar

Enter the location of your icon in the custom_icon field AND tick the use_custom_icon option at the bottom of the list as well.

Then restart the gnome panel handler (Alt+F2 then killall gnome-panel

---

### Post by Tomber on 2006-10-22
about the last 2 posts: this only works if you are using the "real" gnome main menu applet, correct? because ive been wanting to replace the ubuntu logo with gnome logo as well, and it didnt work when i was using the default menu that ubuntu installs. now i need to find out how to get the "locations" menu back in my top panel :)

---

### Post by djb21212 on 2006-11-10
After nearly a year of fighting with it, I fond a way for the Ubuntu logo and Gnome foot to coexist! No messing with gconf is required either!

1: Locate the file "start-here.svg". It should be in the following directories:

/usr/share/icons/Tango/scalable/places
/usr/share/icons/Tangerine/scalable/places

2: Download your desired SVG file from where you like into your home folder. I've included the default Gnome foot for simplicity.

3: Perform the following commands:

sudo cp /home/yourusername/start-here.svg /usr/share/icons/Tango/scalable/places/start-here.svg

sudo cp /home/yourusername/start-here.svg /usr/share/icons/Tangerine/scalable/places/start-here.svg

All of the SVG files in those directories will use your new logo by default from now on. Next, update your icon cache:

sudo gtk-update-icon-cache --force Tango

sudo gtk-update-icon-cache --force Tangerine

4: Perform this command:

sudo mkdir /usr/share/icons/hicolor/places

This will make a new folder inside the directory where the default Gnome icons are stored.

5: Perform this command:

sudo cp /home/yourusername/start-here.svg /usr/share/icons/hicolor/places/start-here.svg

6: Next, refresh the icon cache for this folder as well:

sudo gtk-update-icon-cache --force hicolor

7: Next, perform this command:

sudo nautilus /usr/share/icons/hicolor/48x48/apps

This will let you go to that directory with root privleges. Once there, you'll find the Ubuntu logo as "distributor-logo.png". DO NOT DELETE THIS FILE! Instead rename it to "distributor-logo.png.old"

8: Locate a 48x48 PNG file to use for your new logo. I'd prefer using the Gnome foot again but it's up to you. Copy this file to the folder and rename it "distributor-logo.png".

9: Logout or reboot. When you log back into the desktop and change your theme, the Gnome foot should replace the Ubuntu logo using the default themes and vice-versa for the Ubuntu themes.

Bear in mind that I'm using Dapper Drake for this particular test. It may work for Edgy Eft but I haven't tested it yet. And it took me several trial-and-errors plus reinstallations to finally figure this out. Hope this helps!

---

### Post by bionnaki on 2006-11-10
does this work in edgy?

---

### Post by macewan on 2006-11-21
none of the other instructions seem to do the trick on edgy

---

