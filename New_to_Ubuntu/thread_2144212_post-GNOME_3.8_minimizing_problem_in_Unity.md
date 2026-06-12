---
title: "post-GNOME 3.8 minimizing problem in Unity"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by jaramarana on 2013-05-11
I installed GNOME 3.8 from the PPA on my relatively fresh Raring install, and now whenever I minimize a program in Unity it crashes the computer - everything locks up except the mouse and I have to hard-reset.

Does anyone know what might have caused this? The default system font and icons have all changed to the GNOME defaults as well, which I wasn't expecting; maybe that has something to do with it.

---

### Post by hil4vitkutin on 2013-05-11
[FONT=arial]Hi, could you post the content of your *.xsessions-errors* file located in your home directory.

+ This is something you should try (reset Unity):

[/FONT]```

sudo apt-get install dconf-tools

dconf reset -f /org/compiz/

setsid unity

```[FONT=arial]
[/FONT]

---

### Post by jaramarana on 2013-05-11
The Unity reset hasn't worked, unfortunately. Nor has using ppa-purge to go back to the ordinary repo packages.

Here's how .xsession-errors looks:

> Script for cjkv started at run_im.
Script for default started at run_im.
Script for cjkv started at run_im.
Script for default started at run_im.
gnome-session[1993]: WARNING: Could not parse desktop file /home/XXX/.config/autostart/caffeine.desktop: Key file contains line '&#65533;&#65533;&#65533;&#65533;&#65533;$&#65533;m&#65533;{gJ&#65533;&#65533;&#65533;&#65533;2yv    U&#65533;v&#65533;&#65533;Q$B7&&#65533;:4&#65533;&#65533;&#65533;w&&#65533;&#65533;l&#65533;Y&#65533;&#65533;{&#65533;•&#65533;&#65533;&#669;&#65533;&#1798;&#65533;&#65533;&#65533;2&#65533;Kp&#65533;F&#65533;&#65533;&#65533;&#1130;&#65533;&#15174;]k81&#65533;!&#65533;&#65533;&E    +&#65533;&#65533;n&#65533;6&#65533;]&#65533;&#65533;6"&#65533;J<&#65533;6&#65533;&#65533;_&#65533;f&#65533;[s0&#65533;c5tPy&#65533;#@kK&#65533;*&#65533;b&#65533;&#65533;&#65533;&#65533;L|L&#1154;&#65533;&#65533;&#65533;' which is not a key-value pair, group, or comment
gnome-session[1993]: WARNING: could not read /home/XXX/.config/autostart/caffeine.desktop
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp

(gnome-settings-daemon:2076): color-plugin-WARNING **: failed to get edid: unable to get EDID for output
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl

(gnome-settings-daemon:2076): color-plugin-WARNING **: unable to get EDID for xrandr-LVDS1: unable to get EDID for output
Tracker-Message: Setting up monitor for changes to config file:'/home/XXX/.config/tracker/tracker-store.cfg'
Tracker-Message: Setting up monitor for changes to config file:'/home/XXX/.config/tracker/tracker-store.cfg'
Tracker-Message: Setting up monitor for changes to config file:'/home/XXX/.config/tracker/tracker-miner-fs.cfg'
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
** Message: applet now removed from the notification area
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: decor
** Message: using fallback from indicator to GtkStatusIcon
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
I/O warning : failed to load external entity "/home/XXX/.compiz/session/102b9f21f326306576136828971655878100000019930033"
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
** Message: moving back from GtkStatusIcon to indicator
gnome-session[1993]: WARNING: Could not launch application 'zeitgeist-datahub.desktop': Unable to start application: Failed to execute child process "zeitgeist-datahub" (No such file or directory)

** (gnome-screensaver:2464): WARNING **: screensaver already running in this session

** (nm-applet:2131): WARNING **: Could not find ShellVersion property on org.gnome.Shell after 5 tries
gnome-session[1993]: WARNING: Application 'compiz.desktop' killed by signal 9
gnome-session[1993]: WARNING: App 'compiz.desktop' respawning too quickly
gnome-session[1993]: CRITICAL: We failed, but the fail whale is dead. Sorry....
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Error: Screen 0 on display ":0" already has a window manager; try using the --replace option to replace the current window manager.
compiz (core) - Info: Stopping plugin: core
compiz (core) - Info: Unloading plugin: core
gnome-session[1993]: WARNING: App 'compiz.desktop' respawning too quickly
** Message: using fallback from indicator to GtkStatusIcon
** Message: moving back from GtkStatusIcon to indicator

Thanks for your help.

---

### Post by Frogs Hair on 2013-05-11
I just down-graded  from Gnome 3.8 to 3.6 and the ppa purge did not down-grade nautilus. I had to force re-installation of the old version and once done I was able remove the rest of the packages and re install 3.6  .

---

