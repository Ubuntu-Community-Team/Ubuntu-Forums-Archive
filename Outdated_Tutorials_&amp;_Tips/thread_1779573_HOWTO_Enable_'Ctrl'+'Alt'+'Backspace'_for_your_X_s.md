---
title: "HOWTO: Enable 'Ctrl'+'Alt'+'Backspace' for your X session"
date: 2011-06-10
forum: Outdated Tutorials &amp; Tips
---

### Post by seeker5528 on 2011-06-10
**Method 1: User specific configuration.**

Add the line 'setxkbmap -option terminate:ctrl_alt_bksp' to '~/.xprofile'.

Unless you previously created it this file doesn't exist in which case you can open your favorite text editor (gedit, kate, etc...) and type or copy/paste the following lines:

```
# This file '~/.xprofile' should be used to customize the environment of your X login session similar
# to the way you would use '~/.profile' to customize the environment of your command line login session.

# export PATH="~/some_directory:$PATH"
# export WINDOW_MANAGER="/usr/bin/fluxbox"

# Eexport LIBOVERLAY_SCROLLBAR=1

setxkbmap -option terminate:ctrl_alt_bksp
```

Save the file as ```
~/.xprofile
```

Log out and log in to activate the change.

If you use lxdm as your display manager method 1 will not work because '~/.xprofile' fails to get processed while using it.

To undo open your text editor (gedit, kate, etc...)
Files beginning with a dot are considered hidden so in the file open dialog box where it ask for the location or name type ```
~/.xprofile
``` delete the line of text```
setxkbmap -option terminate:ctrl_alt_bksp
```
save and exit.
Log out and log in to activate the change.

**Method 2: System wide configuration.**

Add the line ```
Option              "XkbOptions" "terminate:ctrl_alt_bksp"
``` to the "InputClass" section of xorg.conf.

Commonly in Ubuntu this file doesn't exist or if it does, doesn't include the "InputClass" section.

Use the key combination 'Alt'+'F2' to get a run box or open a terminal window if 'Alt'+'F2' doesn't work.

Depending on the desktop you run open the text editor by typing one of the following command lines....

```
gksudo gedit /etc/X11/xorg.conf
```
```
kdesudo kate /etc/X11/xorg.conf
```

or this last one should work for everybody

```
sudo -H nano /etc/X11/xorg.conf
```

Type or copy/paste the text for the "InputClass" section 
```

Section "InputClass"
    Identifier          "Keyboard Defaults"
    MatchIsKeyboard	"yes"
    Option              "XkbOptions" "terminate:ctrl_alt_bksp"
EndSection

```

Save and exit.
Log out and log in to activate the change.

To undo open the text editor as indicated earlier using 'Alt'+'F2' or by opening a terminal window and typing ```
sudo -H nano /etc/X11/xorg.conf
``` remove the line ```
 Option              "XkbOptions" "terminate:ctrl_alt_bksp"
```
save and exit.
Log out and log in to activate the change.

I based this on information I found in the [Archlinux wiki](https://wiki.archlinux.org/index.php/Xorg#Ctrl-Alt-Backspace_doesn.27t_work).

Tested this using GDM as my display manager and logging into a Lubuntu desktop and an Ubuntu (Unity) desktop.

Later, Seeker

---

