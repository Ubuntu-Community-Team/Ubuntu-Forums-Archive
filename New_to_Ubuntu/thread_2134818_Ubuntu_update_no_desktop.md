---
title: "Ubuntu update no desktop"
date: 2013-04-12
forum: New to Ubuntu
---

### Post by carusoswi on 2013-04-12
Well, there is a desktop, but there is nothing on it except for two old folders that were present before the update.
I had not updated (or used Ubuntu) in quite a file, so the update was large and took a long time.

Now, after booting up Ubuntu (12.10), I have these two folders, can right click to change the desktop wall paper, but no other elements.

Moving the mouse around on the screen does not reveal any navigational or functional icons.

What's wrong, how to fix this?

Thanks

Caruso

---

### Post by fantab on 2013-04-12
Look in CCSM and check if 'Ubuntu Unity Plugin" is enabled. if it isn't then enable it. reboot.

Also, try reinstalling ubuntu-desktop: If you have Synaptic then remove ubuntu-desktop and reinstall it. Do NOT reboot until ubuntu-destop is reinstalled.

---

### Post by carusoswi on 2013-04-12
> **fantab said:**
> Look in CCSM and check if 'Ubuntu Unity Plugin" is enabled. if it isn't then enable it. reboot.

Also, try re installing ubuntu-desktop: If you have Synaptic then remove ubuntu-desktop and reinstall it. Do NOT reboot until ubuntu-destop is reinstalled.

Thanks for the quick response.  What is CCSM and how might I look there give that I have no apparent navigational control?

Thanks.

---

### Post by fantab on 2013-04-12
"Compiz Config Settings Manager". Can you open the terminal with **Ctrl+Alt+T**?
If you can then in terminal:

```
ccsm
```

If you don't have it installed then:

```
sudo apt-get update
sudo apt-get install compizconfig-settings-manager
```

If "sudo apt-get update" shows any errors post the output here.

---

### Post by carusoswi on 2013-04-12
Thanks again for your help. Will boot into 'buntu and try your suggestions.

> **fantab said:**
> "Compiz Config Settings Manager". Can you open the terminal with **Ctrl+Alt+T**?
If you can then in terminal:

```
ccsm
```

If you don't have it installed then:

```
sudo apt-get update
sudo apt-get install compizconfig-settings-manager
```

If "sudo apt-get update" shows any errors post the output here.

---

### Post by carusoswi on 2013-04-12
fantab:
Typing ccsm revealed that ccsm was not installed, so I ran the install code you suggested to install it.  No error codes.  Entering ccsm again brought up a dialog box, so I know that ccsm is now installed.  However, rebooting my system results in no improvement to my problem.  Only two folders show on my desktop, no other icons or drop down menus available that will allow me to do anything.
I suppose I could try reinstalling Ubuntu, but I am on the road and hesitant to dig into that right now.  If I mess up my windows OS out here, I would be toast for the balance of this business trip.

If you can suggest anything else in the meantime, I would be most appreciative.

For what reason should this problem have cropped up? Just curious.

Thanks again for your suggestions.

Caruso

---

### Post by fantab on 2013-04-12
Did you check whether the "Ubuntu Unity Plugin" is enabled? Have you tried reinstalling 'ubuntu-desktop'?
You can try "[Recovery Mode]("https://wiki.ubuntu.com/RecoveryMode")" from Grub menu (Advanced options) and fix dpkg. On booting into recovery mode you will be presented with a simple GUI and its quite easy from there on.

---

### Post by Frogs Hair on 2013-04-12
The Unity plug-in may not have a  check box in the CCSM as in 12.04, I don't remember seeing it when setting up the cube and it is gone in 13.04 .The reset commands for Compiz and unity have changed for 12.10+ also, use if needed.   

Reset Compiz```
 sudo apt-get install dconf-tools
``````
dconf reset -f /org/compiz/
``` Reset Unity```
setsid unity
```

