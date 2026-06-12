---
title: "gconf-editor apps&gt;metacity missing? 14.04"
date: 2014-05-27
forum: New to Ubuntu
---

### Post by gijs2 on 2014-05-27
As the title says my metacity is missing.



On a side note, my close/maximize/minimize buttons on my files are gone maybe it has something to do with my metacity missing.

---

### Post by ajgreeny on 2014-05-27
14.04 does not use metacity; unity is totally dependent upon using compiz as the window manager, and in any case, gconf-editor is almost deprecated now in favour of dconf-editor, though the latter does not work in exactly the same manner.

I do not use unity or gnome any more having moved to xubuntu and xfce,so I can't really help any more with your gconf problem.

---

### Post by gijs2 on 2014-05-27
> **ajgreeny said:**
> 14.04 does not use metacity; unity is totally dependent upon using compiz as the window manager, and in any case, gconf-editor is almost deprecated now in favour of dconf-editor, though the latter does not work in exactly the same manner.

I do not use unity or gnome any more having moved to xubuntu and xfce,so I can't really help any more with your gconf problem.

If it is not my metacity then how come my files do not have a close/minimize/maximite to it?

---

### Post by egeezer on 2014-05-27
Because Compiz uses different window decoration (which is what determines that line of the window).  You can apt-get install dconf-tools, run dconf-editor in a terminal, navigate to org>gnome>desktop>wm>preferences and change the "theme" value from "Adwaita" to "Greybird".  Log out, log in, and you'll have your window borders.

---

### Post by gijs2 on 2014-05-28
> **egeezer said:**
> Because Compiz uses different window decoration (which is what determines that line of the window).  You can apt-get install dconf-tools, run dconf-editor in a terminal, navigate to org>gnome>desktop>wm>preferences and change the "theme" value from "Adwaita" to "Greybird".  Log out, log in, and you'll have your window borders.

That didn't work, the same problem still excists.

---

### Post by deadflowr on 2014-05-28
Don't know if this will help at all ,but what's
the output of this command
```
gsettings get org.compiz.gwd use-metacity-theme
```

---

### Post by gijs2 on 2014-05-28
> **deadflowr said:**
> Don't know if this will help at all ,but what's
the output of this command
```
gsettings get org.compiz.gwd use-metacity-theme
```

It gives true

---

### Post by monkeybrain20122 on 2014-05-28
Install the dconf-editor instead. Unity/gnome-shell has moved to dconf and gconf is kind of deprecated.

---

### Post by gijs2 on 2014-05-28
> **monkeybrain20122 said:**
> Install the dconf-editor instead. Unity/gnome-shell has moved to dconf and gconf is kind of deprecated.
Already have that.

---

### Post by gijs2 on 2014-05-29
Bump~

---

### Post by kansasnoob on 2014-05-29
The only thing I've seen related to metacity is in dconf; org/gnome/metacity, but it's almost empty:

[ATTACH=CONFIG]253565[/ATTACH]

Are you using Unity or some other desktop?

---

### Post by gijs2 on 2014-05-29
> **kansasnoob said:**
> The only thing I've seen related to metacity is in dconf; org/gnome/metacity, but it's almost empty:

[ATTACH=CONFIG]253565[/ATTACH]

Are you using Unity or some other desktop?

I use unity

---

### Post by gijs2 on 2014-05-29
Editted the main question since the last main question has been answered.

---

### Post by coffeecat on 2014-05-29
> **gijs2 said:**
> Editted the main question since the last main question has been answered.

Please do not do that. It is very confusing for those helping, especially those who join the thread later. I have restored your original text in the OP and the original thread title. If you have a subsidiary question, then just ask it in a subsequent post. If it is a new problem, then a new thread would be appropriate.

---

### Post by gijs2 on 2014-05-29
> **coffeecat said:**
> Please do not do that. It is very confusing for those helping, especially those who join the thread later. I have restored your original text in the OP and the original thread title. If you have a subsidiary question, then just ask it in a subsequent post. If it is a new problem, then a new thread would be appropriate.

Alright noted.

For everyone who is wondering the main question has been answered, wich is that my metacity wasn't listed in gconf-editor.
My subsidiary question is that my close/minimize/maximize are gone on my file manager and i only have a diffrent looking close button on the right of my file manager.
My popup from terminal looks diffrent (as in it has no styles added to it).

Screenshots are below:

File manager:
[IMG]http://i.imgur.com/MW2yAzI.png?1[/IMG]

Terminal popup:
[IMG]http://i.imgur.com/1lc0hjK.png?1[/IMG]

---

### Post by mc4man on 2014-05-29
What you are getting is the nautilus (Files) designed for a gnome/gnome-shell session.
Check that ubuntu-settings is installled, if not install then log out/in
```
sudo apt-get install ubuntu-settings
```

---

### Post by gijs2 on 2014-05-29
> **mc4man said:**
> What you are getting is the nautilus (Files) designed for a gnome/gnome-shell session.
Check that ubuntu-settings is installled, if not install then log out/in
```
sudo apt-get install ubuntu-settings
```

I already have it installed.

---

### Post by gijs2 on 2014-05-29
> **mc4man said:**
> What you are getting is the nautilus (Files) designed for a gnome/gnome-shell session.
Check that ubuntu-settings is installled, if not install then log out/in
```
sudo apt-get install ubuntu-settings
```

Could it work with ubuntu-tweak?

---

### Post by monkeybrain20122 on 2014-05-29
Install the ccsm (CompizConfigSettingsManager) from repo, go to Window Decoration and see that the box is checked, if not, check it, if yes, uncheck and recheck it. 

I don't know anything about all these so called tweak tools that spring up. Basically ccsm has all the settings you need but use it with care.

---

### Post by gijs2 on 2014-05-29
> **monkeybrain20122 said:**
> Install the ccsm (CompizConfigSettingsManager) from repo, go to Window Decoration and see that the box is checked, if not, check it, if yes, uncheck and recheck it.

Tried it, did not work.
The problem is still there

---

### Post by monkeybrain20122 on 2014-05-29
Well try in the terminal

> setsid unity

---

### Post by deadflowr on 2014-05-29
Now to make sure everything else is kosher, You have a launcher(left-side) and a top panel bar, right?
Only window decorations are busted?

What theme(s) are you using?

---

