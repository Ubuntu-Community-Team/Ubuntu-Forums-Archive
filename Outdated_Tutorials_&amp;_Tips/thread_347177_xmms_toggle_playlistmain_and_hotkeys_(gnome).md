---
title: "xmms toggle playlist/main and hotkeys (gnome)"
date: 2007-01-26
forum: Outdated Tutorials &amp; Tips
---

### Post by siikah on 2007-01-26
I though I'd make my contribution to the 'tips and tricks' part of this forum.

Those of you that (before switching to Ubuntu) might have used STP on Windows since the dawn of time (just like me) of course are addicted to being able to toggle mainwin and playlist via hotkeys. STP was kind of a pioneer concerning hotkeys in Windows, global hotkeys from within games on Windows 98 wasn't exactly the usual behaviour of mp3players.

But enough of that.

What this little tip gives you, is hotkeys for xmms. If you don't know how to make custom hotkeys then read in. If you do, skip on to my togglescripts.

'xmms --help' outputs some interesting switches.
xmms -t = play/pause.
xmms -f = forward in playlist.
xmms -r = backwards in playlist.

Then what?

You need decide which keys you wish to use as hotkeys. You can find this out by either launching **Preferences -> Keyboard shortcuts**, or use the lovely program xev. 

If you stick with the first version you just launch it, pick one which isn't in use (says disabled) and press that text. It will switch to "New accelerator" (whatever...). Press the buttons you'd like for xmms to interpret as "backwards". I'll use ctrl+Left. The reason for this is to know how to write your combination in words so that Gnome understands it.

When pressing ctrl+left I'll get the text **<Control>Left**. Now ain't that something... Let's give Gnome some info.

Press alt+f2 to run **gconf-editor** (or use a terminal for that matter').

Hopefully you'll get the Configuration Editor on your screen. Expand **apps** and scroll down to **metacity**. Expand that one too.

global_keybindings is the interesting part atm. Select that one. Here you can enter custom hotkeys on the rows run_command_##. Select **run_command_1** and enter your combination of chosing, I'll write **<Control>Left**. Now Gnome knows which hotkey should "run command 1". But wtf is "command 1" ?

On the left part of the window, select keybinding_commands. Here you go! Doubleclick command_1 and enter **xmms -r** (which corresponds to backwards).

Do the same with any other switches or programs you'd like to be able to run through pressing a hotkey combination and close the editor. Of course, you use **run_command_X** and **command_X**. That's it.

But you can find that info anywhere. The real reason I'm writing this is because of I wish to be able to toggle my main- and playlist-window.

Since xmms doesn't have these options built in as cmdline-switches we'll need a plugin. A great one is **pyxmms-remote**. So:
**sudo apt-get pyxmms-remote**

This program has a gazillion of options so I'll just use the ones that are interesting here.
pyxmms-remote main_win_toggle 0/1
pyxmms-remote pl_win_toggle 0/1

Pretty self explaining huh?

Since you'd need two buttons to able to show (1) and hide (0) the main window we'll need a script which uses pyxmms's switches is_main_win and is_pl_win to make you able to just use one key to toggle the window.

Create a new text-file somewhere. Give it a name that makes sense. The file should have the following text in it:
```
 #!/bin/bash
if [ `pyxmms-remote is_main_win` == 1 ] 
then
pyxmms-remote main_win_toggle 0
else
pyxmms-remote main_win_toggle 1
fi
```
Of course, for Gnome to be able to execute it you'll need to chmod it.
**chmod +x /home/siikah/scripts/xmms_toggle_main**

In gconf-editor you'll just enter the path and filename as a **command_X**.

To toggle playlist, create another file and name it accordingly.
```
#!/bin/bash
if [ `pyxmms-remote is_pl_win` == 1 ]
then
pyxmms-remote pl_win_toggle 0
else
pyxmms-remote pl_win_toggle 1
fi
```

Bind it to a command and a key though gconf-editor, then play along with your new hotkeys.

For more info about what you might be able to do with **pyxmms-remote** go to [http://people.via.ecp.fr/~flo/2002/PyXMMS/doc/xmms.html](http://people.via.ecp.fr/~flo/2002/PyXMMS/doc/xmms.html).

I hope someone sometime finds this useful. I haven't been able to use an mp3player which I couldn't hide and pop back through shortcuts since I stumbled upon STP a long time ago (yeah, this was waaaay before winamp had any form of hotkey support). For more info about STP - Google for SysTrayPlay (haven't been actively developed for a long time, maybe that has changed lately).

My first tip, please keep the flames in private messages ;-)

---

### Post by Bazirker on 2007-08-27
If you are using a composite window manager such as compiz or beryl, this method doesn't work without paying attention to editing those values rather than metacity.

In compiz, you can do this in gconf-editor by going to apps-> compiz->  general-> allscreens-> options, and finding the command and run_command_key values there.

---

