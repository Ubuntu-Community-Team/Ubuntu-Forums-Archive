---
title: "How to change the background color of your screen (the one while gdm loads gnome)"
date: 2006-01-07
forum: Outdated Tutorials &amp; Tips
---

### Post by mindwarp on 2006-01-07
This may seem fairly simple, but took me a good amount of time to figure out.  Neither your gnome theme nor your gdm theme will change the color of the screem from the ugly brown color to fit their styles.  The color I speak of is the one present while the gnome splash screen shows.  In order to change this, just:

* sudo vi /etc/gdm/gdm.conf
* scroll to where it says BackgroundColor=#123123  <-- some ugly value there
* replace with your color (or just #000000 for black)

---

### Post by Mustard on 2006-01-15
Cool.  I've just been playing around with my login screen, splash screen and gnome themes and it was irritating me that I had to put up with the brown screen in between logging in and gdm loading.

NOTE: Personally I would rather use a more user friendly editor than vi. :)

```
sudo gedit /etc/gdm/gdm.conf  # a more user friendly editor for gnome users
```

Worked like a charm, btw.  Thanks for the tip. :D

---

### Post by art on 2006-01-15
A user friendly way is to go System->Administration->Login Screen Setup go to GTK+Greeter, on Background choose Color option, and at the bottom there is a Background chooser, with a color chooser, so you can even choose the color of your wallpaper to match the logon color, See the image

---

### Post by benplaut on 2006-01-16
[QUOTE=art]A user friendly way is to go System->Administration->Login Screen Setup go to GTK+Greeter, on Background choose Color option, and at the bottom there is a Background chooser, with a color chooser, so you can even choose the color of your wallpaper to match the logon color, See the image[/QUOTE]

unfortunately, the image part doesn't work :/

You can, however, make a splash image the size of your screen... looks pretty cool :D

---

### Post by Fisheke on 2006-01-16
Nice, i've been bothered by that colour for quite some time :). Thanks for figuring it out!

---

### Post by ToastedToad on 2006-01-16
Oh yes been trying to figure this one out for a while, thanks!!!!!

---

### Post by cvaty on 2007-09-15
this doesn't seem to be working anymore.
how can i get rid of the orange screen that pops up, after the logon and before the gdm loads...

thanks

---

### Post by AncientPC on 2007-11-02
> **cvaty said:**
> this doesn't seem to be working anymore.
how can i get rid of the orange screen that pops up, after the logon and before the gdm loads...

thanks
Ditto, this doesn't seem to be working anymore in Gutsy.  I've changed both BackgroundColor and GraphicalThemedColor values.

---

### Post by marrowhk on 2007-11-05
> **Caffeine_Junky said:**
> Yep's, same here.   I don't see it as a problem, just something that has been left-out/removed from this release,  it has been this way since T3 was put out.   Maybe it will be addressed soon.  I hope it will be, because looking at a "blank beige screen" between login and desktop seems a little bit untidy IMO


Edit: 
I found a way to change the colour of the "Blank Beige Screen" that is displayed while Gnome is loading:



ps: My Gnome loading time is normal (same time to load as feisty) it is just that there is no splash on it, just a blank screen.

IT WORKS

---

### Post by keforex on 2007-11-05
It doesn't work. No matter what I do, after login in name and password, there's always this beige fugly screen. What to do?

EDIT:

[This thread]("http://ubuntuforums.org/showpost.php?p=3672448&postcount=2") solved my problem.

---

### Post by Perpetual on 2007-11-05
Try

```

sudo gedit /etc/gdm/PreSession/Default
```

Code:
# Default value
if [ "x$BACKCOLOR" = "x" ]; then
]BACKCOLOR="#dab082"


Change BACKCOLOR.

---

