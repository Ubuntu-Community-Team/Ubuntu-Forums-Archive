---
title: "Computer shutdown via anyremote"
date: 2008-12-10
forum: Programming Talk
---

### Post by robi on 2008-12-10
Hi 
 
I would like to write a .cfg file for anyremote that would shutdown my computer. But I'm completely new to programing, so obviously I'm having some problems. 
I use anyremote with Totem application and i want to be able to shutdown my computer after watching a movie via my phone.
Here is a part of Totem.cfg, that i changed to add shutdown command

TOTEM_MENU=Set(menu,add,Fullscreen,File Browser,[COLOR="Red"]Shutdown[/COLOR]);
[COLOR="Red"]Shutdown=Exec(shutdown -h now)[/COLOR]

but nothing happens when i start the command, probably because shutdown command must be run as root...   If anyone has any ideas how to resolve this please let me know.

Thank you

---

### Post by mssever on 2008-12-10
> **robi said:**
> Hi 
 
I would like to write a .cfg file for anyremote that would shutdown my computer. But I'm completely new to programing, so obviously I'm having some problems. 
I use anyremote with Totem application and i want to be able to shutdown my computer after watching a movie via my phone.
Here is a part of Totem.cfg, that i changed to add shutdown command

TOTEM_MENU=Set(menu,add,Fullscreen,File Browser,[COLOR=Red]Shutdown[/COLOR]);
[COLOR=Red]Shutdown=Exec(shutdown -h now)[/COLOR]

but nothing happens when i start the command, probably because shutdown command must be run as root...   If anyone has any ideas how to resolve this please let me know.

Thank you
Put [font=Courier New]sudo[/font] before your shutdown command. You'll probably have to modify your sudoers file so that you won't have to provide a password to shutdown.

By the way, the command [FONT=Courier New]poweroff[/FONT] is simpler to remember than [FONT=Courier New]shutdown -h now[/FONT]. See also [FONT=Courier New]halt[/FONT] and [FONT=Courier New]reboot[/FONT].

---

### Post by robi on 2008-12-10
I added sudo in front of a command, and i added:
 
> %admin ALL = NOPASSWD: /sbin/shutdown

to sudoers file, and it works:D

Thank you very much

---

