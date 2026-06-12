---
title: "Vlc"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-04-29
I tried to install a skin downloaded from VLC website. After that VLC is not starting.
if i type vlc in terminal it gives the following error

vlc
VLC media player 1.1.12 The Luggage (revision exported)
Warning: call to srand(1335672635)
Warning: call to rand()
Blocked: call to setlocale(6, "")
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Blocked: call to setlocale(6, "")

(process:3250): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to rand()
Warning: call to srand(1335672635)
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
[0x9f49aec] skins2 interface: skin: subX  author: Martin Poehlmann
[0xa0fcbd4] qt4 generic error: cannot start Qt4 multiple times
[0xa10020c] skins2 interface error: no suitable dialogs provider found (hint: compile the qt4 plugin, and make sure it is loaded properly)
[0xa10020c] skins2 interface error: cannot instanciate qt4 dialogs provider


I did a COMPLETE removal of VLC a few times. Deteled any folder named vlc, emptied thrash, and restarted the comp and reinstalled vlc but still there is the same problem.

Can any one help.


.

---

### Post by lovinglinux on 2012-04-29
Delete the folder ~/.config/vlc/

You can find it under your home folder. You need to show hidden files to see it. You can do that by hitting CTRL+H.

You should be able to start VLC after that. Keep in mind it will reset all your VLC seetings.

---

### Post by mc4man on 2012-04-29
The other option is to start vlc in the default qt interface & then open  Tools > Preferences, "Use Native Style" or otherwise fix

```
vlc -Iqt4
```

---

### Post by lovinglinux on 2012-04-29
> **mc4man said:**
> The other option is to start vlc in the default qt interface & then open  Tools > Preferences, "Use Native Style" or otherwise fix

```
vlc -Iqt4
```

A better option.

---

### Post by 3dmatrix on 2012-04-29
Thanx every one there are a couple of problems - mainly related to skins !

(1) i dont see a list of skins and cant swap them easily
(2) every time i change the skin it works for some time till i change the skin and then it crashes again and i have to delete the config folder to get it back even vlc -Iqt4 command cannot bring it back.

vlc -Iqt4
VLC media player 1.1.12 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to srand(1335679396)
Warning: call to rand()
Blocked: call to setlocale(6, "")
Blocked: call to setlocale(6, "")

(process:10964): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to rand()
Warning: call to srand(1335679397)
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
[0x9cea64c] skins2 interface: skin: WinAMP 5  author: 
[0x9e83efc] qt4 interface error: cannot start Qt4 multiple times
[0x9e83efc] main interface error: no suitable interface module
[0x9c58174] main libvlc error: interface "default" initialization failed

(3) when i use any skin in full screen mode i find a window of the original size or the interface panel still present.

(4) when the vlc player is playing and i minimize it then the only way to bring it back is to use ALT+TAB as i do not see it in the list of area where all the windows are displayed by bringing the mouse pointer to WINDOWS APPLICATION area. This happens only if i install any skin else after deleting the config folder there is no prob.

I have not copied the skins to any vlc folder rather i am browsing it every time and selecting it from my custom folder.



.

---

### Post by lovinglinux on 2012-04-29
I have tried many skins myself and ended using the default skin for the same reasons you have created this thread. My advice...don't use skins.

---

### Post by 3dmatrix on 2012-04-29
Yes i have also returned back to the default skin.
I would love to use some nice skin but not with so much hassel.
Its strange that it works some times not on other occasions.
Buggyyyyyy !

---

### Post by mc4man on 2012-04-29
Interesting that -Iqt4 failed you, possibly vlc was still running after crashing

Anyway, just a point
Vlc uses interfaces, not skins. The default & most feature rich interface is the qt4 one
An alternate interface is the skins2 one. Whether any of the available skins for that interface work is 50 -50.  They need to be compatible with the version of vlc you have & there could be other factors.

The skins interface & skin used generally don't have all the controls available in the qt interface

---

### Post by 3dmatrix on 2012-04-29
> **mc4man said:**
> Interesting that -Iqt4 failed you, possibly vlc was still running after crashing

Anyway, just a point
Vlc uses interfaces, not skins. The default & most feature rich interface is the qt4 one
An alternate interface is the skins2 one. Whether any of the available skins for that interface work is 50 -50.  They need to be compatible with the version of vlc you have & there could be other factors.

The skins interface & skin used generally don't have all the controls available in the qt interface

How and where do i get tht Qt4 interface ?

---

### Post by LuigiAntoniol on 2012-08-20
> **lovinglinux said:**
> Delete the folder ~/.config/vlc/

You can find it under your home folder. You need to show hidden files to see it. You can do that by hitting CTRL+H.

You should be able to start VLC after that. Keep in mind it will reset all your VLC seetings.

Sorry to cause a diversion in this thread, but the solution you put forward has solved a completely different problem for me:
Clicking on Tools > Effects and Filters crashed VLC
Clicking on Tools > Track Synchronisation crashed VLC

After deleting that config folder, VLC no longer crashes when I use those two options in the menu.

Thank you, you have saved me from getting more grey hairs.:guitar:

---

### Post by lovinglinux on 2012-08-21
> **LuigiAntoniol said:**
> Sorry to cause a diversion in this thread, but the solution you put forward has solved a completely different problem for me:
Clicking on Tools > Effects and Filters crashed VLC
Clicking on Tools > Track Synchronisation crashed VLC

After deleting that config folder, VLC no longer crashes when I use those two options in the menu.

Thank you, you have saved me from getting more grey hairs.:guitar:

You are welcome.

Is track Sync working well for you? It works fine here, but changing values makes the movie freeze sometimes.

---

### Post by geoffree on 2012-08-24
My problem with VLC was that it crashed whenever I tried to open the advanced functions.  Deleting /,config/vlc changed all that enabling the program to start with correct color and value and with ability to use functions. 
Question: Why?

Thanks.

---

