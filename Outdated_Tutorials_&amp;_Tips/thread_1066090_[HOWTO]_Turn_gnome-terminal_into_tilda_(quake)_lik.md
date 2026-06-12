---
title: "[HOWTO] Turn gnome-terminal into tilda (quake) like pop-up terminal"
date: 2009-02-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Hakimio on 2009-02-10
[SIZE="4"]_HOWTO: Turn gnome-terminal, konsole or xfce4-terminal into quake like pop-up terminal_[/SIZE]
**[COLOR="Red"]Updated 2011-03-20[/COLOR]**

[SIZE="3"]**Intro**[/SIZE]

There are a lot of pop-up terminal emulators like [_tilda_](http://tombuntu.com/index.php/2007/12/17/tilda-a-quake-style-terminal-for-gnome/), [_vterminal_](http://www.omgubuntu.co.uk/2011/02/vterminal-is-a-lightweight-pop-up-terminal/), [_guake_](http://guake.org/), [_Yakuake_](http://extragear.kde.org/apps/yakuake/) or [_Yeahconsole_](http://freshmeat.net/projects/yeahconsole/) to choose from, but if none of them satisfies you (none of them supports "drag and drop" functionality for example), I will present here two guides that can be used to turn any ordinary terminal (gnome-terminal, xfce4-terminal, konsole) into a neat pop-up terminal.

[The guides might look a bit long but that's mainly because I have included instructions for all the most popular ubuntu flavours - ubuntu, kubuntu and xubuntu.]

[SIZE="3"]**Guide #1**[/SIZE]
**[COLOR="Green"]Pros:[/COLOR]**
[LIST]
[*]Any keyboard shortcut can be used to hide the terminal
[/LIST]
**[COLOR="Red"]Cons:[/COLOR]**
[LIST]
[*]This guide will NOT work with default Xfce window manager xfwm4, because xfwm4 doesn't allow minimizing windows that have "skip_tasklist" attribute set. However, it will work for xfce users who use compiz instead of xfwm4.
[/LIST]

[LIST=1]
[*]Install the required software[LIST=1]
[*]```
sudo apt-get install devilspie xbindkeys
```
[*][_launch-restore_](http://ubuntuforums.org/showthread.php?p=2356588)
[/LIST]
[*]Set initial title for your terminal which will be used by devilspie a bit later
[LIST]
[*]**gnome-terminal**. Select Edit -> Profile Preferences, "Title and command" tab and input *Terminal* as initial title.
[*]**xfce4-terminal**. Select Edit -> Preferences and specify *Terminal* as initial title.
[*]**konsole**. Right click on the terminal and choose "Configure current profile" from the menu, then put *Terminal* as profile name. Plus there is one more step for this to work: go to "Tabs" tab and replace "Tab title format" with *%w*.
[/LIST]
[*]Get rid of the menubar[LIST]
[*]**gnome-terminal**. Select Edit -> Profile Preferences. Untick "Show menubar by default in new terminals"
[*]**konsole**. Settings -> Show menubar
[*]**xfce4-terminal**. Select Edit -> Preferences, switch to Appearance tab and untick "Display menubar in new windows"
[/LIST]
[*]Create .devilspie directory and open terminal.ds file (KDE users should replace gedit with kate and xfce with mousepad)
```
mkdir ~/.devilspie
gedit ~/.devilspie/terminal.ds
```
[*]Copy the following code to the text file you just opened:
```
; rule for pop-up terminal
( if 
( is ( window_name ) "Terminal" ) 
( begin 
( focus )
( skip_pager )
( skip_tasklist )
( stick )
( undecorate )
; terminal size: 660x400 position (relative to the upper left corner of the screen): +620+340 
( geometry "660x400+620+340" )
( println "match" )
)
)
```
[*]Edit the rule to customize terminal size and position (note the comments in the code)
[*]Open xbindkeys configuration file (KDE users should use kate and xfce - mousepad instead of gedit)
```
gedit ~/.xbindkeysrc
```
[*]Remove default rules (in most cases they are hindering more than helping) and add one of the following rules depending on what terminal emulator you are using (you can run "xbindkeys -k" to see how your preferred keyboard shortcut should be defined):[LIST]
[*]**gnome-terminal** (Gnome)
```
#Open/restore gnome-terminal by pressing Alt+Z
"launch-restore Gnome-terminal gnome-terminal"
Alt + z
```
[*]**konsole** (KDE)
```
#Open/restore konsole by pressing Alt+Z
"launch-restore Konsole konsole"
Alt + z
```
[*]**xfce4-terminal** (Xfce)
```
#Open/restore konsole by pressing Alt+Z
"launch-restore Xfce4-terminal xfce4-terminal"
Alt + z
```
[/LIST]
[*]Now it's time to specify some handy shortcut for hiding the terminal:
[LIST]
[*]**Gnome**. Run *gnome-keybinding-properties* and specify some keyboard shortcut for minimizing windows (if you can't find "Window Management" section there, it means that you are using compiz and should follow the same instructions as XFCE users in this case).
[*]**XFCE**. For this guide to work in XFCE you have to be using compiz. So, install compizconfig-settings-manager, run it (ccsm), select "General Options", "Key bindings" tab and specify some keyboard shortcut for minimizing windows. 
[*]**KDE**. Run *systemsettings*, click "Shortcuts and gestures", go to "Global keyboard shortcuts" section, select KDE component: Kwin and search for "Minimize window".
[/LIST]
[*]Add xbindkeys and devilspie to autostarted application list:[LIST]
[*]**Gnome**. Run gnome-session-properties.
[*]**XFCE**. Run xfce4-session-settings and go to "Application Autostart" tab.
[*]**KDE**. Run *systemsettings* and go to "Startup and Shutdown".
[/LIST]
[*]Finally you can log-out and log-in again (or just run xbindkeys and devilspie) and press keyboard shortcut you specified in xbindkeys config (8th step, Alt+Z by default) to start/show the terminal and the shortcut you specified for minimizing applications to hide it.
[/LIST]

[SIZE="3"]**Guide #2**[/SIZE]
**[COLOR="Green"]Pros:[/COLOR]**
[LIST]
[*]Can be used with any window manager including xfwm4 (default xfce4 window manager)
[/LIST]
**[COLOR="Red"]Cons:[/COLOR]**
[LIST]
[*]Unless you figure out how to fix alltray, very few keyboard buttons will be available for hiding the terminal.
[/LIST]

[LIST=1]
[*]Install all the software we'll need:
[LIST=1]
[*]```
sudo apt-get install xbindkeys alltray
```
[*][_launch-restore_](http://ubuntuforums.org/showthread.php?p=2356588)
[/LIST]
[*]Get rid of the menubar. Same as step 3 in guide #1.
[*]Open .terminal.sh (KDE users should use kate and xfce - mousepad instead of gedit)
```
gedit ~/.terminal.sh
```
[*]Now depending on what kind of terminal you are using copy one of the following bash scripts to the file[LIST]
[*]**gnome-terminal**
```
#!/bin/sh

if (wmctrl -l | grep 'AllTray';) then
	launch-restore Gnome-terminal gnome-terminal
else
	alltray -x -s -st -k 135 -g  660x400+706+210 -nt --skip-taskbar "gnome-terminal"
fi
```
[*]**konsole**
```
#!/bin/sh

if (wmctrl -l | grep 'AllTray';) then
	launch-restore Konsole konsole
else
	alltray -x -s -st -k 135 -g  660x400+706+210 -nt --skip-taskbar "konsole"
fi
```
[*]**xfce4-terminal**
```
#!/bin/sh

if (wmctrl -l | grep 'AllTray';) then
	launch-restore Xfce4-terminal xfce4-terminal
else
	alltray -x -s -st -k 135 -g  660x400+706+210 -nt --skip-taskbar "xfce4-terminal"
fi
```
[/LIST]
[*]Edit the script to suit your taste. Here are a couple of things that you might want to edit:
[LIST]
[*]660x400 here represents the size of the window
[*]+706+210 determines window position (+x+y) relative to the upper left corner of the screen
[*]-k switch followed by keycode determines the keyboard button to be used to hide the terminal. xev or "xbindkeys -k" command line utilities can be used to find out the keycode (135 is Menu - the key that acts like right mouse button). The problem here is that alltray hasn't been updated for a really long time and because of the changes to Xorg server now most of the keys can not be used here - they just cause alltray to crash. Some of the keys that worked for me are PrtSc (107), Menu (135), Insert (118). 
[*]-st switch means that the terminal will be visible on all workspaces (you can run "alltray --help" for some info about the other switches used here)
[/LIST]
[*]Make it executable:
```
chmod +x ~/.terminal.sh
```
[*]Open xbindkeys configuration file (KDE users should use kate and xfce - mousepad instead of gedit):
```
gedit ~/.xbindkeysrc
```
[*]Replace the contents of the file with the following rule which will determine the keyboard shortcut that will be used to show our terminal (in the example "Alt + W" is the shortcut but it can be replaced with anything that suits your taste- just run "xbindkeys -k" to see how your preferred keyboard shortcut should be defined)
```
#Open/restore terminal by pressing Alt + w
"sh $HOME/.terminal.sh"
	Alt + w
```
[*]Add xbindkeys to your autostarted application list
[LIST]
[*]**Gnome**. Run gnome-session-properties.
[*]**XFCE**. Run xfce4-session-settings and go to "Application Autostart" tab.
[*]**KDE**. Run *systemsettings* and go to "Startup and Shutdown".
[/LIST]
[*]Now you can log-out and log-in again (or just run xbindkeys) and press keyboard shortcut you specified in xbindkeys config (7th step, Alt+W by default) to start/show the terminal and the shortcut you specified in *.terminal.sh* script (steps 4 & 5, keycode after -k switch) to hide it.
[/LIST]

[SIZE="3"]**Tips**[/SIZE]
[LIST]
[*]xbindkeys has a handy tool for finding out how to define some hotkey:
```
xbindkeys -k
```
After executing the command just press some keys at once and you should see two ways to define the key combination.
[*]You can use [_gdevilspie_](http://www.gnomefiles.org/app.php?soft_id=2285) devilspie gui to add new rules.
[*]You can use xbindkeys-config xbindkeys gui to add new keyboard shortcuts.
[/LIST]

[SIZE="3"]**Similar guides**[/SIZE]
[HOWTO: Terminal as the desktop background.](http://ubuntuforums.org/showthread.php?t=202249)

---

### Post by Hakimio on 2011-03-20
The guide has been updated. Have fun everyone :)

---

### Post by jtarin on 2011-05-16
I like this. +1

---

### Post by Hakimio on 2011-05-17
> **jtarin said:**
> I like this. +1

Yay! It seems I didn't write it for nothing after all :D

---

### Post by 3 frags left on 2011-05-17
I'll make cowsay's words my words... =)
[[IMG]http://img846.imageshack.us/img846/8140/thanksh.th.png[/IMG]](http://img846.imageshack.us/i/thanksh.png/)
Oh, and one more thing: You can add the minimizing animation in Compiz to make it look exactly like Quake's console =)

---

### Post by mkarnicki on 2011-06-28
Hmm. I'd like to try this, but installing the launch-restore is scary. It says the .deb quality is poor.


```
The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organisation who provided this package file and include the details beneath.

Lintian check results for /home/karni/Desktop/launch-restore-0.52.deb:
E: launch-restore: wrong-file-owner-uid-or-gid usr/ 1000/1000
E: launch-restore: wrong-file-owner-uid-or-gid usr/local/ 1000/1000
E: launch-restore: wrong-file-owner-uid-or-gid usr/local/bin/ 1000/1000
E: launch-restore: wrong-file-owner-uid-or-gid usr/local/bin/launch-restore 1000/1000
```

Did you guys have the same issue? I didn't continue with the install :(

---

### Post by Hakimio on 2011-06-29
> **mkarnicki said:**
> 
Did you guys have the same issue? I didn't continue with the install :(

At least in ubuntu 10.10 and older it install just fine. If you are afraid that the deb package might break something, you can install it manually by just downloading the archive attached to this post, then launching nautilus as root ("sudo nautilus") and extracting the script in the archive to /usr/local/bin .

---

### Post by mkarnicki on 2011-06-29
Thanks! I'll give it a spin :)

---

