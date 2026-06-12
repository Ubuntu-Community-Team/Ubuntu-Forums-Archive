---
title: "My (new and improved) Fluxbox guide"
date: 2008-01-15
forum: Outdated Tutorials &amp; Tips
---

### Post by -grubby on 2008-01-15
My (New and Improved) Fluxbox Guide!

**Section 1 : Fluxbox Editing **

Subsection 1 : **Menu Editing**

	Editing the Fluxbox menu is very straightforward. Nothing really complicated is involved. Basically the menu entry you have made's type (like an executive or a certain special wallpaper trick I will show you) will be a "tag", it will be surrounded in [ ] characters. 

Subsubsection 1 : **"tags"**

1: _Executives_ :  This type of "tag" (I will refer to it now on without quotation marks) links to an executive. Keep in mind by "linking to executives" you can use the commands to run the programs from the terminal...such as "firefox". You use the tag (no quotations) [exec] for this type of tag..read on to find out what to put after it for a complete menu entry.

2: _Submenus_ : Sub-menus are tags that you use for creating of course: submenus. You use the tag [submenu] for sub-menus. Read later about how you can place tags

3: _Ending Submenus_ : Sub-menus have to be ended so you don't accidentally put submenus within sub-menus that weren't meant to be there (for example, if this were the case with gnome-menu, you might accidentally put the "internet" section under "games"). Again, read later about where and how to place these in the menu file

Subsubsubsection 1 : _Special one-of-a-kind tags_

1: _Changing Styles Through Sub-menus_ : This basically indicates that the text that follows (read about it later in the document) will show where the styles directory is. Fluxbox obviously needs to know this so it can place the styles in the specified directory in the specified sub-menu. The tag for it is [stylesdir]

