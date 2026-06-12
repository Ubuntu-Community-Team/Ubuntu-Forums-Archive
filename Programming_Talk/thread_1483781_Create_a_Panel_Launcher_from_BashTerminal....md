---
title: "Create a Panel Launcher from Bash/Terminal..."
date: 2010-05-15
forum: Programming Talk
---

### Post by Dart00 on 2010-05-15
Iv been scratching my head for days.

Im trying to create a panel launcher that will point to $HOME/Documents...now I know this is easy, just drag and drop and stuff like that...but Im trying to have a shell script create one. Its easy to create a desktop launcher from a shell script...but what about a laucher on the panel? Iv played with Gconf, I made a launcher, wrote down all its properties, deleted it and then ran bash commands to recreate it...log out and back in...and no launcher....Something else is going on behind the scenes that I cant figure out... :(

Anyone ever try something like this?

I did manage to find a script and I thought i would do just the trick....but couldnt get it to work. :(

```
#!/bin/bash

# script to add a new application launcher to a GNOME panel 

# first define a new object that describes what you want to add
# name of new object. 
objectname=object_99
newobjectkey=/apps/panel/objects/${objectname}
# set the type of the object
gconftool-2 --type string --set ${newobjectkey}/object_type "launcher-object"
# set were the .desktop file can be found
gconftool-2 --type string --set ${newobjectkey}/launcher_location "/usr/share/applications/MozillaFirefox.desktop"
# number of pixels from the left side of the screen that you want the launcher
# to appear. if you want to define the position from the right set boolean value 
# panel_right_stick to true
gconftool-2 --type int --set ${newobjectkey}/position 500
# which panel the object appears on. look at /apps/panel/toplevels/
# using gconf-editor to get list of valid values for your set up. 
gconftool-2 --type string --set ${newobjectkey}/toplevel_id "panel_0"

panelobjectlistkey=/apps/panel/general/object_id_list
# get the list of objects currently on panels
currentlist=$(gconftool-2  --get $panelobjectlistkey)
# add your new object to list.
gconftool-2 --type list --list-type string --set  $panelobjectlistkey "${currentlist/\]/,${objectname}]}"
```Anyone see whats wrong...or know a way to do it?

---

### Post by yaaarrrgg on 2010-05-20
I recall a script that added these items via shell script.  It actually killed and restarted the panel.

I think you'll need to notify the panel of the change.

---

### Post by roberthr on 2010-08-13
This has been bothering me for months. I can't figure out how to add simple app launcher to panel from command line!!!

It doesn't help if you create .desktop file and put it in ~/.gnome2/panel2.d/default/launchers but there must be the way to accomplish this. 

If anyone knows please help

---

### Post by roberthr on 2010-08-13
I found something that might help in the right direction.

On Ubuntu there's a script for panel manipulation. I've managed to put launcher on panel with this command:

/usr/lib/gnome-panel/gnome-panel-add --launcher=myapp.desktop

.desktop file must be created first and I was standing in home directory so I guess it just takes it from there.

---

### Post by Ctorpor on 2010-10-21
> **roberthr said:**
> I found something that might help in the right direction.

On Ubuntu there's a script for panel manipulation. I've managed to put launcher on panel with this command:

/usr/lib/gnome-panel/gnome-panel-add --launcher=myapp.desktop

.desktop file must be created first and I was standing in home directory so I guess it just takes it from there.
When I tried this I was asked for a panel identifier. I tried "bottom_panel" and "bottom_panel_screen0" as these were both located in gconf-editor under /apps/panel/default_settings/toplevels and /apps/panel/toplevels respectively. Both of these return .."is not an existing panel identifier".

I entered the following into terminal:
```
sudo /usr/lib/gnome-panel/gnome-panel-add --launcher="/usr/share/applications/gedit.desktop" --panel="botom_panel" --right-stick
```

You said you got this to work. What panel identifier did you use? Where did you find it?

---

### Post by Vox754 on 2010-10-21
> **Ctorpor said:**
> When I tried this I was asked for a panel identifier. I tried "bottom_panel" and "bottom_panel_screen0" as these were both located in gconf-editor under /apps/panel/default_settings/toplevels and /apps/panel/toplevels respectively. Both of these return .."is not an existing panel identifier".

I entered the following into terminal:
```
sudo /usr/lib/gnome-panel/gnome-panel-add --launcher="/usr/share/applications/gedit.desktop" --panel="botom_panel" --right-stick
```

You said you got this to work. What panel identifier did you use? Where did you find it?
I just tested this:
```

#works
/usr/lib/gnome-panel/gnome-panel-add --launcher=/usr/share/applications/gedit.desktop

#works
/usr/lib/gnome-panel/gnome-panel-add --launcher=/usr/share/applications/gedit.desktop --panel=top_panel_screen0 --right-stick

#works
/usr/lib/gnome-panel/gnome-panel-add --launcher=/usr/share/applications/gedit.desktop --panel=bottom_panel_screen0 --right-stick

```
No need for "sudo".

I don't have an interest in this, I just ran the commands and they worked.

I'm still using 10.04, so perhaps the interface changed in 10.10, if you are using that. Since "/usr/lib/gnome-panel" is not in the PATH, I think those commands are not meant to be run by users; it would be a bad idea to rely on them.

Also notice that "gnome-panel-add" is actually a Python script, so you are better of reading its source code and finding out how it manipulates the panel.

---

### Post by Ctorpor on 2010-10-22
Weird. It worked just fine without sudo. Thanks! :)

(BTW, do you know the terminal command to remove a panel by any chance?)

---

### Post by geirha on 2010-10-22
> **Ctorpor said:**
> Weird. It worked just fine without sudo. Thanks! :)


