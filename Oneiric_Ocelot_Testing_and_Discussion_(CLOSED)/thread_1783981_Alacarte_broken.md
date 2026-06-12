---
title: "Alacarte broken"
date: 2011-06-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-06-16
After have re-installed OO today I have both alacarte broken and main-menu empty (in fallback mode).

```
$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 37, in <module>
    main()
  File "/usr/bin/alacarte", line 33, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 44, in __loadMenus
    self.applications.path = os.path.join(util.getUserMenuPath(), self.applications.tree.get_menu_file())
  File "/usr/lib/python2.7/posixpath.py", line 66, in join
    if b.startswith('/'):
AttributeError: 'NoneType' object has no attribute 'startswith'
```

---

### Post by Harry33 on 2011-06-16
Try to purge it and then install it again.

---

### Post by lucazade on 2011-06-17
> **Harry33 said:**
> Try to purge it and then install it again.

tried but no luck, still broken :/

---

### Post by cariboo on 2011-06-17
I get the same output when trying to start alacarte in a terminal.

---

### Post by mc4man on 2011-06-17
Seems to work fine here (gnome-panel 3 - fully updated with exception of libcairo2 which shouldn't much  matter

While probably won't use this login for real  for the moment adding a few things from Desktop > Admin to Appl.. > System Tools  by running 2 alacarte's at once and copying over
(have Applications and Places on panel, - no Pref's or Admin

---

### Post by lucazade on 2011-06-17
Thanks guys for feedbacks.

I was looking for differences between OO and NN and
~/.config/menus is empty in OO

any way to generate again these .desktop files?

---

### Post by mc4man on 2011-06-17
> **lucazade said:**
> Thanks guys for feedbacks.

I was looking for differences between OO and NN and
~/.config/menus is empty in OO

any way to generate again these .desktop files?
By default there is no ~/.config/menus in NN or OO

As far as OO it was created as soon as I did some 'alacarte-made' .desktops
In unity/GS i just use gedit to create .desktops which doesn't create/use ~/.config/menus
(though all the .desktops I previously made in unity did show up in alacarte

---

### Post by lucazade on 2011-06-17
@mc4man

ok! :)

This is what I have in Natty:
```
$ ls /etc/xdg/menus/
applications.menu  gnome-screensavers.menu  unity-place-applications.menu
gnomecc.menu       settings.menu

$ echo $X
$XAUTHORITY          $XDG_DATA_DIRS       
$XDG_CONFIG_DIRS     $XDG_SESSION_COOKIE  

$ echo $XDG_DATA_DIRS 
/usr/share/gnome-2d:/usr/share/gnome:/usr/local/share/:/usr/share/

$ echo $XDG_CONFIG_DIRS 
/etc/xdg/xdg-gnome-2d:/etc/xdg
```

and in Oneiric:
```
$ ls /etc/xdg/menus/
gnome-applications.menu  gnomecc.menu  unity-place-applications.menu

$ echo $X
$XAUTHORITY          $XDG_DATA_DIRS       $XDG_SESSION_COOKIE

$ echo $XDG_DATA_DIRS 
/usr/share/gnome:/usr/local/share/:/usr/share/
```

In OO $XDG_CONFIG_DIRS is missing (I believe is important for XDG menus) and .menu files are a bit different (like gnome- prefix).
Maybe the problem is here.

---

### Post by mc4man on 2011-06-17
I'm going to maybe do a fresh O install on a laptop IF the live cd can do a manual partioning ect.

I see in this package what you're missing?, though packages.ubuntu can fall out of date sometimes in some areas ( applications.menu, settings.menu
[http://packages.ubuntu.com/oneiric/gnome-menus/filelist](http://packages.ubuntu.com/oneiric/gnome-menus/filelist)

Edit: and it's in the manifest for the current live
> gnome-menus	3.0.1-0ubuntu2

re-edit:
this just added yet another thing I'm not liking in gnome3/nautilus3 - gedit's search used to have a drop down history - if there's one there now i can't see it.

---

### Post by lucazade on 2011-06-17
> **mc4man said:**
> I'm going to maybe do a fresh O install on a laptop IF the live cd can do a manual partioning ect.

I see in this package what you're missing?, though packages.ubuntu can fall out of date sometimes in some areas ( applications.menu, settings.menu
[http://packages.ubuntu.com/oneiric/gnome-menus/filelist](http://packages.ubuntu.com/oneiric/gnome-menus/filelist)

Edit: and it's in the manifest for the current live


re-edit:
this just added yet another thing I'm not liking in gnome3/nautilus3 - gedit's search used to have a drop down history - if there's one there now i can't see it.

Thanks for info, haven't tought to gnome-menus.
I'll see if a bug report is present and if there will be changes to gnome-menu package.

Yep, gedit's search has been rewritten, haven't noticed the lack of history, damn,  hope it is a temporary bug :)

---

### Post by mc4man on 2011-06-17
> Yep, gedit's search has been rewritten, haven't noticed the lack of history, damn, hope it is a temporary bug
Maybe - there seems to be a trend of some things not being seen as important. ('design' rules the day

One that struck me right away is custom commands have been removed from the context menus. You can currently get around by  creating a .desktop to do the custom command, instead of the previous, -  using a  custom command creates the .desktop (userapp.desktop
(one of the real pluses of quicklists which can execute pretty much anything

So in that regard alacarte could continue to be useful if one wanted a custom .desktop created for them,  even in unity/GS, after making, it can be dragged or added to launcher(s) from ~/.local/share/applications/

Also thought I saw in a changelog that desktop launchers may be eliminated at some point.
(File Management > Media is also gone though it still shows in a slightly neutered form.

---

### Post by lucazade on 2011-06-17
> **mc4man said:**
> Maybe - there seems to be a trend of some things not being seen as important. ('design' rules the day

One that struck me right away is custom commands have been removed from the context menus. You can currently get around by  creating a .desktop to do the custom command, instead of the previous, -  using a  custom command creates the .desktop (userapp.desktop
(one of the real pluses of quicklists which can execute pretty much anything

So in that regard alacarte could continue to be useful if one wanted a custom .desktop created for them,  even in unity/GS, after making, it can be dragged or added to launcher(s) from ~/.local/share/applications/

Also thought I saw in a changelog that desktop launchers may be eliminated at some point.
(File Management > Media is also gone though it still shows in a slightly neutered form.

Absolutely right, the removal of custom commands from context menu is pretty absurd, like the lack of gedit's search history and the removal of "Go to parent dir/ Up a level" button from nautilus toolbar (I was fond of it :) )

I'm still waiting to see gnome3 guidelines, nautilus toolbar is so inconsistent with the rest I want to know how it was designed.. :)

---

### Post by mc4man on 2011-06-17
Well - 
got a fresh install of todays iso on this laptop - seemed to be some significant differences from a 2 week old on a desktop where it all works fine

Saw same deal as you when running alacarte, plus in gnome-panel (3) login no applications dropdown.
Same on GS login - applications just caused crash.

Tried matching a number of things, no dice
Plus in the unity dash - no installed apps section
So I'd say there is a bug -  pretty screwed up, going to dump this install
(in unity I can access anything from some pre-made launcher menus

Now because I don't particularly care went ahead and got it (alacarte and applications menu in gnome-panel login, full apps in GS) to 'work' by copying all the entries to ~/.config/menus but that's highly improper

---

### Post by lucazade on 2011-06-17
> **mc4man said:**
> 
Now because I don't particularly care went ahead and got it (alacarte and applications menu in gnome-panel login, full apps in GS) to 'work' by copying all the entries to ~/.config/menus but that's highly improper

"If the hill will not come to Mahomet, Mahomet will go to the hill" - Francis Bacon

---

### Post by mc4man on 2011-06-17
Went ahead with a fresh install/updated again from an iso  about 5 days old this time.
The same deal occurred in the gnome panel login - the Applications menu wouldn't drop down and obviously alacarte would fail as seen.

Turns out  /ect/xdg/menus now uses gnome-applications.menu but the current gnome 3 panel won't use it.
(on my older install I had both in there, that's why it worked.

So for the moment renaming it back to applications.menu allowed the Apps menu dropdown.
As far as alacarte it still wouldn't work, only an empty ~/.config/menus is created
So copying the /ect/xdg/menus/applications.menu into the home menus folder gets it going. (also would take care of the above..

There's no real use for the system (settings.menu) anymore other than if wanting to copy some launcher's info to new ones, then you could add in natty's for such stuff (opening 2 alacartes, C&P,  ect.

I'd assume they'll get this squared away as far as the naming, alacarte who knows..

(another thing of small interest is I couldn't figure why 'Startup Applications' wasn't showing up in unity's dash. Turns out it has a line in the .desktop - NoDisplay=true, good to disable alot of the junk

---

### Post by lucazade on 2011-06-17
> **mc4man said:**
> Went ahead with a fresh install/updated again from an iso  about 5 days old this time.
The same deal occurred in the gnome panel login - the Applications menu wouldn't drop down and obviously alacarte would fail as seen.

Turns out  /ect/xdg/menus now uses gnome-applications.menu but the current gnome 3 panel won't use it.
(on my older install I had both in there, that's why it worked.

So for the moment renaming it back to applications.menu allowed the Apps menu dropdown.
As far as alacarte it still wouldn't work, only an empty ~/.config/menus is created
So copying the /ect/xdg/menus/applications.menu into the home menus folder gets it going. (also would take care of the above..

There's no real use for the system (settings.menu) anymore other than if wanting to copy some launcher's info to new ones, then you could add in natty's for such stuff (opening 2 alacartes, C&P,  ect.

I'd assume they'll get this squared away as far as the naming, alacarte who knows..

(another thing of small interest is I couldn't figure why 'Startup Applications' wasn't showing up in unity's dash. Turns out it has a line in the .desktop - NoDisplay=true, good to disable alot of the junk

Thanks for your infos, I will replicate your steps on my setup, for sure.

---

### Post by mc4man on 2011-07-25
> **lucazade said:**
> Absolutely right, the removal of custom commands from context menu is pretty absurd, like the lack of gedit's search history and the removal of "Go to parent dir/ Up a level" button from nautilus toolbar (I was fond of it :) )

I'm still waiting to see gnome3 guidelines, nautilus toolbar is so inconsistent with the rest I want to know how it was designed.. :)
The 'new' nautilus window seems ok here with the exception of Ctrl+l - the location window is too small and a bit of a pita to use (ambiance/unity

Also today the option to create desktop launchers was removed completely as it was non-functional without gnome-panel being installed
Not a big deal here, custom commands can be still used by manually creating the .desktop w/ desired Exec=, though maybe some will miss

---

### Post by lucazade on 2011-07-25
> **mc4man said:**
> The 'new' nautilus window seems ok here with the exception of Ctrl+l - the location window is too small and a bit of a pita to use (ambiance/unity

Also today the option to create desktop launchers was removed completely as it was non-functional without gnome-panel being installed
Not a big deal here, custom commands can be still used by manually creating the .desktop w/ desired Exec=, though maybe some will miss

Nautilus is probably the worst component of GNOME3.
I tried to get back the old toolbar functions (uplevel, navigation breadcrumb/full path switch) by playing with nautilus.xml interface file but these functions are totally removed from core.
Didn't know about desktop launcher removal, good to know or better bad to know. Really disappointed about this. One step forward, two steps backward. :/

---

### Post by mc4man on 2011-07-25
Will be interesting to see what the combined philosophies of limited by design(teams) will have produced by O's release.
Atm it seems a bit too early to see, some config/mod options may not be gone, more that nothings yet in place (though some may be gone for good or never intended

Ex. - was noticing yesterday that the dash defaults app's, (the 3 that could, photos is hard coded), weren't responding to sysinfo. Probably because dash uses gconf, sysinfo gsettings, so that should be fixed.
What would be nice though is to be able to put whatever you wanted there, that will probably never happen
(screen - I altered dash's source a bit as to what **I'd** want on **this** machine though a gui method would be best

---

### Post by seeker5528 on 2011-07-25
> **lucazade said:**
> Nautilus is probably the worst component of GNOME3.
I tried to get back the old toolbar functions (uplevel, navigation breadcrumb/full path switch)

'Ctrl'+'L' switches you to the path, but it is only good for entering a path not for navigation, 'Esc' cancels it, taking you back to the bread crumb.

I could see how people might prefer to have an up button, but since you can click any place in the bread trail to gett to an upper level directory (the HD icon at the beginning of the trail for '/'), not having the up button seems like a minor detail.

Later, Seeker

---

### Post by mc4man on 2011-07-25
I just don't like how it ( the location box), is limited to 20 visible characters, not like it's taking space away from anything

---

### Post by lucazade on 2011-07-26
> **seeker5528 said:**
> 'Ctrl'+'L' switches you to the path, but it is only good for entering a path not for navigation, 'Esc' cancels it, taking you back to the bread crumb.

I could see how people might prefer to have an up button, but since you can click any place in the bread trail to gett to an upper level directory (the HD icon at the beginning of the trail for '/'), not having the up button seems like a minor detail.

Later, Seeker

I know about ctrl+l and up-level from breadcrumb.

To me is not a minor detail, a filemanager should show all the necessary buttons in a sane way and without special shortcuts.
Navigation arrows at the end of the toolbar are really a bad decision which breaks also gnome hig guidelines and are not pratical at all.

Instead of playing poorly with the toolbar I would have expected something better.. look at Dolphin, another world.

No possibility of undo/redo, 
no right sidebar with info about files, 
you can't select multiple files in detailed view with mouse (only in icon view or using shift/ctrl), 
you can paste files only r.clicking on the directory or in empty space (if exists),
huge time to load big directories
and a lot of other issues..

---

### Post by mc4man on 2011-07-26
As mentioned I don't particularly use desktop launchers but for those that find them useful - 
As long as gnome-panel is available and installed - this is a command

```
 gnome-desktop-item-edit "$(date).desktop"
```

Create in dir. terminal prompt is at, default home. So for Desktop

```
cd Desktop && gnome-desktop-item-edit "$(date).desktop"
```

---

### Post by seeker5528 on 2011-07-27
> **lucazade said:**
> I know about ctrl+l and up-level from breadcrumb.

To me is not a minor detail, a filemanager should show all the necessary buttons in a sane way and without special shortcuts.
Navigation arrows at the end of the toolbar are really a bad decision which breaks also gnome hig guidelines and are not pratical at all.

Instead of playing poorly with the toolbar I would have expected something better.. look at Dolphin, another world.

If I look at Dolphin.... it gives the option for more things on the toolbar, but OOB it unless it carried it over from previous versions it seems for arrows you have forward and back, no up, 'Ctl'+ 'L' to be able to type a path, 'Esc' to get back to the bread crumb.

They do call Nautilus a 'file browser' not a 'file manager' so maybe that gives some indication of where the developers heads are at, but even as a browser it could do more. Maybe filing a bug upstream about improving the behavior of the location entry box would be more productive, I don't know.

Maybe requesting some of the other stuff could produce some results as well, but the general attitude toward adding features among Gnome developers versus KDE developers seems pretty well known at this point.

Later, Seeker

---

### Post by mc4man on 2011-07-27
The location box is much improved today - probably worth waiting till no more upstream versions till thinking it's an issue

(Do have this annoying cursor off by some pixels in unity only, hopefully that will resolve itself

---

### Post by lucazade on 2011-07-27
> **seeker5528 said:**
> If I look at Dolphin.... it gives the option for more things on the toolbar, but OOB it unless it carried it over from previous versions it seems for arrows you have forward and back, no up, 'Ctl'+ 'L' to be able to type a path, 'Esc' to get back to the bread crumb.

They do call Nautilus a 'file browser' not a 'file manager' so maybe that gives some indication of where the developers heads are at, but even as a browser it could do more. Maybe filing a bug upstream about improving the behavior of the location entry box would be more productive, I don't know.

Maybe requesting some of the other stuff could produce some results as well, but the general attitude toward adding features among Gnome developers versus KDE developers seems pretty well known at this point.

Later, Seeker

You highlighted valid points, nothing to add.
Probably the manager <> browser distinction could explain some decisions behind the scenes but still don't get how removing buttons from the toolbar or hide useful functions could help me managing files. Looks like an oversemplification just for the sake of it or just to follow a trend of remove chrome.
As a said it is just Nautilus, with the rest of gnome I feel comfortably. Gnome3 was an opportunity to give more love to Nautilus not to make it worst :)

---

