---
title: "Think I have broke my Ubuntu 12.10"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by maxalman on 2013-03-01
Hi, I have a Dell Inspiron laptop dual booting Windows XP & Ubuntu 12.10. The other day I did a update for Ubuntu 12.10 and after a restart I lost my Unity panel, all I had was my screensaver. I then tried to do a restore using Ubuntu one but I found I couldn't connect to the internet so I checked my network in settings and it showed I was connected to my router. So after doing some research on the internet I tried to reinstall Unity and my internet, anyway it's all gone pear shaped now. After doing a restart all I have now is a black screen with a log in option. After logging in it appears as if I am in a terminal screen/mode, just like when I did Ctrl Alt T gives you, but this time the whole screen is a terminal.
Can anyone help me please this is doing my head in.

Thanks for reading, Alan

---

### Post by Gone fishing on 2013-03-01
I would think that sudo apt-get install --reinstall ubuntu-desktop will get your desktop back. Obviously you will need to be connected to the net but I if you connect to your router using a cable when you start up it should get an address etc and be connected to the net.

---

### Post by maxalman on 2013-03-01
> **Gone fishing said:**
> I would think that sudo apt-get install --reinstall ubuntu-desktop will get your desktop back. Obviously you will need to be connected to the net but I if you connect to your router using a cable when you start up it should get an address etc and be connected to the net.

Thanks, I will give that a try when I get home from work.

---

### Post by wojox on 2013-03-01
Try starting x server and see if their are any errors.
```
sudo service lightdm start
```

---

### Post by maxalman on 2013-03-01
> **wojox said:**
> Try starting x server and see if their are any errors.
```
sudo service lightdm start
```

Thanks I will try this also.

---

### Post by unelement on 2013-03-01
Same problem here, no problem starting X, I think that what is broke is OpenGL, which got updated yesterday, so Unity (or Gnome Shell) won't start, Gnome classic works OK. Also Ubuntu session doesn't fall back to Unity 2D.

From within a ubuntu session if I try to start Unity I get this output:

```
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
unity-panel-service: no process found
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
Xlib:  extension "GLX" missing on display ":0".
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Error: Plugin initScreen failed: opengl
compiz (core) - Error: Failed to start plugin: opengl
compiz (core) - Info: Unloading plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Error: Plugin 'opengl' not loaded.

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
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: wall
compiz (core) - Error: Failed to start plugin: wall
compiz (core) - Info: Unloading plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: animation
compiz (core) - Error: Failed to start plugin: animation
compiz (core) - Info: Unloading plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: fade
compiz (core) - Error: Failed to start plugin: fade
compiz (core) - Info: Unloading plugin: fade
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: unitymtgrabhandles
compiz (core) - Error: Failed to start plugin: unitymtgrabhandles
compiz (core) - Info: Unloading plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Error: Plugin 'opengl' not loaded.

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: scale
compiz (core) - Error: Failed to start plugin: scale
compiz (core) - Info: Unloading plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: expo
compiz (core) - Error: Failed to start plugin: expo
compiz (core) - Info: Unloading plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: ezoom
compiz (core) - Error: Failed to start plugin: ezoom
compiz (core) - Info: Unloading plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: unityshell
compiz (core) - Error: Failed to start plugin: unityshell
compiz (core) - Info: Unloading plugin: unityshell
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Stopping plugin: workarounds
compiz (core) - Info: Unloading plugin: workarounds
compiz (core) - Info: Stopping plugin: gnomecompat
compiz (core) - Info: Unloading plugin: gnomecompat
compiz (core) - Info: Stopping plugin: session
compiz (core) - Info: Unloading plugin: session
compiz (core) - Info: Stopping plugin: imgpng
compiz (core) - Info: Unloading plugin: imgpng
compiz (core) - Info: Stopping plugin: regex
compiz (core) - Info: Unloading plugin: regex
compiz (core) - Info: Stopping plugin: grid
compiz (core) - Info: Unloading plugin: grid
compiz (core) - Info: Stopping plugin: move
compiz (core) - Info: Unloading plugin: move
compiz (core) - Info: Stopping plugin: place
compiz (core) - Info: Unloading plugin: place
compiz (core) - Info: Stopping plugin: resize
compiz (core) - Info: Unloading plugin: resize
compiz (core) - Info: Stopping plugin: mousepoll
compiz (core) - Info: Unloading plugin: mousepoll
compiz (core) - Info: Stopping plugin: snap
compiz (core) - Info: Unloading plugin: snap
compiz (core) - Info: Stopping plugin: vpswitch
compiz (core) - Info: Unloading plugin: vpswitch
compiz (core) - Info: Stopping plugin: decor
compiz (core) - Info: Unloading plugin: decor
compiz (core) - Info: Stopping plugin: compiztoolbox
compiz (core) - Info: Unloading plugin: compiztoolbox
compiz (core) - Info: Stopping plugin: composite
compiz (core) - Info: Unloading plugin: composite
compiz (core) - Info: Stopping plugin: ccp
compiz (core) - Info: Unloading plugin: ccp
compiz (core) - Info: Stopping plugin: core
compiz (core) - Info: Unloading plugin: core

(process:10681): GLib-WARNING **: /build/buildd/glib2.0-2.34.1/./glib/gmain.c:1817: ref_count == 0, but source was still attached to a context!
```

