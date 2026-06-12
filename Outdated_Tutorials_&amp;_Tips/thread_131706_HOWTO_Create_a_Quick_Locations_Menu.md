---
title: "HOWTO: Create a Quick Locations Menu"
date: 2006-02-16
forum: Outdated Tutorials &amp; Tips
---

### Post by Parkotron on 2006-02-16
This is just a simple HOWTO that adds a button to your KDE panel to quickly access your favourite directories. It uses only KMenu and the default KDE kicker. I'm sure many of you already know how to do this, but have never thought (or bothered) do it. It's tremendously simple to setup, but the gains in usability are tremendous. You can open any of you most visited folders in just two clicks or just one click and drag. See the first attachment for a screenshot of my setup.

[LIST=1]
[*]Open the KDE Menu Editor either by right-clicking on the KMenu button and choosing "Menu Editor" or by running **kmenuedit**.


[*]Create a new submenu via *File | New Submenu*. Name the submenu "Locations" or something similar.


[*]No our attention moves to the fields on the right side of the window. 
  Click the button with the cardboard box on it. Select an appropriate icon for your menu. I went with the "system" icon under Devices. You can add a description or a comment if you like, but this information won't be shown anywhere.


[*]As an example, we'll now create a entry to allow us quick access to the Home directory. 
  [LIST=a]
[*]Select the new submenu and create a new entry inside it via *File | New Item*. Name the new item "Home".
  [*]As you did for the submenu, select an icon for the entry. Since we're creating a list of folders most the icons we're looking for will be listed under "Filesystems". See the attached screenshot for some examples.
  [*]Again, you can add a description or a comment if you'd like. Descriptions will only be displayed if you have them turned on in KControl or System Settings under *Desktop | Panels | Menus*. Comments are never displayed.
  [*]In the Command field enter "konqueror pathToDirectory". Since we're creating an entry for the home directory, replace pathToDirectory with "~".
  [/LIST]


[*]Repeat step 5 to create all the other entries you want. You can rearrange the entries by dragging them. You can add separators via *File | New Separator*. You can also add submenus to your submenu if you'd like.


[*]Once you're satisfied, save the changes via *File | Save*. Then close the KDE Menu Editor.


[*]This step differs slightly depending on which version of KDE you have installed.
  [LIST=*]
[*]**KDE3.4 -** Right click on the panel then go *Add | Application Button | The Name of Your Submenu | Add This Menu*.
  [*]**KDE3.5 -** You'll probably need to unlock your panel by right-clicking on it and selecting *Unlock Panels*. Right click on it again then go *Add Application to Panel | The Name of Your Submenu | Add This Menu*.
  [/LIST]


[*]Right-click on the new button and select *Move ... Menu* and slide the menu to the desired position. KDE3.5 users will probably want to relock the panel when finished.
[/LIST]

Of course you can apply this technique to things other than folders, like for example the Diablo II menu in the third screenshot. I hope someone finds this useful.

Parker

**Note:** If you don't use Konqueror as your primary browser you can get nearly the same result in a much easier way. Simply bookmark the directories you want to use in Konqueror, then add the Bookmark Menu to the kicker. Of course if you do this you dont get to choose your icons, but it certainly is less work to setup.

---

