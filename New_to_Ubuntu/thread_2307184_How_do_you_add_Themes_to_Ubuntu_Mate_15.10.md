---
title: "How do you add Themes to Ubuntu Mate 15.10"
date: 2015-12-22
forum: New to Ubuntu
---

### Post by cwmoser on 2015-12-22
How do you add Themes to Ubuntu Mate 15.10 ?
I tried to download both gtk2.0 and gtk3.0 based themes 
and extracted them to **~/.themes** but they just will not
show up under[B] System -> Preferences -> Look and Feel -> Appearance.
[/B]

Wanting to install a clear theme to make the desktop easier to read.

---

### Post by Dennis N on 2015-12-22
You put the themes in one of the correct locations, but a theme won't appear as one of the big icons in the Appearance Preferences window unless it is a Gnome Metatheme. But, it may be usable if you select your existing theme, click on the Customize button, and look for the new theme in the Controls tab of the window that pops up.

> Explanation of Gnome Metatheme
Gnome Metathemes have a text file named index.theme in their theme folders which specifies the name, gtk theme, window theme, icon theme, and cursor theme (and sometimes more). The index.theme file has a special format like this: 

```
[Desktop Entry]
Type=X-GNOME-Metatheme
Name=Greybird-Blue
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=Greybird
MetacityTheme=Zukitwo-Dark
IconTheme=Mint-X-Blue
CursorTheme=Breeze-White
CursorSize=40

```

This one will be called "Greybird-Blue" in the Appearance Preferences window.

---

### Post by blade4 on 2015-12-24
Dunno if this will still work ( it used to work for Ubuntu Lucid which used Gnome 2 ) but try dragging and dropping the tar.gz theme files on to the themes tab in the appearance section.

---

### Post by cwmoser on 2015-12-24
> **blade4 said:**
> Dunno if this will still work ( it used to work for Ubuntu Lucid which used Gnome 2 ) but try dragging and dropping the tar.gz theme files on to the themes tab in the appearance section.


When I download *.gz Theme files, the drag and drop seems to work but I get an Icon with a big question mark.
Could be that Ubuntu Mate 15.10 uses a different file configuration.

I think this is a bug in Mate 15.10

---

### Post by Dennis N on 2015-12-24
> **cwmoser said:**
> When I download *.gz Theme files, the drag and drop seems to work but I get an Icon with a big question mark.
Could be that Ubuntu Mate 15.10 uses a different file configuration.

I think this is a bug in Mate 15.10

The question mark may be because you need all the components that are specified in the index.theme file to be available on your computer. One or more parts is missing - for example, the correct icon theme may not be present. See my post #2 for description of an **index.theme** file. Look for this file inside the theme folder of the theme you are trying to use.

---

### Post by Dennis N on 2015-12-24
What is the name of the theme you are trying to install?

---

### Post by cwmoser on 2015-12-24
Where are themes that you can select that Ubuntu Mate 15.10 will accept?

---

### Post by blade4 on 2015-12-24
Try ubuntu tweak or Gnome tweak tool . I have the same problem with Unity in my Ubuntu setup. My theme files are detected by ubuntu tweak but not by unity's appearance tab.

---

### Post by Dennis N on 2015-12-25
> **cwmoser said:**
> Where are themes that you can select that Ubuntu Mate 15.10 will accept?

You probably can find something that works just by taking one of the existing metathemes in the window and customizing it by the Customize button at the bottom of the Appearance window. _Changing the selection for 'Controls' changes the entire gtk theme in use to this selection_. So if you start with Ambient-MATE which is the default theme, and change the controls to Clearlooks, you are now using the Clearlooks gtk theme. You can then also change the colors, Window Border, icon theme,  and pointer if you want.

As soon as you start customizing, a new theme box is created in the window called 'Custom'. 

When you are done, use the Save button at the bottom, which saves all your choices as a metatheme that now appears in the Appearance window with the name you gave it. 

You can add more gtk themes from gnome-look.org. When you extract the theme folders to ~/.themes, they become available under the 'Controls' tab. 
Using the 'Install' button has the same result - it automatically extracts folders from an archive to ~/.themes.

