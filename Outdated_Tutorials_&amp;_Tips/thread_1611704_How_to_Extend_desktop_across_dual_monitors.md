---
title: "How to: Extend desktop across dual monitors"
date: 2010-11-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Crusty Old Fart on 2010-11-02
**_Here's the problem:_** The default RandR extension that configures monitors won't do it.
**_Here's the fix:_** You'll need to use the Xinerama extension from within xorg.conf.

_Here's a step by step set of instructions:_

[COLOR=Red]_**NOTE:**_ [/COLOR][COLOR=Red]The commands in the following procedure need to be entered in a virtual shell. While doing so, the graphical desktop will not be available. Consequently, if the steps presented below have not been committed to memory, written down, printed out, displayed on another computer, or are not available for reference by any other means, they will be impossible to perform.[/COLOR]

[LIST=1]
[*]Press the key combination [COLOR=Blue]**Ctrl+Alt+F1**[/COLOR] to drop to tty1 virtual shell.
[br]1[/br]
[*]Log in with your username and password at the prompts.
[br]1[/br]
[*]Stop gdm/X with the following command:
```

sudo service gdm stop

```
[*]Generate an xorg configuration file with the following command:
```

sudo X -configure

```[INDENT]The newly generated xorg configuration file will be created in your home (~) directory.
It will be named: **[COLOR=Green]xorg.conf.new[/COLOR]**
This file needs to be edited.
But, it will be owned by: **root**, so: **sudo** will be required at the beginning of the editing command as shown in the following step.
[/INDENT]
[*]Open **[COLOR=Green]~/xorg.conf.new[/COLOR]** for editing with the following command:
```

sudo nano ~/xorg.conf.new

```
[*]At the top of this file is the **ServerLayout** Section. Add the lines shown in **[COLOR=Red]red[/COLOR]** below to it:
```

Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" RightOf "Screen0"
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
        [B][COLOR=Red]# Added the following line to enable Xinerama dual screen output.
        Option         "Xinerama" "True"[/COLOR][/B]
EndSection

```
[*]Save your changes and exit your editor.
[br]1[/br]
[*]Copy this configuration file to [COLOR=Green]**/etc/X11**[/COLOR] as [COLOR=Green]**xorg.conf**[/COLOR] with the following command:
```

sudo cp ~/xorg.conf.new /etc/X11/xorg.conf

```
[*]Start gdm/X with the following command:
```

sudo service gdm start

```
[*]Log in to the GUI with your username and password.
[br]1[/br]
[*]At this point, if you don't have a desktop that spans both of your monitors, then you'll need to reboot. (Sorry, I just can't remember if restarting gdm/X was enough of a kick-start to bring the extended desktop to life. So, you may need a reboot.)
[/LIST]
[INDENT]**_NOTE:_** The presence of an xorg.conf file in the /etc/X11 directory causes the system to abandon RandR and gives priority to xorg.conf for configuration settings. So, any configuration changes you may want to make will need to be done by manually editing /etc/X11/xorg.conf instead of using xrandr. Furthermore, Xinerama will disable randr to the point where it won't even recognize your displays. None of this is a problem, as long as the configuration in xorg.conf is good. The automatically generated configuration seems to work very well.
[/INDENT]**_How to undo the changes:_** Follow the steps below to reverse the changes made above and put your system back to the way it was before you read this post.
[LIST=1]
[*]Delete the xorg configuration files from /etc/X11 and your home directory as follows:
```

sudo rm /etc/X11/xorg.conf
sudo rm ~/xorg.conf.new

```
[*]Reboot.
[/LIST]
If you have any problems with this, I'll be happy to try to answer them.

Here's a helpful reference: [https://secure.wikimedia.org/wikipedia/en/wiki/Xinerama](https://secure.wikimedia.org/wikipedia/en/wiki/Xinerama)

Good Luck,

Crusty

---

