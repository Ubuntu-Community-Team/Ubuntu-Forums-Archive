---
title: "How to install mouse cursor for  Ubuntu 12.10"
date: 2013-12-03
forum: New to Ubuntu
---

### Post by wolfzrat2 on 2013-12-03
Hi guys im learning as i am going because in new to Ubuntu and linux. I would like to know where I can download mouse cursors. I would like to know how to install them in the version of Ubuntu 12.10. Thank you =)

---

### Post by fantab on 2013-12-04
You can find Cursor themes at:
[http://gnome-look.org/index.php?xcontentmode=36&PHPSESSID=fa4135597f53d51cbc2f096420b1b887](http://gnome-look.org/index.php?xcontentmode=36&PHPSESSID=fa4135597f53d51cbc2f096420b1b887)
There may be more, use google.

To install them you have to put the cursor_theme-folder in /usr/share/icons (you should be root to be able to copy files to /usr/share/icons): To open nautilus as root-
```
gksudo nautilus
```

Then run:
```
sudo update-alternatives --config x-cursor-theme
```
... find your theme in the listed themes, note its number and enter.

Restart computer if needed.

If you see old cursor theme on some apps and new on some then; 
Open '**dconf Editor**' and navigate to org->gnome->desktop->interface - and look for 'cursor-theme'... and change it to 'your cursor theme'. 

You can also change the 'cursor-size' likewise in dconf.
If you see that applications show different 'cursor-size' then Create a hidden file in your Home Folder and name it .Xresources (*$ gedit ~/.Xresources*) and put "**Xcursor.size: 48**" (without quotes) in the file and save it. 

Reboot...

---

### Post by oldos2er on 2013-12-04
Moved to Absolute Beginners.

---

### Post by stinkeye on 2013-12-04
To change between existing cursor themes you need to...change the **dconf setting** and the **alternatives setting** as fantab stated.
**New themes** need to be **added to alternatives first**.

The new theme will not show up when you run **sudo update-alternatives --config x-cursor-theme**
You need to add it to alternatives first.

These are the steps for a downloaded theme.
[LIST=1]
[*]Extract from archive.
[*]Check for a cursor.theme file
[*]Move theme to /usr/share/icons
[*]Add to alternatives
[*]Select with alternatives
[*]Select in dconf
[/LIST]



For a gui to manage alternatives, install galternatives.....
```
sudo apt-get install galternatives
```

_**1.**_
A downloaded theme archive must be extracted to reveal the theme folder.

_**2.**_
In this folder there must be **cursor.theme** file.
Create one using gedit, if necessary.
For an example , look at **/usr/share/icons/DMZ-White/cursor.theme**.
[ATTACH=CONFIG]248350[/ATTACH]
```
[Icon Theme]
Inherits=[COLOR="#696969"]<insert your cursor name>[/COLOR]
```

_**3.**_
Move theme folder to /usr/share/icons as described earlier by **fantab**

_**4.**_
Add theme to alternatives using **galternatives**
Run galternatives and select **x-cursor-theme** in the left panel.
Click on the add button >browse
Then use the top drop down to navigate to /usr/share/icons . Start with "**/**" then in the left column progressively choose(double click) **usr/** [COLOR="#696969"]>[/COLOR] **share/** [COLOR="#696969"]>[/COLOR] **icons/**
Select your theme in the left column and then select **cursor.theme** in right column and hit the ok button.
[ATTACH=CONFIG]248352[/ATTACH] 

**_5._**
Select your theme in galternatives and close.
[ATTACH=CONFIG]248353[/ATTACH]

_**6.**_
Now you just need to select your new theme using a tweak tool like unity-tweak-tool, gnome-tweak-tool or ubuntu-tweak.
The tweak tools change the dconf setting shown earlier by fantab.

After changing a cursor theme you need to log out/in for it to be consistent.

---

