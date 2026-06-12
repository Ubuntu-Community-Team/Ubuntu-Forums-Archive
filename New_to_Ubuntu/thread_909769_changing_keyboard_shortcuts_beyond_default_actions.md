---
title: "changing keyboard shortcuts beyond default actions?"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by treehouse on 2008-09-03
System>Preferences>Keyboard Shortcuts presents me with a list of global shortcuts to define. It's really limited, however. In order to get Guake hotkeyed, I had to switch over and define it in the preferred applications. I can't create my own actions to hotkey. For instance, I would like to create a shortcut that executes 'mpc next'. I also don't get how I have auto-assigned hotkeys on my media keys. I can assign my media next key to the CD next action in the Keyboard Shortcuts menu, but it comes up as 'XF86Calculator', which appears to be some prior assignment, so if I try to use that key, it opens the default calculator. I'm really lost.

---

### Post by Diabolis on 2008-09-03
To make custom key shortcuts in gnome, you have to modify 2 values for each key shortcut. Press <Alt><F2> and execute **gconf-editor**. Look for this options:

[B]/apps/metacity/global_keybindings/

/apps/metacity/keybinding_commands/[/B]

An example of how to bind the execution of  command to a key combination can be found here:
[http://ubuntuforums.org/showthread.php?t=781345&highlight=dmenu+gnome](http://ubuntuforums.org/showthread.php?t=781345&highlight=dmenu+gnome)

---

### Post by treehouse on 2008-09-03
Thank you very much.

I still don't get how to configure my media keys. I don't understand why it shows up as 'XF86something' and automatically does what the name states or how I change it.

---

### Post by treehouse on 2008-09-03
Okay, I figured it out. The keyboard shortcuts menu was using the hex value of the media keys to open the default calculator, and I doubled it, but when it grabbed the key, it named it differently. The metacity dealy was working okay, but I found a solution I liked better since I don't know the names of all the media keys (some are very non-intuitive): xbindkeys and xbindkeys-config. I just deleted everything out of the default gnome keyboard shortcuts dialog.

I'm looking for a safe way to get rid of the default keyboard shortcuts dialog as I no longer need it, and I imagine its taking up resources by waiting for keys to be pressed.

---

