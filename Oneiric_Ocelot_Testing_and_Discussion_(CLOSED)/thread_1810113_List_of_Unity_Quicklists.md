---
title: "List of Unity Quicklists"
date: 2011-07-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2011-07-22
I've used [this page]("http://askubuntu.com/questions/35488/list-of-custom-launchers-quicklists-for-unity") for a while and thought the fora needed a thread to coordinate with that page and, maybe, putting our own out there.

I'll start with the two I find most useful:

[Google+ Quicklist]("http://www.omgubuntu.co.uk/2011/07/google-unity-launcher/") via [Joey Sneddon]("http://www.omgubuntu.co.uk/author/d0od") at [OMG!Ubuntu!]("http://www.omgubuntu.co.uk/")

[Places Quicklist]("http://www.omgubuntu.co.uk/2011/04/how-to-add-folder-quicklists-to-the-home-launcher-in-ubuntu-unity/") via [Joey Sneddon]("http://www.omgubuntu.co.uk/author/d0od") at [OMG!Ubuntu!]("http://www.omgubuntu.co.uk/")

---

### Post by cariboo on 2011-07-22
Check [here]("https://wiki.ubuntu.com/PowerUsers/Tweaking") for links to more Quicklists

---

### Post by kansasnoob on 2011-07-23
Thanks to both of you for pointing this out. This link in particular has some useful stuff for me:

