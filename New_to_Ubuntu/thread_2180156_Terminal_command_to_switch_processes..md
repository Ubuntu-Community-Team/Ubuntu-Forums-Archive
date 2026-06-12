---
title: "Terminal command to switch processes."
date: 2013-10-11
forum: New to Ubuntu
---

### Post by yyttr3 on 2013-10-11
I want to create a custom key (cntrl+F) to open firefox, the Terminal (cntrl+~), spotify (through wine) (cntrl+ S), and others.
This is pretty easy using 'firefox' as the command, but if firefox is already open somewhere I don't want it to open another browser, just switch the screen to firefox.

I want to be able to create hotkeys to switch screens without leaving fullscreen and without creating multiple instances of the same program, how would I go about this?

---

### Post by vasa1 on 2013-10-11
Interesting! I'm sure the scripting wizards will find you a solution but it may help them if you  mention your operating system, the particular flavor (desktop environment), and the window manager and their respective versions. 

Also, IMO, if you have a "custom key", you wouldn't need a "terminal command", in the literal sense, to switch processes.

---

### Post by yyttr3 on 2013-10-11
I'm using Ubuntu 12.04

---

### Post by stinkeye on 2013-10-12
Install wmctrl...
```
sudo apt-get install wmctrl
```

...and try as the command in keyboard shortcuts....
```
sh -c "wmctrl -a Firefox || firefox"
```

The command will switch to the desktop that has a window with "Firefox" in the title, raise the window, and give it focus.
If a window with "Firefox" in the title doesn't exist, it will start firefox.

So to use with other apps use the same format...
eg 
```
sh -c "wmctrl -a [COLOR="#0000FF"]<str>[/COLOR] || [COLOR="#FF8C00"]<start command>[/COLOR]"
```
... which will switch to a window containing the string [COLOR="#0000FF"]<str>[/COLOR] in the title or 
if there is no window containing the string it will run [COLOR="#FF8C00"]<start command>[/COLOR]

[COLOR="#FF0000"]EDIT[/COLOR] If you are using unity though, just use the super+number shortcuts as **Vaphell** stated.

---

### Post by Vaphell on 2013-10-12
ctrl+f and ctrl+s? Good luck with that. 1st one is a classic 'find' option in countless programs, while the other is an equally classic 'save' option.

That said, sure it can be scripted but why don't you just use the built-in feature of the unity launcher bar? Pin stuff to it and since programs will be in a predictable order you can use win+<number> to do run 1st/switch to existing. Shift+win+<number> forces spawning new window. Holding win shows numbers assigned to icons.

---

### Post by vasa1 on 2013-10-12
Just to say that stinkeye's solution works for me in Lubuntu 13.04 which has Openbox as window manager though I'll spend a while figuring out what "**||**" does :)

---

### Post by Vaphell on 2013-10-12
|| is logical operator OR
in the context of commands it makes the following command to execute on failure, as opposed to && (AND) which executes on success.

---

### Post by vasa1 on 2013-10-12
> **Vaphell said:**
> || is logical operator OR
in the context of commands it makes the following command to execute on failure, as opposed to && (AND) which executes on success.
Thanks! So it's a *specialized* meaning of OR. Quite powerful!

---

### Post by vasa1 on 2013-10-13
A bit OT but I just found out that both wmctrl and xwininfo don't mention Leafpad when a window of Leafpad is open! xprop does so and so does xlsclients.

Edit: but see [http://ubuntuforums.org/showthread.php?t=2182648](http://ubuntuforums.org/showthread.php?t=2182648)

---

### Post by heir4c on 2013-10-13
You use Ubuntu 12.04 so I think it is still the same as in 13.10. 
When you click on the "Super" key (The "Windows" key on your keyboard) and hold it in, than you see on the icons a number (not on all unfortunately). When you use that number with the Super key than it switch to that Program. So here on the icon of FireFox I have a 2, so I use: Super+2 and it switch to FireFox. (even when I on a other workspace)

It's numbered from 1 to 0 and also for Show-Desktop a d for the Workspaceswitcher a s and the Trashcan a t.
When you use some programs regularly than you can stick there icons in the Launcher and in the first 10 positions. Than you can use the numbers 0 - 9 for them.

---

### Post by moshefeit on 2013-10-14
Ubuntu created the side bar for ease access, and there is a mouse, even now touchpad, so you only need one finger. Why you die hard using 2 finger to open an application?

---

