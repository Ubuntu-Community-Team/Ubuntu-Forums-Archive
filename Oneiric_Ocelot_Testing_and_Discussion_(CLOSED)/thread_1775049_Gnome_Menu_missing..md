---
title: "Gnome Menu missing."
date: 2011-06-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by celticbhoy on 2011-06-04
After updating last night I no longer have any entries in the Apps menu in Gnome Classic. Places, and System menu's show, and work as they should. By default I have installed and use Gnome Shell from the Repo's, so I dont know if this is part of the cause, as if I try to start a session in Gnome Shell I get an error screen telling me to log out. 

I am really posting to check if anyone else has the same issue, or if during all my messing about with the install I have changed/installed something is causing the problem.

Just to add, that if I load a Unity session, then the system runs as it should, ie all apps available from the app menu.

---

### Post by Bowmore on 2011-06-04
Yes, it's a bit messy now with the Applications menu. Hopefully, this will be fixed soon.

The reason is that the /etc/xdg/menus/ files have been renamed/removed, thus
- applications.menu renamed to gnome-applications.menu
- settings.menu removed
This also is the reason why the folder ~/.config/menus/ is empty for new installations.

A workaround is to recreate the Applications file named applications.menu, i.e
create it with
```
gedit ~/.config/menus/applications.menu
```
and paste the following into it
```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
   <Name>Applications</Name>
   <MergeFile type="parent">/etc/xdg/menus/gnome-applications.menu</MergeFile>
</Menu>
```
Now the Applications menu should work.

However, editing the menu still fails so you also have to create the settings.menu file to make editing (alacarte) work, so create that too with
```
gedit ~/.config/menus/settings.menu
```
and paste this into it
```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
   <Name>Desktop</Name>
   <MergeFile type="parent">/etc/xdg/menus/gnome-settings.menu</MergeFile>
</Menu>
```

You may wonder about the file gnome-settings.menu as it does not exist. Could be any name here but alacarte requires this file too, including a correct format, so it's a dummy only for now until the Applications menu is fixed.

---

### Post by celticbhoy on 2011-06-04
Cheers for the info, at work just now, but dont want to go home and spend too much time looking for an answer if its down to something I have done.

I will give your workaround a go when I get home.

Thanks again.

---

### Post by kansasnoob on 2011-06-04
> **celticbhoy said:**
> After updating last night I no longer have any entries in the Apps menu in Gnome Classic. Places, and System menu's show, and work as they should. By default I have installed and use Gnome Shell from the Repo's, so I dont know if this is part of the cause, as if I try to start a session in Gnome Shell I get an error screen telling me to log out. 

I am really posting to check if anyone else has the same issue, or if during all my messing about with the install I have changed/installed something is causing the problem.

Just to add, that if I load a Unity session, then the system runs as it should, ie all apps available from the app menu.

I have the same problem, but I also have no System Menu :(

---

### Post by dino99 on 2011-06-04
> **kansasnoob said:**
> I have the same problem, but I also have no System Menu :(

hey, thats the new gnome3 design, so im looking at kde right now as it let you tweak your system as you like (eg: gnome3 new concept is to lock everything by removing direct access)

Looking at Vuntz blog about new gnome-panel I've found:
"Still editable, but not by accident: this all sounds cool, but you tried to add an applet, or to even just move one, but without success? There's a secret trick here: press alt (or the modifier configured for metacity, if you changed it) and right-click"

So secret that I need also the left-click.. woohoo!!

---

### Post by kansasnoob on 2011-06-04
> **dino99 said:**
> hey, thats the new gnome3 design, so im looking at kde right now as it let you tweak your system as you like (eg: gnome3 new concept is to lock everything by removing direct access)

Looking at Vuntz blog about new gnome-panel I've found:
"Still editable, but not by accident: this all sounds cool, but you tried to add an applet, or to even just move one, but without success? There's a secret trick here: press alt (or the modifier configured for metacity, if you changed it) and right-click"

So secret that I need also the left-click.. woohoo!!

I'm looking very seriously at Lubuntu ATM. 

I just don't seem to be smart enough for Unity and/or gnome3.

---

### Post by bmbaker on 2011-06-04
> **Bowmore said:**
> Yes, it's a bit messy now with the Applications menu. Hopefully, this will be fixed soon.

The reason is that the /etc/xdg/menus/ files have been renamed/removed, thus
- applications.menu renamed to gnome-applications.menu
- settings.menu removed
This also is the reason why the folder ~/.config/menus/ is empty for new installations.

A workaround is to recreate the Applications file named applications.menu, i.e
create it with
```
gedit ~/.config/menus/applications.menu
```and paste the following into it
```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
   <Name>Applications</Name>
   <MergeFile type="parent">/etc/xdg/menus/gnome-applications.menu</MergeFile>
</Menu>
```Now the Applications menu should work.

However, editing the menu still fails so you also have to create the settings.menu file to make editing (alacarte) work, so create that too with
```
gedit ~/.config/menus/settings.menu
```and paste this into it
```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
   <Name>Desktop</Name>
   <MergeFile type="parent">/etc/xdg/menus/gnome-settings.menu</MergeFile>
</Menu>
```You may wonder about the file gnome-settings.menu as it does not exist. Could be any name here but alacarte requires this file too, including a correct format, so it's a dummy only for now until the Applications menu is fixed.

this worked great, thank you :-)
i had just finished installing gnome-shell in oneiric and it kept crashing ....... now with this fix its good :-)

