---
title: "Equivelent to ctrl + alt +del in windows?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by swimm3r137@gmail.com on 2008-06-25
Hey in windows, whenever stuff froze or an application had an error or just firefox had an error, i used ctrl alt del alot and it was a simple way to end a program.  I now use ubuntu hardy, and love it, but is there any equivelent to this command in ubuntu cuz its always very helpful if i have to quickly close something.

---

### Post by sharks on 2008-06-25
To instant logout u can press ctrl--alt---backspace. it logs out restarting xserver.

---

### Post by dfreer on 2008-06-25
You can use System -> Administration -> System Monitor, very much like the Task Manager in Windows. There is even a way to bind it to ctrl+alt+delete, but I haven't managed to accomplish it in Hardy yet (tried using gconf-editor for metacity and compiz-manager, but for some reason it still just logs me out).

---

### Post by sharks on 2008-06-25
or this:
[www.howtogeek.com/howto/ubuntu/kill-a-process-by-process-name-from-ubuntu-command-line](www.howtogeek.com/howto/ubuntu/kill-a-process-by-process-name-from-ubuntu-command-line)

---

### Post by greyfox1 on 2008-06-25
I added System Monitor to my panel (right-click the panel and choose "add to panel") so not only can I keep an eye on my system stats, but I can launch System Monitor just by clicking on the system performance graphs right there on my panel!

---

### Post by dfreer on 2008-06-25
> **sharks said:**
> or this:
[www.howtogeek.com/howto/ubuntu/kill-a-process-by-process-name-from-ubuntu-command-line](www.howtogeek.com/howto/ubuntu/kill-a-process-by-process-name-from-ubuntu-command-line)

If you are using the command line, I like to launch htop to graphically view processes and kill them.

---

### Post by iaculallad on 2008-06-25
> **swimm3r137@gmail.com said:**
> Hey in windows, whenever stuff froze or an application had an error or just firefox had an error, i used ctrl alt del alot and it was a simple way to end a program.  I now use ubuntu hardy, and love it, but is there any equivelent to this command in ubuntu cuz its always very helpful if i have to quickly close something.

For the keyboard binding part: bind gnome-system-monitor to Ctrl+Alt+Del key combo.

```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

```

Other option would be Alt+F2 + xkill to find out "uncontrolled" applications.

---

### Post by Gripp on 2008-06-25
i think that ctrl+shift+esc should be assigned to the process viewer.  that is the case with windows.. and as far as i know there is no such short cut in ubuntu. 

>     *      CTRL + ALT+ F2 (get to a terminal, you can then run top/kill/pkill to discover and kill the offending process)
    *      ALT+ SYSRQ + R then CTRL + ALT+ F2 (as above, but first try to regain control of the keyboard)
    *      CTRL + ALT + Backspace (kills the graphic session and goes to a console, all graphical applications are terminated too)
    *      ALT+ SYSRQ + R then ALT + Backspace (as above, but first try to regain control of the keyboard)
    *      CTRL + ALT + DEL (reboot)
    *      ALT+ SYSRQ + R then CTRL + ALT + DEL (as above, but first try to regain control of the keyboard)
    *      ALT+ SYSRQ + R + S + U + B (forces a clean reboot even when the keyboard is not responding)

is from a wiki.  SYSRQ is the print screen key on my keyboard.  it may differ for you.

here is a good site with more answers to your question:

[http://www.freesoftwaremagazine.com/columns/closing_down_gnu_linux_safely_with_sysrq+](http://www.freesoftwaremagazine.com/columns/closing_down_gnu_linux_safely_with_sysrq+)

---

### Post by greyfox1 on 2008-06-25
Oh yeah, another thing: you might want to check out the "Force Quit" applet.  Very useful for misbehaving/frozen apps (right click a panel and choose "Add to Panel").  Cheers!

---

### Post by ryanhaigh on 2008-06-25
Alt-F2 to bring up run dialog, enter ```
xkill
``` then click on the app you want to terminate.

---

### Post by jmagsho on 2008-06-25
This is exactly what I use.  I created a drawer on the panel to house useful applets like force quit and just open it up and click away when I have an app that is misbehaving!

---

### Post by dfreer on 2008-06-26
> **iaculallad said:**
> For the keyboard binding part: bind gnome-system-monitor to Ctrl+Alt+Del key combo.

```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

```


Question is, how would you do this hardy with desktop effects enabled (not using metacity)?

EDIT: Come to think of it, the logout dialog still popped up even with desktop effects disabled and the metacity keybinding set, if I remember correctly.

---

### Post by barbedsaber on 2008-06-26
you can add a force quit applet to your panel.

---

### Post by billgoldberg on 2008-06-26
Yes, the "force quit" applet comes in handy sometimes.

But you could just use the terminal.

---