### Post by gijs2 on 2014-05-29
> **monkeybrain20122 said:**
> Well try in the terminal

From setsid unity i got this output:

```
unity-panel-service stop/waitingunity-panel-service start/running, process 11794
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : default
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
WARN  2014-05-29 22:46:19 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.Shell' yet as we don't have a connection, waiting for it...
ERROR 2014-05-29 22:46:19 unity.debug.interface DebugDBusInterface.cpp:196 Unable to load entry point in libxpathselect: libxpathselect.so.1.4: cannot open shared object file: No such file or directory
WARN  2014-05-29 22:46:19 xim.controller XIMController.cpp:103 IBus natively supported.
WARN  2014-05-29 22:46:19 unityct(io) <unknown>:0 Desktop file '/usr/share/applications/google-chrome.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2014-05-29 22:46:19 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Launcher' yet as we don't have a connection, waiting for it...
WARN  2014-05-29 22:46:19 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Dash' yet as we don't have a connection, waiting for it...
WARN  2014-05-29 22:46:19 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.SessionManager.EndSessionDialog' yet as we don't have a connection, waiting for it...
WARN  2014-05-29 22:46:19 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Session' yet as we don't have a connection, waiting for it...
WARN  2014-05-29 22:46:19 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.ScreenSaver' yet as we don't have a connection, waiting for it...
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
ERROR 2014-05-29 22:46:20 unity.shell.compiz unityshell.cpp:2719 Decoration plugin is active, disabling it...
compiz (core) - Info: Unloading plugin: decor
ERROR 2014-05-29 22:46:20 unity.glib.dbus.server GLibDBusServer.cpp:524 DBus name lost 'org.gnome.Shell'
ERROR 2014-05-29 22:46:20 unity.glib.dbus.server GLibDBusServer.cpp:524 DBus name lost 'com.canonical.Unity'



``` 

> **deadflowr said:**
> Now to make sure everything else is kosher, You have a launcher(left-side) and a top panel bar, right?
Only window decorations are busted?

What theme(s) are you using?

Yes everything is kosher, although whenever i do something in ccsm i need about 15-20 minutes to fix it because then my top/side bar get removed and i cant get my terminal open so i'd like not to use ccsm anymore :P

I am using Ubuntu (Default) and my theme is Numix but my problem got here before i started using Numix so it is not that.
And today i removed my other shells.

---

### Post by monkeybrain20122 on 2014-05-29
Well it says "No default decoration found, placement will not be correct" and also "Unity is not supported by your hardware. Enabling software rendering instead (slow)"

Forget about the second one for a second. Open CCSM, Window Decoration, what do you see in the "Command" box? In mine it says "/usr/bin/gtk-window-decorator"

---

### Post by gijs2 on 2014-05-29
> **monkeybrain20122 said:**
> Well it says "No default decoration found, placement will not be correct" and also "Unity is not supported by your hardware. Enabling software rendering instead (slow)"

Forget about the second one for a second. Open CCSM, Window Decoration, what do you see in the "Command" box? In mine it says "/usr/bin/gtk-window-decorator"

It says exactly the same for me, although my checkbox unter "Use This Plugin" is white with a red check mark and yours is grey does that mean anything?

---

### Post by monkeybrain20122 on 2014-05-29
Mine is grey because I disabled auto sorting of plugins to work around a bug that hot corners of certain plugins not being remembered, it doesn't have anything to do with your problem.

---

### Post by gijs2 on 2014-05-29
> **monkeybrain20122 said:**
> Mine is grey because I disabled auto sorting of plugins, it doesn't have anything to do with your problem.

Hm alright do you have any other ideas?

---

