---
title: "Program to drag a section on the screen for a screenshot?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-05-10
Is there some sort of program that allows me to screenshot by dragging the section on the screen that I want to save?

---

### Post by macaholic on 2008-05-10
You can do that with compiz, with the screenshot plugin.

---

### Post by Monicker on 2008-05-10
Ksnapshot will also work for that.  Gimp also has a screenshot function which would work.

---

### Post by noynac on 2008-05-10
The commandline utility import--which is a part of the ImageMagick package--creates screenshots and allows you to select the area of the screen to be included as well as the file format of the screenshot file. You can try this out by typing the following in a terminal window:

```
import filename.png
```

If you decide to use this on a regular basis, you can assign this command to a launcher or keyboard key.

The commandline utility scrot will do the same thing, although it has fewer options.

---

### Post by linkmaster03 on 2008-05-11
Thank you everybody!

---

### Post by LMP900 on 2008-05-13
> **macaholic said:**
> You can do that with compiz, with the screenshot plugin.

How do you enable the plugin? I'm using Ubuntu 8.04 and running the out-of-box settings of Compiz ("Normal" visual effects).

---

### Post by siouzi on 2008-05-21
> **LMP900 said:**
> How do you enable the plugin? I'm using Ubuntu 8.04 and running the out-of-box settings of Compiz ("Normal" visual effects).

First you need the Compiz settings manager:
System > Preferences > Advanced Desktop Effects Settings

If it's not there, use the Synaptic Package Manager to install it. The name of the package is compizconfig-settings-manager.

Once you have it, tick the Screenshot plugin (under Extras) and click it to set the directory where you want to save the images.


I haven't tried g/scrot and the Graphics/ImageMagick import command seemed to do the same thing as compiz's screenshot plugin, except compiz allows you to launch a program after the capture. You can use whatever you want, for example, a script.

You could use something like this to get a "save as" dialog and copy the filename to clipboard (for quick browse file... upload etc).
```

#!/bin/bash
#
# Requires:
#       zenity -- For dialogs, comes with ubuntu hardy
[ ! -x /usr/bin/zenity ] && exit

#       xclip  -- Optional, to copy filename to clipboard (middle click
#       to paste). Use `sudo apt-get install xclip` to install the command.
#
# Handler (Launc Application) for compiz's screenshot plugin. Asks where do
# you want to save the file and also copies the path to the clipboard. Deletes
# the file if you don't want to save (compiz automatically saves the
# captures).
#
# Save anywhere, make this executable and set the "Launch Application".


# Better to have the full path. If the path is not absolute, try to find it
path=$1
if [ "`expr match $path '^[^/]'`" -gt 0 ]; then
        if [ -e "`pwd`/$path" ]; then
                path="`pwd`/$path"
        elif [ -e "$HOME/$path" ]; then
                path="$HOME/$path"
        else
                zenity --error --text "Couldn't find the file path:\n$path"
                exit
        fi
fi

# Ask where to save the file
saveas=`zenity --title "Save capture as..." --file-selection --save --confirm-overwrite --filename="$path"`

# Delete the capture if the user cancels
if [ ! $saveas ]; then
        rm -f $path
        exit
fi

# Rename the capture if the filename was changed
if [ $path != $saveas ]; then
        mv $path $saveas
        path=$saveas
fi

# If we have xclip copy the filename to clipboard, middle click to paste
[ -x /usr/bin/xclip ] && echo $path | xclip -i

```

N.B. I'm not an experienced bash scripter so it may not work in your system and I'm not responsible if something goes wrong =)

Edit: some tyops :p

---

