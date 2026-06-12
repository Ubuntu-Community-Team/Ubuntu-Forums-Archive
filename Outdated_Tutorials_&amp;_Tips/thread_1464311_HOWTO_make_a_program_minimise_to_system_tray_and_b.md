---
title: "HOWTO: make a program minimise to system tray and back with a shortcut key"
date: 2010-04-28
forum: Outdated Tutorials &amp; Tips
---

### Post by jerremy-tamlin on 2010-04-28
In this HowTo I'll explain what I did to make gnome terminal minimize to the system tray and back when pressing the F12 key.
*Other programs should be able to be substituted in place of gnome terminal without affecting the procedure at all.*

Specifically I had to figure out three things.
[LIST=1]
[*]How to call a script when a particular key combination was pressed (KeyBinding)
[*]How to test if a window is minimized or not
[*]How to minimize and unminimize a window from within a shell script
[/LIST]

I'm using Ubuntu 9.04 *Jaunty Jackalope* and to do this I needed three programs.
[LIST]
[*]alltray - to minimise gnome-terminal to the tray
[*]wmctrl - to output some info about open windows
[*]devilspie - to do the minimising and unminimising
[/LIST]

Firstly there is a great tutorial on how to make a [_[COLOR="Blue"]transparent borderless Pop-up Terminal[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=81727") It's a little out of date but is well written and it enabled me to get it working with a minimal of fuss. This howto builds on and updates that one. However, You DO NOT need to have read that howto to make sense of this one.

Here's the process in a nutshell:
[LIST]
[*]Install Alltray
**sudo apt-get install alltray**
*Alltray is in the Universe repository, see [_[COLOR="Blue"]http://ubuntuguide.org[/COLOR]_]("http://ubuntuguide.org") for how to enable it.*
[*]Install xcompmgr **(Optional)**
*xcompmgr makes gnome-terminal's (and other) transparent background features 'truly' transparent rather than just allowing you to see the desktop background beneath an application like a portable hole.*

Make xcompmgr start automatically by adding an entry in System->Preferences->Startup Applications click "Add" & the command you want is "xcompmgr" (or you could add a .desktop file to ~/config/autostart/)
*Note: On my system new windows do not automatically appear on top of other windows when xcompmgr is running. This may be just an issue with my system as I haven't found any other reports of it. See below for a workaround.*

Now if in gnome-Terminal you go to Edit->Profile Prefferences->Background Tab. and select transparent background it should be truly transparent showing other windows below it.
[*]Install wmctrl and devilspie
**sudo apt-get install wmctrl devilspie**
[*] next you need to make a bash script and a devilspie script similar to those below
**Bash Script**
```
#!/bin/sh
# Launch gnome-terminal as drop-down window (alltray)
# Or if already running (determined with wmctrl) show/minimise it with devilspie

if (wmctrl -l | grep 'AllTray';) then
  devilspie /home/jerremy-tamlin/scripts/toggle_AllTray_Terminal.ds
else
  alltray -x -st -s -g 1270x400+7+0 --skip-taskbar "gnome-terminal --window-with-profile=tterm" &
  sleep 1 && wmctrl -r alltray -b add,above && echo Drop-Down Terminal Started OK;
fi
```
**wmctrl -l** lists information about open windows. grep searches this for a line containing 'AllTray'
*(Note if you want to use AllTray for more than one program you will need to alter this to be more specific.)*
**devilspie** runs with devilspie script (below) which either minimizes or give focus to the AllTray docked terminal.
The **alltray** command starts the gnome terminal with no border and the size of the top half of my screen
*(you may need to adjust the numbers for your screen size. They are WIDTHxHEIGHTxLEFTxTOP)*
The **--window-with-profile=** option of gnome terminal is so that the profile 'tterm' (can be whatever you call the profile) can be set to have no menu by default, etc.
**sleep 1** just waits for a moment to allow gnome-terminal and alltray to have been loaded.
**wmctrl -r alltray -b add,above** checks the "always on top" checkbox *See man wmctrl for more details*

**Devilspie Script**
*This should be placed somewhere other than ~/.devilspie/ so that it is not applied to ALL new terminal windows.*
```
(begin
  (if (matches (window_name) "(AllTray)")
    (if (matches (application_name) "Terminal")
      (if (matches (window_property "_NET_WM_STATE") "_NET_WM_STATE_HIDDEN")
	(begin
         (focus)
         (above)
	  (quit)
	)
	(begin
         (minimize)
	  (quit)
	)
      )
    )
  )
  (quit)
)
```
**(begin ... )** This is needed to perform more than one command.
**(if (matches (window_name) "(AllTray)")** This line is a 'matches' using regular expressions (window_name) against "(AllTray)" devilspie will go through all open windows and compare their window_name property with "(AllTray)". Adding "(debug)" to the start of the script will give you a readout of all these when run from a terminal.
**(if (matches (application_name) "Terminal")** Does the same thing but with the (application_name). This is important because, as I found when writing my scripts, some editors like gedit include the filename of the text file they are editing in their (window name) so the window name would be "toggle_AllTray_Terminal.ds (~/scripts) - gedit" which will match!
**(if (matches (window_property "_NET_WM_STATE") "_NET_WM_STATE_HIDDEN")** This line checks to see if the terminal is minimised (Hidden) or not.
[I]The (window_property) command is VERY useful! It allows you to check all kinds of things and has the format:
(window_property "_NET_WM_XXXXX") See [_[COLOR="Blue"]http://standards.freedesktop.org/wm-spec/1.3/ar01s05.html[/COLOR]_]("http://standards.freedesktop.org/wm-spec/1.3/ar01s05.html") for details on this specification.[/I]
**The structure of IF statements is** (if (matches (SOMETHING) "SOME TEXT") (THEN) (ELSE) ) The THEN and ELSE are handled simply by the order of statements NOT by a key word like in bash scripts. Here IF statements can have only **one** THEN argument and **one** ELSE argument. To have more than one we need to use **(begin ... )**
**(focus)** activates the terminal window bringing it to the front
**(above)** makes it 'always on top'
**(quit)** exits the script *without this the script does not end and you will end up with multiple scripts running but doing nothing*
**(minimize)** minimises the terminal. *AllTray ensures it goes back to the system tray*

There you have it. Test out these scripts in an ordinary terminal window to check that they work.
Test the devilspie script with: **devilspie toggle_AllTray_Terminal.ds**
Run the Bash Script with: **./whatever_you_called_it.sh**
*I called my script "gnome-terminal-drop-down.sh" because I like to be verbose :-) It helps when I'm looking back three years later and wondering what I did.*

Now all that is left is to associate the Bash Script with a shortcut key

This is really easy in Gnome using metacity (Standard Ubuntu) I'm not sure if its the same in KDE/Kubuntu so please let me know if you can.
You'll need to edit two keys in gconf-editor.
[LIST]
[*]In a terminal type:
**gconf-editor** *or you can press Alt+F2 to bring up gnome's "Run Application" dialogue and type it there.*
[*]In the folder like, tree structure, on the left navigate to the **keybinding_comands** /apps/metacity/keybinding_commands
[*]Find an unused **"command_X"** and select it.
[*]To Edit the Value you can either click on the value space or press ENTER.
[*]Enter the **full path to your Bash Script** [I]/home/jerremy-tamlin/scripts/gnome-terminal-drop-down.sh[\I]
[*]Next click the **"global_keybindings"** folder/category on the left.
*You should now be looking at /apps/metacity/global_keybindings*
[*]Find the **"run_command_X"** that corresponds to the command you entered and select it in the same manner
[*]Enter **"F12"** as the value for run_command_X and you're done! :-P
[I]You can substitute other values for "F12" If you want. I haven't found a list of acceptable values but below are the ones I've found to work.
[LIST]	F1 to F12
	Alpha Numeric
	Escape
	Break
	End
	Home
	Insert
	Up
	Down
	Left
	Right
	BackSpace
	Print
	Tab
	<Alt>
	<Ctrl> or <Control>
	<Shift>[/I][/LIST]
The global_keybindings take effect immediately so you can test them out without even closing the gconf-editor.
[/LIST][/LIST]

---------------------------
**Workaround: Create a devilspie script to activate (focus on) all new windows**
when run as a deamon, devilspie will apply all .ds scripts contained in /etc/devilspie or ~/.devilspie to each newly created window.

So simply create a devilspie script called focus_new_windows.ds and place it in your ~/.devilspie folder
```
(begin
  (focus)
)
```
Then to make it start automatically on startup:
[LIST]
[*]Go to System->Preferences->Startup Applications
[*]Click "Add"
[*]Enter:[LIST]Name: Devilspie
Command: devilspie
Description: Starts Devilspie[/LIST]
[*]Save and Close
[/LIST]
Devilspie will now start on startup and apply your focus_new_windows.ds to all new windows. :P


I Hope you're found this How To useful. :-D

---

### Post by badcloud56 on 2010-05-30
this was amazing, thanks so much :)

how do I implement the same thing on a specific non-alltray'ed program (e.g. minimise/maximise skype to bottom tray and not to system tray, or even better, to trigger the minimising *to* the system tray, since I don't want to use alltray on a program that has a built-in tray icon. the later would probably involve snooping around in skype's code, I ignorantly assume)

any thoughts on this?

---

