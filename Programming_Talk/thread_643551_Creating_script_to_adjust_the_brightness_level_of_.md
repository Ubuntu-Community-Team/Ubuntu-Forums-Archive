---
title: "Creating script to adjust the brightness level of the monitor"
date: 2007-12-17
forum: Programming Talk
---

### Post by Catalyst2Death on 2007-12-17
Hello,

I am running ubuntu gutsy on a Dell inspiron 1501.  My fn brightness keys don't work, and I don't want to downgrade my bios (in fact, I can't because I'm running ubuntu/vista and the downgrade software only works in xp and earlier) 

 So, I'm wondering if it is possible to write a shell script to adjust the brightness (one for up and another for down) and then bind them to keys on the keyboard (like alt+up or alt+down to increase and decrease brightness respectively)

this would circumvent the use of the fn key, but I don't have a clue how to begin to implement something like this

---

### Post by mridkash on 2007-12-18
Do you know the commands to use for brightness. Can you do it in terminal?

If yes then you can make a bash script and run it on some key combination.

---

### Post by moma on 2007-12-18
Just a tiny idea.

Check if the [XRandr]("http://www.x.org/wiki/Projects/XRandR") utility can change the brightness value.

Check 
$ [COLOR="SeaGreen"]man xrandr[/COLOR]

and Google for "xrandr brightness"
----

Notice also that most of the graphic cards (drivers) have their own command line and GUI config tools.
Such as  ATI has "aticonfig". 
NVIDIA has "nvidia-settings"  and "nvidia-xconfig" 
----

Related stuff, URandR: [http://albertomilone.com/wordpress/?p=142](http://albertomilone.com/wordpress/?p=142)

Merry Christmas
$ xsnow

---

### Post by Catalyst2Death on 2007-12-18
I googled "xrandr" and it looped my back here! oh well, thanks for the advice.
I know the command for brightness, the only problem is that you must be logged on as root to adjust the brightness... sudo doesn't work, anyway how do I do this? 

 I'm not entirely familiar with shell scripts, so I don't know how to get it to login as root and then adjust brightness.  I would like to just press alt+up and have the brightness incrementally change, but I don't have a clue how to get going.

---

### Post by mridkash on 2007-12-19
to set custom keyboard shortcuts,

in terminal,
```
gconf-editor
```

a config editor window will open. Browse to apps> metacity> global keybindings
here you'll see "run_command_#" textboxes. type the shortcut in the value box. To set the commands, browse to keybindings_command and type the command.

it will work if you have desktop effects disabled. If you have compiz enabled then you have to install ccsm package to edit shortcuts.

---

### Post by deuce868 on 2007-12-19
If you feel like playing with DBus programming, there seems to be a dbus interface to the power manager. 

org.freedesktop.PowerManagement

Not sure what language you wanted to work on a script in, but python and dbus are pretty simple and you could write up a script to change the setting from there.

---

### Post by stevew45 on 2009-12-17
> **Catalyst2Death said:**
> I googled "xrandr" and it looped my back here! oh well, thanks for the advice.
I know the command for brightness, the only problem is that you must be logged on as root to adjust the brightness... sudo doesn't work, anyway how do I do this? 

 I'm not entirely familiar with shell scripts, so I don't know how to get it to login as root and then adjust brightness.  I would like to just press alt+up and have the brightness incrementally change, but I don't have a clue how to get going.

I have the same sort of problem, no fn keys. What commands do you use to adjust brightness from within the terminal?

---

### Post by deuce868 on 2009-12-17
I use this script I call 'powermode'. I call it with either:

disable
powermode d 

partial
powermode p

all
powermode a

```

#!/bin/bash
if test "$1" = "a"
then
    sudo -v
    cpu_speed set powersave && sudo echo -n 20 | sudo tee /proc/acpi/video/VID/LCD0/brightness
    
    # turns a noatime mount
    mount -o remount,noatime /home
    mount -o remount,noatime /
elif test "$1" = "p"
then
    sudo -v
    cpu_speed set conservative && sudo echo -n 60 | sudo tee /proc/acpi/video/VID/LCD0/brightness

    # turns a noatime mount
    mount -o remount,noatime /home
    mount -o remount,noatime /
elif test "$1" = "d"
then
    sudo -v
    cpu_speed set ondemand && sudo echo -n 100 | sudo tee /proc/acpi/video/VID/LCD0/brightness
else
        echo "Usage:"
        echo "  $(basename $0) a # all out powersave mode"
        echo "  $(basename $0) p # powersave"
        echo "  $(basename $0) d # disable powersave modes"
fi
echo ""

```

It's the setting in /proc/acpi/video/VID/LCD0/brightness that adjusts the backlight.

---

### Post by haldean on 2011-01-14
You should look into the xbacklight tool -- the syntax is incredibly easy, and it's in the repos. It's as simple as:

```

xbacklight = 0 # Turn off backlight
xbacklight = 50 # Backlight at 50%
xbacklight = 100 # Backlight at full
xbacklight - 20 # -20%
xbacklight + 10 # +10%

```

I know this is an old thread, but it's also the first Google result for "backlight shell script", and I thought this was useful.

---

