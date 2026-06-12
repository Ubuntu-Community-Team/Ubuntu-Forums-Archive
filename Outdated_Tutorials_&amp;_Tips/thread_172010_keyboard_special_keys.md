---
title: "keyboard special keys"
date: 2006-05-07
forum: Outdated Tutorials &amp; Tips
---

### Post by brucehohl on 2006-05-07
Mapping of special keys found on many keyboards has been covered a few times.  Here's my version which is intended to be a quick and easy solution.  Enjoy those fancy keyboards!

MY FILE: /usr/share/hotkey-setup/generic.hk
# Special key bindings via /usr/share/hotkey-setup/generic.hk
# Kernel key mappings for special keys can be set in this file
#
# STEP 1 - FIND SCANCODES 
# When an unmapped special keys is pressed a message is written
# to /var/log/messages which indicates the "scancode".
# To find the scancode for an unmapped special key press the key
# then check /var/log/messages.
#
# STEP 2 - FIND UNUSED KEYCODES
# use "$ sudo dumpkeys" to find unused keycodes
# example of unused keycode: "keycode 120 ="
# 
# STEP 3 - MAP SCANCODE TO KEYCODE
# format = setkeycodes scancode keycode
# example "setkeycodes e02a 120"
# add each mapping entry to this file
#
# STEP 4 - RESTART HOTKEY-SETUP
# after edit restarting the hotkey-setup service by:
# $ sudo /etc/init.d/hotkey-setup restart
#
# STEP 5 - MAP KEYCODE TO ACTION
# X11 mapping can be done with gnome-keybinding-properties
# which is System > Preferences > Keyboard Shortcuts
#
#
setkeycodes e02a 120      # gnome-keybinding-properties "Lock screen"
setkeycodes e023 121      # gnome-keybinding-properties "Home folder"
setkeycodes e015 122      # gnome-keybinding-properties "Launch help browser"
setkeycodes e026 123      # gnome-keybinding-properties "Launch calculator"
setkeycodes e06e 124      # gnome-keybinding-properties "Launch web browser"

---

### Post by yoramdavid on 2008-11-25
Hello,

That would be very nice although before I ad a program where I could choose my keyboard make and model and it would recognize all my hotkeys. But I cannot remember the name of this package...
So I was doing what you suggested but got an error on setting a keycode to an unused key, ie: setkeycodes e073 85
and got this error: [Couldnt get a file descriptor referring to the console]

Any idiea why?

Yoram

---

### Post by linfidel on 2008-12-23
> **yoramdavid said:**
> Hello,

That would be very nice although before I ad a program where I could choose my keyboard make and model and it would recognize all my hotkeys. But I cannot remember the name of this package...
So I was doing what you suggested but got an error on setting a keycode to an unused key, ie: setkeycodes e073 85
and got this error: [Couldnt get a file descriptor referring to the console]

Any idiea why?

Yoram
A little late, but always try "sudo setkeycodes..." when something like this doesn't work.  That error is what you would get without "sudo".

---

### Post by yoramdavid on 2008-12-25
> **linfidel said:**
> A little late, but always try "sudo setkeycodes..." when something like this doesn't work.  That error is what you would get without "sudo".

Thank you.

Late but I will try since the problem is not yet solved.
I found the program I used before (keyTouch) but it does not work like before. I think I have tried so many different things that the keys must be assigned by something else and conflict.
I also used XbindKes....
I have tried uninstalling them all and reinstalling only one, but the settings are still there messed up somewhere...

Regards,

---

