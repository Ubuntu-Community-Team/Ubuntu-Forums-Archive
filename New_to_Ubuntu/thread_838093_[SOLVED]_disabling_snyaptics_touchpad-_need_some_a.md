---
title: "[SOLVED] disabling snyaptics touchpad- need some advice"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by scotcella on 2008-06-23
I have found this [howto]("http://ubuntuforums.org/showthread.php?t=271052") tutorial for disabling the touchpad, it's driving me nuts that my cursor keeps flicking somewhere else in the middle of typing, as you will.

Anyway I have a couple questions....

What is the first step, I'm not quite sure what this means....

[I]> 
1. Turn on SHMCONFIG[/I]

Secondly, would I be able to turn the touchpad on/off by using key shortcuts? ie, alt T for alternating tabs. 
I don't want to be clicking a bunch of buttons to turn it off.

Thanks in advance...

---

### Post by drs305 on 2008-06-23
> **scotcella said:**
> 
What is the first step, I'm not quite sure what this means....

Secondly, would I be able to turn the touchpad on/off by using key shortcuts? ie, alt T for alternating tabs. 
I don't want to be clicking a bunch of buttons to turn it off.

Thanks in advance...

I will start by stating there should be, and probaby is, an easier method of turning off and on the touchpad. Does your laptop have a key combination that will do this (Fn + *)? I would guess someone has made a small app to do this but I don't have issues with my keyboard so I am not familiar with one. 

SHMConfig is a process invoked in the xorg.conf that configures your touchpad. The link edits /etc/Xll/xorg.conf to enable this feature.

If you want to continue, first make a backup of xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak1
```

This is the first step described in the link. You would open your text editor as root (gksudo gedit /etc/X11/xorg.conf) and edit this section of xorg.conf:
```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

```

Look like this:
```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
	**Option         	"SHMConfig"             "true"**
EndSection

```
Save the file and reboot.

As for the second part of your question, after accomplishing the above you  might prefer the solution presented in the link's post #11, where you use a shortcut to turn the touchpad off/on. Before actually going to the trouble of making a keyboard shortcut, you might try the commands in terminal to make sure they work on your laptop.

You would make scripts with the commands given below, make them executable (chmod a+x /pathtoscript/scriptname.sh), then make a keyboard or panel shortcut to invoke them. The shortcuts must include the full path to the script.

The scripts would look like this:
touchpad_off.sh
```

#!/bin/bash
synclient TouchpadOff=1

```

touchpad_on.sh
```

#!/bin/bash
synclient TouchpadOff=0

```

I don't have the time at the moment to give the details of how to create the keyboard shortcuts but a search of the forum should provide the answer.

---

### Post by scotcella on 2008-06-23
After fiddling around with the original how to that I posted, I found a way to get it working.

I'm still after a shortcut, if you have time later, would love to hear it.

Cheers and thanks heaps.

---

### Post by drs305 on 2008-06-23
> **scotcella said:**
> After fiddling around with the original how to that I posted, I found a way to get it working.

I'm still after a shortcut, if you have time later, would love to hear it.

Cheers and thanks heaps.

I read about syndaemon and it seems like a good way to deal with touchpad wanderings.

Anyway, to create a keyboard shortcut:
1. Open gconf-editor.
```
gconf-editor
```
2. Go to apps/metacity/keybinding_commands and double click a command number. We'll use command_10. 
3. Enter the command you want run. For the example, we'll turn off the touchpad. Type or paste in the command and ENTER.
```
synclient TouchpadOff=1
```
4. Now go back and click on global_keybindings.
5. Select the same designation as in step 2 (run_command_10)
6. Select a key combination and enter. Make sure it isn't being used by another shortcut. Look at other preset settings for the format. For our example, we'll use <Alt>9
7. Exit out of gconf-editor. The keyboard shortcut should be saved. Invoke it with <Alt>9
8. Repeat the process to create a keyboard shortcut to turn it back on using ```
synclient TouchpadOff=0
```.

If these don't work, it is possible the command you entered in Sessions to change the touchpad properties is interfering with these commands. To just play with setting up keyboard shortcuts, replace the *syncient* command with something simple like *gedit* or another app you have installed on your computer to see how it works.

---

