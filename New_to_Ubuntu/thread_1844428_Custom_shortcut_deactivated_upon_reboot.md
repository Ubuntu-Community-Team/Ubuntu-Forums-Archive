---
title: "Custom shortcut deactivated upon reboot"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by setarigar on 2011-09-15
Ubuntu Unity 11.04

I have added the shortcut 'gnome-terminal -x tmux', called with <Ctrl> + <Alt> + T, via System Settings -> Keyboard Shortcuts -> add. It works, though after restarting the machine it seems the custom shortcut is not loaded properly. It is still present in the Keyboard Shortcuts window, and altering 'gnome-terminal -x tmux' slightly to 'gnome-terminal tmux' makes the shortcut work again, though same story upon restart. How do I make the custom shortcut work at start-up?

Bonus info: 1) Pre-defined shortcuts such as "Run a terminal" works at startup (with custom shortcut calls, e.g <Ctrl> + <Alt> + M). 2) My internet browser (Chrome) asks me whether I would like to set it as default after restart, even though I've done that in previous sessions (additional evidence that previous sessions are not stored properly). 3) I also tried adding the shortcut in (<Alt>F2) gconfig -> apps -> metacity -> keybinding_commands/global_keybindings, doesn't improve the situation.

Any ideas? Is Unity the culprit?

---