Any help much appreciated!

---

### Post by maxalman on 2013-03-01
I installed Ubuntu 12.10 using a usb stick, can I reinstall Ubuntu 12.10 the same way if nothing else works?

---

### Post by maxalman on 2013-03-01
> **Gone fishing said:**
> I would think that sudo apt-get install --reinstall ubuntu-desktop will get your desktop back. Obviously you will need to be connected to the net but I if you connect to your router using a cable when you start up it should get an address etc and be connected to the net.

Tried what you  said but it didn't work. can I reinstall Ubuntu the same way I installed it via a usb stick,

---

### Post by Bashing-om on 2013-03-01
maxalman;
(re)installing is a drastic solution, but yes if all else fails is doable.
Here though is the how-to to reset the desktop in version 12.10:
[URL="http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html"]http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html
[/URL][INDENT=2][URL="http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html"]hth

[/URL]
[/INDENT]

---

### Post by maxalman on 2013-03-01
> **Bashing-om said:**
> maxalman;
(re)installing is a drastic solution, but yes if all else fails is doable.
Here though is the how-to to reset the desktop in version 12.10:
[URL="http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html"]http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html
[/URL][INDENT=2][URL="http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html"]hth

[/URL]
[/INDENT]


Just tried that and it didn't work this is the reply I got,
cannot access ppa (htpps://launchpad.net/apii/01/~amith/xarchive/ubuntutools)to get paa info, please check your internet connection.

---

### Post by Bashing-om on 2013-03-01
maxalman;
Just a matter of fixing your desk top, (re)installing should be considedered a last resort (unless one had absolutely nothing to loose/no data to save).

On that link is two methods// I also do not subscribe to adding PPA's to my system. The second method is my recomendation.

The first method requires that the PPA be added to the source.list file to obtain a script that will enabale an "implication" of "unity --reset"// I do not abscribe to adultriating my system files thus the second method is recommended.
[INDENT=3]try'n to help

[/INDENT]

---

### Post by maxalman on 2013-03-01
> **Bashing-om said:**
> maxalman;
Just a matter of fixing your desk top, (re)installing should be considedered a last resort (unless one had absolutely nothing to loose/no data to save).

On that link is two methods// I also do not subscribe to adding PPA's to my system. The second method is my recomendation.

The first method requires that the PPA be added to the source.list file to obtain a script that will enabale an "implication" of "unity --reset"// I do not abscribe to adultriating my system files thus the second method is recommended.[INDENT=3]try'n to help

[/INDENT]


Thanks for your help, but I tried the second method and that didn't work either, I did the first stage ok but when I did the second stage, deconf reset -f /org/compiz/ 
this is what I got error spawning command line dbus --launch --autolaunch:a6140999735897661f4cb23c50ebfd83--binary-syntax --close-stderr':child process exited with code 1
Also I really don't mind doing a reinstall as I have nothing to loose I keep everthing on windows xp. My only concern is I am dual boot and I don't want to loose my windows xp, and I would need some guidence in how to reinstall safetly

---

### Post by Bashing-om on 2013-03-01
maxalman;

Yes, one may (re)install and if the same username and password is utilized, current configs and setting MIGHT be retained.

I have not seen the 12.10 version, but the process, I imagine, is the same as from older versions.

In terminal identify all current partitions:
```
sudo fdisk -l
```
Then in the installer choose the option of "something else" keeping in mind what partitions Windows has (ntfs formatted partitions)// Point the installer to install on the partitions that were ubuntu (ext4 format).
For your comfort, in the installer's final stage is an advisory for what it is going to do, nothing is changed to this time. Once you look at this advisory and tell the installer to go ahead and install it is done as per that advisory.
In this manner Windows is not touched, and the install proceedure will pick up Window's as an operating system and chainload it's booloader onto grub. 

(re)installing is a sledgehammer approach, but is certainly effective.
Your current desk top is fixable with some time and effort - might be additive to the learning curve.
If you are still unsure, by all means we will help. Post back to us -between code tags for readability- the output of the "fdisk" command to proceed with (re)installing.[INDENT=3]try'n to help

[/INDENT]

---

### Post by maxalman on 2013-03-02
> **Bashing-om said:**
> maxalman;

Yes, one may (re)install and if the same username and password is utilized, current configs and setting MIGHT be retained.

I have not seen the 12.10 version, but the process, I imagine, is the same as from older versions.

In terminal identify all current partitions:
```
sudo fdisk -l
```
Then in the installer choose the option of "something else" keeping in mind what partitions Windows has (ntfs formatted partitions)// Point the installer to install on the partitions that were ubuntu (ext4 format).
For your comfort, in the installer's final stage is an advisory for what it is going to do, nothing is changed to this time. Once you look at this advisory and tell the installer to go ahead and install it is done as per that advisory.
In this manner Windows is not touched, and the install proceedure will pick up Window's as an operating system and chainload it's booloader onto grub. 

(re)installing is a sledgehammer approach, but is certainly effective.
Your current desk top is fixable with some time and effort - might be additive to the learning curve.
If you are still unsure, by all means we will help. Post back to us -between code tags for readability- the output of the "fdisk" command to proceed with (re)installing.[INDENT=3]try'n to help

[/INDENT]


Good morning, I have just done a reinstall and every thing is working ok now.

Thanks for all your help it was very helpful.

Alan

---

### Post by Bashing-om on 2013-03-02
maxalman;

Pleased that you have resolution to your satisfaction. Glad to be of small assit.

Please mark this thread as "solved"; it aids others seeking solutiuons and others time not looking at a solved situation.
[INDENT=4]

enjoy ubuntu

[/INDENT]

---

### Post by maxalman on 2013-03-02
> **maxalman said:**
> Tried what you said but it didn't work. can I reinstall Ubuntu the same way I installed it via a usb stick,

> **Bashing-om said:**
> maxalman;

Pleased that you have resolution to your satisfaction. Glad to be of small assit.

Please mark this thread as "solved"; it aids others seeking solutiuons and others time not looking at a solved situation.[INDENT=4]

enjoy ubuntu

[/INDENT]


Sorry I don't know how to mark as solved.

---

### Post by Bashing-om on 2013-03-02
maxalman;
My failure. see if the option to mark as "solved" is not an option in "thread tools" at the top of the post.
[INDENT=3]

regards

[/INDENT]

---

### Post by maxalman on 2013-03-02
> **Bashing-om said:**
> maxalman;
My failure. see if the option to mark as "solved" is not an option in "thread tools" at the top of the post.[INDENT=3]

regards

[/INDENT]


Tried looking there first but I don't seem to have that option.

---

### Post by Bashing-om on 2013-03-02
oops; There exist a bug in the current update. Work-a -round here;
[http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

Thanks for your patience and consideration !

---

### Post by maxalman on 2013-03-02
> **Bashing-om said:**
> oops; There exist a bug in the current update. Work-a -round here;
[http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

Thanks for your patience and consideration !

I can't find the option to edit the prefix in the advanced mode.

---

### Post by coffeecat on 2013-03-02
@maxalman, have another look in the advanced editor for future reference. The prefix field is there. I've marked this thread as solved for you.

---

