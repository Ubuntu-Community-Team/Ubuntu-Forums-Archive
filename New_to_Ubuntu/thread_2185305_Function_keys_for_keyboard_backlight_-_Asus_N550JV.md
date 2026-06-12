---
title: "Function keys for keyboard backlight - Asus N550JV - lubuntu 14.04 &amp; 13.10"
date: 2013-11-02
forum: New to Ubuntu
---

### Post by Remten on 2013-11-02
_Updated May 2014: confirmed that the following also works in Lubuntu 14.04 (without xfce4)._

I have a new ASUS N550JV laptop with lubuntu 13.10 and xfce4 installed.

The top row of keys on the keyboard includes function keys F1 - F12.
F3 and F4 are supposed to raise and lower the backlight, but they don't  do anything when I press them (whether with or without the Fn key).
I haven't seen clear step-by-step instructions in a single place on how  to get the function keys working for the keyboard backlight, so I  thought I would post this in case someone else experiences the same  problem.

Thanks to these threads/articles for pointing me in the right direction,  especially the first one by user Banderlog at an Asus-related  discussion board:
[http://rog.asus.com/forum/archive/index.php/t-35889.html](http://rog.asus.com/forum/archive/index.php/t-35889.html)

[https://help.ubuntu.com/community/AsusZenbookPrime#A.28Xubuntu.2BAC8-Lubuntu_only.29_Manually_setting_keyboard_backlight_brightness](https://help.ubuntu.com/community/AsusZenbookPrime#A.28Xubuntu.2BAC8-Lubuntu_only.29_Manually_setting_keyboard_backlight_brightness)

[http://www.ryananddebi.com/2010/06/04/ubuntu-xbindkeys-to-replace-firefoxs-clippings-extension/](http://www.ryananddebi.com/2010/06/04/ubuntu-xbindkeys-to-replace-firefoxs-clippings-extension/)

[http://ubuntuforums.org/showthread.php?p=12819607](http://ubuntuforums.org/showthread.php?p=12819607)

[https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting)

**_[COLOR=#0000cd] My setup[/COLOR]_**

lubuntu 13.10 saucy amd64 alternate install  (dual boot encrypted Win 7 & encrypted lubuntu)
linux 3.11.0.12-generic
xfce4 4.10.1 metapackage
xfce4-goodies 4.10 metapackage

I have seen various posts around the internet that say the ASUS function  keys should work out of the box with certain recent installations of  linux, but that simply wasn't the case with my laptop. Also, I read an [Ubuntu.com help article]("https://help.ubuntu.com/community/AsusZenbookPrime#A.28Xubuntu.2BAC8-Lubuntu_only.29_Manually_setting_keyboard_backlight_brightness")  on a different ASUS laptop model that said Xubuntu and Lubuntu use  Xfce4-power-daemon, which affects the backlight in a different way than  is the case with Ubuntu. The article said that it is possible to use  gnome-settings-daemon instead of Xfce4-power daemon to get the function  keys working out of the box. This didn't work for me. So instead I used  the other option that that article recommends (which is basically the  same idea as what Banderlog recommended).

(you don't necessarily need to check these next three things  - I only  mention them because they gave me some confidence that the  problem did  not seem to be that my laptop hardware was completely  defective)

First, I knew that the function keys were physically functional and  sending signals that could be read because they triggered keypress codes  when I ran this in a terminal:
```
xev | sed -n 's/^.*state \([0-9].*\), keycode *\([0-9]\+\) *\(.*\), .*$/keycode \2 = \3, state = \1/p'
```

Second, I knew a keyboard backlight was installed because it would  activate whenever I booted the system. However, it would turn off as  soon the linux kernel loaded (or thereabouts).

Third, I knew that it was possible to raise or lower the keyboard  backlight within lubuntu from this command, which turned the keyboard  backlight on:
```
echo 3 > /sys/class/leds/asus::kbd_backlight/brightness
```

So I just needed to create scripts to send codes to that file (that is, to [COLOR=#0000cd]/home/mynamehere/sys/class/leds/asus::kbd_backlight/brightness[/COLOR] ) when I pressed the function keys.

Here's how:

**[COLOR=#0000cd](1) Create two scripts[/COLOR]** -- one to lower the keyboard backlight brightness, and one to raise it.

In terminal, create a script to lower brightness - I'll call it[COLOR=#0000cd] leds_down.sh[/COLOR]
(substitute whatever your own account name is where I've typed "yourname")
```
nano /home/yourname/.scripts/leds_down.sh
```

the code for the script:
```
#!/bin/bash
brightness=$(cat "/sys/class/leds/asus::kbd_backlight/brightness")
a=$((brightness-1))

if [ "$brightness" -gt 0]
then
echo $a >> /sys/class/leds/asus\:\:kbd_backlight/brightness
fi
```

then create the script to raise the brightness:
```
nano /home/yourname/.scripts/leds_up.sh
```

with this code:
```
#!/bin/bash
brightness=$(cat "/sys/class/leds/asus::kbd_backlight/brightness")
a=$((brightness+1))

if [ "$brightness" -lt 3]
then
echo $a >> /sys/class/leds/asus\:\:kbd_backlight/brightness
fi
```

now change their [COLOR=#0000cd]permissions[/COLOR] so that they are executable:
```
chmod +x /home/yourname/.scripts/leds_down.sh
chmod +x /home/yourname/.scripts/leds_up.sh
```

edit the file rc.local and add a line that will permanently give all users the ability to change the file on every boot:
```
sudo nano /etc/rc.local
```

specifically, enter this line 
```
chmod 666 /sys/class/leds/asus\:\:kbd_backlight/brightness
```

right BEFORE "exit 0" so that the file looks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


chmod 666 /sys/class/leds/asus\:\:kbd_backlight/brightness
exit 0
```

[COLOR=#0000cd]**(2)**[/COLOR] Next we need to **[COLOR=#0000cd]remap the keyboard[/COLOR]** so that pressing the function keys will trigger the scripts. To do that we need to get a program called [COLOR=#0000cd]xbindkeys[/COLOR] (and its configuration GUI, [COLOR=#0000cd]xbindkeys-config[/COLOR]):
```
sudo apt-get install xbindkeys xbindkeys-config
```

[COLOR=#0000cd]create a configuration file[/COLOR] (and load a few default settings into it):
```
xbindkeys -d > /home/yourname/.xbindkeysrc
```

Now launch the xbindkeys configuration GUI from a terminal:
```
xbindkeys-config
```

a window will open
click on "New" at the bottom

choose a name for your function, and type that name in the box on the upper right under "Edit" in the space next to "Name:"
This is just to remind you what this function does if you need to change things in the future.
(for example, I chose "keyboardbacklight_down" - without the quotes - for the name for lowering the backlight brightness)

click on "Get Key" just slightly below where you typed the function name
a window will open on the desktop
press the key you want to assign the keyboard backlight lowering function to
(I chose F3 on the top row of the keyboard, without the Fn key)

next type the location of your script for lowering the keyboard  brightness in the box next to "Action:", in the space where it says  "Command"
[COLOR=#0000cd] /home/yourname/.scripts/leds_down.sh[/COLOR]

click Apply, then click Save & Apply & Exit
(you probably can get away with just clicking Apply and then directly  going on to set the next key-binding instead of first clicking Save  & Apply & Exit (which forces you to have to relaunch the GUI),  but I haven't tried it that way)

relaunch the configuration GUI with xbindkeys-config in the terminal (if  necessary because you clicked Save & Apply & Exit in the last  step)

repeat the above steps for assigning a key to a function, this time  choosing a name for the raising-the-keyboard-backlight-brightness  function (I chose "keyboardbacklight_up"), and getting the key press  that you want to activate that function (I chose F4, without the Fn key)  and supplying the location of the script
[COLOR=#0000cd]/home/yourname/.scripts/leds_up.sh[/COLOR]

then Apply,
Save & Apply & Exit

---

