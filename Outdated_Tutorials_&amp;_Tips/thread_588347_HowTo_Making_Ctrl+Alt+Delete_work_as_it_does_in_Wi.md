---
title: "HowTo: Making Ctrl+Alt+Delete work as it does in Windows"
date: 2005-06-12
forum: Outdated Tutorials &amp; Tips
---

### Post by bobgreen5s on 2005-06-12
This is how to make CTRL+ALT+DELETE open up the gnome-system-monitor:

```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"

gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```

**Edit**: See [post #20 of the thread](http://ubuntuforums.org/showpost.php?p=3611118&postcount=20) for how to do it with Compiz on 7.10 (Gutsy Gibbon).

---

### Post by moment on 2005-06-12
Should we emulate that lethal blue screen of Windows as well?  :) 

I have the "System Monitor" added to my panel and I can reach to gconftool by just a click of mouse. But I don't use it for GUI applications. I binde <Control><Alt>k to xkill and whenever a GUI application freezes I kill it by that. For non gui applications when I have a terminal open I just use killall.

---

### Post by jr0 on 2005-06-24
Will this work for Kubuntu? I'd try but I don't know linux too good yet...
(just windoze)

---

### Post by benplaut on 2005-06-24
[QUOTE=jr0]Will this work for Kubuntu? I'd try but I don't know linux too good yet...
(just windoze)[/QUOTE]

unfortunately, no... it won't  :?

---

### Post by evs on 2005-06-24
[QUOTE=jr0]Will this work for Kubuntu? I'd try but I don't know linux too good yet...
(just windoze)[/QUOTE]

Ctrl + Esc brings up KSysGuard in KDE/Kubuntu, which is the equivalent of System Monitor

---

### Post by MetalMusicAddict on 2005-06-24
[QUOTE=bobgreen5s]This is how to make CTRL+ALT+DELETE open up the gnome-system-monitor:

```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"

gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```[/QUOTE]
Thanx man. I was TOTALLY tryin to figure this out. ;)

---

### Post by jr0 on 2005-06-25
hmm. I get bash: gconftool-2: command not found
(Kubuntu) and too drunk to dig deeper at this time  ;-)

---

### Post by wirjo on 2005-06-25
[QUOTE=jr0]hmm. I get bash: gconftool-2: command not found
(Kubuntu) and too drunk to dig deeper at this time  ;-)[/QUOTE]
 It only works in Gnome.

---

### Post by jr0 on 2005-06-25
Damn gnome. 
We'll see about that once I gain more KDE experience...(and sober up ;P )

---

### Post by manicka on 2005-06-25
[QUOTE=bobgreen5s]This is how to make CTRL+ALT+DELETE open up the gnome-system-monitor:

```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"

gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```[/QUOTE]
 Emulating windows functions.... tut tut ;)

---

### Post by FrzzMan on 2005-06-25
[QUOTE=manicka]Emulating windows functions.... tut tut ;)[/QUOTE]
 lol... Windoze have something good bro :D

It works great, thanks.

---

### Post by evs on 2005-06-25
[QUOTE=jr0]Damn gnome. 
We'll see about that once I gain more KDE experience...(and sober up ;P )[/QUOTE]

When you sober up a little more, try  Ctrl+Esc, it's a default shortcut in KDE to bring up the Process Table in KDE System Guard.  (Just like Windows Ctrl+Alt+Del  )

---

### Post by jr0 on 2005-06-25
Hey thanks, I'm sober now. There must be a way to make Ctrl+Alt+Delete bring up KDE's process table instead of a shutdown prompt, but.. Ctrl+Esc ain't so bad, and this is a bit of a "nitpick feature" compared to other things I'd like to see. Like graphical bootup, and 100 other things from the How-To's.

I just got an image in Grub! Linux is great. \\:D/  At this rate I don't think I'll need LongHorn. I want to make a distro I can give to my grandma(for ex.) that even she can use (read:Windows-like). So far (k)Ubuntu is the only distro near that. 

Guys it's not bad to emu windows. If we want Linux on more desktops, it's got to get more familiar and intuitive for average PC users.. who happen to be running windoze at the moment. I have a list of what I'd like to change about Linux, but I think this isn't the place, and I need to learn more first...

BTW... I did it for KDE and it's probably even EASIER than Gnome (no terminal). In Kubuntu, you can simply go to your Control Center->Regional & Accessability->Keyboard Shortcuts. Scroll down the list to Desktop (it's near the bottom) and highlight "Show Taskmanager". Select "Custom" under Shortcut for Selected Action, and press Ctrl+Alt+Del to set it. Click Apply. 

Ta-da, now you have it in KDE/Kubuntu as well.  :grin:

---

### Post by Zeddicus on 2005-06-26
For the record, if you *really* like Windows-style shortcuts, you can set your shortcut scheme to Windows on that same page. :p

(in KDE, that is)

---

### Post by jr0 on 2005-06-27
Nice Zeddicus! Guess I missed that somehow.

---

### Post by noodle on 2005-06-27
Is there a way to do it in XFCE? Using Ctrl+Shift+Escape instead?