---

### Post by celticbhoy on 2011-06-04
Just for confirmation, Bowmore's fix has also worked for me. I did have to remove the original contents of the applications.menu file before it worked, but all is good again.

Once again thanx for the quality advice.

Been a while since I have been active on the forum's, when did they remove the thanks button ?

---

### Post by jerrylamos on 2011-06-04
4 June Daily Build has menus although incomplete.  Alpha 1 was DOA for me.

I've run 4 June Live persistent on three test pc's so far.

Jerry

---

### Post by Bowmore on 2011-06-05
> **kansasnoob said:**
> I have the same problem, but I also have no System Menu :(You can find the System menu items in the Applications menu at the end under **Other**.

If you don't find *Other* in the menu try remove (rename) the file
/etc/xdg/menus/applications.menu

For some reason applications.menu (depreciated) interfers with the Applications menu.

By default only these file should be located there
/etc/xdg/menus/gnome-applications.menu
/etc/xdg/menus/gnomecc.menu
/etc/xdg/menus/unity-place-applications.menu

---

### Post by dino99 on 2011-06-06
> **Bowmore said:**
> You can find the System menu items in the Applications menu at the end under **Other**.

If you don't find *Other* in the menu try remove (rename) the file
/etc/xdg/menus/applications.menu

For some reason applications.menu (depreciated) interfers with the Applications menu.

By default only these file should be located there
/etc/xdg/menus/gnome-applications.menu
/etc/xdg/menus/gnomecc.menu
/etc/xdg/menus/unity-place-applications.menu

If i follow the lines above (renaming applications.menu) then Applications menu dont open (empty ?) Anyway "Other" submenu dont show "System" entries.

Edit: need to change the previous url by that one too:
'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
into gnome-applications.menu to get Applications scrolldown menu back.
I find "Editing menus" under Other, but that one is not the same we had with gnome2:
- no "properties" entry, no "add" entry, no "remove" entry
- no "preferences" submenu, no "administration" submenu

what a headache :( :(

---

### Post by Bowmore on 2011-06-06
I guess it's the *Menu Editor* (command: gmenu-simple-editor) you ran into. Just run *Edit menus* (alacarte) and uncheck it if you don't want that one to be visible.

About *Settings* and *Administration* submenus those seem to have been merged into one menu now. But as long as the .desktop-files *Categories* settings remain the old way it should be possible to create those submenus under Other with some minor hacking in the gnome-applications.menu. Maybe a "new" feature request?

---

### Post by dino99 on 2011-06-06
As i've saved the old *.menu, i use them back as i cant find an easy way to get "Applications" working: only work with applications.menu (on a natty upgraded to oneiric)
About alacarte, now the right panel with: edit/remove/... is lost.

---

### Post by Bowmore on 2011-06-06
Ok, have you read my first post?

The file ~/.config/menus/**applications.menu** shall contain a line
<MergeFile type="parent">/etc/xdg/menus/**gnome-applications.menu**</MergeFile>
thus pointing to the file /etc/xdg/menus/**gnome-applications.menu**

In Gnome 3 the file gnome-applications.menu replaces applications.menu in the folder /etc/xdg/menus/.

Your ~/.config/menus/applications.menu probably still points to the depreciated /etc/xdg/menus/applications.menu and thus the reason why you still need the depreciated file to make it work.

About alacarte, that's really strange!

Same here, running a Natty upgraded to Oneiric.

---

### Post by dino99 on 2011-06-06
Thanks for following this misconfig :)

yes i've followed the post #10, but i've some doubts about removing or not "applications.menu", and it dont have that line pointing to gnome-applications.menu

my bad, the previous answers was about /etc/xdg/... files

here is .config/menus/applications.menu

<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
</Menu>

so i see 1 thing to update:
- pointing to gnome-applications.menu

do you agree ?

---

### Post by dino99 on 2011-06-06
ok i've made the changes into .config/menu/applications.menu & removed  /etc/xdg/menus/applications.menu

now "Other" have the old "system" menu entries mixed, what a mess :(

and still no alacarte menu

---

### Post by Bowmore on 2011-06-06
Yes, that should work.

Just discovered that I'm using the old url because it was there and I didn't notice but changed that now in my home directory files applications.menu and settings.menu :)

---

