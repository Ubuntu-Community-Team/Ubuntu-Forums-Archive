---
title: "windows managers/nautilus"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-28
I've read about windows managers.  I don't get it.  I'm thinking it is like nautilus?  If so, What do windows managers offer in the way of advantage?  And if want to tool around with one, is it difficult to switch from nautilus, or is it automatic?

---

### Post by newbuntuxx on 2008-07-28
A windows manager is a program that is responsibe for displaying all the windows (basically the guis) that you see on your monitor. 

You have the KDE windows manager, you have the Gnome windows manager. And some others.

They have have advantages/disadvantges. KDE is more pleasing to the eye, but, slower than Gnome. Gnome is decent in terms of looks, but faster than KDE. 

of course different people with different systems have different opinions.

hope this helps!

---

### Post by Dr Small on 2008-07-28
Nautilus is not a window manager, it is a File Manager.
A WM (Window Manager) is the GUI that manages your windows.

For example of different WMs, there are:
Openbox
Fluxbox
IceWM
PekWM
Blackbox
etc.

---

### Post by Dr Small on 2008-07-28
> **newbuntuxx said:**
> A windows manager is a program that is responsibe for displaying all the windows (basically the guis) that you see on your monitor. 

You have the KDE windows manager, you have the Gnome windows manager. And some others.

They have have advantages/disadvantges. KDE is more pleasing to the eye, but, slower than Gnome. Gnome is decent in terms of looks, but faster than KDE. 

of course different people with different systems have different opinions.

hope this helps!
KDE and GNOME are not Window Managers, they are DEs (Desktop Environments).

---

### Post by coffeecat on 2008-07-28
But if you mean **file managers**, the default ones are:

Windows XP - Explorer
Mac OS - Finder
Gnome desktop - Nautilus
KDE desktop - Konqueror (or Dolphin in KDE 4)
Xfce desktop - Thunar

But in Linux you can install/use others. Konqueror works in Gnome, but looks a bit out of place. Or you can get Gnome-commander, X-commander and some others which are inspired by midnight-commander.

---

### Post by newbuntuxx on 2008-07-28
> **Dr Small said:**
> KDE and GNOME are not Window Managers, they are DEs (Desktop Environments).


pardon my ignorance, but what is the difference?

Also, what is the name of the windows manager that the Gnome desktop environment uses?

---

### Post by Dr Small on 2008-07-28
> **newbuntuxx said:**
> pardon my ignorance, but what is the difference?

Also, what is the name of the windows manager that the Gnome desktop environment uses?
GNOME uses no window manager. It is it's own Desktop Environment, meaning, there are alot of libraries and other software that get installed, when you install a DE.

A window manager on the other hand, when installed, meerly installs the WM.

---

### Post by adamogardner on 2008-07-28
oh k,  little clearer now.  I'm in the desktop environment GNOME.   So a window manager works "inside" the desktop enviornment?  What changes exactly when I change window manager - the visual window borders and titlebars and such?  do the compiz animations change?  what r some functional differences?  I understand Fluxbox is not fully suppoted with gnome.  I like fast and not as pleasant to the eye so gnome is good for me.  Any recomended WMs for GNome?

---

### Post by Dr Small on 2008-07-28
> **adamogardner said:**
> oh k,  little clearer now.  I'm in the desktop environment GNOME.   So a window manager works "inside" the desktop enviornment?  What changes exactly when I change window manager - the visual window borders and titlebars and such?  do the compiz animations change?  what r some functional differences?  I understand Fluxbox is not fully suppoted with gnome.  I like fast and not as pleasant to the eye so gnome is good for me.  Any recomended WMs for GNome?
A Window manager and a DE are completely different.

Fluxbox is a Window Manager.
GNOME is a Desktop Environment.

When you use a Window Manager, you are no longer using a Desktop Environment.

---

### Post by TheMemphisExperience on 2008-07-28
> **Dr Small said:**
> GNOME uses no window manager. It is it's own Desktop Environment, meaning, there are alot of libraries and other software that get installed, when you install a DE.

A window manager on the other hand, when installed, meerly installs the WM.

Okay, now I feel like I'm missing something. GNOME is the DE for Ubuntu, and Nautilus is the FM. The WM is Compiz? Then there is the compositor that is Compiz-Fusion? So GNOME is the enviornmen, but what does hat entail? Does that mean it is just a place where things like apps and icons can potentially be?

---