2: _Reconfiguring Fluxbox_ : You must reconfigure Fluxbox after certain changes such as editing your keys file. You can enter a long and complicated command into the terminal (which I don't even remember right now) to reconfigure Fluxbox, but putting this in your Fluxbox menu will make it much more convenient. The tag is [reconfigure] 

3: _Wallpaper Sub-menu_ : This is a very nice trick I learned off of a Linux forum with a Google search for a GUI wallpaper setter for fbsetbg -f. It allows you to (similar to "changing styles with a sub-menu") set wallpapers from a certain directory by clicking on their names in the menu. The tag for this is [wallpapers]. You have to create a sub-menu for this btw. 


Subsubsection 2: _Naming Menu entries (and some special functions) _

1: _Actually naming entries_ : Naming menu entries is the easiest thing with editing the Fluxbox menu (or maybe the hardest, if you can't think of a decent name for a sub-menu or something). All you do is put the name in parentheses. For example : (Firefox). Easy as pie. Stay tuned for the other (not-so) easy part.

Subsubsection 3: _Entering commands for your executables _

1: _Commands for an application_ : This is (usually) very straightforward. You just use the command within {} characters. In most cases, it's just the name of the application that you fill between those 2 characters. But in some cases, apps have an unusual name to start from the terminal. Read on in the next paragraph to fix this.

2: _Uncommon commands for an application_ : This is the unusally non-straighforward way to find out how to run an application from the terminal. If it's not the name of the app or something very similar, I recommend you open up your favorite file browser and look in /usr/bin for the executable. For some reason, I don't understand at all, the executables for programs (unusual command programs) are usually titled the same name as the program or very similar. To put this in the menu entry, you use {/path/to/executable} where the path to the executable is usually  /usr/bin/executable-name/ .

3: _More explanation_ : You should also know that not every menu entry needs a command. For example sub-menus, don't need one. The "styles" and "wallpapers" entry also does not need one. You don't even have to put {} because if you just don't put any ascii characters at all Fluxbox just acts as if that is not there. So {} and entering nothing are exactly the same. 

Subsubsection 4 :_ Putting icons in the menu _

1 : _Special Rules_ : Fluxbox only accepts .png and .xpm files for menu icons as far as I know. I would recommend you use .xpm 100% of the time. Sometimes Fluxbox seems to randomly reject .png files (they don't work) because of their size (pixels) or some other reason.

2 : _Putting Icons In The Menu_ : To put icons in the menu you put the path to them in <> characters. Usually icon's files can be found in /usr/share/pixmaps. That's not always the case: they may be in /usr/share/pixmaps/app-name/icons/icon.xxx. If they're not in either have good luck tracking them down. Here's an example of how to do it: </usr/share/pixmaps/abiword.xpm>. Note if you don't have any icons at all that you can usually find them in the net, but you better hope they're small or they look good if they have to be resized

Subsubsection 5 :  _How it all comes together_

1 : _In what order to place the tags,names,etc on one menu entry_ : You place the letters in special characters (LISP I'll call it) in the following order : 
```
[tag] (name) {command} <icon>
```
Doing it in the wrong order will render the menu entry invalid and Fluxbox won't show the entry in the menu. So example for Firefox you would enter:
```
[exec] (Firefox) {firefox} </usr/share/pixmaps/firefox/icons/mozicon128.png>
```

2 : _Using Sub-menus correctly_ : Using sub-menus is slightly complicated. After each sub-menu you put the [end] tag. That is true unless you want to make a sub-sub-menu. In that case you would put [end] after the sub-menu you made and then after you've made all your sub-menus you would put a final [end] on it. For example:

```
[submenu] (apps)
[submenu] (internet)
[end]
[submenu] (system)
[end]
[end]
```

     In the example above you can see that you put the [end] tag first after the "internet" submenu. Confused? Look at the bottom [end] tag. That's where the "big" sub-menu ends. I screwed up my menu once or twice getting confused by this and it is a pain to track down what [end] tag I left out.

Notes : If you have problems with your menu or want some more info you think I didn't include here please check out [Redsquirrel's guide]("http://ubuntuforums.org/showthread.php?t=371144"). 

**Subsection 2** : The Startup File : The startup file is really the easiest thing ever to edit (I've said that about 5 things or so about now haven't I?). I don't even know If I'll need a subsubsection for it. All the startup is is basically the list of apps and/or commands you run at startup. Almost exactly the same as (in GNOME) going to System>Preferences>Sessions. Read on for instructions on it

_Subsubsection 1_ : Running Applications : To run applications when you start Fluxbox, just simply put their names anywhere in the file above where it says "exec /usr/bin/startfluxbox" (explanation a few paragraphs down) with an "&" sign after them. For example (here's an example startup file)

```
idesk &
killall gnome-panel

exec /usr/bin/startfluxbox
```

Subsubsection 2 : _Running Commands_ : If you want to run commands for some reason on startup, then just put them exactly the same as running applications except without an "&" at the end. The & signals you want it to continuously run.

Subsubsection 3 : _Running The Last Application In The List_ : Running the last application on the list is exactly the same as running the first one except that you have to put "exec" before it. Now by default this is Fluxbox and I don't recommend you do it. I've never tried it because I don't want to know the results. 

Notes: There are no guides that I know of that are more complicated than this. As far as I know, this is the only guide on the startup file at all.

Subsubsection 4 : _Having A Wallpaper At Startup_ : If you don't like manually going through each sub-menu all the way to the "wallpapers" sub-menu when you start so you can have a wallpaper, then (it's commented in the file too). You just enter "fbsetbg -f /path/to/wallpaper/" at the beginning of you startup file. This makes it seem more organized (or so I think) and prettier to look at. If Fbsetbg complains about not being able to find an application to set the wallpaper then just install the one it recommends :
sudo apt-get install app-name

Subsection 3 : **Fluxbox Keys **
    Explaining how Fluxbox keys works is really beyond me. I only know how to run executables so you might as well check out [this guide]("http://ubuntuforums.org/showthread.php?t=617812&highlight=power+fluxbox+keys") that really helped me. I find it nice that I can have gpe-screenshot mapped to the printscreen key. 
[COLOR="Red"]UPDATE: PLEASE NOTE THAT IF YOU RUN THE GUI PROGRAM "fluxkeys" THE CONNECTION TO YOUR MOUSE IN FLUXBOX WILL BE BROKEN[/COLOR]

Subsection 4 : **Init**
    As above, explaining how init works would be beyond me. Also, it would take a couple pages to explain it anyway. Most of it's editing is easy (if you think about it and if you know Linux well enough). But explaining the meaning of every little line is too advanced for me. Go on to the next section which won't be nearly as big as this one if I have predicted right.

Section 2 : **Miscellaneous** 

 Subsection 1 : **Setting Your GTK And/Or Your QT Themes In Fluxbox**
     It can be frustrating having an ugly QT and/or GTK theme with Fluxbox but not knowing how to fix it. I recommend the following apps for changing (in order) the GTK ,QT3, and QT4 themes. Respectively. Just install :

GTK-CHtheme 
```
sudo apt-get install gtk-chtheme
```
QT3-QTconfig
```
sudo apt-get install qt3-qtconfig
```
QT4-QTconfig 
```
sudo apt-get install qt4-qtconfig
```

Note: to start QT3-QTconfig and QT4-config is different then their names (makes no sense to me either). You have to start QT3 and QT4 config (in order) by :

```
qt-qt3config
qt-qt4config

```
Note : I still can't find a way to install GTK themes with GTK-CHtheme. Unless you find another app for this, I just recommend you keep GNOME installed. Also, GTK-CHtheme can also set other settings for GTK (like fonts)

Subsection 2 : **Icons**

    As I explained in my last guide, I tried installing fbdesk but I couldn't find the config file for it (if I installed it again and tried to look for it I bet I could find it though). So I just use (used as of yesterday) idesk. To get idesk to start for the first time, you have to make a .idesktop folder in your home directory. Inside, you'll find the icon files. You'll obviously want to add icon files as the default idesk file doesn't do anything relatively interesting at all. To make an icon file you have to make a .lnk text file within ~/.idesktop/. It always has a simple format to follow that is always the exact same thing for every icon file.

The format is (below) and I will elaborate in the next paragraph

```
table Icon
  Caption: Home
  Command: thunar /home/nathan
  Icon: /usr/share/idesk/folder_home.xpm
  Width: 48
  Height: 48
  X: 33
  Y: 27
end
```

    The editing is pretty straightforward and self explanatory. But I'll explain anyway. 
     The line "table icon" means...well..I have no idea. All I know is that you have to put it before anything else in each and every file no exceptions no excuses. 
     "Caption" means what the icon's name will be (the text under it). Just put a good name there and you're all set. 

     The line "Command" is what is executed when you click on the icon. Basically what you would think of what the "command" to start an application is. 

    "Icon" is the path to the icon you're going to use. Most icons are stores in /usr/share/pixmaps unless they're stored in their application folder under that directory. 

    The "Width" and "Height" are the icon's height in pixels. If you want it to look nice, I recommend you keep both of these exactly the same value. As you can see in the example, I've kept mine the default, which is 48x48

    The "X" and "Y" are the icon's position on the desktop. Since the desktop doesn't look like a grid, I just recommend you keep these around (33,27) and then move them from the desktop itself.
     "end" just means to end. It's sort of like the [end] tag in the Fluxbox Menu.

    Subsection 3 : **File Managers**
    Basically just use your favorite one. All I have to say here is that to run Nautilus you have to run it with the "--no-desktop" argument while in Fluxbox or else it will try to control the desktop and you will be in a half-GNOME, half-Fluxbox Frankenstein monster of a desktop. So you run it like this :

```
nautilus --no-desktop
```


Well that was my Fluxbox guide. I hoped it's helped you. I decided to redo it when I realized IMO that my Previous Fluxbox guide wasn't (isn't) very good.

Notes : My Fluxbox Menu is attached.
A .doc file of my guide is [here]("http://www.mediafire.com/?cmzixx5jyz1") because It's too big for UF's file size for .docs

UPDATE: My website (that I share with another user, Fedex1993) is now up. See the Fluxbox guide uploaded there [here]("http://eblognuts.org/nath/fluxguide/fluxboxguideintro.html")

---

### Post by -grubby on 2008-01-16
Well when this got approved it got all the way to the 2nd page. And it's been 24 hours and no replies apparently so i guess this is a bump

---

### Post by nikoPSK on 2008-01-16
Very nice! :)

---

### Post by NovaAesa on 2008-01-16
Awsome guide xD You have inspired to me try a fluxbox distro on an old lappy I have.

---

### Post by nikoPSK on 2008-01-16
> **NovaAesa said:**
> Awsome guide xD You have inspired to me try a fluxbox distro on an old lappy I have.

you should, it's nice. Try openbox too. :)

---

### Post by EXCiD3 on 2008-01-20
Nice work...once i get back to skool im gonna try this!

---

### Post by il-luzhin on 2008-03-27
Neither QT will start for me.  "Command not found"

Any advice?

EDIT: nvrmind, i got impatient and just decided to install the entire kde package.

---

### Post by Rodney9 on 2011-06-26
thanks

---

