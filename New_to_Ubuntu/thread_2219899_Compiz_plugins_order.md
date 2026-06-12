---
title: "Compiz plugins order"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2014-04-25
I am having on-going problems with some compiz plugins not working on reboot since 12.04 and now on a different machines. I have managed to work around them in 13.04 and 13.10 but it seems that everytime when a new Ubuntu is release, a different set of workarounds would be needed as whatever worked before would stop working.

So now Trusty is upon us and here we go again. Now I have hot corners for expo and scale addon activated but when I reboot one of them would stop working. So I disable auto plugin sorting in Preference and place either scale or expo in the bottom of the list
 [http://askubuntu.com/questions/140759/scale-plugin-keeps-forgetting-hot-corner-settings-on-restart](http://askubuntu.com/questions/140759/scale-plugin-keeps-forgetting-hot-corner-settings-on-restart)

 But those work arounds and their variations no longer work in 14.04 The problem is that unity-plugin depends on scale and if I put scale below unity, initiating scale hot corner would kill unity. Expo has to go the bottom of the list.

I wonder if there is any point of filing bugs against compiz because they are never fixed. 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/858845](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/858845)

Just look for a work around at this point.

---

### Post by monkeybrain20122 on 2014-04-26
Upgraded Compiz and Unity from proposed updates still no luck.
If auto sort plugins then neither scale nor expo work
expo only works if placed at the very bottom of the list.

so the order now is  scale  > scaleaddon > unity > expo  (> means above)
With this expo always work but scale pretty much never works.

This is really frustrating. I don't even do edge flipping this time. Everytime when a new Ubuntu comes out I am like walking on egg shell configuring compiz. Without these plugins to switch workplaces and pick application Unity's usability is greatly reduced.

---

### Post by monkeybrain20122 on 2014-04-26
Running "unity --replace" results in ugly black edges between workspace with expo (no orange high light) Putting the command in startup application results in slugguish behaviour and freeze, maybe the command is executed constantly?

Scale's hot corner can be enabled by using unity tweak tool to disable and then enable hot corners. Anyone knows what the comands are? maybe can put in a startup script.

---

### Post by Frogs Hair on 2014-04-26
The reset command for Unity changed  in 12.10. Try the following if you haven't already.

Unity:```
setsid unity
```
Compiz:```
dconf reset -f /org/compiz/

```

---

### Post by monkeybrain20122 on 2014-04-26
> **Frogs Hair said:**
> The reset command for Unity changed  in 12.10. Try the following if you haven't already.

Unity:```
setsid unity
```
Compiz:```
dconf reset -f /org/compiz/

```

Thanks. Will try this later.

---

### Post by monkeybrain20122 on 2014-04-27
As a crude workaroud I make a script with the command "setsid unity" and add it to startup applications. This is ugly and behaviour isn't really consistent. Sometimes expo would just shows workplaces separated by black borders without the orange highlight (though not very often)

I will appreciate it if there is better way..

---

### Post by monkeybrain20122 on 2014-04-28
Ran setsid unity in the terminal and got these outputs(unity restarts ok)

 > unity-panel-service stop/waiting
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
unity-panel-service start/running, process 2423
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: text
compiz (core) - Info: Starting plugin: text
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: commands
compiz (core) - Info: Starting plugin: commands
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: shift
compiz (core) - Info: Starting plugin: shift
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: wobbly
compiz (core) - Info: Starting plugin: wobbly
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
WARN  2014-04-28 03:39:45 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.Shell' yet as we don't have a connection, waiting for it...
ERROR 2014-04-28 03:39:45 unity.debug.interface DebugDBusInterface.cpp:196 Unable to load entry point in libxpathselect: libxpathselect.so.1.4: cannot open shared object file: No such file or directory
WARN  2014-04-28 03:39:45 xim.controller XIMController.cpp:103 IBus natively supported.
WARN  2014-04-28 03:39:45 unityct(io) <unknown>:0 Desktop file '/usr/share/applications/google-chrome.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2014-04-28 03:39:45 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Launcher' yet as we don't have a connection, waiting for it...
WARN  2014-04-28 03:39:46 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Dash' yet as we don't have a connection, waiting for it...
WARN  2014-04-28 03:39:46 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.SessionManager.EndSessionDialog' yet as we don't have a connection, waiting for it...
WARN  2014-04-28 03:39:46 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Session' yet as we don't have a connection, waiting for it...
WARN  2014-04-28 03:39:46 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.ScreenSaver' yet as we don't have a connection, waiting for it...
compiz (core) - Info: Loading plugin: scaleaddon
compiz (core) - Info: Starting plugin: scaleaddon
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
ERROR 2014-04-28 03:39:47 unity.glib.dbus.server GLibDBusServer.cpp:524 DBus name lost 'org.gnome.Shell'
ERROR 2014-04-28 03:39:47 unity.glib.dbus.server GLibDBusServer.cpp:524 DBus name lost 'com.canonical.Unity'


Maybe the errors are the causes of this problem. Can anyone provide some insight to this?

---

### Post by monkeybrain20122 on 2014-04-28
There are some updates today and now it appears to be working. Rebooted a few times and compiz didn't forget the hot corners, login also seemed  a lot faster than before. Not sure if that was a fluke or something that will stay. Will test some more tonight.

---

### Post by Frogs Hair on 2014-04-28
Exporting, modifying , and importing the compiz profile is possible though preferences in the CCSM , but I have only done this with very explicit instructions. The profile has to be named correctly for import and I haven't done since 11.04 or 11.10. It is one way to make a backup of settings for currently installed version.

---

### Post by monkeybrain20122 on 2014-04-29
After yesterday's update it seems to be "fixed". Yay!

Still need the following workaround:
Open ccsm, go to Preferences and disable auto-sorting. Expo has to be at  the bottom of the plugin  list for hot corner to be remembered. Then  followed by (in ascending order, i.e going up the list) scaleaddon,  unity shell and scale so hot corner for spread (scale) would work too.  Basically the same work around in 13.10 but the order wasn't as  stringent before. In particular hot corner for expo used to work without  being near the bottom of the plugin list.
 
Haven't brought in edge flip for wall, I just set the unity launcher  to auto-hide this time. Not sure if edge flip will work (used to have to  place wall at the bottom, but the spot is now taken by expo, if put it  in second place scale get pumped up so that may not work)

 It is not really a fix but I am relief that at least the work around from before sort of works. Also since the update log in is a lot faster (boot is always fast with 14.04.--as with 13.10,--, but login took a long time in 14.04 perhaps because of difficulties in loading the unity desktop, that appears to be fixed along with the problem of this thread)

So I am marking this thread as solved for now, and I hope the next update doesn't mess it up... It seems that these problems never really get fixed.

---

