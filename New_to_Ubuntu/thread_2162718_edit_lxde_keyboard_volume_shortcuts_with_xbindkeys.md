---
title: "edit lxde keyboard volume shortcuts with xbindkeys"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by opiumpoetry on 2013-07-15
[COLOR=#323D4F][FONT=Lucida Grande]1. install xbindkeys in Synaptic or in terminal: sudo apt-get install xbindkeys xbindkeys-config[/FONT][/COLOR]

[COLOR=#323D4F][FONT=Lucida Grande]2. execute this in terminal: xbindkeys --defaults > ~/.xbindkeysrc (to create the necessary file)[/FONT][/COLOR]

[COLOR=#323D4F][FONT=Lucida Grande]3. to open xbindkeys GUI, execute this in terminal: xbindkeys-config[/FONT][/COLOR]

[COLOR=#323D4F][FONT=Lucida Grande]4. press the "New" button on bottom to create a new keybinding[/FONT][/COLOR]

[COLOR=#323D4F][FONT=Lucida Grande]5. the basics:[/FONT][/COLOR]

[COLOR=#323D4F][FONT=Lucida Grande]Name: Mute[/FONT][/COLOR]
[COLOR=#323D4F][FONT=Lucida Grande]Action: amixer sset Master toggle[/FONT][/COLOR]

[COLOR=#323D4F][FONT=Lucida Grande]Name: Increase volume[/FONT][/COLOR]
[COLOR=#323D4F][FONT=Lucida Grande]Action: amixer sset Master 1+ unmute[/FONT][/COLOR]

[COLOR=#323D4F][FONT=Lucida Grande]Name: Decrease volume[/FONT][/COLOR]
[COLOR=#323D4F][FONT=Lucida Grande]Action: amixer sset Master 1- unmute[/FONT][/COLOR]

[COLOR=#323D4F][FONT=Lucida Grande]6. after entering each "Name/Action" pair, press the "Get Key" button on right>>a blank white window will open (you may need to maximize it), press the key or combination of keys you want, and it will capture it for you; then hit the "Apply" button on right[/FONT][/COLOR]

[COLOR=#323D4F][FONT=Lucida Grande]7. go to the "File" tab in the upper left corner and hit "Save to default File" in the dropdown menu[/FONT][/COLOR]

[COLOR=#323D4F][FONT=Lucida Grande]8. add "xbindkeys &" to your autostart.sh file (you'll have to look for it in your distro) so it always runs on startup (this link might help [/FONT][/COLOR][http://peppermintos.net/viewtopic.php?f=8&t=5043](http://peppermintos.net/viewtopic.php?f=8&t=5043))[COLOR=#323D4F][FONT=Lucida Grande]
[/FONT][/COLOR]
[COLOR=#323D4F][FONT=Lucida Grande]Finished.[/FONT][/COLOR]

---

