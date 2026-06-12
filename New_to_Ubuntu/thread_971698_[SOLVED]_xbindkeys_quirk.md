---
title: "[SOLVED] xbindkeys quirk"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-11-05
Since installing Intrepid my xbindkeys has been acting funny. everything works except one command: nautilus.

I have bound 
```
"nautilus"
    m:0x8 + c:24
    Alt + q

```
 and I've tried other bindings as well. If I run xbindkeys-config and hit the apply button then save,apply,and exit button it will work. But I have to open xbindkeys-config everytime I login and repeat the process or this keybinding (for nautilus only mind you) won't work. It is loading the proper config file because when I type ```
xbindkeys -s
``` I get the proper configuration, but I still have to open xbindkeys-config and hit apply each login or it will forget or something.

---

### Post by JohnGalt131 on 2008-11-05
I saved the current file as default then just had it open the default instead of a specific file and that worked.

---

### Post by caecus314 on 2008-11-15
I've been having the exact same problem with xbindkeys.

Here's the important part of my .xbindkeysrc file:
> 
#Nautilus
"nautilus"
   Mod4 + E

#Firefox
"firefox"
   Mod4 + I

#Gedit
"gedit"
   Mod4 + N

#Terminal
"gnome-terminal"
   Mod4 + T

#Synaptic
"gksu /usr/sbin/synaptic"
   Mod4 + P

#OooWriter
"ooffice -writer"
   Mod4 + W

#Brasero
"brasero"
   Mod4 + 3

#Exaile
"exaile"
   Mod4 + J

#Pidgin
"pidgin"
   Mod4 + G

#Gimp
"gimp"
   Mod4 + M

I set up xbindkeys to run automatically using System -> Preferences -> Sessions.  I added an entry for xbindkeys and had it run the command 'xbindkeys'.  At startup, xbindkeys runs automatically and everything works perfectly... except for the Nautilus shortcut.  I tried changing the shortcut to a different key combination, but it didn't work either.  As far as I can tell, the only way to get the shortcut to work is to start up xbindkeys-config and hit "Apply".

How did you get the Nautilus shortcut to work exactly?  My xbindkeys is already using the default config file.

---

### Post by JohnGalt131 on 2008-11-16
> **caecus314 said:**
> I've been having the exact same problem with xbindkeys.

Here's the important part of my .xbindkeysrc file:


I set up xbindkeys to run automatically using System -> Preferences -> Sessions.  I added an entry for xbindkeys and had it run the command 'xbindkeys'.  At startup, xbindkeys runs automatically and everything works perfectly... except for the Nautilus shortcut.  I tried changing the shortcut to a different key combination, but it didn't work either.  As far as I can tell, the only way to get the shortcut to work is to start up xbindkeys-config and hit "Apply".

How did you get the Nautilus shortcut to work exactly?  My xbindkeys is already using the default config file.

Sorry. False alarm. It still does not work the way it should.

---

### Post by brntoki on 2009-05-25
I'd like an answer as well.  Nautilus simply doesn't want to launch from any xbindkey method.

---

