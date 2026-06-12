---
title: "HOWTO: Brief guide to editing themes"
date: 2007-12-16
forum: Outdated Tutorials &amp; Tips
---

### Post by soulmatic09 on 2007-12-16
Ubuntu's ability to customize & design themes is fantastic, but finding a simple guide to tweak them has been difficult for me.

So I'm going to compile some info and tutorials I've found in this post. If anyone finds others, feel free to add on.

---

### Post by soulmatic09 on 2007-12-16
**Emerald themes:** This is the equivalent to the blue top title bar from Windows. The information is inside a tar.gz file, but the extension must be changed to .emerald.

The best thing to do is to download a theme you like, and change the file extension from ".emerald" to "tar.gz" then extract the contents of the file.

You should find a series of image files which are the icons for close, minimize, maximize, etc. Each file should have a few different colors of the same image. 

Each represents a different state; i.e. unfocused, focused, on mouseover & prelight, etc. Edit these in GIMP to your liking. 

once the files are saved, compress it into .tar.gz format, and change the extension back to ".emerald" 

One important step: make sure all the image files are in the root directory of the .tar.gz; if they are inside a folder, emerald won't install it.

once the theme is installed, you can edit it in depth in the emerald theme manager, under System -> Preferences. If you don't have it, you may have to install it through synaptic.

---

### Post by soulmatic09 on 2007-12-16
**GTK Themes**: This is just about everything else in GNOME: The main navigation icons in GNOME/Nautilus, the scrollbars, right-click menus, the panels, progress bars, checkboxes, font colors, etc.

The process is similar to editing emerald themes, except you don't have to rename the file extension. Just leave it as .tar.gz.

Go to the "gtk-2.0" folder for the images to edit.

There will be a bunch of folders inside, each folder is for a different element of the navigation window.

Buttons are basic clickable items, i.e. back, reload, etc.
Checkradio are the round radiobuttons
Combobos are drop down menus, i.e. view as icons in nautilus
Menu is for right click menus
Range are sliders
Scroll is the scrollbar
Panel, Progressbar, tabs, etc. should be self-explanatory.

editing these images will change the appearance of the interface.

The key to the GTK is the gtkrc file. This controls the font colors, the spacing and padding of images. The only thing I would change in this file are the colors which are in hexidecimal format.

The easiest way to get the colors is by installing the gcolor2 application through synaptic, but picking colors in GIMP will work too.

a good guide to understanding the elements of the gtkrc file can be found here:
[http://ubuntuforums.org/showthread.php?t=377397](http://ubuntuforums.org/showthread.php?t=377397)


when you're done, compress into a tar.gz file, and install.

---

### Post by soulmatic09 on 2007-12-16
[http://ubuntuforums.org/showthread.php?t=545075](http://ubuntuforums.org/showthread.php?t=545075)

---

### Post by soulmatic09 on 2007-12-16
This post goes into more detail, in terms of how to change the GRUB menu, icons inside individual applications, panels, cursors, etc. It's a really in depth post.

[http://ubuntuforums.org/showthread.php?t=203093](http://ubuntuforums.org/showthread.php?t=203093)

---

### Post by soulmatic09 on 2008-01-06
If you want to remove or edit the background in list view, check out this post.

You can alternate the color of rows, like the MacOS, or customize the background colors as needed:

[http://ubuntuforums.org/showpost.php?p=414548&postcount=5](http://ubuntuforums.org/showpost.php?p=414548&postcount=5)

It's a setting in the theme itself, not Nautilus.

---

### Post by soulmatic09 on 2008-01-16
I found some code to make drop down menus transparent and blurry.

it's all in the compiz settings:

a) Transparency:

1) compizconfig-settings-manager -> General Options -> Opacity Settings

2) Add: (name=Vista) | (name=gimmie_applet) | (name=gnome-panel) | (type=Menu | PopupMenu | DropdownMenu | Dialog | ModalDialog) -18621  <- also you need to specify the transparency level in this setting. 0 is completely transparent.

b) Blur:

1) compizconfig-settings-manager ->Blur windows -> Alpha blur windows

2) Add: (name=Vista) | (name=gimmie_applet) | (name=gnome-panel) | (type=Menu | PopupMenu | DropdownMenu | Dialog | ModalDialog)

3) blur alpha - make sure the check box is ticked

4) gaussian blur - filter

source:
[http://www.gnome-look.org/content/show.php/BlueSpace?content=73599](http://www.gnome-look.org/content/show.php/BlueSpace?content=73599)

---

### Post by lbelloq on 2009-05-05
Excellent. I always wanted to port some of my favorite XP styles to Ubuntu, so I'll try to put this guide to good use. Thanks for the info.

---

