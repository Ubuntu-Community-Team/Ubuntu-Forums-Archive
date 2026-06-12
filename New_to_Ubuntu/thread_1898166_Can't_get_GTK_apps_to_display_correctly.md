---
title: "Can't get GTK apps to display correctly"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by x C0MMAND0 x on 2011-12-20
I am now running Kubuntu 11.10, and everything is (mostly) working just fine.  When I run apps like "gedit" or "nautilus" there themes don't match up at all with what I have configured.

I have tried "gtk-chtheme", I have tried installing "qtcurve" and following tutorials on those, but no matter what I try apps that use GTK are not displaying properly.

Any thoughts/ideas?

---

### Post by x C0MMAND0 x on 2011-12-20
And it's actually only some apps, Firefox and Banshee appear with the correct GTK theme settings I have defined, but other applications dont.

---

### Post by marl30 on 2011-12-20
I found a very neat work around for this on the Kubuntu forum. Here's the information I got from Kubuntu forum:


 HOWTO: gtk3-engines-oxygen for gtk3 apps
« on: October 24, 2011, 04:19:42 pm »     
Before using gtk3-engines-oxygen gtk3 apps look like this:
[http://www.dodaj.rs/?3p/XO/NioDUSf/snapshot1.jpg](http://www.dodaj.rs/?3p/XO/NioDUSf/snapshot1.jpg)

After setting up gtk3-engines-oxygen:
[http://www.dodaj.rs/f/P/ul/441HhOUh/snapshot7.png](http://www.dodaj.rs/f/P/ul/441HhOUh/snapshot7.png)

gtk3-engines-oxygen can be found in this ppa: [https://launchpad.net/~gnumdk/+archive/ppa]("https://launchpad.net/%7Egnumdk/+archive/ppa")
Download deb from there and install it or add whole ppa:
Code:
> 
sudo apt-add-repository ppa:gnumdk/ppa
sudo apt-get update
sudo apt-get install gtk3-engines-oxygen
After installing it, make gtk-3.0 folder in ~/.config folder. Then in gtk-3.0 folder create text file settings.ini with following contents:
Code:

 [Settings]
gtk-theme-name = oxygen-gtk

Link: [http://kubuntuforums.net/forums/index.php?topic=3118994.0](http://kubuntuforums.net/forums/index.php?topic=3118994.0)

Works perfectly for me. :)

---

### Post by marl30 on 2011-12-20
I might add... what you're having issue with is actually a problem with GTK3 integration. Most GTK2 apps will work perfectly, but GTK3 integration is yet to be added to KDE.

---

### Post by x C0MMAND0 x on 2011-12-20
You are definitely correct!  It is in issue with GTK3, and your fix did work, but I'm having the following issue:  Now when I open gedit or nautilus they are reallllllly slow.  I opened it from terminal and here's the output

```
$ gedit 

(gedit:9492): Gtk-WARNING **: Theme parsing error: gtk.css:58:46: Unknown value 'GTK_SHADOW_NONE' for enum type 'GtkShadowType'

(gedit:9492): Gtk-WARNING **: Theme parsing error: gtk.css:58:46: Unknown value 'GTK_SHADOW_NONE' for enum type 'GtkShadowType'

(gedit:9492): Gtk-WARNING **: Theme parsing error: gtk.css:58:46: Unknown value 'GTK_SHADOW_NONE' for enum type 'GtkShadowType'

** (gedit:9492): WARNING **: Could not load theme icon gtk-home: Icon 'gtk-home' not present in theme

(gedit:9492): GtkSourceView-WARNING **: no color named 'white'


``` 

Nautilus
```
(nautilus:9506): Gtk-WARNING **: Theme parsing error: gtk.css:58:46: Unknown value 'GTK_SHADOW_NONE' for enum type 'GtkShadowType'

(nautilus:9506): Gtk-WARNING **: Theme parsing error: gtk.css:58:46: Unknown value 'GTK_SHADOW_NONE' for enum type 'GtkShadowType'

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed
                                                                                                                                                             
(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:9506): LIBDBUSMENU-GLIB-CRITICAL **: dbusmenu_server_set_root: assertion `DBUSMENU_IS_MENUITEM(root)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:9506): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:9506): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_m
```

---

### Post by marl30 on 2011-12-20
I don't know why you're getting those errors. I haven't had any such issues. I also have Nautilus installed and working with Dropbox, and is working fine.

---

