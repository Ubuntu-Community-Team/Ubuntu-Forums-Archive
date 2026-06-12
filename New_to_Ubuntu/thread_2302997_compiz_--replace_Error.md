---
title: "compiz --replace Error"
date: 2015-11-15
forum: New to Ubuntu
---

### Post by ChrispyChris on 2015-11-15
I'm trying to play around in the Unity Tweak Tool and change my cursor theme. I am on a fresh Ubuntu install and am a total noob, so please bear with me. I first changed my cursor theme and then closed the Unity Tweak Tool. I then ctr+alt+t and type "compiz --replace", to no avail. I receive this on pressing enter:
```

chrispychris@ChrisUbuntu:~$ compiz --replace
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
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: commands
compiz (core) - Info: Starting plugin: commands
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
WARN  2015-11-15 08:32:13 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.Shell' yet as we don't have a connection, waiting for it...
ERROR 2015-11-15 08:32:13 unity.debug.interface DebugDBusInterface.cpp:216 Unable to load entry point in libxpathselect: libxpathselect.so.1.4: cannot open shared object file: No such file or directory
WARN  2015-11-15 08:32:13 xim.controller XIMController.cpp:103 IBus natively supported.
WARN  2015-11-15 08:32:13 unityct(io) <unknown>:0 Desktop file '/usr/share/applications/google-chrome.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2015-11-15 08:32:13 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Launcher' yet as we don't have a connection, waiting for it...
WARN  2015-11-15 08:32:13 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Dash' yet as we don't have a connection, waiting for it...
WARN  2015-11-15 08:32:13 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.SessionManager.EndSessionDialog' yet as we don't have a connection, waiting for it...
WARN  2015-11-15 08:32:13 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Session' yet as we don't have a connection, waiting for it...
WARN  2015-11-15 08:32:13 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.ScreenSaver' yet as we don't have a connection, waiting for it...
ERROR 2015-11-15 08:32:14 unity.glib.dbus.server GLibDBusServer.cpp:524 DBus name lost 'org.gnome.Shell'
ERROR 2015-11-15 08:32:14 unity.glib.dbus.server GLibDBusServer.cpp:524 DBus name lost 'com.canonical.Unity'

```

Then when I try to close the terminal, it says a process is still running. What am I doing wrong to not be able to run this command correctly? I would appreciate any help!

Thanks,
Chris

---

### Post by grahammechanical on 2015-11-15
First, you do not tell us the version of Ubuntu you are using and that could make a difference in the instructions we give.
Second, what do you mean by "to no avail." What were you expecting to happen?
Third, Do you still have a usable desktop or is the user interface unusable?
Fourth, I think this is a better command to use to restart Compiz in newer versions of Ubuntu.

```
dconf reset -f /org/compiz/
```

And to restart Unity

```
setsid unity
```

Regards.

---

### Post by ChrispyChris on 2015-11-15
Sorry, I downloaded and installed the Ubuntu version 14.04.3 LTS on this laptop. If you need more information I would be happy to provide it!

What I meant by that was, I was expecting my mouse cursor to reset and change to the newly selected theme.

The desktop is usable still, although once I highlighted it all in the console and hit ctr+c and that made it unusable, so I had to hard reset. I've just been right click and copying from now on.

I tried out the first command and nothing happened. The second command did some stuff, I'll post a log below.
```

chrispychris@ChrisUbuntu:~$ dconf reset -f /org/compiz/
chrispychris@ChrisUbuntu:~$ setsid unity
chrispychris@ChrisUbuntu:~$ unity-panel-service stop/waiting
unity-panel-service start/running, process 10085
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
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: commands
compiz (core) - Info: Starting plugin: commands
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
WARN  2015-11-15 10:54:57 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.Shell' yet as we don't have a connection, waiting for it...
ERROR 2015-11-15 10:54:57 unity.debug.interface DebugDBusInterface.cpp:216 Unable to load entry point in libxpathselect: libxpathselect.so.1.4: cannot open shared object file: No such file or directory
WARN  2015-11-15 10:54:57 xim.controller XIMController.cpp:103 IBus natively supported.
WARN  2015-11-15 10:54:57 unityct(io) <unknown>:0 Desktop file '/usr/share/applications/google-chrome.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2015-11-15 10:54:57 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Launcher' yet as we don't have a connection, waiting for it...
WARN  2015-11-15 10:54:57 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Dash' yet as we don't have a connection, waiting for it...
WARN  2015-11-15 10:54:57 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.SessionManager.EndSessionDialog' yet as we don't have a connection, waiting for it...
WARN  2015-11-15 10:54:57 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Session' yet as we don't have a connection, waiting for it...
WARN  2015-11-15 10:54:57 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.ScreenSaver' yet as we don't have a connection, waiting for it...
WARN  2015-11-15 10:54:58 unity.launcher.icon LauncherIcon.cpp:458 Unable to load '/tmp/.bamficonKB097X' icon: Failed to open file '/tmp/.bamficonKB097X': No such file or directory
ERROR 2015-11-15 10:54:58 unity.glib.dbus.server GLibDBusServer.cpp:524 DBus name lost 'org.gnome.Shell'
ERROR 2015-11-15 10:54:58 unity.glib.dbus.server GLibDBusServer.cpp:524 DBus name lost 'com.canonical.Unity'

```

