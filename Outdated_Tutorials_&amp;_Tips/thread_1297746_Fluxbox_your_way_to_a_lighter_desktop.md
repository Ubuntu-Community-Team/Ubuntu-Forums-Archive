---
title: "Fluxbox: your way to a lighter desktop"
date: 2009-10-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Bodsda on 2009-10-22
This How-To has been tested on the following Ubuntu Versions:

[LIST]
[*]Jaunty
[*]Karmic
[/LIST]

For those of you who don’t know, Fluxbox is a lightweight window manager based upon the Blackbox 0.61.1 code. It is very light on resources which means it will run very fast or it can be used to give an old computer a new lease of life.

I am going to show you how to install Fluxbox from the Ubuntu repositories. I am also going to show how to write your own Fluxbox menu without the use of menu generators.

[SIZE="4"]Installing Fluxbox[/SIZE]

To install fluxbox you need to first open a terminal

**Applications / Accessories / Terminal**

Once the terminal has loaded, enter the following command
```

sudo apt-get install fluxbox feh

```

Now that Fluxbox is installed, I hear you asking, “So, where is it?”

To get a fluxbox session you first need to log out. Then at the login screen, find the ‘Options’ button, and from there, the ‘Sessions’ choice.

This should now present you with a list of sessions available, chances are there is a Gnome, Fluxbox, and a couple of failsafe sessions. From this menu, choose Fluxbox. Now log in. You will be prompted to decide whether you want to log into fluxbox just once or if you want to make Fluxbox the default session. After you decide, you are logged into your brand spanking new Fluxbox!

But wait, with no icons or menu bars how do we get to our stuff! Don’t panic, Fluxbox uses a powerful right click menu system, give it a go, right click on the desktop.
[SIZE="4"]
Writing a Fluxbox menu[/SIZE]

In this section I am goinng to show you how to write your own sub menu for the Fluxbox right click menu. I find that having to delve through the menu is a bit time consuming so I wrote a ‘My common apps’ sub menu for it.

First, we should take a look at the default menu template. Found in **~/.fluxbox/menu**

```

[begin] (fluxbox)
    [include] (/etc/X11/fluxbox/fluxbox-menu)
[end]

```
Now, let me take a moment to go through that. The first line **[begin] (fluxbox)** The begin means that this is the start of the menu code. The **(fluxbox)** is the title of the first menu, the one shown immediately upon right click. If you fancy, go ahead and change the name inside **( )** to whatever you like.
The next line
**[include] (/etc/X11/fluxbox/fluxbox-menu)** tells the system to use the menu setup at that file path. This is what enables you to have the default menu.
The final line is **[end]** This, as you probably guessed, tells the system that it is the end of the menu file.

Now, lets go familiarize ourselves with a few things before we make our own sub menu. The basic syntax of a menu is as follows

```
[menu-command] (Menu-name)
    [menu-command] (Name) {executable location)
    [end]
[end]
```

Now, that may look slightly confusing, instead of talking about it, lets write a new menu entry to understand it. First lets decide what we want. We want a menu with two sub menu’s, one containing the standard fluxbox menu and one containing our common apps.

We use the **[submenu]** menu command to denote a submenu. Below is how you would add the fluxbox menu to a new submenu.

```
[begin] (My menu)
    [submenu] (Fluxbox menu)
        [include] (/etc/X11/fluxbox/fluxbox-menu)
    [end]
[end]
```

By just quickly looking at this, we can see that not much is new, we have simple encapsulated what was there originally into a submenu. Now, to add our common apps.
```

[begin] (My menu)
    [submenu] (Common apps)
        [exec] (Firefox) {/usr/bin/firefox}
```

You will have noticed the new **[exec]** menu-command in this example. This simply tells the system to execute whatever is in **{}** when the entry is clicked. The paths for your applications can be found by typing **which <command>** at a terminal, so to find out where firefox lives do ```
which firefox
```. Also, the path in-between the **<>** is a path to a small .png file that will be shown in line in the menu.

Finally all we need to do is stitch the two examples together, below is the complete menu.

```
[begin] (My menu)
    [submenu] (Fluxbox menu)
        [include] (/etc/X11/fluxbox/fluxbox-menu)
    [end]
    [submenu] (Common apps)
        [exec] (Firefox) {/usr/bin/firefox} </usr/share/pixmaps/firefox-3.0.png>
        [exec] (Xchat) {/usr/bin/xchat}
        [exec] (Terminal) {/usr/bin/gnome-terminal}
    [end]
[end]
```

There you have it, your own personalized Fluxbox menu. For another impressive Fluxbox introduction/How-To please see [_[COLOR="Red"]RedSquirrel’s excellent HOWTO: get a Fluxbox menu (and customization)]("http://ubuntuforums.org/showthread.php?t=371144")[/COLOR]_

Thanks for reading,

Regards,

Bodsda

---

