---
title: "No unity 12.10 tried multiple fixes."
date: 2013-03-02
forum: New to Ubuntu
---

### Post by dedpossum on 2013-03-02
I am working under the assumption that this is a display issue.  I have gone through quite a few steps including multiple fresh installations.  I have a dell dimension 8300.  It apparently has an ATI card.  I followed the directions to purge and reset unity, purge and reset my vid card drivers and i still get this message.   I am able to right click, opens files, even create a word doc.   I can see my other computers on my network, but I cannot pull up a browers.  I have spent approximately 6 hours trying to resolve this and am hitting a wall.  Here is the error message I get when I try and do a unity-reset:

```
Schema org.compiz.session successfully reset

Schema org.compiz.scaleaddon successfully reset

Schema org.compiz.core successfully reset

Schema org.compiz.clone successfully reset

Schema org.compiz.ring successfully reset

Schema org.compiz.scale successfully reset

Schema org.compiz.composite successfully reset

Schema org.compiz.screenshot successfully reset

Schema org.compiz.mblur successfully reset

Schema org.compiz.workarounds successfully reset

Schema org.compiz.animation successfully reset

Schema org.compiz.shift successfully reset

Schema org.compiz.winrules successfully reset

Schema org.compiz.opengl successfully reset

Schema org.compiz.water successfully reset

Schema org.compiz.fade successfully reset

Schema org.compiz.mousepoll successfully reset

Schema org.compiz.gnomecompat successfully reset

Schema org.compiz.grid successfully reset

Schema org.compiz.shelf successfully reset

Schema org.compiz.unitydialog successfully reset

Schema org.compiz.opacify successfully reset

Schema org.compiz.obs successfully reset

Schema org.compiz.cube successfully reset

Schema org.compiz.annotate successfully reset

Schema org.compiz.maximumize successfully reset

Schema org.compiz.staticswitcher successfully reset

Schema org.compiz.kdecompat successfully reset

Schema org.compiz.firepaint successfully reset

Schema org.compiz.trailfocus successfully reset

Schema org.compiz.resize successfully reset

Schema org.compiz.splash successfully reset

Schema org.compiz.neg successfully reset

Schema org.compiz.profile successfully reset

Schema org.compiz.wobbly successfully reset

Schema org.compiz.unityshell successfully reset

Schema org.compiz.extrawm successfully reset

Schema org.compiz.switcher successfully reset

Schema org.compiz.titleinfo successfully reset

Schema org.compiz.place successfully reset

Schema org.compiz.snap successfully reset

Schema org.compiz.scalefilter successfully reset

Schema org.compiz.resizeinfo successfully reset

Schema org.compiz.vpswitch successfully reset

Schema org.compiz.commands successfully reset

Schema org.compiz.widget successfully reset

Schema org.compiz.decor successfully reset

Schema org.compiz.showdesktop successfully reset

Schema org.compiz.expo successfully reset

Schema org.compiz.addhelper successfully reset

Schema org.compiz.rotate successfully reset

Schema org.compiz.td successfully reset

Schema org.compiz.move successfully reset

Schema org.compiz.crashhandler successfully reset

Schema org.compiz.imgsvg successfully reset

Schema org.compiz.mag successfully reset

Schema org.compiz.put successfully reset

Schema org.compiz.ezoom successfully reset

Schema org.compiz.wall successfully reset

Schema org.compiz.showrepaint successfully reset

Schema org.compiz.imgjpeg successfully reset

Schema org.compiz.notification successfully reset

Schema org.compiz.bench successfully reset

Schema org.compiz.networkarearegion successfully reset

Schema org.compiz.workspacenames successfully reset

Schema org.compiz.fadedesktop successfully reset

Schema org.compiz.showmouse successfully reset

Schema org.compiz.unitymtgrabhandles successfully reset

Schema com.canonical.Unity.Dash successfully reset

Schema com.canonical.Unity successfully reset

Schema com.canonical.Unity.FilesLens successfully reset

Schema com.canonical.Unity.Runner successfully reset

Schema com.canonical.Unity.Devices successfully reset

Schema com.canonical.Unity.ApplicationsLens successfully reset

Schema com.canonical.Unity.Panel successfully reset

unity-panel-service: no process found

compiz (core) - Info: Loading plugin: core

compiz (core) - Info: Starting plugin: core

compiz (core) - Info: Loading plugin: ccp

compiz (core) - Info: Starting plugin: ccp

compizconfig - Info: Backend     : gsettings

compizconfig - Info: Integration : true

compizconfig - Info: Profile     : unity

compiz (core) - Info: Loading plugin: composite

compiz (core) - Info: Starting plugin: composite

compiz (core) - Info: Loading plugin: opengl

X Error of failed request:  BadRequest (invalid request code or no such operation)

  Major opcode of failed request:  135 (GLX)

  Minor opcode of failed request:  19 (X_GLXQueryServerString)

  Serial number of failed request:  22

  Current serial number in output stream:  22

compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).

X Error of failed request:  BadRequest (invalid request code or no such operation)

  Major opcode of failed request:  135 (GLX)

  Minor opcode of failed request:  19 (X_GLXQueryServerString)

  Serial number of failed request:  22

  Current serial number in output stream:  22

compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).

compiz (core) - Info: Starting plugin: opengl

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

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

compiz (core) - Info: Loading plugin: vpswitch

compiz (core) - Info: Starting plugin: vpswitch

compiz (core) - Info: Loading plugin: snap

compiz (core) - Info: Starting plugin: snap

compiz (core) - Info: Loading plugin: mousepoll

compiz (core) - Info: Starting plugin: mousepoll

compiz (core) - Info: Loading plugin: resize

compiz (core) - Info: Starting plugin: resize

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

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0


(process:2066): GLib-GIO-WARNING **: g_settings_set_value: value for key 'visual-bell-type' in schema 'org.gnome.desktop.wm.preferences' is outside of valid range


(process:2066): GLib-GIO-WARNING **: g_settings_set_value: value for key 'visual-bell-type' in schema 'org.gnome.desktop.wm.preferences' is outside of valid range

```

I am grateful for any help



Ded.

---

### Post by arpanaut on 2013-03-02
With 12.10 the command to reset the unity session is:
```
setsid unity
```

Try that and note if there any errors that may give you clues, 
is your session reset?
if not try rebooting.

Hope that Helps

---

### Post by dedpossum on 2013-03-03
Is there anyway to get a solution for this?   there seems to be a problem with the opengl, but i cant find a solution that uses terminal.  this is a problem as i have no interface.

---

### Post by arpanaut on 2013-03-03
Have you been able to get the default radeon driver set for your system?
Because if you still have the card that machine was shipped with (9800 Pro) it should work.
I have a machine that has that card and 3d and opengl work out of the box.  
And yes the propriatary drivers will not work with that card, so make sure that you have purged your system if you have tried to install other drivers. The link below may help with that. If you don't know what card you have this link will help too.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

If that doesn't work you might try Xubuntu or Lubuntu that don't have the video demands that Unity Desktop has.
Another option is to go back to 12.04 and use unity 2d.  Supported through 2017

---

### Post by dedpossum on 2013-03-04
Problem Solved!!!  I just installed windows 7, an operating system that works right from the box and doesnt require 4 days of dead ends, non solutions, and frustration.   gg ubuntu.

---

