---
title: "'Empty' desktop after i installed nvidia drivers, no window borders and such"
date: 2013-09-12
forum: New to Ubuntu
---

### Post by gremious on 2013-09-12
I have seen that there are already forums about this problems but alas, they didn't help me. I installed the Nvidia drivers(Nvidia-current) on Ubuntu 13.4(witch was working quite nicely before that but i needed the drivers so a certain game would run without crashing on me, since that's what the forums said i needed to do.),and after reboot i come to an empty desktop, no side bar launcher thingy, "start menu" or anything, as well as my borders of my windows are gone, and from what i've searched, i believe basically Unity isn't running. Luckuly enough i could right click-create a new folder and i searched for mozzila to get here. 
I tried to purge unninstall nvidia and nvidia current , and they did unninstall, then reboot, but it didn't fix anything.
Tried to launch the unitiy, (though ccsm i belive) witch made a big load of pop ups that other programs are not running as well, and after enabling averything...nothing happened. Reboot after that didn't work ether.
Reinstall nvidia current back didn't help.
Don't remeber if i did anyhting apart from that, i've been at this for quite a while now
So, if anyone can help me, that would be very appreciated ^^

---

### Post by Jonathan Precise on 2013-09-12
Try running this in a terminal (Ctrl. - Alt. - T):

```
unity
```

Post any errors here.

---

### Post by gremious on 2013-09-12
> **Jonathan Precise said:**
> Try running this in a terminal (Ctrl. - Alt. - T):

```
unity
```

Post any errors here.

Done, this is what came in:

compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
unity-panel-service: no process found
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Error: Plugin 'opengl' not loaded.

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
 
---
aaand, 
"Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0"
just keeps on continuing to appear. And then it was killed.

---

### Post by Jonathan Precise on 2013-09-12
Please post errors with code tags:

(code)Compositing isn't available(/code)

Replace parenthesis with brackets:

```
Compositing isn't available
```

As for the unity problem, looks like the driver you have does not support effects (thus why the errors say compositing isn't available; compositing=effects).
Looks like you are running ubuntu 12.10 or 13.04 (unity plug-in in compiz). If you have 13.04 then in a terminal, type:

```
software-properties-gtk
```

Wait......................................................................................................................................................
Once it shows up, go to the "Additional Drivers" tab, and choose the open-source driver. Apply the changes. Then in the terminal, type:

```
gnome-session-quit --power-off
```

Choose restart. If nothing appears, then:

```
sudo reboot
```

Enter password. If the PC freezes during restart, press and hold the power-button, as the system is already halted:

[IMG]http://popey.com/blog/wp-content/uploads/2010/03/boot.png[/IMG]

Wait..............

Problem solved! Should anything happen (any error message), please post them here with code tags.

---

### Post by gremious on 2013-09-12
As much as i'd love to click the install button on that driver that fixes everything..there is nothing there. When i open up the additional drivers tab, it is empty.
At the bottom, it says "No proprietery drivers are in use".

```
 Also, this is just a little test to see if i get it right. 
```

---

### Post by Jonathan Precise on 2013-09-12
> **gremious said:**
> As much as i'd love to click the install button on that driver that fixes everything..there is nothing there. When i open up the additional drivers tab, it is empty.
At the bottom, it says "No proprietery drivers are in use".

```
 Also, this is just a little test to see if i get it right. 
```

```
Yes, you have it right ;)!
*********************************
YIKES!!!!!!!!!!!!!!!
Try:

[CODE]sudo apt-get install xserver-xorg-video-ati && gnome-session-quit --power-off
```

installs open-source driver and shows the reboot dialog to reboot.
[INDENT]Hope this fixes it![/INDENT]
[/CODE]

---

### Post by gremious on 2013-09-12
Did it! and, 
Sorry to dissapoint you, but i'm an unlucky person ^^
Yeah, it Didn't work, also, i do believe it said that i already have that driver at the latest version. I copied the code without the reboot thingie, and i do believe this is exactly what it said the first time:
```

xserver-xorg-video-ati is already the newest version.
The following package was automatically installed and is no longer required:
  libvdpau1
Use 'apt-get autoremove' to remove it.


```

---

### Post by Jonathan Precise on 2013-09-12
> **gremious said:**
> Did it! and, 
Sorry to dissapoint you, but i'm an unlucky person :(
Yeah, it Didn't work, also, i do believe it said that i already have that driver at the latest version. I copied the code without the reboot thingie, and i do believe this is exactly what it said the first time:
```

xserver-xorg-video-ati is already the newest version.
The following package was automatically installed and is no longer required:
  libvdpau1
Use 'apt-get autoremove' to remove it.


```
===Read Everything before preforming===

Try:

```
sudo apt-get remove nvidia-current
```

If you get a black screen, press the power-button. Wait a couple of minutes...

Start the PC. Black-screen again, then choose "recovery mode" and FailSafeX.

Still get a black screen, make an ubuntu Live DVD and re-install (remember to not change the graphics driver). Copy everything you need to a USB (as files in the live media and files in the partition will get ERASED).
============================

---

### Post by buzzingrobot on 2013-09-12
If your machine has two video cards, as do many laptops,  the "discrete" Nvidia card will be invisible until it is enabled in the BIOS.  If you are using such a machine, make sure the Nvidia is enabled, then see what "Additional Drivers" says.

---

### Post by gremious on 2013-09-12
> **Jonathan Precise said:**
> ===Read Everything before preforming===

Try:

```
sudo apt-get remove nvidia-current
```

If you get a black screen, press the power-button. Wait a couple of minutes...

Start the PC. Black-screen again, then choose "recovery mode" and FailSafeX.

Still get a black screen, make an ubuntu Live DVD and re-install (remember to not change the graphics driver). Copy everything you need to a USB (as files in the live media and files in the partition will get ERASED).
============================
But i neeeeed an updated nvidia driver D: ..[SIZE=1]i think[/SIZE] 
removing nvidia current fixed nothing.
So i restarted in recovery mode, and after selecting failSafeX, it gives me an option to start in low graphics, something esle or quit and such, however, i cannot selct any mode. I don't have a cursor there and keyboard does nothing. Any help with that? Since i don't really want to reinstal unless it's the only thing possible.

---

### Post by gremious on 2013-09-12
> **buzzingrobot said:**
> If your machine has two video cards, as do many laptops,  the "discrete" Nvidia card will be invisible until it is enabled in the BIOS.  If you are using such a machine, make sure the Nvidia is enabled, then see what "Additional Drivers" says.

Hmm, nope, I don't believe i have two video cards!

---

### Post by buzzingrobot on 2013-09-12
> **gremious said:**
> Hmm, nope, I don't believe i have two video cards!

Is it a laptop? If not, what is the motherboard?

Reinstalling is often the quickest route to ixing these issues.  It's difficult to completely remove the detritus of a broken driver install before you move on to try something else.

---

### Post by gremious on 2013-09-12
> **buzzingrobot said:**
> Is it a laptop? If not, what is the motherboard?

Reinstalling is often the quickest route to ixing these issues.  It's difficult to completely remove the detritus of a broken driver install before you move on to try something else.

Yeah, and that's what i just did. Apparently my computer hates Nvidia drivers with linux then >~>
Guess i'll start anew. 
Really do wish i could use a new nvidia driver, i do like gaming so it's sorta a must, but i guess i'll have to figure out a way arround it. Probably install windows for a dual boot, just for gaming purpous.
---
Anyways, to both of ya, thank you!
*Hugs*

---

