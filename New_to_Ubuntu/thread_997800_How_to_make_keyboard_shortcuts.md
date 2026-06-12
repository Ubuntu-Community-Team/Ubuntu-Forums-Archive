---
title: "How to make keyboard shortcuts?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by Ghaban on 2008-11-30
Hi everyone, i as wondering if i can make custom keyboard shortcuts to any application i want? for example i would like xchat to start if i press let's say ctrl+alt+x.

Ghaban

---

### Post by muted1987 on 2008-11-30
goto system preferences keyboard shortcuts

---

### Post by Elfy on 2008-11-30
Do Alt+F2 then run gconf-editor in ubuntu - no idea about kub or xub

Navigate to /apps/metacity - you need to be working on
global_keybindings
keybindings_commands

In global_keybindings in for instance run_command_1 set the key sequence, double click in right hand pane = I use the calculator button so have XF86Calculator, then OK

In keybindings_commands - command_1 to match run_command_1, double click and put the command to run - I have /usr/bin/xchat to run xchat, Ok 

Close gconf_editor and it should work.

Be aware that iof you are using compiz it's likely that there is already a shortcut :)

---

### Post by Ghaban on 2008-11-30
> **muted1987 said:**
> goto system preferences keyboard shortcuts

You can't make shortcuts for any application in there.

---

### Post by Ghaban on 2008-11-30
> **forestpixie said:**
> Do Alt+F2 then run gconf-editor in ubuntu - no idea about kub or xub

Navigate to /apps/metacity - you need to be working on
global_keybindings
keybindings_commands

In global_keybindings in for instance run_command_1 set the key sequence, double click in right hand pane = I use the calculator button so have XF86Calculator, then OK

In keybindings_commands - command_1 to match run_command_1, double click and put the command to run - I have /usr/bin/xchat to run xchat, Ok 

Close gconf_editor and it should work.

Be aware that iof you are using compiz it's likely that there is already a shortcut :)

cool, that really helped me out a lot =)
Don't use that much on compiz, just some effects.

---

