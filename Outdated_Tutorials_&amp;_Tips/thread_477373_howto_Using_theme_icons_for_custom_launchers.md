---
title: "howto: Using theme icons for custom launchers"
date: 2007-06-18
forum: Outdated Tutorials &amp; Tips
---

### Post by vexorian on 2007-06-18
This howto is at least valid for ubuntu feisty.

It happens, you create a *launcher*  for some program or command just to have easy desktop double click (or app menu) access to it.

But you got to pic an icon, when you go to the pic icon option it would just show: /usr/share/pixmaps which got some nice stuff but doesn't have everything. If you have been tweaking the theme you should know that there are plenty of icon themes in the filesystem.

It is probable that you want to use an icon from the theme, Let's say for example you want to pic the screensaver icon, it is the image of an screen with some night background in it.

**Where are the icon themes?**
If you want to pic the icon you first got to find it, the preinstalled icon themes are typically in /usr/share/icons there you can head towards your current icon theme.

You will find some folders, there are different versions for each icon, some for small resolutions and finally the scalable one which is used when you stretch the icon to the max so it won't pixelate. For our current purposes it is wise to head to scalable, since it can also scale well to small sizes.

Then there are the categories, your wanted icon might be on any of them

 It is likely you won't find the wanted icon there though, icon themes use a concept called inheritance, it means that an icon theme may just specify some of the icons and otherwise use an icon in another theme if it can't find it.

For example, human inherits from tangerine, tango and gnome in that order, this means that if the system wants an icon and it can't find it in human it will then look for it in tangerine, then tango and finally gnome.

So you will have to find in other icon themes as well, there is a trick, tangerine mostly replaces some of the icons in Tango, and Tango got all of the required icons, so it is most likely that you can  find the icon in Tango.

I have found the example icon in /scalable/apps/screensaver.svg so just select it and done!.

**But, what if I change the icon theme?**
Ok, here it becomes problematic, if you change the icon theme and that icon is different in the new theme and it causes a mismatch with the other icons you might want it to be changed correctly, you may change it manually again.. but if you change your icons with some frequency that is not good... There is also an issue, what if the launcher is in a shared folder? Another user might have access to the launcher but use another theme.

After checking out how the default launchers work I have figured a way to actually use the theme's icon.

**.desktop files**
Launchers are actually files with the .desktop extension, the GUI to edit the launchers through right click/properties is good and all but it sometimes is not enough, but we can always edit the file ourselves.

We can just use gedit, open gedit and use the file open dialog to find the folder where you located the launcher, then make gedit open it.

You'll see something like
```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=NAMEOFLAUNCHER
Type=Application
Terminal=false
Name[es_YOURLANGUAGE]=NAMEAGAIN
Exec=(command line)
Icon[es_YOURLANGUAGE]=/usr/share/icons/human/scalable/applications/screensaver.svg
Icon=/usr/share/icons/human/scalable/applications/screensaver.svg
```

The theme icon lookup works by just typing the name of the icon, the system will actually handle everything else including picking a correct size version, thus if we already know that the name of the icon is "screensaver" we may simply remove all the /usr/share/icons/theme/scalable/category/ path and leave Icon=screensaver (the name of the icon which may also have hyphens, like dialog-question)

Yep, there may be two Icon entries, one for your language, you may simply remove that entry or type the icon name once again.

Yes, the icon entry is sometimes added twice since there are variations for your language, you may just remove that entry or change it again.

---