---

### Post by fantab on 2013-04-12
> **Frogs Hair said:**
> The Unity plug-in may not have a  check box in the CCSM as in 12.04, I don't remember seeing it when setting up the cube and it is gone in 13.04 .The reset commands for Compiz and unity have changed for 12.10+ also, use if needed.   

I just checked my 13.04 install and yes, you are right the 'check-box' is gone. As I don't have 12.10, I cannot confirm.

---

### Post by carusoswi on 2013-04-13
Ran all the code suggested above.
setsid unity returned the following error (cannot guarantee that case is exactly correct, as I copied the message by hand).

Glib-warning **: /build/buildd/glib 2.0 - 2.34.1/./glib/gmain.c = 1817 : ref_count == 0, but source was still attached to a context!

Hopefully, someone can explain this, and, perhaps correction will lead to resolution of my problem.

I must say that I am disappointed that Ubuntu, all on its own, broke my install.
I would re-install as a simpler solution, but, really, such should not be necessary.  Ubuntu should not break itself during an update.

Thanks again for the replies.

Caruso

---

### Post by carusoswi on 2013-04-13
Ran all the code suggested above.
setsid unity returned the following error (cannot guarantee that case is exactly correct, as I copied the message by hand).

Glib-warning **: /build/buildd/glib 2.0 - 2.34.1/./glib/gmain.c = 1817 : ref_count == 0, but source was still attached to a context!

Hopefully, someone can explain this, and, perhaps correction will lead to resolution of my problem.

I must say that I am disappointed that Ubuntu, all on its own, broke my install.
I would re-install as a simpler solution, but, really, such should not be necessary.  Ubuntu should not break itself during an update.

Thanks again for the replies.

Caruso

---

### Post by Jonny87 on 2013-04-13
I don't have an install of 12.10 to confirm if this would still work but try opening your terminal (ctrl+T) and type the following and hit enter.

```
unity
```

Then let us know if your unity interface comes back. If not, please post any errors.

---

### Post by fantab on 2013-04-13
What happens if you choose an older kernel to boot? You can boot into an older kernel from Grub-Menu-> Advanced options.
Have you re-installed 'ubuntu-desktop'?
Have your tried 'Recovery Mode'?

[QUOTE=carusoswi]I must say that I am disappointed that Ubuntu, all on its own, broke my install.
I would re-install as a simpler solution, but, really, such should not  be necessary.  Ubuntu should not break itself during an update.
[/QUOTE]

I usually update Ubuntu weekly. However, sometimes I can't and updates pile on. In such a case I use:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

If you re-install, let me suggest that you opt for Ubuntu 13.04 beta2... IMO its way too stable than 12.10. 12.10 was one of those versions that I want to forget about. These things happen. There are not 'supposed to' but they do. [For the life of me, I could not figure out why 11.04 Natty didn't install on my machine. I still don't know why.] :confused: 

I have two versions of Ubuntu on my machine, currently 12.04 and 13.04 and all it takes is an additional space >15-20GB space.

---

### Post by BobosAbelMihai on 2013-04-13
I had the same problem after an update, it was because of kernel version and the video card, so i entered recovery mode, chose an previous version, and voila. When computer starts, press shift a lot to enter grub, then Advanced option and choose a version with recovery mode. For me that fixed the problem. Then i put hold on the working version of kernel.

See if another version works for you, from grub-->Advanced options-->......(Recovery mode).

---

### Post by carusoswi on 2013-04-13
The output returned when I input "unity" in terminal follows:

