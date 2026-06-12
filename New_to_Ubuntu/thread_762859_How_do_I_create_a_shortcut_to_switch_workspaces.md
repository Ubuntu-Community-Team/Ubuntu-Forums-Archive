---
title: "How do I create a shortcut to switch workspaces?"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by steelmole on 2008-04-22
I have four workspaces but can only switch to 2 of them directly with a keyboard shortcut.  How can I add a keyboard shortcut for 3 and 4?

---

### Post by Joeb454 on 2008-04-22
What are the keyboard shortcuts currently?

And you can use Ctrl+Alt+Left/Right to move between workspaces in a linear manner :)

---

### Post by Het Irv on 2008-04-22
What shortcut are you using to switch?
Do you have Compiz Settings Manager installed?

---

### Post by steelmole on 2008-04-22
I set them to ctrl-1 and ctrl-2, so I can just use my left hand.  I know you can move along them in a line, but I want to be able to move to them in an absolute way.

---

### Post by Joeb454 on 2008-04-22
If you set them yourself, can you not set Ctrl+3/4 the same way? Seems like you should be able to :)

---

### Post by steelmole on 2008-04-22
Therein lies the rub.  On the keyboard shortcuts menu there are options for "switch to workspace 1" and "switch to workspace 2" but not for 3 and 4.

---

### Post by Het Irv on 2008-04-22
I am in Hardy, but I have 'Switch to Workspace 1-4' in my keyboard shortcuts menu.  If you were planning to upgrade, it might be best to just sweat it out for two more days.  If you wern't planning to upgrade, try downloading the CCSM, It has a few more options that you may be able to play with.

---

### Post by Joeb454 on 2008-04-22
Ah, found the fix :)

Fire up a terminal, and type (or copy) ```
gconf-editor
```
Then choose apps > metacity > global_keybindings (some scrolling required)

Your commands are in there, you just need to assign a key to them :)

---

### Post by steelmole on 2008-04-22
Ahh, thankyou very much.

Still should've been in the menu.  Grr.

---

### Post by Joeb454 on 2008-04-22
It probably should, but Ubuntu comes with only 2 workspaces enabled by default if I remember right. So that would also explain why there was only 2 options available :)

---

### Post by DarkN00b on 2008-04-22
1. Press <ALT>+F2
2. Type "gconf-editor" (w/o quotes) and hit enter.
3. Navigate to apps>metacity>global_keybindings
4. Scroll down to the switch_to_workplace_1 (thru 12) keys
5. Change what you need.

You have to type in what you want, there is no capture.

EDIT: Oops, I forgot to mention that this is for Gnome; I don't know abour KDE or other DEs.

---

### Post by mmcnama4 on 2008-04-25
So if I wanted to make the "home" button the toggle between screens key, what would the name for the home button be? 

To copy something it is <control><c>.
What do I type between the <> to make the little house button the button I want?

Thanks,
M

---

### Post by DarkN00b on 2008-04-25
To get keycodes and names, open a terminal window and type:
```
xev
``` and hit enter.

Press any key and you'll get a lot of info related to that key including its key code and name.

For example here's the output of xev when I press the home key:
```
KeyPress event, serial 30, synthetic NO, window 0x3200001,
    root 0x187, subw 0x0, time 2256951755, (256,233), root:(267,281),
    state 0x10, keycode 97 (keysym 0xff50, Home), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

So using <home> should work as an input string.

As far as using the home key to toggle between screens, I don't know if that is possible. There is no option to do that in gconf-editor.

---

### Post by cycle_mycle on 2009-09-13
This works great! It's very clear and easy to do.

[http://desipenguin.com/techblog/2009/02/13/gnome-switch-to-workspace-3-and-4-using-keyboard-shortcut/](http://desipenguin.com/techblog/2009/02/13/gnome-switch-to-workspace-3-and-4-using-keyboard-shortcut/)

---