Also, some excellent gtk themes like greybird and numix are available in the Ubuntu repositories.

---

### Post by cwmoser on 2015-12-25
I like the TraditionalOK theme but don't like that the font color of desktop icons is black.
I would like to customize that theme by changing the desktop icon font to color white.

How do you do that?

---

### Post by cwmoser on 2016-01-01
I think Themes in 15.10 is just buggy.

---

### Post by Dennis N on 2016-01-02
> **cwmoser said:**
> I like the TraditionalOK theme but don't like that the font color of desktop icons is black.
I would like to customize that theme by changing the desktop icon font to color white.

How do you do that?

I would like to know that too. With most desktop environments this is difficult as you probably have to edit the theme files somewhere to do this. It is not in any user dialog. A rare exception is Lubuntu which has the option to change the text color of the desktop icons from its desktop settings dialog - so if you want orange text, you can have it. You can also easily change the color of the panel text in Lubuntu. 

In Gnome 2, there was a tool to do this called **gnome color chooser**, but it doesn't work for icon text color in Ubuntu MATE. You can change some other colors, however (like panel text color).  

I have also seen this question on icon text color on the MATE discussion forums, but no responses.

That aside, I think the metatheme concept is very clever and useful once you get the hang of it.

---

### Post by cwmoser on 2016-04-13
Bump
(Actually testing if my login is now working)

---

### Post by vasa1 on 2016-04-13
Dennis N, thanks for explaining what `index.theme` is all about! Lubuntu themes don't seem to use it.

The Greybird theme in 14.04 (part of shimmer-themes) doesn't seem to use it. And I don't have such a file in my *~/.themes* themes either.

In Lubuntu 14.04's Openbox session, I edit *~/.gtkrc-2.0* or *~/.config/gtk-3.0/settings.ini* to change gtk2 and gtk3 themes, respectively, by leaving uncommented the theme I want to use. I don't use LXAppearance.

```
# DO NOT EDIT! This file will be overwritten by LXAppearance.
# Any customization should be done in ~/.gtkrc-2.0.mine instead.
#gtk-theme-name="Mymix"
#gtk-theme-name="Greybird"
#gtk-theme-name="Lubuntu-default"
gtk-theme-name="Mybird"
gtk-icon-theme-name="NoInherits"
#gtk-icon-theme-name="gnome"
gtk-font-name="Ubuntu 12"
gtk-cursor-theme-name="oxy-red-argentina"
gtk-cursor-theme-size=18
gtk-toolbar-style=GTK_TOOLBAR_ICONS
gtk-toolbar-icon-size=GTK_ICON_SIZE_LARGE_TOOLBAR
gtk-button-images=0
gtk-menu-images=1
gtk-enable-event-sounds=1
gtk-enable-input-feedback-sounds=1
gtk-xft-antialias=1
gtk-xft-hinting=1
gtk-xft-hintstyle="hintslight"
gtk-xft-rgba="rgb"
include "/home/vasa1/.gtkrc-2.0.mine"
```

And```
[Settings] 
gtk-double-click-time=1000

#gtk-theme-name=freebird
#gtk-theme-name=Numix
gtk-theme-name=Mymix
gtk-icon-theme-name=NoInherits
gtk-font-name=Ubuntu 12
gtk-cursor-theme-name=oxy-red-argentina
gtk-cursor-theme-size=18
gtk-toolbar-style=GTK_TOOLBAR_ICONS
gtk-toolbar-icon-size=GTK_ICON_SIZE_LARGE_TOOLBAR
gtk-button-images=0
gtk-menu-images=0
gtk-enable-event-sounds=1
gtk-enable-input-feedback-sounds=1
gtk-xft-antialias=1
gtk-xft-hinting=1
gtk-xft-hintstyle=hintslight
gtk-xft-rgba=rgb
gtk-primary-button-warps-slider=false

```(The last line provides "legacy" scrolling in gtk3 apps.)

---