caruso@caruso-G74Sx:~$ unity
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
^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[A^[[AXlib:  extension "GLX" missing on display ":0".
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


Thanks again to all who have offered helpful suggestions.
As frustrating as some Ubuntu has been of late, one of the reasons I have stuck with it over the years is the help that seems readily available on this forum.
I think I will download 13.04 onto a penn drive, although I have never had any success getting my machine to boot from same (that's all I have with me at the moment).
Anxious to hear what you gleen from the above error messages.

Caruso

> **Jonny87 said:**
> I don't have an install of 12.10 to confirm if this would still work but try opening your terminal (ctrl+T) and type the following and hit enter.

```
unity
```

Then let us know if your unity interface comes back. If not, please post any errors.

---

### Post by Jonny87 on 2013-04-13
Please as a future tip, please use the code # tags to post logs and portions of code and output like the above. If using the quick reply at the bottom of the page you'll need to click "Go Advanced".

I can see some errors occurring in there but I'm not 100% sure what's causing them. perhaps someone else may have some more insight on that side of things. Though I'm wondering, are you using a specific video card and driver such as NVidia?

Have you tried booting to an earlier Kernel as Fantab has suggested and/or the command that fantab also suggested?
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update && sudo apt-get dist-upgrade[/FONT][/COLOR]
```
Or uninstalling and reinstalling ubuntu-desktop from the synaptic package manager?
This will not affect your Windows install it's not a full reinstall of your ubuntu setup. It just removes the main ubuntu packages and then re-installs them, this will make sure that none of them are broken or corrupt. Just make sure that you reinstall it straight away as Fantab said. Don't reboot in between.

---

### Post by carusoswi on 2013-04-14
Please explain further your 'future tip'.  I don't understand how to do it or why it is necessary.  Did I do something wrong or undesirable?  In order to copy/paste that code, I had to Gedit to copy it, save it on my windows drive, then boot into windows to copy/paste here.  Please do tell me more about how I should have done this, thanks.

I tried apt-get update.  It reports that no changes were made to my computer.
Haven't yet tried the upgrade code.
As for uninstalling/reinstalling Ubuntu-desktop from synaptic, how would I do that if I don't have any desktop navigation controls?  My desktop is totally blank save for two non-system folders.

I can click on them to open, but there isn't even a little 'x' that allows me to close them.  

Sorry if I seem dense, but I thank you for your help.

Caruso

---

### Post by fantab on 2013-04-14
> **carusoswi said:**
> Please explain further your 'future tip'.  I don't understand how to do it or why it is necessary.  Did I do something wrong or undesirable?  In order to copy/paste that code, I had to Gedit to copy it, save it on my windows drive, then boot into windows to copy/paste here.  Please do tell me more about how I should have done this, thanks.

I tried apt-get update.  It reports that no changes were made to my computer.
Haven't yet tried the upgrade code.
As for uninstalling/reinstalling Ubuntu-desktop from synaptic, how would I do that if I don't have any desktop navigation controls?  My desktop is totally blank save for two non-system folders.

I can click on them to open, but there isn't even a little 'x' that allows me to close them.  

Sorry if I seem dense, but I thank you for your help.

Caruso

It is easier to read large chunk of code if it is wrapped in codes: see the screenshot below:

[ATTACH=CONFIG]241314[/ATTACH]

If you explore the above editor you will see that there is Quote, url, etc. Which you can use to edit your written text to post on the forum. Its simple.

From Terminal (ctrl+alt+T) you can type:

```
gksudo synaptic
```

type 'ubuntu-desktop' in the Synaptic Search and 'mark for complete removal/installation'.. see the screenshot below:

[ATTACH=CONFIG]241315[/ATTACH]

Then you 'APPLY' the operation. It will want to remove whole lot of apps and libs. Let it do its job. Then select it again and "mark for installation" and apply.

Also try 'Recovery Mode' from Grub-Menu.

---

### Post by Jonny87 on 2013-04-14
> **fantab said:**
> 
From Terminal (ctrl+alt+T) you can type:

```
gksudo synaptic
```



Just incase, I thought I'd say, if you don't have it installed as it's no longer included in the default install. you can install it with;

```
sudo apt-get install synaptic
```

> **fantab said:**
> **Also try 'Recovery Mode' from Grub-Menu.**

---