### Post by monkeybrain20122 on 2014-05-29
Not at the moment I am afraid. :) If ccsm and restarting unity don't work I doubt that any "tweak tool" would, it may have something to do with hardware or some conf file somewhere, sorry can't be of any help. :(

---

### Post by gijs2 on 2014-05-29
> **monkeybrain20122 said:**
> Not at the moment I am afraid. :) If ccsm and restarting unity don't work I doubt that any "tweak tool" would, it may have something to do with hardware or some conf file somewhere, sorry can't be of any help. :(

It's probably hardware since it also happends in guest session

---

### Post by grumblebum2 on 2014-05-29
> **monkeybrain20122 said:**
> Well it says "No default decoration found, placement will not be correct" and also "Unity is not supported by your hardware. Enabling software rendering instead (slow)"

Forget about the second one for a second. Open CCSM, Window Decoration, what do you see in the "Command" box? In mine it says "/usr/bin/gtk-window-decorator"
In 14.04 the Window Decoration plugin can't be enabled with unity.
The unity plugin provides window decoration.

The problem is probably related to this....
> **gijs2 said:**
> 
And today i removed my other shells.

---

### Post by gijs2 on 2014-05-30
> **grumblebum2 said:**
> In 14.04 the Window Decoration plugin can't be enabled with unity.
The unity plugin provides window decoration.

The problem is probably related to this....

The same is happening, the only thing that was diffrent with me is "Overide Theme Settings" but that didn't change anything for me.

---

### Post by monkeybrain20122 on 2014-05-30
> **grumblebum2 said:**
> In 14.04 the Window Decoration plugin can't be enabled with unity.
The unity plugin provides window decoration.

The problem is probably related to this....

Yeah you are right, that screenshot was taken from 13.10. OP's setsid unity outputs say that his hardware doesn't support Unity may be that's the reason, as you said in 14.04 window decoration is provided by unity.

---

### Post by gijs2 on 2014-05-30
> **monkeybrain20122 said:**
> Yeah you are right, that screenshot was taken from 13.10. OP's setsid unity outputs say that his hardware doesn't support Unity may be that's the reason, as you said in 14.04 window decoration is provided by unity.

That's weird since my unity is on in my ccsm

---

### Post by monkeybrain20122 on 2014-05-30
Do you have window decoration in a live usb session? Is this an upgrade or a fresh install?

---

### Post by gijs2 on 2014-05-30
> **monkeybrain20122 said:**
> Do you have window decoration in a live usb session? Is this an upgrade or a fresh install?

Before this I had Windows 8 but i used Dariks boot and nuke to nuke my hard drive, then i installed from a usb ubuntu 14.04 LTS

---

### Post by monkeybrain20122 on 2014-05-30
If the hardware works for Win8 then for sure it would work for Unity. Boot off the usb and see if you have window decoration.

---

### Post by gijs2 on 2014-05-30
> **monkeybrain20122 said:**
> If the hardware works for Win8 then for sure it would work for Unity. Boot off the usb and see if you have window decoration.

Windows decoration works fine when i boot off usb.

---

### Post by monkeybrain20122 on 2014-05-30
So it seems you messed up something? Would it be too much trouble to just reinstall?

---

### Post by gijs2 on 2014-05-30
> **monkeybrain20122 said:**
> So it seems you messed up something? Would it be too much trouble to just reinstall?

I'm sorry but it would, i don't want to reinstall everything.
Is there maybe some way to get default settings back?

---

### Post by mc4man on 2014-05-30
> **gijs2 said:**
> Could it work with ubuntu-tweak?
No - did you ck. to see that that package is installed? (it's nothing you run or open, it's sets proper overrides for an ubuntu (unity) session inc. giving you proper window deco & controls in nautilus, ect.
(whether it works for your current theme no clue but it must be installed anyway

---

### Post by gijs2 on 2014-05-31
> **mc4man said:**
> No - did you ck. to see that that package is installed? (it's nothing you run or open, it's sets proper overrides for an ubuntu (unity) session inc. giving you proper window deco & controls in nautilus, ect.
(whether it works for your current theme no clue but it must be installed anyway

I installed it manually, does that matter?

---

### Post by grumblebum2 on 2014-05-31
What matters is why it wasn't installed or uninstalled in the first place.

---

### Post by gijs2 on 2014-05-31
> **grumblebum2 said:**
> What matters is why it wasn't installed or uninstalled in the first place.

Can I give any error reports?
If so please tell me wich one ^^

---

### Post by grumblebum2 on 2014-05-31
**ubuntu-desktop** is a meta package that depends on all of the packages in the Ubuntu desktop system.
It contains no application itself but will be removed if you remove one of it's dependencies.
Check to see if it is installed....
```
apt-cache policy ubuntu-desktop
```

If not installed it will show a line...
```
Installed: **(none)**
```

If not installed what does this show (will just simulate without installing)
```
sudo apt-get install --simulate ubuntu-desktop
```

---

### Post by gijs2 on 2014-05-31
> **grumblebum2 said:**
> **ubuntu-desktop** is a meta package that depends on all of the packages in the Ubuntu desktop system.
It contains no application itself but will be removed if you remove one of it's dependencies.
Check to see if it is installed....
```
apt-cache policy ubuntu-desktop
```

If not installed it will show a line...
```
Installed: **(none)**
```

If not installed what does this show (will just simulate without installing)
```
sudo apt-get install --simulate ubuntu-desktop
```

It is already installed.

---

### Post by grumblebum2 on 2014-05-31
Have you installed other desktop meta packages like Kubuntu-desktop, Lubuntu-desktop,Xubuntu.
As with ubuntu-desktop, removing the *-desktop only removes that package and not all the packages it installed.
Kubuntu is known not to play well with ubuntu already installed.

Added any third party ppas?

From your posts you have obviously been experimenting/customizing and without knowing what you have or haven't done
it's very hard to come up with definitive solutions to your problems.
Nothing wrong with experimenting but honestly the easiest solution sometimes is to reinstall.

---

### Post by gijs2 on 2014-05-31
> **grumblebum2 said:**
> Have you installed other desktop meta packages like Kubuntu-desktop, Lubuntu-desktop,Xubuntu.
As with ubuntu-desktop, removing the *-desktop only removes that package and not all the packages it installed.
Kubuntu is known not to play well with ubuntu already installed.

Added any third party ppas?

From your posts you have obviously been experimenting/customizing and without knowing what you have or haven't done
it's very hard to come up with definitive solutions to your problems.
Nothing wrong with experimenting but honestly the easiest solution sometimes is to reinstall.

I did not install any other than ubuntu only shells (wich i removed).

And I'd rather not reinstall since I don't want to reset my harddrive again and reinstall everything that I installed.
If there is like a recovery for ubuntu that does not affect my files then i'd be gladly to try it out.

---

### Post by vasa1 on 2014-05-31
Why don't you run```
dpkg --get-selections > ~/Desktop/installed-software
```and upload the file using **pastebinit** and provide the link here? That way, people will get an idea of what's on your system.

---

### Post by gijs2 on 2014-05-31
> **vasa1 said:**
> Why don't you run```
dpkg --get-selections > ~/Desktop/installed-software
```and upload the file using **pastebinit** and provide the link here? That way, people will get an idea of what's on your system.

How do I upload a directory using pastebinit, the tutorial only showed files.

---

### Post by kansasnoob on 2014-05-31
> **grumblebum2 said:**
> Have you installed other desktop meta packages like Kubuntu-desktop, Lubuntu-desktop,Xubuntu.
As with ubuntu-desktop, removing the *-desktop only removes that package and not all the packages it installed.
**[COLOR="#FF0000"]Kubuntu is known not to play well with ubuntu already installed[/COLOR]**.

Added any third party ppas?

From your posts you have obviously been experimenting/customizing and without knowing what you have or haven't done
it's very hard to come up with definitive solutions to your problems.
Nothing wrong with experimenting but honestly the easiest solution sometimes is to reinstall.

Nor do the 'ubuntu-gnome-desktop' or 'gnome' meta-packages :(

I speak from experience. There are a gazillion small conflicts with 'unity-settings-daemon' and 'unity-control-center'.

---

### Post by gijs2 on 2014-05-31
> **kansasnoob said:**
> Nor do the 'ubuntu-gnome-desktop' or 'gnome' meta-packages :(

I speak from experience. There are a gazillion small conflicts with 'unity-settings-daemon' and 'unity-control-center'.

Any way to set unity to default settings?

---

### Post by kansasnoob on 2014-05-31
> **gijs2 said:**
> Any way to set unity to default settings?

I gave up and reinstalled. What meta-packages had you installed?

---

### Post by gijs2 on 2014-05-31
> **kansasnoob said:**
> I gave up and reinstalled. What meta-packages had you installed?

How can i check that, i think the latest version

---

### Post by kansasnoob on 2014-05-31
> **gijs2 said:**
> How can i check that, i think the latest version

But the latest version of what package?

Had you tried other desktop environments?

You can look in /var/log/apt:

```
lance@lance-desktop:~$ ls /var/log/apt
history.log  history.log.1.gz  term.log  term.log.1.gz

```

Usually the history.log is most useful, but notice that once it gets about so big the older parts of the log get archived as .1.gz, .2.gz, etc, etc.

Of all the desktop environments you've tried in 14.04 which did you like the best?

---

### Post by gijs2 on 2014-05-31
> **kansasnoob said:**
> But the latest version of what package?

Had you tried other desktop environments?

You can look in /var/log/apt:

```
lance@lance-desktop:~$ ls /var/log/apt
history.log  history.log.1.gz  term.log  term.log.1.gz

```

Usually the history.log is most useful, but notice that once it gets about so big the older parts of the log get archived as .1.gz, .2.gz, etc, etc.

I've added my history.log and term.log in the attachements since i have no clue where to look ^^.

> **kansasnoob said:**
> Of all the desktop environments you've tried in 14.04 which did you like the best?

After trying alot, my honest opinion is that Ubuntu is still the best.
Every other desktop enviroment has cool little tweaks but overall I like Ubuntu the most.

Now i've added the Numix theme to my Ubuntu to give it a bit of a nicer look to it.

---

### Post by kansasnoob on 2014-05-31
I see you've installed 'gnome-shell', 'gnome-shell-extensions', 'gnome-session-flashback, 'fvwm-crystal', and 'unity8-desktop-session-mir'. Then you later purged the meta-packages but just running autoremove leaves a lot of cruft.

If you give me about 24 hours I'll cook up some commands to try and get back to a pure Ubuntu but even then there are no guarantees.

Do yourself a favor though and remove 'tasksel' before it eats your whole desktop:

[https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/574287](https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/574287)

That bug has reared it's head off and on for many years.

---

### Post by gijs2 on 2014-05-31
> **kansasnoob said:**
> I see you've installed 'gnome-shell', 'gnome-shell-extensions', 'gnome-session-flashback, 'fvwm-crystal', and 'unity8-desktop-session-mir'. Then you later purged the meta-packages but just running autoremove leaves a lot of cruft.

If you give me about 24 hours I'll cook up some commands to try and get back to a pure Ubuntu but even then there are no guarantees.

Do yourself a favor though and remove 'tasksel' before it eats your whole desktop:

[https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/574287](https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/574287)

That bug has reared it's head off and on for many years.

Thanks for all of your effort in advance.

The link you send me already gave me an error when i try the second test case ^^

```
Can't call method "set" on an undefined value at /usr/share/perl5/Debconf/FrontEnd.pm line 126, <GEN0> line 5.Use of uninitialized value $ret in scalar chomp at /usr/share/perl5/Debconf/Client/ConfModule.pm line 132, <STDIN> line 4.
Use of uninitialized value $ret in split at /usr/share/perl5/Debconf/Client/ConfModule.pm line 133, <STDIN> line 4.
Use of uninitialized value $ret[0] in string eq at /usr/share/perl5/Debconf/Client/ConfModule.pm line 134, <STDIN> line 4.
Use of uninitialized value $ret[0] in string eq at /usr/bin/debconf-apt-progress line 173, <STDIN> line 4.
tasksel: aptitude failed (255)



```

---

### Post by kansasnoob on 2014-05-31
> **gijs2 said:**
> Thanks for all of your effort in advance.

The link you send me already gave me an error when i try the second test case ^^

```
Can't call method "set" on an undefined value at /usr/share/perl5/Debconf/FrontEnd.pm line 126, <GEN0> line 5.Use of uninitialized value $ret in scalar chomp at /usr/share/perl5/Debconf/Client/ConfModule.pm line 132, <STDIN> line 4.
Use of uninitialized value $ret in split at /usr/share/perl5/Debconf/Client/ConfModule.pm line 133, <STDIN> line 4.
Use of uninitialized value $ret[0] in string eq at /usr/share/perl5/Debconf/Client/ConfModule.pm line 134, <STDIN> line 4.
Use of uninitialized value $ret[0] in string eq at /usr/bin/debconf-apt-progress line 173, <STDIN> line 4.
tasksel: aptitude failed (255)



```

**[COLOR="#FF0000"]DO NOT run any of the test cases in that bug report![/COLOR]**

I just noticed you had installed the package 'tasksel' which can be quite hazardous, in that it forcefully blows up the whole OS! So I said just "remove tasksel"!

---

### Post by kansasnoob on 2014-05-31
I also notice that you installed bum and rcconf. Why?

Were you following some guide like this:

[http://ksearch.wordpress.com/2014/05/13/improve-ubuntu-performance/](http://ksearch.wordpress.com/2014/05/13/improve-ubuntu-performance/)

If so just chalk it up to experience and reinstall.

---

### Post by mc4man on 2014-05-31
Plus - what's this about - 
install unity8-desktop-session-mir

---

### Post by gijs2 on 2014-06-01
> **kansasnoob said:**
> I also notice that you installed bum and rcconf. Why?

Were you following some guide like this:

[http://ksearch.wordpress.com/2014/05/13/improve-ubuntu-performance/](http://ksearch.wordpress.com/2014/05/13/improve-ubuntu-performance/)

If so just chalk it up to experience and reinstall.

I did follow a tutorial like that, not exactly that one but it was similair to that.

> **mc4man said:**
> Plus - what's this about - 
install unity8-desktop-session-mir

My Unity did not work right, then i followed a tutorial and then it did.

---

### Post by kansasnoob on 2014-06-01
[B]This is a last-ditch effort so if you choose to proceed just understand that [COLOR="#FF0000"]there are no guarantess! If things blow up you get to keep all of the peices![/COLOR] If one step in the process fails DO NOT proceed with the rest (or even reboot or log out) until you figure out why!
[/B]
If you've not already backed up any important data to an external source do so now!

Open System Settings > User Accounts, unlock, select Automatic Login = Off, lock again, then run:

```
sudo dpkg-reconfigure lightdm
```

Select lightdm as the default display manager (just use the arrow keys to highlight lightdm and the Tab key to select OK, then the Enter key to complete), then close all running apps and reboot. You should be confronted with the Unity Greeter but if you automatically just login then go back to System Settings > User Accounts, unlock, select Automatic Login = Off, lock again. Then perform another reboot to be sure auto-login is off and be sure to select Ubuntu as the running session.

**Only once that completes successfully** you can proceed to remove the unwanted bits:

**NOTE**: The command is incredibly long so must be properly copy-n-pasted. It ends with && sudo apt-get install ubuntu-desktop^ which is important because an incomplete command will leave you with a totally borked system!

The **[COLOR="#FF0000"]^[/COLOR]** is NOT a typo, it invokes tasksel and helps resolve missing dependencies but **[COLOR="#FF0000"]it must never be used in conjunction with apt-get remove![/COLOR]**

```
sudo apt-get purge xfwm4 gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdm-1.0 gir1.2-gkbd-3.0 gir1.2-gtop-2.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-nmgtk-1.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs gnome-icon-theme-full gnome-shell gnome-shell-extensions gnome-themes-standard gnome-themes-standard-data gtk2-engines-pixbuf libcaribou-common libcaribou0 libgdm1 libgjs0e libmozjs-24-0 libmutter0c libxcb-xf86dri0 mutter-common xserver-xephyr alacarte gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data gnome-control-center gnome-control-center-data gnome-media gnome-panel gnome-panel-data gnome-session gnome-session-flashback gnome-settings-daemon gstreamer0.10-gconf indicator-applet-complete libgnome-media-profiles-3.0-0 libgoa-backend-1.0-1 libpanel-applet-4-0 metacity notification-daemon audacious audacious-plugins audacious-plugins-data fvwm fvwm-crystal fvwm-icons gawk gtk2-engines-pixbuf hsetroot imagemagick imagemagick-common libaudclient2 libaudcore1 libbinio1ldbl libbs2b0 libcue1 libencode-locale-perl libfile-listing-perl libfont-afm-perl libgif4 libglade2-0 libguess1 libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libid3tag0 libimlib2 libio-html-perl libjpeg-progs libjpeg-turbo-progs liblqr-1-0 liblwp-mediatypes-perl liblwp-protocol-https-perl libmagickcore5 libmagickcore5-extra libmagickwand5 libmowgli2 libmpdclient2 libnet-http-perl libnetpbm10 libperl4-corelibs-perl librplay3 libsidplayfp libsigsegv2 libstroke0 libwww-perl libwww-robotrules-perl libx11-protocol-perl mpc netpbm perl-tk pmount trayer xscreensaver xscreensaver-data  account-plugin-ubuntuone accountsservice-ubuntu-schemas accountsservice-ubuntu-touch-schemas apparmor-easyprof apparmor-easyprof-ubuntu click click-apparmor gir1.2-click-0.4 gir1.2-gee-0.8 gir1.2-json-1.0 gsettings-ubuntu-touch-schemas indicator-network libandroid-properties1 libboost-iostreams1.54.0 libboost-program-options1.54.0 libboost-serialization1.54.0 libcapnp-0.4.0 libclick-0.4-0 libcontent-hub0 libdbus-cpp2 libdee-qt5-3 libgflags2 libgoogle-glog0 libhud-client2 libhybris-common1 libjsoncpp0 liblttng-ust-ctl2 liblttng-ust0 libmediascanner-2.0-0 libmirclient7 libmirclientplatform-mesa libmirplatform libmirplatformgraphics-mesa libmirprotobuf0 libmirserver18 libofono-qt1 libonline-accounts-client1 libpgm-5.1-0 libprocess-cpp1 libqdjango-db0 libqgsttools-p1 libqmenumodel0 libqt5multimedia5-plugins libqt5multimediaquick-p5 libqt5multimediawidgets5 libqt5systeminfo5 libqt5xmlpatterns5 libsystemsettings1 libubuntu-application-api-mirclient1 libubuntu-application-api-mirserver1 libubuntu-application-api-test1 libubuntu-application-api1 libubuntu-download-manager-client0 libubuntu-download-manager-common0 libubuntu-download-manager-priv0 libubuntu-location-service0 libubuntu-platform-hardware-api1 libubuntuoneauth-2.0-0 libunity-api0 libunity-mir1 libunity-scopes1 libunwind8 libupstart-app-launch2 liburcu1 libusermetricsoutput1 libzmq3 libzmqpp3 mediascanner2.0 packagekit-tools python3-apparmor python3-apparmor-click python3-click python3-gnupg python3-libapparmor qmenumodel-qml qtdeclarative5-dee-plugin qtdeclarative5-folderlistmodel-plugin qtdeclarative5-gsettings1.0 qtdeclarative5-qtmultimedia-plugin qtdeclarative5-systeminfo-plugin qtdeclarative5-ubuntu-content0.1 qtdeclarative5-ubuntu-settings-components qtdeclarative5-ubuntu-settings-components-assets qtdeclarative5-ubuntu-thumbnailer0.1 qtdeclarative5-ubuntuone1.0 qtdeclarative5-unity-notifications-plugin qtdeclarative5-xmllistmodel-plugin qtubuntu-desktop qtubuntu-sensors sqlite3 suru-icon-theme system-image-common system-image-dbus thumbnailer-service ubuntu-download-manager ubuntu-keyboard-data ubuntu-mobile-icons ubuntu-purchase-service ubuntu-system-settings ubuntu-system-settings-online-accounts ubuntu-touch-sounds ubuntuone-credentials-common unity-plugin-scopes unity-scope-click unity-scope-mediascanner2 unity-scope-scopes unity-system-compositor unity8 unity8-desktop-session-mir unity8-private upstart-app-launch upstart-app-launch-tools url-dispatcher usermetricsservice && sudo apt-get install ubuntu-desktop^

```
**Only once that is complete ([COLOR="#FF0000"]which will take a long time[/COLOR]) run:**

```
sudo apt-get autoremove
```

Then run each of the following commands - **DO NOT use sudo!**

```
mv .compiz .compiz_OLD
```

```
mv .config .config_OLD
```

```
mv .gconf .gconf_OLD
```

```
mv .local .local_OLD
```

```
mv .cache .cache_OLD
```

Then reboot. The Ubuntu session should be the only one offered on the login screen so select it (if a selection is even offered) and login with your fingers crossed. That should get things as close to "out-of-box" as I'm capable of.

---

### Post by gijs2 on 2014-06-01
> **kansasnoob said:**
> [B]This is a last-ditch effort so if you choose to proceed just understand that [COLOR=#FF0000]there are no guarantess! If things blow up you get to keep all of the peices![/COLOR] If one step in the process fails DO NOT proceed with the rest (or even reboot or log out) until you figure out why!
[/B]
If you've not already backed up any important data to an external source do so now!

Open System Settings > User Accounts, unlock, select Automatic Login = Off, lock again, then run:

```
sudo dpkg-reconfigure lightdm
```

Select lightdm as the default display manager (just use the arrow keys to highlight lightdm and the Tab key to select OK, then the Enter key to complete), then close all running apps and reboot. You should be confronted with the Unity Greeter but if you automatically just login then go back to System Settings > User Accounts, unlock, select Automatic Login = Off, lock again. Then perform another reboot to be sure auto-login is off and be sure to select Ubuntu as the running session.



I cannot select anything, when i paste in the line in my terminal nothing happends:

```
Gijs:~# sudo dpkg-reconfigure lightdm
Gijs:~# 

```
Any ideas why?

---

### Post by gijs2 on 2014-06-01
> **kansasnoob said:**
> 
The **[COLOR=#FF0000]^[/COLOR]** is NOT a typo, it invokes tasksel and helps resolve missing dependencies but **[COLOR=#FF0000]it must never be used in conjunction with apt-get remove![/COLOR]**

```
sudo apt-get purge xfwm4 gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gck-1 gir1.2-gcr-3 gir1.2-gdm-1.0 gir1.2-gkbd-3.0 gir1.2-gtop-2.0 gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-nmgtk-1.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs gnome-icon-theme-full gnome-shell gnome-shell-extensions gnome-themes-standard gnome-themes-standard-data gtk2-engines-pixbuf libcaribou-common libcaribou0 libgdm1 libgjs0e libmozjs-24-0 libmutter0c libxcb-xf86dri0 mutter-common xserver-xephyr alacarte gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gnome-applets gnome-applets-data gnome-control-center gnome-control-center-data gnome-media gnome-panel gnome-panel-data gnome-session gnome-session-flashback gnome-settings-daemon gstreamer0.10-gconf indicator-applet-complete libgnome-media-profiles-3.0-0 libgoa-backend-1.0-1 libpanel-applet-4-0 metacity notification-daemon audacious audacious-plugins audacious-plugins-data fvwm fvwm-crystal fvwm-icons gawk gtk2-engines-pixbuf hsetroot imagemagick imagemagick-common libaudclient2 libaudcore1 libbinio1ldbl libbs2b0 libcue1 libencode-locale-perl libfile-listing-perl libfont-afm-perl libgif4 libglade2-0 libguess1 libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libid3tag0 libimlib2 libio-html-perl libjpeg-progs libjpeg-turbo-progs liblqr-1-0 liblwp-mediatypes-perl liblwp-protocol-https-perl libmagickcore5 libmagickcore5-extra libmagickwand5 libmowgli2 libmpdclient2 libnet-http-perl libnetpbm10 libperl4-corelibs-perl librplay3 libsidplayfp libsigsegv2 libstroke0 libwww-perl libwww-robotrules-perl libx11-protocol-perl mpc netpbm perl-tk pmount trayer xscreensaver xscreensaver-data  account-plugin-ubuntuone accountsservice-ubuntu-schemas accountsservice-ubuntu-touch-schemas apparmor-easyprof apparmor-easyprof-ubuntu click click-apparmor gir1.2-click-0.4 gir1.2-gee-0.8 gir1.2-json-1.0 gsettings-ubuntu-touch-schemas indicator-network libandroid-properties1 libboost-iostreams1.54.0 libboost-program-options1.54.0 libboost-serialization1.54.0 libcapnp-0.4.0 libclick-0.4-0 libcontent-hub0 libdbus-cpp2 libdee-qt5-3 libgflags2 libgoogle-glog0 libhud-client2 libhybris-common1 libjsoncpp0 liblttng-ust-ctl2 liblttng-ust0 libmediascanner-2.0-0 libmirclient7 libmirclientplatform-mesa libmirplatform libmirplatformgraphics-mesa libmirprotobuf0 libmirserver18 libofono-qt1 libonline-accounts-client1 libpgm-5.1-0 libprocess-cpp1 libqdjango-db0 libqgsttools-p1 libqmenumodel0 libqt5multimedia5-plugins libqt5multimediaquick-p5 libqt5multimediawidgets5 libqt5systeminfo5 libqt5xmlpatterns5 libsystemsettings1 libubuntu-application-api-mirclient1 libubuntu-application-api-mirserver1 libubuntu-application-api-test1 libubuntu-application-api1 libubuntu-download-manager-client0 libubuntu-download-manager-common0 libubuntu-download-manager-priv0 libubuntu-location-service0 libubuntu-platform-hardware-api1 libubuntuoneauth-2.0-0 libunity-api0 libunity-mir1 libunity-scopes1 libunwind8 libupstart-app-launch2 liburcu1 libusermetricsoutput1 libzmq3 libzmqpp3 mediascanner2.0 packagekit-tools python3-apparmor python3-apparmor-click python3-click python3-gnupg python3-libapparmor qmenumodel-qml qtdeclarative5-dee-plugin qtdeclarative5-folderlistmodel-plugin qtdeclarative5-gsettings1.0 qtdeclarative5-qtmultimedia-plugin qtdeclarative5-systeminfo-plugin qtdeclarative5-ubuntu-content0.1 qtdeclarative5-ubuntu-settings-components qtdeclarative5-ubuntu-settings-components-assets qtdeclarative5-ubuntu-thumbnailer0.1 qtdeclarative5-ubuntuone1.0 qtdeclarative5-unity-notifications-plugin qtdeclarative5-xmllistmodel-plugin qtubuntu-desktop qtubuntu-sensors sqlite3 suru-icon-theme system-image-common system-image-dbus thumbnailer-service ubuntu-download-manager ubuntu-keyboard-data ubuntu-mobile-icons ubuntu-purchase-service ubuntu-system-settings ubuntu-system-settings-online-accounts ubuntu-touch-sounds ubuntuone-credentials-common unity-plugin-scopes unity-scope-click unity-scope-mediascanner2 unity-scope-scopes unity-system-compositor unity8 unity8-desktop-session-mir unity8-private upstart-app-launch upstart-app-launch-tools url-dispatcher usermetricsservice && sudo apt-get install ubuntu-desktop^

```
**Only once that is complete ([COLOR=#FF0000]which will take a long time[/COLOR]) run:**



That gave me an error:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Package 'gir1.2-accountsservice-1.0' is not installed, so not removed
Package 'gir1.2-clutter-1.0' is not installed, so not removed
Package 'gir1.2-cogl-1.0' is not installed, so not removed
Package 'gir1.2-coglpango-1.0' is not installed, so not removed
Package 'gir1.2-gkbd-3.0' is not installed, so not removed
Package 'gir1.2-gtop-2.0' is not installed, so not removed
Package 'gir1.2-polkit-1.0' is not installed, so not removed
Package 'gir1.2-telepathylogger-0.2' is not installed, so not removed
Package 'gir1.2-xkl-1.0' is not installed, so not removed
Package 'gstreamer0.10-gconf' is not installed, so not removed
Package 'libid3tag0' is not installed, so not removed
Package 'libimlib2' is not installed, so not removed
Package 'libperl4-corelibs-perl' is not installed, so not removed
Package 'libubuntu-application-api-mirclient1' is not installed, so not removed
Package 'libubuntu-application-api1' is not installed, so not removed
Package 'alacarte' is not installed, so not removed
Package 'fvwm' is not installed, so not removed
Package 'fvwm-crystal' is not installed, so not removed
Package 'fvwm-icons' is not installed, so not removed
Package 'gir1.2-caribou-1.0' is not installed, so not removed
Package 'gnome-applets' is not installed, so not removed
Package 'gnome-applets-data' is not installed, so not removed
Package 'gnome-media' is not installed, so not removed
Package 'hsetroot' is not installed, so not removed
Package 'indicator-applet-complete' is not installed, so not removed
Package 'libcaribou-common' is not installed, so not removed
Package 'libcaribou0' is not installed, so not removed
Package 'libgnome-media-profiles-3.0-0' is not installed, so not removed
Package 'libmozjs-24-0' is not installed, so not removed
Package 'libmpdclient2' is not installed, so not removed
Package 'libmutter0c' is not installed, so not removed
Package 'librplay3' is not installed, so not removed
Package 'libstroke0' is not installed, so not removed
Package 'libubuntu-application-api-test1' is not installed, so not removed
Package 'libx11-protocol-perl' is not installed, so not removed
Package 'mpc' is not installed, so not removed
Package 'perl-tk' is not installed, so not removed
Package 'pmount' is not installed, so not removed
Package 'qtubuntu-desktop' is not installed, so not removed
Package 'qtubuntu-sensors' is not installed, so not removed
Package 'trayer' is not installed, so not removed
Package 'unity-system-compositor' is not installed, so not removed
Package 'unity8-desktop-session-mir' is not installed, so not removed
Package 'gir1.2-nmgtk-1.0' is not installed, so not removed
Package 'gnome-panel' is not installed, so not removed
Package 'gnome-panel-data' is not installed, so not removed
Package 'libpanel-applet-4-0' is not installed, so not removed
Package 'gir1.2-panelapplet-4.0' is not installed, so not removed
Package 'gnome-session-flashback' is not installed, so not removed
Package 'gdm' is not installed, so not removed
Package 'gjs' is not installed, so not removed
Package 'mutter-common' is not installed, so not removed
Package 'gnome-shell' is not installed, so not removed
Package 'gnome-themes-standard' is not installed, so not removed
Package 'gir1.2-telepathyglib-0.12' is not installed, so not removed
Package 'gir1.2-upowerglib-1.0' is not installed, so not removed
Package 'gir1.2-mutter-3.0' is not installed, so not removed
Package 'gnome-shell-extensions' is not installed, so not removed
Package 'gir1.2-gck-1' is not installed, so not removed
Package 'gir1.2-gcr-3' is not installed, so not removed
Package 'gnome-themes-standard-data' is not installed, so not removed
Package 'libgjs0e' is not installed, so not removed
Package 'libgdm1' is not installed, so not removed
Package 'gir1.2-gdm-1.0' is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 default-jre : Depends: openjdk-7-jre (>= 7~u3-2.1.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.



```

---

### Post by kansasnoob on 2014-06-01
Odd, I can see that gdm was installed along with gnome-shell but not where it was removed. Better have you post the output of both of these:

```
apt-cache policy lightdm
```

```
apt-cache policy gdm
```

---

### Post by gijs2 on 2014-06-01
> **kansasnoob said:**
> Odd, I can see that gdm was installed along with gnome-shell but not where it was removed. Better have you post the output of both of these:

```
apt-cache policy lightdm
```

```
lightdm:
  Installed: 1.10.1-0ubuntu1
  Candidate: 1.10.1-0ubuntu1
  Version table:
 *** 1.10.1-0ubuntu1 0
        500 http://nl.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.10.0-0ubuntu3 0
        500 http://nl.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```


> **kansasnoob said:**
> ```
apt-cache policy gdm
```

```
gdm:
  Installed: (none)
  Candidate: 3.12.2-0ubuntu1~trusty1
  Version table:
     3.12.2-0ubuntu1~trusty1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ trusty/main amd64 Packages
     3.10.0.1-0ubuntu3 0
        500 http://nl.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages

```

---

### Post by kansasnoob on 2014-06-01
> **gijs2 said:**
> That gave me an error:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Package 'gir1.2-accountsservice-1.0' is not installed, so not removed
Package 'gir1.2-clutter-1.0' is not installed, so not removed
Package 'gir1.2-cogl-1.0' is not installed, so not removed
Package 'gir1.2-coglpango-1.0' is not installed, so not removed
Package 'gir1.2-gkbd-3.0' is not installed, so not removed
Package 'gir1.2-gtop-2.0' is not installed, so not removed
Package 'gir1.2-polkit-1.0' is not installed, so not removed
Package 'gir1.2-telepathylogger-0.2' is not installed, so not removed
Package 'gir1.2-xkl-1.0' is not installed, so not removed
Package 'gstreamer0.10-gconf' is not installed, so not removed
Package 'libid3tag0' is not installed, so not removed
Package 'libimlib2' is not installed, so not removed
Package 'libperl4-corelibs-perl' is not installed, so not removed
Package 'libubuntu-application-api-mirclient1' is not installed, so not removed
Package 'libubuntu-application-api1' is not installed, so not removed
Package 'alacarte' is not installed, so not removed
Package 'fvwm' is not installed, so not removed
Package 'fvwm-crystal' is not installed, so not removed
Package 'fvwm-icons' is not installed, so not removed
Package 'gir1.2-caribou-1.0' is not installed, so not removed
Package 'gnome-applets' is not installed, so not removed
Package 'gnome-applets-data' is not installed, so not removed
Package 'gnome-media' is not installed, so not removed
Package 'hsetroot' is not installed, so not removed
Package 'indicator-applet-complete' is not installed, so not removed
Package 'libcaribou-common' is not installed, so not removed
Package 'libcaribou0' is not installed, so not removed
Package 'libgnome-media-profiles-3.0-0' is not installed, so not removed
Package 'libmozjs-24-0' is not installed, so not removed
Package 'libmpdclient2' is not installed, so not removed
Package 'libmutter0c' is not installed, so not removed
Package 'librplay3' is not installed, so not removed
Package 'libstroke0' is not installed, so not removed
Package 'libubuntu-application-api-test1' is not installed, so not removed
Package 'libx11-protocol-perl' is not installed, so not removed
Package 'mpc' is not installed, so not removed
Package 'perl-tk' is not installed, so not removed
Package 'pmount' is not installed, so not removed
Package 'qtubuntu-desktop' is not installed, so not removed
Package 'qtubuntu-sensors' is not installed, so not removed
Package 'trayer' is not installed, so not removed
Package 'unity-system-compositor' is not installed, so not removed
Package 'unity8-desktop-session-mir' is not installed, so not removed
Package 'gir1.2-nmgtk-1.0' is not installed, so not removed
Package 'gnome-panel' is not installed, so not removed
Package 'gnome-panel-data' is not installed, so not removed
Package 'libpanel-applet-4-0' is not installed, so not removed
Package 'gir1.2-panelapplet-4.0' is not installed, so not removed
Package 'gnome-session-flashback' is not installed, so not removed
Package 'gdm' is not installed, so not removed
Package 'gjs' is not installed, so not removed
Package 'mutter-common' is not installed, so not removed
Package 'gnome-shell' is not installed, so not removed
Package 'gnome-themes-standard' is not installed, so not removed
Package 'gir1.2-telepathyglib-0.12' is not installed, so not removed
Package 'gir1.2-upowerglib-1.0' is not installed, so not removed
Package 'gir1.2-mutter-3.0' is not installed, so not removed
Package 'gnome-shell-extensions' is not installed, so not removed
Package 'gir1.2-gck-1' is not installed, so not removed
Package 'gir1.2-gcr-3' is not installed, so not removed
Package 'gnome-themes-standard-data' is not installed, so not removed
Package 'libgjs0e' is not installed, so not removed
Package 'libgdm1' is not installed, so not removed
Package 'gir1.2-gdm-1.0' is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 default-jre : Depends: openjdk-7-jre (>= 7~u3-2.1.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.



```

Probably something broken from installing this:

> Start-Date: 2014-05-20  14:08:31
Commandline: apt-get install smartgithg
Install: gcj-jre-headless:amd64 (4.8.2-1ubuntu6, automatic), smartgithg:amd64 (5.0.8-0~eugenesan~trusty1), liberror-perl:amd64 (0.17-1.1, automatic), git-man:amd64 (1.9.1-1, automatic), git:amd64 (1.9.1-1, automatic), libgcj-common:amd64 (4.8.2-1ubuntu6, automatic), gcj-4.8-jre-lib:amd64 (4.8.2-19ubuntu1, automatic), mercurial-common:amd64 (2.8.2-1ubuntu1, automatic), gcj-4.8-jre-headless:amd64 (4.8.2-19ubuntu1, automatic), mercurial:amd64 (2.8.2-1ubuntu1, automatic), libgcj14:amd64 (4.8.2-19ubuntu1, automatic)
End-Date: 2014-05-20  14:08:57

I'd noticed you'd also installed yum. Almost impossible to resolve dependencies when packages have been compiled from source or installed via means other than an operating systems own package management system.

I very strongly recommend you simply reinstall and use more caution applying changes next time.

---

### Post by gijs2 on 2014-06-01
> **kansasnoob said:**
> Probably something broken from installing this:



I'd noticed you'd also installed yum. Almost impossible to resolve dependencies when packages have been compiled from source or installed via means other than an operating systems own package management system.

I very strongly recommend you simply reinstall and use more caution applying changes next time.

Smartgithg isn't the problem, Yum could be.

If I reinstall Ubuntu, would i have to reset my hard disk or is there a repair thing?

---

### Post by kansasnoob on 2014-06-01
I just noticed you even have the gnome3 staging PPA installed :(

[https://launchpad.net/~gnome3-team/+archive/gnome3-staging?field.series_filter=trusty](https://launchpad.net/~gnome3-team/+archive/gnome3-staging?field.series_filter=trusty)

What all PPA's do you have installed?

You should use ppa-purge to clean up the PPA mess and then try that long command again.

You really have created quite a mess and you clearly don't read and follow directions as requested, eg that PPA clearly states:

> === *WARNING* ===
The packages here have been deemed not ready for general use, they have known bugs and/or regressions, sometimes of a critical nature. Mostly things should run smoothly but be prepared to use ppa-purge, when you encounter issues!

If they break your system, you get to keep both halves.

=== Installing ===
To use this PPA, you should enable the main GNOME3 PPA.

- You need to run 'sudo apt-get dist-upgrade' to avoid problems. Please read the output before entering 'Y' to make sure important packages won't be removed.

=== Removing ===
Use ppa-purge to remove this PPA.

And in post #62 I said:

> If one step in the process fails DO NOT proceed with the rest (or even reboot or log out) until you figure out why!


But before I had a chance to respond to the display manager thing you jumped right in head first.

So I'm done even attempting to help you.

---

### Post by gijs2 on 2014-06-02
Thanks for the troubles and thanks for all the effort.
I've decided to reinstall Ubuntu and be more carefull in the future, so far everything seems to work and i've installed all my programs again so that's great.
Solved~

---

### Post by chujen on 2014-08-24
I think **egeezer** was very near the answer.
I you open dconf-editor in a terminal, navigate to org>gnome>desktop>wm>preferences
You will find at the right windows -> button-layout
You can see: close,minimize,maximize:
Double clic on the value and write ->   :minimize,maximize,close
Pay attention that it starts with colon
That indicates that the buttons will be placed at the right side.
The change is automatic. Close the dconf editor.

---

