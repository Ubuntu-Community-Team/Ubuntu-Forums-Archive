---
title: "Changing a single setting in a config file every time the system tray updates?"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by nullified_nostalgia on 2012-05-20
I use a transparent background on my panel and I've noticed that occasionally the system tray area's background will get skewed to the side.  I think this is caused by items being added or removed from the tray and the tray stretching but not updating the background image.

I can get it to reset by turning panel transparency off and back on.  I don't want to do this on the regular though, so I want to write a script to turn transparency off and back on whenever there is a change in the system tray.

First, I don't know how to make a script change a single setting in the config file.  The config file in question, located at /home/owner/.config/lxpanel/Lubuntu/panels, contains the following:
```
# lxpanel <profile> config file. Manually editing is not recommended.
# Use preference dialog in lxpanel to adjust config when you can.

Global {
    edge=bottom
    allign=left
    margin=0
    widthtype=percent
    width=100
    height=24
    transparent=1
    tintcolor=#000000
    alpha=0
    autohide=0
    heightwhenhidden=2
    setdocktype=1
    setpartialstrut=1
    usefontcolor=1
    fontcolor=#ffffff
    background=0
    backgroundfile=/usr/share/lxpanel/images/lubuntu-background.png
    iconsize=22
}

Plugin {
    type = menu
    Config {
        image=/usr/share/lubuntu/images/lubuntu-logo.png
        system {
        }
        separator {
        }
        item {
            command=run
        }
        separator {
        }
        item {
            image=gnome-logout
            command=logout
        }
    }
}

Plugin {
    type = launchbar
    Config {
        Button {
            id=pcmanfm.desktop
        }
        Button {
            id=/usr/share/applications/firefox.desktop
        }
    }
}

Plugin {
    type = space
    Config {
        Size=4
    }
}

Plugin {
    type = taskbar
    expand=1
    Config {
        tooltips=1
        IconsOnly=0
        ShowAllDesks=0
        UseMouseWheel=1
        UseUrgencyHint=1
        FlatButton=0
        MaxTaskWidth=150
        spacing=1
        GroupedTasks=0
    }
}

Plugin {
    type = volumealsa
}

Plugin {
    type = tray
}

Plugin {
    type = dclock
    Config {
        ClockFmt=%A, %B %d, %l:%M %p
        TooltipFmt=%A %x
        BoldFont=0
        IconOnly=0
    }
}


```
I would need to change the "transparent=1" to "transparent=0" and then back to "transparent=1".  How can I make a script change this one setting?

Second, is there a way to make a script monitor the system tray for changes so it would fire only when something is added or removed from the system tray?

Thanks in advance!

---

### Post by MG&amp;TL on 2012-05-20
I don't know how to listen for events from lxpanel, but this should work, albeit probably a little excessively:

```

#!/bin/bash

#put it on a continuous loop
while true
do

#replace transparent=1 with transparent=0
sed -i 's/transparent\=1/transparent\=0/g' ~/.config/lxpanel/Lubuntu/panels

#wait for panel to read file
sleep 2

#switch it back again
sed -i 's/transparent\=0/transparent\=1/g' ~/.config/lxpanel/Lubuntu/panels

#go on with life as normal
sleep 100

#go back to start
done

```

I have no idea howw regularly the applets read their config files, or even if they do at all without using the preferences dialog, so this might require some tweaking or not work at all.

If you want to know more about how this works, google "while loops bash" and "sed tutorial"

---