---

### Post by Frogs Hair on 2015-11-15
What desktop is in use ? I see a Gnome Shell reference in the output which doesn't use compiz.

> Can't register object 'org.gnome.Shell

```
echo $XDG_CURRENT_DESKTOP
```

If in Unity you should see this output.

```
~$ echo $XDG_CURRENT_DESKTOP
Unity

```

---

### Post by ChrispyChris on 2015-11-15
I did see Unity after inputting [COLOR=#000000][FONT=Ubuntu Mono]echo $XDG_CURRENT_DESKTOP.[/FONT][/COLOR]

---

### Post by CantankRus on 2015-11-15
The messages you are seeing are quite normal when running **setsid unity** or **compiz --replace**
Doesn't mean the commands aren't working.
You can achieve the same result by logging out and back in.

Changing cursors isn't as simple as just using Unity Tweak Tool. 
[http://ubuntuforums.org/showthread.php?t=2221942&page=2&p=13028225#post13028225](http://ubuntuforums.org/showthread.php?t=2221942&page=2&p=13028225#post13028225)
What cursor theme are you trying to change to?

---

### Post by ChrispyChris on 2015-11-15
Oh wow, I thought it would be simpler than that with the tool. I was just picking any of the few in there, for example Redglass. I can't seem to get it working though.

---

### Post by CantankRus on 2015-11-15
> **ChrispyChris said:**
> Oh wow, I thought it would be simpler than that with the tool. I was just picking any of the few in there, for example Redglass. I can't seem to get it working though.
After selecting the cursor theme in unity-tweak-tool, also select the theme in alternatives.
eg using the terminal...
```
sudo update-alternatives --config x-cursor-theme
```

Log out and back in to complete the change.

---

### Post by ChrispyChris on 2015-11-16
I gave that a shot too, and still no luck. This isn't the biggest deal ever, but I thought it would be cool to learn something simple to start. Haha the way my luck goes, simple things get overcomplicated! Any other suggestions?

---

### Post by CantankRus on 2015-11-16
If you have set the theme in unity tweak and alternatives the following 2 commands should both show redglass.
```
dconf read /org/gnome/desktop/interface/cursor-theme
update-alternatives --display x-cursor-theme | head -n2
```

eg what my terminal shows...
```
**[COLOR="#006400"]glen@Trusty:~$[/COLOR] dconf read /org/gnome/desktop/interface/cursor-theme**
'redglass'

**[COLOR="#006400"]glen@Trusty:~$[/COLOR] update-alternatives --display x-cursor-theme | head -n2**
x-cursor-theme - manual mode
  link currently points to /etc/X11/cursors/redglass.theme
```

---

### Post by ChrispyChris on 2015-11-16
This is what I'm getting back, so something is going wrong somewhere here!

```

chrispychris@ChrisUbuntu:~$ dconf read /org/gnome/desktop/interface/cursor-theme'DMZ-White'
chrispychris@ChrisUbuntu:~$ update-alternatives --display x-cursor-theme | head -n2
x-cursor-theme - manual mode
  link currently points to /usr/share/icons/DMZ-White/cursor.theme

```

---

### Post by CantankRus on 2015-11-16
All Unity-tweak-tool(UTT) does is change a dconf setting.
You can see this by opening a terminal and running...
```
dconf watch /
```
Then open UTT and change your cursor to redglass.
You should see the dconf setting change.
[ATTACH=CONFIG]265630[/ATTACH]

Then run...
```
sudo update-alternatives --config x-cursor-theme
```
and enter your redglass selection number.
It should confirm your choice.
[ATTACH=CONFIG]265631[/ATTACH]


Log out.

---

### Post by ChrispyChris on 2015-12-04
Okay, after a couple weeks I decided to come back and work at this again. I watched the dconf change, and it did to Redglass. Now in my terminal, I see a red text cursor, but nowhere else on my screen, for example when hovering over the desktop. It's just the normal black one. Am I expecting different results than what this is actually supposed to do, or is something still incorrect?

Thanks again for all the help!

---

### Post by CantankRus on 2015-12-04
Two settings have to change.
Dconf and alternatves.

Are you seeing the last line as below when updating alternatves?
```
**[COLOR="#006400"]glen@Trusty:~$[/COLOR] sudo update-alternatives --config x-cursor-theme**
[sudo] password for glen: 
There are 31 choices for the alternative x-cursor-theme (providing /usr/share/icons/default/index.theme).

  Selection    Path                                                   Priority   Status
------------------------------------------------------------
  0            /usr/share/icons/DMZ-White/cursor.theme                 100       auto mode
  1            /etc/X11/cursors/redglass.theme                         20        manual mode
  2            /usr/share/icons/AlkanoBlack/cursor.theme               20        manual mode
  3            /usr/share/icons/Breeze/cursor.theme                    20        manual mode
  4            /usr/share/icons/DMZ-Black-Large/cursor.theme           20        manual mode
* 5            /usr/share/icons/DMZ-Black-Medium/cursor.theme          20        manual mode
  6            /usr/share/icons/DMZ-Black/cursor.theme                 20        manual mode
  7            /usr/share/icons/DMZ-White-Large/cursor.theme           20        manual mode
  8            /usr/share/icons/DMZ-White-Medium/cursor.theme          20        manual mode
  9            /usr/share/icons/DMZ-White/cursor.theme                 100       manual mode


Press enter to keep the current choice[*], or type selection number: 1
update-alternatives: using /etc/X11/cursors/redglass.theme to provide /usr/share/icons/default/index.theme (x-cursor-theme) in manual mode
```
Log out and back in to complete the cursor change.

---

### Post by ChrispyChris on 2015-12-04
I see that line, but under that I see:
update-alternatives: warning: not replacing /usr/share/icons/default/index.theme with a link

Is this my problem?

---

### Post by CantankRus on 2015-12-04
> **ChrispyChris said:**
> I see that line, but under that I see:
update-alternatives: warning: not replacing /usr/share/icons/default/index.theme with a link

Is this my problem?
I think what this is saying is **/usr/share/icons/default/index.theme** is a normal file when it should be a link.
It can't replace this file with a link.
You must have changed something in your previous efforts to change the cursor.

Try this.
Move your **/usr/share/icons/default/index.theme** file to a backup file...
```
sudo mv /usr/share/icons/default/index.theme /usr/share/icons/default/index.theme.bak
```

Then update alternatives again and choose redglass.
It may give an error about a broken link....ignore.
```
sudo update-alternatives --config x-cursor-theme
```

Set redglass in unity tweak tool as well.
Logout and back in.

---

### Post by ChrispyChris on 2015-12-04
Oh my, it worked haha! Thank you so much for bearing with me brother. How in the world could that have happened? I'm curious how that could have happened though! 

Also, is it okay for me to delete /usr/share/icons/default.index.theme.bak now?

---

### Post by CantankRus on 2015-12-04
> **ChrispyChris said:**
> Oh my, it worked haha! Thank you so much for bearing with me brother. How in the world could that have happened? I'm curious how that could have happened though! 

Also, is it okay for me to delete /usr/share/icons/default.index.theme.bak now?
Should be ok to delete.
update-alternatives should have created a new **/usr/share/icons/default/index.theme** file which is a link to **/etc/alternatives/x-cursor-theme** 

To remove /usr/share/icons/default/index.theme.bak...
```
sudo rm /usr/share/icons/default/index.theme.bak
```

---

### Post by Geoffrey_Arndt on 2015-12-05
Wow . . . sure am glad I have no interest in changing cursor pointers or themes in the default Unity DE.    I guess if I did, I'd have to go back to KDEPlasma5 in the latest Suse . . . or Xubuntu XFCE!

---

### Post by CantankRus on 2015-12-05
> **Geoffrey_Arndt said:**
> Wow . . . sure am glad I have no interest in changing cursor pointers or themes in the default Unity DE.    I guess if I did, I'd have to go back to KDEPlasma5 in the latest Suse . . . or Xubuntu XFCE!
Not that hard.
All things being normal, it's just a matter of changing 2 settings.
Similar process in Xubuntu.

---