It's not weird at all; it's a user preference, not a system administration task. 

The main reason it fails is because sudo filters out the dbus environment variables, which gconf relies on. 

And if it had worked with sudo, you'd likely have files not owned by you in your homedir, and gotten weird issues because those files would not be writable by you.

Don't use sudo unless absolutely necessary. At least try without sudo first.


Removing it from the list /apps/panel/general/object_id_list (in gconf), should remove it. See the man-page of gconftool.

---

### Post by gpwil1 on 2010-11-25
I love ubuntu forums. So helpful!

I was wondering if you could expand on the above and please let me know what would the command would be to add a terminal and chrome shortcut to the top panel?

Cheers

Edit - never mind I figured it out:
/usr/lib/gnome-panel/gnome-panel-add --launcher=/usr/share/applications/gnome-terminal.desktop --panel=top_panel_screen0 --right-stick

/usr/lib/gnome-panel/gnome-panel-add --launcher=/usr/share/applications/chromium-browser.desktop --panel=top_panel_screen0 --right-stick

however id still like to know how to change the shortcuts location to be on the left...

---

### Post by PFrenssen on 2011-02-19
> **gpwil1 said:**
> /usr/lib/gnome-panel/gnome-panel-add --launcher=/usr/share/applications/gnome-terminal.desktop --panel=top_panel_screen0 --right-stick

/usr/lib/gnome-panel/gnome-panel-add --launcher=/usr/share/applications/chromium-browser.desktop --panel=top_panel_screen0 --right-stick

however id still like to know how to change the shortcuts location to be on the left...
To get them on the left remove the "--right-stick" parameter from your command. This is only needed if you want your icons to stick to the right hand side of the panel ;)

---

### Post by cwhittier on 2011-09-14
I'm working in ubuntu 9.04, it seems that gnome-panel-add does not exist anymore. Does anyone know where it moved to, or how to accomplish this without it?

---

### Post by rewolff on 2011-11-29
9.04 is older than 10.4 and 10.10 that the others were talking about. 

By the time you asked that, 11.04 was already out. 

now I'm running 11.10, and the gnome-panel-add script still exist, but doesn't work. :-(

Suggestions anybody?

---

### Post by NickFenger on 2011-12-09
This seems to work [http://wiki.blagblagblag.org/Gconf](http://wiki.blagblagblag.org/Gconf)
Needs panel="top_panel_screen0" in 10.04

---

