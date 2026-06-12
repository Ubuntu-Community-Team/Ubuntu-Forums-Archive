---
title: "HOWTO: Custom Icon Themes"
date: 2006-09-05
forum: Outdated Tutorials &amp; Tips
---

### Post by crossedout on 2006-09-05
I've read many posts where folks want to use a custom icon for an application or apply an icon to an app that currently doesn't have an icon tied to it and decided to share my solution and hopefully help someone else.

Preparation:
-d/l at least one icon theme from gnome-look.org and install it.
--Installing an Icon Theme:  Open System->Preferences->Theme, click Theme Details, click icons and drag/drop the theme tar file onto the icons frame.  Confirm the installation and when complete you will see it present in the list.

-I recommend viewing: [http://live.gnome.org/GnomeArt/Tutorials/IconThemes]("http://live.gnome.org/GnomeArt/Tutorials/IconThemes") to familiarize yourself with how icon themes work and how they call upon icons when changing themes.

Notes:
-I am running gnome 2.14.3; Dapper
-If running gdesklets, you'll have to manually alter those icons.  gdesklets doesn't conform to the current theme.

[COLOR="Blue"]Step 1[/COLOR]:
Open your Home folder, ctrl-h  (to expose hidden folders/files), navigate to .icons folder.  Inside the .icons folder will be the installed theme(s) .  
Right-click and copy one of the theme folders and paste it to your desktop.  
Rename the folder, for this how-to I will use <Myicons>.  
Right-click and cut the folder from the desktop and paste it back into the .icons folder.

[COLOR="Blue"]Step 2[/COLOR]:
Open a terminal window.
```
gedit .icons/Myicons/index.theme
```
(Reminder: case sensitive)

[COLOR="Blue"]Step 3[/COLOR]:
At the top of the file are generic terms:
[Icon Theme]
Name=<themename> --> This is the theme name that will be displayed in Theme Manager.  This name needs to match exactly to the theme folder name.
Comments=<theme comment> --> Use as a simple descriptor.
Inherits=<root theme> --> This is used if an icon is not supplied by the current theme.

Edit the file to match as follows:
[Icon Theme]
Name=Myicons
Comment=Myicons Custom
Inherits=gnome
Save and exit.
You have now told the file to display the Myicons name in the Theme Manager and to read from the root gnome icons if an icon is not supplied with this theme.  If you open Theme Manager, you will now see the choice of Myicons under the icons tab.

Within the Myicons folder are subfolders showing which icons are supplied and what type.  For example, many icon themes have a gaim replacement icon located under the apps subfolder.  Some icons are placed in alternate folders depending upon the theme and artist.

[COLOR="Blue"]Step 4[/COLOR]:
Replace/Add icons based on the app/device/place/etc.
--You now have a custom icon folder.  If you have specific icons locate them or icon themes install them.
For this step I will use 2 examples:
Example A:  We want to replace the gaim icon.  
Navigate to the apps subfolder in the Myicons theme folder as well as  in <Alternate theme 1>.  Rename gaim.* to gaim-OLD.* in Myicons/<subfolder>/apps.  
Copy the gaim.* icon from <Alternate theme 1> and paste it into the Myicons/<subfolder>/apps folder.
**<subfolder> usually refers to <scalable>.  If <scalable> isn't available choose the highest resolution folder, ie <128x128>.

Example B:  We want to replace the ubuntu logo located next to the applications menu.  
Choose the icon you want to use as the replacement.  
Rename it to distributor-logo.*
Copy/paste it to Myicons/<subfolder>/apps.
**This example doesn't call for a rename and replacement setup b/c I've personally never seen a theme that comes with a replacement for that icon.  I mainly used this example b/c I've seen several posts looking for a quick fix for replacing the ubuntu logo.

[COLOR="Blue"]Step 5[/COLOR]: (optional)
Reload the desktop.  Logout/Login or open a terminal window and type ```
killall gnome-panel
```
or
```
killall kicker
``` 
The icons should now be replaced.

Advanced Tip:
If you have multiple icon themes installed and you are fond of some more than others or more than the root gnome icons, then edit the index.theme file to merge them.

```
gedit .icons/Myicons/index.theme
```

Alter the Inherits line to look like this:
Inherits=<MoreIcons>, gnome
--Where <MoreIcons> is the name of an alternate theme.  That will force your Myicons theme to read from <MoreIcons> first and then read from the root gnome icons if an icon isn't supplied.


That's about it  I hope I described the process simply and directly in a way that is understandable.  If anyone notices any discrepancies, please let me know.



-Xout

---

### Post by Heero_Yuy_X on 2010-10-14
Even after 4 years !! it's very helpful thanks alooot !! :)

---

### Post by crossedout on 2011-04-04
After all this time, I say thanks..glad it was of use to someone. :)

-Xout

---

### Post by Claus7 on 2011-04-23
Hello,

really comprehensible even 5! years after first posted, and I see without any editing! The only problem is not with the guide, yet with the process itself, which requires some time as far as the resizing of the icons is concerned! 

Also the existence of scalable folders is an issue as well as the fact that different themes use slightly different logic, yet with your guide I finally was able to change globally most of the icons I wanted!

Happy ubuntu-ing,
Regards!

---

### Post by JuliaS on 2011-04-23
Thank you, it's very helpful!

Julia

---

### Post by Claus7 on 2011-04-24
Hello,

the story:
I downloaded from gnome-look-org the icon theme named linuxlex, which has a great variety of icons for the whole system of ubuntu (from applications and places menu icons till type of folders). The problem was that I did not like the icons that it proposed for folders.

One way was to use the Candy icon theme, and place the folder icons of linuxlex inside the scalable directory. The problem was that this directory had svg files and the linuxlex directories were png files. As a result the transformation from png to svg was not so good.

Instead I put them (128 pixel size) inside the folder named places, at the beginning in the one with the highest pixel size (64), just renaming the folders with the way Candy theme proposed [I saw what name Candy had for the folder of music and that is how I named the music folder from linuxlex theme]. That way under my home folder I had some huge folder icons. Then I resized them to 64 pixel size, and the size in my home folder was ok. (Just to note here that I had copy-pasted candy as candy2 and I had changed the name candy to candy2 inside the index.theme file as proposed here in the guide.)

I had to do this for every available size so as to have the linuxlex foder icon patterns in my entire system (for the folder icons that is). Yet, that way I was able to use only the folder icons. Linuxlex theme has also a variety of other icons as well.

I checked at a closer look the folder named places inside linuxlex theme. And there I was able to see that existed a variety of colours for the basic folder icons, just named like: "colour_of_folder"folder-music.png
The only thing I had to do, in order to use different colour folders, was to remove the *"colour_of_folder"*folder-music.png string from the ones I wanted to keep, overwrite the default ones, and use linuxlex theme in its entirety along with its other icons!

Thanks again for the valuable info,
Regards!

---