### Post by adamogardner on 2008-07-28
i see Dr Small.  sounds like the conversion would be exttremely difficult.  Is this true?  I wonder if there are WM's shown on utube.  I'm having difficulty visualizing this since gnome Is all I know.

---

### Post by Dr Small on 2008-07-28
> **adamogardner said:**
> i see Dr Small.  sounds like the conversion would be exttremely difficult.  Is this true?  I wonder if there are WM's shown on utube.  I'm having difficulty visualizing this since gnome Is all I know.
There is nothing difficult about a WM. I use openbox, but you just have to configure it. Go install IceWM or something, and then at the GDM, select IceWM as your session.

---

### Post by st33med on 2008-07-28
Difference between a Desktop Environment and a Window Manager:
Desktop Environments (eg: KDE, GNOME, etc.) are implementations to run a GUI. They cannot provide those window borders by themselves. They just provide a 'box', per say, to render what the program wants.

A Window Manager, however, allows fancy decorations and effects. For example, Compiz is a Window Manager that allows you to spin your cube and move windows. If Ubuntu can't run Compiz for whatever reason, it falls back to Metacity, which is a basic WM.

Then there are Window Decorators. Sometimes the WM doesn't want to decorate windows and leaves the task to a Window Decorator. For example, Compiz relies on Metacity or Emerald to decorate windows for it.

The best way to demonstrate this is to just kill compiz:
```
sudo killall compiz
```

Notice how the window borders are gone and, whenever you open a new window, it will be in the top right corner usually with no way to move it. Plus, you can't change workspaces since they do not exist without Compiz or Metacity.

Hope I made this much clearer :)

Edit: Err.. To restart compiz, you might have to open a terminal and type:
```
compiz &
```

---

### Post by DJ_Peng on 2008-07-28
> **TheMemphisExperience said:**
> Okay, now I feel like I'm missing something. GNOME is the DE for Ubuntu, and Nautilus is the FM. The WM is Compiz? Then there is the compositor that is Compiz-Fusion? So GNOME is the enviornmen, but what does hat entail? Does that mean it is just a place where things like apps and icons can potentially be?

> **Dr Small said:**
> A Window manager and a DE are completely different.

Fluxbox is a Window Manager.
GNOME is a Desktop Environment.

When you use a Window Manager, you are no longer using a Desktop Environment.
It's easy to get confused in these parts, and I couldn't find a wiki page that explains it clearly. At the risk of muddying the waters rather than clearing them, let's look at it this way.

[LIST]
[*]GNOME/KDE - Desktop environment. The layer that brings the GUI so you can work in your OS.
[LIST]
[*]Compiz Fusion/Metacity - The window manager. It controls the look of the windows that you use your applications in. Not 100% sure of what this layer does, but I know it's important because there are desktop effects I can do in Compiz that break in Gtk
[LIST]
[*]Window Decorator - Gtk/Emerald - The layer that adds your borders and buttons (menu, minimize. maximize, close) to your window.
[/LIST]
[/LIST]
[/LIST]
I hope this helps, adamogardner and TheMemphisExperience

---

### Post by adamogardner on 2008-07-28
So If I use another window manager, I effectually lose compiz?  Gnome is an invisible "box" or slate upon which window managers and such can be diplayed?  It is faster than kde in the demonstration of package effects such as window managers. Windows managers can be changed like an article of clothing depending upon the eccentricities of the user, providing configuration is a success.  ? 
I'm gonna try iceWM now, and see how that goes.

---

### Post by st33med on 2008-07-28
You essentially do loose Compiz when you use another WM. In order to replace a WM with another one, just type:
```
<wm-program> --replace
```
'--replace' is an option available, I believe, in all WM's to kill the other WM and run.

---

### Post by Pogeymanz on 2008-07-28
Compiz is a window manager. You can only run one window manager at a time, so yes, if you want to change window managers you lose compiz and it's special effects.

Of course, you can have multiple WM's and switch between them all day. It doesn't matter.

And a desktop environment is just a bunch of programs and libraries that are tied together to give you a working desktop. The window manager Metacity is included in GNOME (except that Ubuntu includes Compiz as well).

Let me explain this further:
In GNOME, you have metacity to control the windows (borders, titlebar, movement, workspaces).
You have nautilus which is a file manager and also draws your background wallpaper.
You have Gnome-panel for your task bar and main menu.
You also have a whole bunch of applications that come bundled with it, such as Gedit, a screensaver app, gnome terminal, etc, etc.