---

### Post by Jeff Eklund on 2005-09-17
Could you use this method to bind laptop keys/extra keys to specific commands? 
Does anyone know anyplace where I can read more about this to finally get my laptop keys working?

---

### Post by BLTicklemonster on 2005-10-09
LMAO, how cool is that. I guess I'm going to have to make a wallpaper that's a copy of a bsod, and make it say something like "windows has totally goofed up, defaulting to UBUNTU at this time" instead of the usual. :cool:

---

### Post by REDISISTone.nl on 2005-12-12
Good, works and I am used to this, :)

---

### Post by nusigmaforce on 2005-12-15
It was useful to me. Thanks

---

### Post by starpause on 2006-04-02
[QUOTE=noodle]Is there a way to do it in XFCE? Using Ctrl+Shift+Escape instead?[/QUOTE]

edit

/usr/share/themes/Default/xfwm4/keythemerc

(if it's not there, try "locate keythemerc" from the prompt and edit what you find)

change:

```

shortcut_3_key=Alt+Control+Delete
shortcut_3_exec=xflock4

```

to

```

shortcut_3_key=Alt+Control+Delete
shortcut_3_exec=xfce4-taskmanager

```

i don't know the easist way to get the changes to take effect ... login again? also, can someone point at a list of valid "key=" values? but Esc seems a safe bet.

**EDIT:**

i've installed **xbindkeys** and the package really rocks--the keybindings i made were instantly availible and **xbindkeys-config** made the configuration dead simple (with key-capture & trying out your commands). highly recommended!

---

### Post by redcharlie on 2006-06-28
I'm running Xubuntu 6.01,  and I'm trying to use alt-space instead of alt-tab to cycle windows for ease of use with vnc

I've got two keythemerc files
~/.themes/vnc/xfwm4/keythemerc
/usr/share/themes/Default/xfwm4/keythemerc

I've edited both to have the line
"cycle_windows_key=Alt+space"

and tried to switch using the settings manager->window manager->keyboard

also logging out and back in, and rebooting

nothing has an effect.  xfwm still uses alt-tab to cycle windows, conflicting with the host window in vnc

I've seen another posting with this problem
[http://www.ubuntuforums.org/showthread.php?t=177734&highlight=keythemerc](http://www.ubuntuforums.org/showthread.php?t=177734&highlight=keythemerc)
but the thread is closed :(

This has worked for me for xfce4 on Fedora...don't know what's wrong now...

---

### Post by redcharlie on 2006-07-21
Seems that locking down alt+tab is a "feature" of xfce 4.4 beta 1
[http://www.ubuntuforums.org/showthread.php?t=205455](http://www.ubuntuforums.org/showthread.php?t=205455)

Can't change it until we get another release of xfce :(

---

### Post by Epperly on 2006-07-21
Automatix also has an option to enable ALT+CTRL+DEL to system monitor.

---

### Post by Matuku on 2007-10-23
Many people who transfer over from Windows to Ubuntu often voice that they wish that Ubuntu had something similar (or in many cases exactly the same as) Ctrl+Alt+Delete in Windows so I thought, for my first howto, I'd show you how to do this in Gutsy Gibbon:

1) You will need to have the Advanced Desktop Effects Setting installed (CompizConfig Settings Manager for those who used it before). This can be done by:
```
 sudo apt-get install compizconfig-settings-manager 
```
or by searching for "CompizConfig" in Synaptic Package Manager. You may need to reboot after that in order to use it, I can't remember.

2) Now we have this we need to deactivate the current settings of Ctrl+Alt+Delete (which brings up the Log Out screen by default). To do this we go to System>Preferences>Keyboard Shortcuts and then scroll down until the Desktop section and then click on where it says Ctrl+Alt+Delete next to "Log Out" and it should change colour to dark orange and say "New Accelerator...". Just press the new key combination you want to use (I put Ctrl+Alt+End because it wasn't in use as far as I could see) or if you want to remove it entirely hit Backspace.

3) Now you need to go to System>Preferences>Advanced Desktop Effects Settings and then click General Options and go to the Commands tab.

4) In the Command Line 0 box (or whichever one is free) enter:
```
gnome-system-monitor
```

5) Now go to the Actions tab, open the Commands subsection and then click where it says "Disabled" alongside whichever "Run Command X" you assigned it to. This will bring up the "New Accelerator..." again and then you can just press Ctrl+Alt+Delete. After this close the Settings Manager and it should then bring up the Systems Monitor when you press Ctrl+Alt+Delete. (NB I had to reboot on one PC to get it to work but not another).

---

### Post by luckylucky on 2007-10-23
Thank you for submitting a HowTo... keep 'em coming!  Will try this out.

---

### Post by rickycodie on 2007-10-23
alot of people will hate me for this, an easy way to do it is to use automatix. although it might break your system.

---

### Post by sozz on 2007-10-23
Thanks for the trick!

---

### Post by detroitrockcity on 2007-10-23
Nifty!..:popcorn:

---

### Post by Scimu on 2007-11-01
Thanks a lot for this! :D

---

