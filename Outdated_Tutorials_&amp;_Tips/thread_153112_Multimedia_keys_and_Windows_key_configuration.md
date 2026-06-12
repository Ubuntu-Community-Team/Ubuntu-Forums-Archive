---
title: "Multimedia keys and Windows key configuration"
date: 2006-03-31
forum: Outdated Tutorials &amp; Tips
---

### Post by localzuk on 2006-03-31
Many people own multimedia keyboards, laptops with extra keys and/or are simply used to the Windows key opening the 'K' menu/Start Menu in Windows.

This Howto should, hopefully, provide you with the information needed in order to set up these keys to do what you want in KDE/Kubuntu.

The process is quite short and simple, if repetitive.
[SIZE="4"]**Stage 1 - Enabling the keys**[/SIZE]
[LIST=1]
[*]Open a Konsole (type Ctrl+Alt+F2, type konsole and click OK),
[*]ensure that you have the 'xev' package installed, ```
sudo apt-get install xev
```
[*]launch xev in the konsole, ```
xev
```
[*]you can safely ignore the text that appears, now press one of the keys you wish to use; you should see an output such as:
```
KeyPress event, serial 28, synthetic NO, window 0x2c00001,
    root 0x135, subw 0x0, time 1344281323, (-281,237), root:(317,257),
    state 0x0, **keycode 160** (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 28, synthetic NO, window 0x2c00001,
    root 0x135, subw 0x0, time 1344281323, (-281,237), root:(317,257),
    state 0x0, **keycode 160** (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
```

You are interested in the highlighted number.

[*]take a note of the number and which key it is,
[*]repeat the last 2 steps for each key you wish to assign/re-assign,
[*]create a new file ~/.Xmodmap as such:
```
kate ~/.Xmodmap
```
[*]add a line for each of your keys as such:
```
keycode 160 = F13
keycode 161 = F14
```
The keycode's should be the ones you wrote down earlier. The F key numbers should be numbered after those that are actually present on your keyboard (so if you have a standard windows keyboard, you would have 12, if you have a mac keyboard you will have 16 so start at 17).
[*]save the file,
[*]make a new directory:
```
mkdir ~/.kde/env
```
[*]create another new file ~/.kde/env/xmodmap.sh
```
kate ~/.kde/env/xmodmap.sh
```
[*]enter the following into kate:
```
#!/bin/bash
xmodmap ~/.Xmodmap
```
[*]save that file,
[*]make that file executable
```
chmod +x ~/.kde/env/xmodmap.sh
```
[*]execute that file
```
sh ~/.kde/env/xmodmap.sh
```
[*]load the KDE System Settings program from the 'K' menu,
[*]click on the 'Regional & Accessibility' icon.
[/LIST]

You are now at the stage of being able to assign your keys to what you want them to do. The following sections will cover each possible action type you can assign.

[SIZE="4"]**Stage 2 - Setting the keys to an action**[/SIZE]
**Standard Keyboard Shortcuts**
If you wish, for example, to launch the 'K' menu by pressing a single button, eg. the Windows key, you should:
[LIST=2]
[*]click on the 'Keyboard Shortcuts' icon
[*]select the action from the lists (choose if you wish to do a Global shortcut, Shortcut Sequence, Application Shortcut or Command Shortcut)
[*]select the 'Custom' radio button at the bottom of the window
[*]click on the button next to it (it may say 'None' or it may say what it is currently mapped to
[*]press the key you wish to assign
[*]click Apply
[/LIST]

**Input Actions - DCOP**
This is for those that wish to use keys such as volume up and volume down keys (via kmix in this example).
[LIST=3]
[*]click on the 'Input Actions' icon,
[*]click the 'New Action' button at the bottom of the screen
[*]click in the 'Action name' field in the top right and enter a name for your action
[*]Select what you wish to do from the drop down menu - I am setting a volume up key so select 'Keyboard Shortcut -> DCOP Call (simple)'
[*]click on the 'Keyboard Shortcut' tab at the top
[*]click on the empty button
[*]click on the empty button next to the X arrow
[*]press the key you wish to use
[*]go to a console and type 'dcop' followed by the name of the k application you wish to control. You will see a list, each item is referred to as an 'Object'. Choose the item you wish to use (in my case 'Mixer0'),
[*]enter the KDE application you wish to control
[*]enter the object you wish to control (Mixer0 in my case),
[*]back on the konsole, type 'dcop appname objectName' eg:
```
dcop kmix Mixer0
``` to discover the functions that can be called on that object.
[*]enter the function you wish to call into the 'Called function' box and any required arguments in the 'Arguments' box (in our case a 0 as there are no arguments)
[*]click 'Apply'
[*]try out your newly mapped item.
[/LIST]
In the above steps you use the command line to discover information about 'dcop' commands. Instead of this, you can use a program called 'kdcop' - to launch this, click the 'Run KDCOP' button. Now you can investigate the dcop functions available to you. Note: you have to have the K application you wish to control via dcop open before it will appear in that listing.

**Input Actions - Command/URL**

[LIST=4]
[*]Click on the 'Input Actions' icon,
[*]click on the 'New Action' button,
[*]change the name of the action in the top right,
[*]select 'Keyboard Shortcut -> Command/URL (simple) from the dropdown list,
[*]click on the 'Keyboard Shortcut' tab at the top,
[*]click on the empty button,
[*]click on the empty button next to the X arrow,
[*]press the key you wish to use,
[*]click on the 'Command/URL Settings' tab,
[*]enter the command/url you wish to launch,
[*]click 'Apply'
[/LIST]

You should now have a set of working keys, doing what you want :)

---

### Post by Jaxilian on 2007-06-19
Does this work for Gnome too?

---

### Post by Jaxilian on 2007-06-24
bump

---

### Post by Jaxilian on 2007-07-03
bump

---

### Post by teaker1s on 2007-07-03
gnome can be mapped by looking at link for gnome related configuration
[https://help.ubuntu.com/community/MultimediaKeys]("https://help.ubuntu.com/community/MultimediaKeys")

---

