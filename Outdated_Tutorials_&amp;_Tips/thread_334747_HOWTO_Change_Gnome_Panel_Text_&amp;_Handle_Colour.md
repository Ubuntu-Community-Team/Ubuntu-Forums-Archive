---
title: "HOWTO Change Gnome Panel Text &amp; Handle Colour"
date: 2007-01-09
forum: Outdated Tutorials &amp; Tips
---

### Post by _simon_ on 2007-01-09
Note: I cannot help with transparency, I have looked all over the place but not been able to find a working guide.

Create an empty file called .gtkrc-2.0 in /home

If you already have a .gtkrc-2.0 then just add the code to your existing file.

Paste the following code inside:

```

style "panel"
{
    bg[NORMAL]               = "#"
    fg[NORMAL]               = "#"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"

```

bg[NORMAL] is what defines your Gnome panel handles colour, simply add the hex code for the colour that you require. - you will probably want it to match the colour of your Gnome panels.

fg[NORMAL] is what defines your Gnome panel text colour, again simply add the hex code for the colour that you require.

e.g.

    bg[NORMAL]               = "#000000"
    fg[NORMAL]               = "#FFFFFF"

This gives me a handle colour of black and a text colour of white.

Now save the file, logout and back in and you should see the changes take effect.

---

### Post by nimbledinosaur on 2008-01-07
Thanks for the how too, worked perfectly.

---

### Post by aktiwers on 2008-01-08
Here is another way (almost the same)
[http://ubuntuforums.org/showthread.php?t=334570](http://ubuntuforums.org/showthread.php?t=334570)

---

### Post by ravenon on 2008-01-08
Gnome Color Chooser also works nicely. It is available on gnome-look.org

---

### Post by JackTheDipper on 2008-01-08
it's available on [http://www.punk-***-bitch.org/gnome-color-chooser/](http://www.punk-***-bitch.org/gnome-color-chooser/) and not on gnome-look.org anymore ;-)

[edit]
ok, the forum doesn't like that address *g*
but it can be downloaded here: [http://sourceforge.net/projects/gnomecc/](http://sourceforge.net/projects/gnomecc/)
[/edit]

---

### Post by el-mar01 on 2008-05-27
Hey,

How would I exclude the gnome window list from the colour/font change in the panel ??

Thanks

---

### Post by sethborders on 2009-07-22
i tried it and it didnt work. did i miss something?

---

### Post by nathan726 on 2009-08-01
> **sethborders said:**
> i tried it and it didnt work. did i miss something?

You need to restart the panel for any changes to take effect. You can do that by opening the terminal and typing:
```
killall gnome-panel
```One question: how do you change the "hover" text colour?

---

### Post by Veggiet on 2010-01-06
Gnome-color-chooser does let you pick the text color, but still doesn't include those pesky panel handles, so this tutorial worked great, now if only I could save the theme completely!

---

### Post by 10fps on 2010-03-13
Is there any way of changing the colour for the text in each panel separately? Also what do the other lines do?

---

### Post by opethfan89 on 2010-03-21
I'm not an expert, 10fps, but in my experiments, each panel is independent of each other as far as the color you choose.  Here is a screenshot showing this:

[IMG]http://i42.tinypic.com/2hfuqkw.png[/IMG]

Also, I know this is an old thread but I'm guessing that in the latest GNOME and 9.10 image, this was changed as you can now have transparency without having to run any script. Right click on the panel --> properties --> background --> choose solid color --> set the transparency bar.

As for the hover color, right click on desktop -->change desktop background -->theme --> customize--> and experiment here until you get it. I currently have a black background over white text for my hover colors, to match with my theme.


Hope that helps!
Opethfan89

---

### Post by Amazing Alexander on 2010-06-22
If you want transparency, you need to change the background to a transparent one.

note: you can only see the desktop wallpaper behind a transparent panel. you cant see any windows half off the screen on the panels side.

---

### Post by elementxyz on 2010-08-19
hey so old but always usable thank you!!!!!!!!

---