On MY computer, I don't use a "desktop environment" so I just have to make sure to install different applications to handle the same tasks I mentioned above.
Openbox is my window manager.
Thunar is my file manager.
Feh sets my background wallpaper.
Tint and stalonetray replace my need for a panel.
Urxvt is my terminal program.

The only difference is that a DE includes all that stuff by default. So, I basically "built" my own Desktop Environment by installing all the pieces separately.

EDIT: And to elaborate on St33med's tip, use synaptic to install IceWM. Then, from a terminal run ```
icewm --replace
``` and compiz will be killed and icewm will manage your windows. If you want Compiz back, just open the terminal again and type ```
compiz --replace
```

EDIT 2: I hate to say this, but a lot of the posts in this thread are inaccurate. DE's and WM's are not "completely different." A DE just has a WM plus a lot more. There is nothing magical about a DE and you do not need one at all. As I explained, a DE is just a bundle of applications that share some libraries.

---

### Post by DJ_Peng on 2008-07-28
Right. If you switch to Metacity, for example, anything that depends on Compiz Fusion won't be able to work. I'm not sure how much faster the KDE window manager is but if you were to switch to KDE you'd lose a lot of the functionality of GNOME, as KDE and GNOME are two different desktop environments, although you can load some KDE programs in GNOME. I run Amarok, a KDE media player, and I just had to install some KDE libraries.

If you have multiple window managers you can switch between them using something like the [Compiz Fusion Icon]("http://packages.ubuntu.com/hardy/x11/fusion-icon"). It's pretty quick, and the only glitch I see is that sometimes Firefox crashes while I switch window managers.

---

### Post by st33med on 2008-07-28
> **DJ_Peng said:**
> 
If you have multiple window managers you can switch between them using something like the [Compiz Fusion Icon]("http://packages.ubuntu.com/hardy/x11/fusion-icon"). It's pretty quick, and the only glitch I see is that sometimes Firefox crashes while I switch window managers.

I think I know what you are talking about. Clicking on anything in Firefox doesn't give any response. Try [un]maximizing it and it should respond fine then...

---

### Post by billgoldberg on 2008-07-28
> **Pogeymanz said:**
> Compiz is a window manager. You can only run one window manager at a time, so yes, if you want to change window managers you lose compiz and it's special effects.

Of course, you can have multiple WM's and switch between them all day. It doesn't matter.

And a desktop environment is just a bunch of programs and libraries that are tied together to give you a working desktop. The window manager Metacity is included in GNOME (except that Ubuntu includes Compiz as well).

Let me explain this further:
In GNOME, you have metacity to control the windows (borders, titlebar, movement, workspaces).
You have nautilus which is a file manager and also draws your background wallpaper.
You have Gnome-panel for your task bar and main menu.
You also have a whole bunch of applications that come bundled with it, such as Gedit, a screensaver app, gnome terminal, etc, etc.

On MY computer, I don't use a "desktop environment" so I just have to make sure to install different applications to handle the same tasks I mentioned above.
Openbox is my window manager.
Thunar is my file manager.
Feh sets my background wallpaper.
Tint and stalonetray replace my need for a panel.
Urxvt is my terminal program.

The only difference is that a DE includes all that stuff by default. So, I basically "built" my own Desktop Environment by installing all the pieces separately.

EDIT: And to elaborate on St33med's tip, use synaptic to install IceWM. Then, from a terminal run ```
icewm --replace
``` and compiz will be killed and icewm will manage your windows. If you want Compiz back, just open the terminal again and type ```
compiz --replace
```

EDIT 2: I hate to say this, but a lot of the posts in this thread are inaccurate. DE's and WM's are not "completely different." A DE just has a WM plus a lot more. There is nothing magical about a DE and you do not need one at all. As I explained, a DE is just a bundle of applications that share some libraries.

I kind of did the same on my desktop.

I removed unnecessary apps and the dependencies, and slapped fluxbox on that baby. 

It's faster than I could have imagened, while being far more user friendly (the way you can customize the keyboard shortcuts and menu is great).

And it looks great (screenshot [1]("http://billgoldbergmania.deviantart.com/art/Ubuntu-hardy-fluxbox-1-92915770") & [2]("http://billgoldbergmania.deviantart.com/art/Ubuntu-hardy-fluxbox-92914541"))

---

### Post by Pogeymanz on 2008-07-28
Yeah, it does look great. Especially the top left corner.

I would post my own screenshot but I'm not home right now.

---

### Post by adamogardner on 2008-07-28
thankyou, for that excellent post!

---