[http://askubuntu.com/questions/30334/list-of-application-indicators](http://askubuntu.com/questions/30334/list-of-application-indicators)

Particularly Caffeine and a couple of the "sys-load" indicators.

Neat stuff to try :D

This is going to require some more study:

[http://www.florian-diesch.de/software/classicmenu-indicator/](http://www.florian-diesch.de/software/classicmenu-indicator/)

---

### Post by moore.bryan on 2011-07-23
Happy to oblige!

---

### Post by mc4man on 2011-07-23
> **kansasnoob said:**
> 
This is going to require some more study:

[http://www.florian-diesch.de/software/classicmenu-indicator/](http://www.florian-diesch.de/software/classicmenu-indicator/)
While I prefer custom quicklists to create category style menus in the unity launcher, that one should work out ok, certainly in natty

Atm It runs fine in O, what would be interesting is how to edit it if desired, currently alacarte seems quite broken

---

### Post by moore.bryan on 2011-07-23
As a side-note--and I'm not sure if this is just my Oneiric install right now--I can't add anything to the Unity panel...

---

### Post by mc4man on 2011-07-23
> I can't add anything to the Unity panel...
Drag & Drop is currently non functional here, other methods are ok (fresh install today

---

### Post by moore.bryan on 2011-07-23
"Other methods?"

---

### Post by mc4man on 2011-07-23
> **moore.bryan said:**
> "Other methods?"

You can start something, then r. click keep in launcher
Also dconf and gsettings are still working

What's also non functional for the moment is the drag file (mimetype) over the launcher to highlight and drop on suitable icon

---

### Post by moore.bryan on 2011-07-23
Previously, I used a few quicklists and can confirm using dconf-editor and adding them in manually under desktop>unity>launcher>favorites *does not* add the quicklist in ~/.local/share/applications; in fact, the edits aren't even being saved.

Perhaps that's not the place to put them? Or, better, is there a config file I can just straight edit with nano?

---

### Post by mc4man on 2011-07-23
> in fact, the edits aren't even being saved.
To edit a string in dconf-editor you need to - 
click on  the line with the mouse till it turns 'white' (no  highlight color
Make your entry or edit, then do not click out with the mouse
With the cursor still in the box _Press enter on the keyboard_ to set the change

> is there a config file I can just straight edit with nano?
You can use gsettings in a terminal, takes a little reading/learning - man gsettings
For the launcher the string may be quite long, easier in dconf
(custom .desktops added from ~/.local/share/applications may be needlessly fullpathed in the string making it even longer

---

### Post by moore.bryan on 2011-07-23
> **mc4man said:**
> To edit a string in dconf-editor you need to - 
click on  the line with the mouse till it turns 'white' (no  highlight color
Make your entry or edit, then do not click out with the mouse
With the cursor still in the box _Press enter on the keyboard_ to set the change

Already did this and the settings *did not* save.

Nevermind... if I add one at a time, sometimes it saves, sometimes it doesn't, but--more importantly--I was *eventually* able to get them all on there.

Thanks for the guidance.

---

### Post by malspa on 2011-07-23
Is it possible (how do I word this?) to create a button on the launcher that brings up other application buttons? Like a "favorites" button for your favorite applications?

---

### Post by mc4man on 2011-07-23
> **moore.bryan said:**
> Already did this and the settings *did not* save.Don't know, works here fine on 2 installs, one old, one new

Here's an Ex of gsettings - I previously added totem.desktop w/ dconf a min. ago so I want to remove and clean up the string

First to get the current string
> gsettings get com.canonical.Unity.Launcher favorites
[COLOR="Blue"]['/home/doug/.local/share/applications/nautilus-home.desktop', 'google-chrome.desktop', 'utility.desktop', 'multimedia.desktop', 'gnome-terminal.desktop', 'mplayer1.desktop', 'mplayer2.desktop', 'firefox.desktop', 'totem.desktop'][/COLOR]

Now with the set command coping and pasting the blue above, editing and adding " to front and end of string

```
gsettings set com.canonical.Unity.Launcher favorites "['nautilus-home.desktop', 'google-chrome.desktop', 'utility.desktop', 'multimedia.desktop', 'gnome-terminal.desktop', 'mplayer1.desktop', 'mplayer2.desktop', 'firefox.desktop']"
```

The get will now return the new setting

> gsettings get com.canonical.Unity.Launcher favorites
['nautilus-home.desktop', 'google-chrome.desktop', 'utility.desktop', 'multimedia.desktop', 'gnome-terminal.desktop', 'mplayer1.desktop', 'mplayer2.desktop', 'firefox.desktop']


 pretty easy once you get the idea and read the man

useful commands are 
gsettings list-schemas

and then taking a schema and finding the keys
gsettings list-keys <schema>

ect. ect.

---

### Post by mc4man on 2011-07-23
> **malspa said:**
> Is it possible (how do I word this?) to create a button on the launcher that brings up other application buttons? Like a "favorites" button for your favorite applications?
Sure - very easy once you do once or twice
There is also a gui quicklist editor being developed - it's linked from the page linked in post 2
There isn't a ppa yet, but fairly easy to 'install' and use
(there are a couple of things being added that should make it more useful and may be in a ppa fairly soon

If you had a simple one in mind post what apps you want to see in it, the name of the launcher icon, what icon  you wish to use in the launcher and i'll post example .desktop for you

I'm just setting up this install - screen shows a Utilities  and Multimedia icons and quicklist, in this case some standard apps and some scripted ones like Update Sources and Restart

For these I haven't set a l. click action on the icon though they could have one, I prefer to just have as menus

---

### Post by malspa on 2011-07-23
mc4man, you the Man! That is exactly what I'm thinking of. I would actually prefer the menus without the icons, like you did. If you can post an example .desktop for the Utilities one, I think I can figure it out from there; that's the kind of thing I'd like to set up here.

Edit: Well, I might need some add'l pointers, but I'll try to research it tonight on my own first. Gotta head off to work.

---

### Post by mc4man on 2011-07-24
malspa - 

First a few points that may prove useful now or later

Normally to add one of these type .desktops to the launcher you'd create, _then_ just D&D onto the launcher. Till that's fixed, (if bkoken for you), you can use dcon-editor, gsettings as 'explained' in prior posts above or something I'll mention at end.

I prefer to create and store in ~/.local/share/applications though you could place in /usr/local/share/applications for multiple users from one location. 9you'd likely need to create dir. tree first

The 'action' line is  X-Ayatana-Desktop-Shortcuts= (blue in code box), it is 1 continuous line ; between Shortcut Group names
This determines what shows up in the quicklist and in what order
So for example I could have 15 Shortcut Group sections but only choose to display 10 of them atm. To do that I'd just remove the Shortcut Group name from the  X-Ayatana-Desktop-Shortcuts= line
No need to remove the Shortcut Group section if you may use later

The entries on the  X-Ayatana-Desktop-Shortcuts= line are  the Shortcut Group  name and must match exactly.
The Name= line in each group entry will be the name displayed in the quicklist, use whatever suits you.
The order in which <whatever> Shortcut Group section is listed in the .desktop is irrelevant
If you later decide to add on to a quicklist just create new sections at the bottom and enter the Shortcut Group name into the X-Ayatana-Desktop-Shortcuts= line where you'd like it/them to appear

By default a text editor like gedit will not open an existing .desktop, I use a nautilus action for .desktops but - 
If you need to edit one than just open a gedit window and drop the .desktop into.

The Exec= line in the Groups can be of quite a number of things - 
For apps you can use the default launch command, if you don't know then open it's default .desktop, usually in /usr/share/applications, in a text editor to see
You can also add any app specific option/parameter to that command.

Any command you can run from Alt+F2 can be used on the Exec= line
You can also use a scriptname that's in your PATH or use the full path to a script

For these menu style quicklists I prefer not to have an active left click on the launcher icon - that's why the Exec= in the main desktop section at the top is left blank. You can have one if you wish, I think better to leave inactive in most cases.

The display name of your launcher icon and it's launcher icon are set in the top section also. (Name= and Icon= 
You can name it whatever you wish and use pretty much any icon
Some icons can be set by name only, otherwise use full path to it's location
Only the launcher itself gets an icon

Note on editing an existing .desktop that are in the launcher - 
When you login all the favorites .desktops are, for lack of better words, preloaded
If you decide to make changes to the launcher's .desktop you need to do a logout/in for the change to take affect.

===============================================================
I'm going to remove the script  and nautilus-actions entries from the utility desktop - will make easier to see in thread, just ask if interested - 1 updated the sources, the other ran htop and i just added a restart one till that's fixed.

So you'd go (make sure you have a ./local/[COLOR="Blue"]applications[/COLOR] folder first in your home folder - view > show hidden files
The name of the .desktop itself doesn't particularly matter - should be short, simple and  for most cases,  unique
```
gedit ~/.local/share/applications/utility.desktop
```

```

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=
Name=Utilities
Icon=/usr/share/icons/Humanity/categories/48/applications-other.svg
[COLOR="Blue"]X-Ayatana-Desktop-Shortcuts=Synaptic;UpdateManager;CompizConfig;DconfEditor;GconfEditor;ForceQuit;ScreenShot;SeachFiles;[/COLOR]

[Synaptic Shortcut Group]
Name=Synaptic
Exec=gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic
TargetEnvironment=Unity

[UpdateManager Shortcut Group]
Name=Update Manager
Exec=/usr/bin/update-manager
TargetEnvironment=Unity

[CompizConfig Shortcut Group]
Name=Compiz Settings
Exec=ccsm
TargetEnvironment=Unity

[GconfEditor Shortcut Group]
Name=Gconf Editor
Exec=gconf-editor
TargetEnvironment=Unity

[ForceQuit Shortcut Group]
Name=Force Quit
Exec=xkill
TargetEnvironment=Unity

[ScreenShot Shortcut Group]
Name=Screen Shots
Exec=gnome-screenshot --interactive
TargetEnvironment=Unity

[SeachFiles Shortcut Group]
Name=Search For Files
Exec=gnome-search-tool
TargetEnvironment=Unity

[DconfEditor Shortcut Group]
Name=Dconf Editor
Exec=dconf-editor
TargetEnvironment=Unity

```

If you want to add anything else just create a new section(s) at bottom, name the Group, fill in the Name= and Exec= lines and add Group name to action line in position desired
Blank section template

```
[[COLOR="Blue"]Whatever[/COLOR] Shortcut Group]
Name=
Exec=
TargetEnvironment=Unity
```

Note - spaces between the various Group entries are not required - I like because easier to view and edit

If having trouble adding the launcher then you can use the top main Exec= that I've left blank to run the .desktop once to add. Then you can edit it out if not using from the .desktop in gedit

To 'run' a custom .desktop, assuming the top Exec= has a command
After creating the .desktop then r. click > properties and make executable.
The .desktop will change from looking like a file to it's icon and display name.
Then just d. click on

---

### Post by malspa on 2011-07-24
Very nice, mc4man -- worked beautifully!

The drag & drop worked for me. I actually use Dolphin in Natty, and I was able to drag & drop the files from within Dolphin right to the launcher.

Thank you very much for taking the time to post all that!

---

### Post by mc4man on 2011-07-24
> I actually use Dolphin in Natty
The D&D is only broken in 11.10, at least here

Hopefully you can now see how these are created and or edited/expanded when desired
Any  .desktops you create can be held on to and re-used, most of the ones I have in O are from natty
I just store on a usb and copy into ~/.local/... on new installs
(if doing that beware that .desktops should be C&P from or to usb drives, not D&D. If you D&D the .desktop will be moved, not copied
Another type of launcher icon that's interesting is a custom Drag & Drop icon based on mimetype. It uses unity's file drag function to run the Exec= on the file you drop on the icon
If ever interested just ask.

---

### Post by malspa on 2011-07-24
> **mc4man said:**
> The D&D is only broken in 11.10, at least here

Good to know. Most likely I'll be skipping 11.10 and waiting for 12.04 -- I normally stick with LTS versions only.

> **mc4man said:**
> Hopefully you can now see how these are created and or edited/expanded when desired

Yep. I created two of them, and have already edited them and added a few things to them!

Thanks again for the great info! This really helped me to clean up my Unity launcher; makes getting to certain apps very convenient!

---

