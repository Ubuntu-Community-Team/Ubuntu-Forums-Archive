---
title: "Xubuntu 12:4 themes"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by jim Kane on 2012-06-18
i notice in usr/share/themes that Clearlooks is listed, but not in the Window manager.
Is it possible to install this theme from the above directory.
or better still im really after Piranha which i loved in 10:4 it had window roll-up which was a godsend with Gimps side panels on a small screen, why so many themes were removed from the new LTS is beyond me  

Jim K

---

### Post by Toz on 2012-06-18
> **jim Kane said:**
> i notice in usr/share/themes that Clearlooks is listed, but not in the Window manager.
Clearlooks is an appearance theme only - not a window theme. 
> Is it possible to install this theme from the above directory.
or better still im really after Piranha which i loved in 10:4 it had window roll-up which was a godsend with Gimps side panels on a small screen, why so many themes were removed from the new LTS is beyond me  

Jim K

Many of the previous themes were moved to another package. Look for **xfwm4-themes** in the software manager and install it to get them back. Sorry, but I don't remember a theme called Piranha. If the theme you choose supports rollups, you can them to the window decoration from Settings Manager -> Window Manager -> Style tab by dragging the roll-up icon from the hidden section to the button layout section.

EDIT: Looks like there's a Clearworks xfwm (Window manager theme) [here]("http://xfce-look.org/content/show.php/Clearlooks+for+XFWM4?content=137055").

---

### Post by vasa1 on 2012-06-18
> **Toz said:**
> Clearlooks is an appearance theme only - not a window theme. 
...
Toz, could you please explain (or link to) the distinction between appearance theme and window theme?

---

### Post by Toz on 2012-06-18
In Xfce there are two aspects to themes - the gtk "appearance" and the xfwm "window theme". 

The elements that make a _window theme_ are the borders, action buttons, title text, etc. Have a look at */usr/share/themes/greybird/xfwm4* to see the elements of the window manager theme for the Greybird theme. You'll notice that they are all graphic files which are used to create the window decorations. There is also a themerc file that controls some basic aspects of the window theme. 
The window manager theme is set at **Settings Manager -> Window Manager -> Style tab**.

The other elements within the window, the widgets, the canvas, the text, the graphics, etc are controlled by GTK. Xfce calls this the _"Appearance"_. Have a look at */usr/share/themes/greybird/gtk-2.0* and */usr/share/themes/greybird/gtk-3.0* directories for configuration files that control the display of those elements.
The appearance theme is set at **Settings Manager -> Appearance -> Style tab**.

Yes, you can mix and match appearance (GTK) and window manager (xfwm) themes. If you have a look at the themes in /usr/share/themes, only those with an xfwm4 directory will have a window manager theme. And only those with a gtk-2.0 (and more recently gtk-3.0) directories will have an appearance theme.

Although it is a little confusing, you can see how the elements are managed differently. As for a reference link, look [here]("http://wiki.xfce.org/howto/install_new_themes"). It's brief and it also talks about cursors and icons. There is also [this]("http://docs.xfce.org/xfce/xfce4-settings/start").

---

### Post by vasa1 on 2012-06-19
Thanks for the detailed reply and links. Much appreciated :)

Edit:
While **themerc** was a new one for me, I've played around a lot with gtkrc in gtk-2.0 and with settings.ini and a couple of .css files in gtk-3.0 to set things up without having to download any additional theme. I used Ambiance as a starting point and the nice thing is that I have the same (as far as possible) looks if I log into a Unity 3D session.

As for the links, I think the Xfce team has done a very decent job with respect to documentation.

---

### Post by jim Kane on 2012-06-19
> **Toz said:**
>  If the theme you choose supports rollups, you can them to the window decoration from Settings Manager -> Window Manager -> Style tab by dragging the roll-up icon from the hidden section to the button layout section.
.
Hi Toz
thank you for your help
i am testing 12.4 on a spare PC before i install it on my main one, will look at the xfwm-themes later in the week when i get time.
I cant quite understand what you were saying in the quote above have included photo of Piranha theme, its the fourth (or third in the gimp side panels) roll up button that is so useful to me.

[IMG]http://img88.imageshack.us/img88/3331/piranha.png[/IMG]

---

### Post by Toz on 2012-06-19
If the rollups are available for the window manager theme, they can be enabled/set in the Settings Manager->Window Manager->Style tab. Simply drag the rollup icon from the **Hidden** area (pic1) to the **Button Layout** area (pic2).

---

### Post by jim Kane on 2012-06-20
> **Toz said:**
> If the rollups are available for the window manager theme, they can be enabled/set in the Settings Manager->Window Manager->Style tab. Simply drag the rollup icon from the **Hidden** area  to the **Button Layout** area .

Ah so simple thanks,
 none of the themes in 10.4 that i have ever looked at have had a hidden &#65279;roll-up button, thats why i was confused.
i will have a look through all the available themes for 12.4 at the weekend.
thanks again for your help 

Jim

---

### Post by Peripheral Visionary on 2012-06-20
If you've found everything you needed, be sure to mark this thread as SOLVED so others can benefit from this discussion. Best "layman's language" description of Window Managers and Desktop Environments I've found online can be read [here]("http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893").

---

### Post by jim Kane on 2012-06-21
[FONT=Arial]Just as a final solved post [/FONT]
    [LEFT][FONT=Arial]i installed the xfwm4-themes tonight, Piranha was there as well as just about every other combination of Theme imaginable.[/FONT][/LEFT]
    [LEFT][FONT=Arial]I do love Xubuntu&#8217;s customization  
[/FONT]


[FONT=Arial]Jim K
[/FONT][/LEFT]

---

