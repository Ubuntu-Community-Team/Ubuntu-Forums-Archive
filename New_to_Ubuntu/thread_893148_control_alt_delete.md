---
title: "control alt delete"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by penguinee on 2008-08-18
Hi! It's been a while. I'm posting here because I am wondering what the Ubuntu-equivalent is for control-alt-delete in windows. Is there a similar function in ubuntu? Thanks!

---

### Post by tuxxy on 2008-08-18
Yes, I think you mean the system monitor, to view processes and applications etc

You could access it at **system > admin > sys monitor** I like to have it displayed at all times though by adding to desktop panel, right click your taskbar, click add to panel and find sys monitor

---

### Post by meanburrito920 on 2008-08-18
If you need to kill some misbehaving programs and the GUI is frozen, I Ctrl-Alt-F1 my way to a terminal, then log in and run top. Then kill that greedy little bugger. 

NOTE: don't hit ctrl-alt-del in linux, it will log off/shut down the computer depending on where you are when you press it.

---

### Post by alienexplorers on 2008-08-18
ctrl-alt-del on my system brings up the shutdown/restart screen.

---

### Post by K7522 on 2008-08-18
I had this listed in my [diary]("http://ubuntuforums.org/showthread.php?t=821208&page=3")


I wanted to set up System Monitor to CTRL+ALT+DEL so here's what I did:
System->Preferences->Keyboard Shortcuts
Desktop -> Logout and hit BACKSPACE to remove the shortcut.

```

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

```

EDIT: "System Monitor" is the equivelant of CTRL+ALT+DEL in windows, if you were wondering.

---

### Post by oldsoundguy on 2008-08-18
ctrl - alt - backspace will usually get you out of trouble without a total re-boot.

---

### Post by Oldsoldier2003 on 2008-08-18
> **oldsoundguy said:**
> ctrl - alt - backspace will usually get you out of trouble without a total re-boot.

Killing X is a little drastic. 

If you know what process or program is stuck you can easily kill it off in a terminal or by using xkill. 

If this isn't feasible just change to another tty (not terminal) buy CTRL+ALT+F1 then ps to get the pid of the stuck process and kill it from there. Once completed CTRL+ALT + F7 to return to the gui.

---

### Post by penguinee on 2008-08-20
> **K7522 said:**
> I had this listed in my [diary]("http://ubuntuforums.org/showthread.php?t=821208&page=3")


I wanted to set up System Monitor to CTRL+ALT+DEL so here's what I did:
System->Preferences->Keyboard Shortcuts
Desktop -> Logout and hit BACKSPACE to remove the shortcut.

```

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

```

EDIT: "System Monitor" is the equivelant of CTRL+ALT+DEL in windows, if you were wondering.




Yay! This was exactly what I was looking for! Thanks for the quick replies!

And thank-you to everyone else who contributed! :)

---

