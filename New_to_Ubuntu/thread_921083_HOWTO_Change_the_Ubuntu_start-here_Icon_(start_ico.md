---
title: "HOWTO: Change the Ubuntu start-here Icon (start icon)"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by Crafty Kisses on 2008-09-15
So basically I've seen a lot of tutorials out there, but none seem to work with Hardy, I've found a couple of ways you can do this fast and very simple, here are three ways you can do it, let me list them, then I'll give you guy step-by-step tutorials.

[LIST]
[*]Removing current "start-here" file and replacing it
[*]Making a replacement folder
[*]Change it through gconf-editor
[/LIST]

The following is one of the easier ways, first you need to get the icon you want, so for example if you want the "Gentoo" icon for your new start icon, download it, and rename it **"start-here"**, open the following folder, you need to go through nautilus first though, so do the following:
```
gksudo nautilus
```
Once you're browsing your folders as root, go to this directory:
```
/usr/share/icons/themename/24x24/places/
```
Once you're in there, remove the **start-here** file, before removing it, I'd back it up and put it in a folder, but that's up to you. Once you remove it, put your icon named **"start-here"** in the folder, and make sure your icon is 24x24, if it isn't you can scale the image in GIMP.

Once you've place your file inside the following directory:
```
/usr/share/icons/themename/24x24/places/
```
Run the following command:
```
sudo gtk-update-icon-cache /usr/share/icons/Human/
```
Then after you ran that, run this:
```
killall gnome-panel
```
Then you should have your custom start icon in place, that's one way of doing it.

The second way, Ayisu gave a good tutorial on it, but I'll put it in this tutorial anyway.

One of the more simpler ways to do this is to create a folder in your home directory for the icon theme you use and then put your custom icon in there.

So for example, if your using the Human Icon pack it would be:
```
/home/username/.icons/Human/scalable/places/distributor-logo.png

```
Then press Alt-F2 and type
```
killall gnome-panel
```
After you should have your custom start icon.

The third way is a little bit more difficult, but let's give it a shot.

First press Alt+F2 and run this:
```
gconf-editor
```
Once you're in there do the following:

**Apps -> Panel -> Objects -> Object_1** Once you've done that you might want to check, as yours might be different, that the "tooltip" has the value "Main Menu", if it doesn't then check the different Objects like 2,3,4 etc, until you find one which has the "Main Menu" tooltip), then check the custom icon option, then set the "custom icon" value to the path of the icon you want.

Those are all three good ways of doing this, I hope I helped, I want to thank these people that help me compile this tutorial (information used), **aysiu**, and **LinuxisInnovation**.

Thanks for reading!

---

### Post by modmadmike on 2008-09-15
Crap I'm not the only one who found this out lol

---

