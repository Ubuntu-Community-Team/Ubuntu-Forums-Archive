---
title: "execute script after waking"
date: 2010-02-15
forum: Programming Talk
---

### Post by flyingsliverfin on 2010-02-15
i usually put my computer to sleep instead of turning it off. however, i only know how to set a script to run at startup/login. Is there a way to make a script execute after logging in( after wake up)

---

### Post by cubeist on 2010-02-15
sure, the scripts that run when your computer sleeps/wakes are in:
/usr/lib/pm-utils/sleep.d

Look at the scripts in there for the format (95led is a good example), then write your script in a similar format and cp into a spot where it will execute...

---

### Post by flyingsliverfin on 2010-02-20
um.. its not exactly working...
the thing i want to excecute is really simple


```
#! /bin/sh
#choose a new desktop picture randomly from a set of pictures in the designated file


gconftool-2 --type str --set /desktop/gnome/background/picture_filename "$(ls /home/joshua/Desktop/ALL/downloaded_wallpaper/desktop-changing-script-wallpapers/*.jpg|sort -R| head -n1)"
```

1 command... anyway, i saved it in a file in the sleep.d folder and set it as an executable. the desktop didnt change. i did it a couple times to make sure it didnt randomly choose the same picture again, but still no change.

something wrong with the format of my command? as far as i could tell a simple command could just be typed in like that

---

### Post by cubeist on 2010-02-22
Hi,
It is always a good idea to test a command in your terminal to ensure it works perfectly before making it executable and placing it in your system... in this case it is a pretty harmless command, but other commands can quickly destroy parts of your system!

Anyway, on the command:
From the gconftool-2 --help pages (man pages are the first place to look when something doesn't work) it says the available types are
```
-t, --type=int|bool|float|string|list|pair 
```
so the command should be:
```
gconftool-2 -t string -s /desktop/gnome/background/picture_filename "$(ls /home/joshua/Desktop/ALL/downloaded_wallpaper/desktop-changing-script-wallpapers/*.jpg|sort -R| head -n1)"
```
cheers

---

### Post by flyingsliverfin on 2010-02-22
i dont think thats the problem. as a normal script it works (when i just run it) but for suspend it doesnt

---

### Post by jirik on 2011-02-27
You have to format your script to accept a parameter to distinguish between various situations.

Here is the outline of the script:
```

#!/bin/bash
case $1 in
    hibernate)
        echo "Hey guy, we are going to suspend to disk!"
        ;;
    suspend)
        echo "Oh, this time we're doing a suspend to RAM. Cool!"
        ;;
    thaw)
        echo "oh, suspend to disk is over, we are resuming..."
        ;;
    resume)
        echo "hey, the suspend to RAM seems to be over..."
        ;;
    *)  echo "somebody is calling me totally wrong."
        ;;
esac

```
Source: [https://wiki.archlinux.org/index.php/Pm-utils#Creating_your_own_hooks](https://wiki.archlinux.org/index.php/Pm-utils#Creating_your_own_hooks)

Read the linked document if interested in more details.

---

### Post by jirik on 2011-02-27
I myself did use this to set sensitivity to trackpoint device. What you may find useful is that I had to set some delay between running script and executing commands in it. It seems that pm scripts are run very early after wakeup and those commands weren't working properly.

For debugging look into /var/log/pm-suspend.log.

Here is my script for setting trackpoint sensitivity:

```

#!/bin/bash
case "${1}" in
	resume|thaw)
	# Trackpoint sensitivity
	( sleep 5 ; echo -n 130 > /sys/devices/platform/i8042/serio1/speed ; echo -n 255 > /sys/devices/platform/i8042/serio1/sensitivity ) &
	;;
esac

```

Also more proper place to put your custom scripts is /etc/pm/sleep.d/.

---

