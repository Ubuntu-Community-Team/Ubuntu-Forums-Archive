---
title: "[SOLVED] GConf-editor &amp;gt; Apps &amp;gt; Nautilus &amp;gt; Preferences &amp;gt; Show desktop"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by Piraja on 2008-08-04
Dear all,

I fiddled around with gconf-editor and unchecked "Show desktop" (Alt+F2 > gconf-editor > Apps > Nautilus > Preferences > Show desktop). Well, I got the desired effect — the desktop icons disappeared. However, I came to have second thoughts about this, especially because there were a couple of launchers I would have liked to keep on the desktop or recreate now that I seem to have destroyed them... And I also discovered that right-clicking on the desktop does nothing now; actually I'd like it to work as it used to, and also would like to have the other default desktop functionalities back in use. Checking the "Show desktop" option again seems to have no effect.

My distro's Hardy Heron. Thanks in advance!

---

### Post by Vivaldi Gloria on 2008-08-04
> **Piraja said:**
> Dear all,

I fiddled around with gconf-editor and unchecked "Show desktop" (Alt+F2 > gconf-editor > Apps > Nautilus > Preferences > Show desktop). Well, I got the desired effect — the desktop icons disappeared. However, I came to have second thoughts about this, especially because there were a couple of launchers I would have liked to keep on the desktop or recreate now that I seem to have destroyed them... And I also discovered that right-clicking on the desktop does nothing now; actually I'd like it to work as it used to, and also would like to have the other default desktop functionalities back in use. Checking the "Show desktop" option again seems to have no effect.

My distro's Hardy Heron. Thanks in advance!

I don't understand your problem. What do you want keep and what do you not want to keep on the desktop. Are you talking about the drive icons?

---

### Post by Piraja on 2008-08-04
Well, I would like to regain the settings that I had previously (i.e. before unchecking the "Show desktop" box). But the most important point is that I would like to be able to add launchers (etc.) by right-clicking on the desktop, as by default (i.e. before I played around with gconf-editor). I can only hope I'm clear enough.

**EDIT:**

My question can be reformulated as follows: I'd like to restore the settings I had previous to doing **Alt+F2 > gconf-editor > Apps > Nautilus > Preferences > uncheck "Show desktop" box**. The problem is that re-checking the "Show desktop" box doesn't seem to have any effect.

---

### Post by Vivaldi Gloria on 2008-08-04
> **Piraja said:**
> Well, I would like to regain the settings that I had previously (i.e. before unchecking the "Show desktop" box). But the most important point is that I would like to be able to add launchers (etc.) by right-clicking on the desktop, as by default (i.e. before I played around with gconf-editor). I can only hope I'm clear enough.

I understand what you want to keep but I don't understand which icons you do NOT want to keep. 

> Well, I got the desired effect — the desktop icons disappeared

Which desktop icons disappeared? Are you talking about the drive icons?

---

### Post by Piraja on 2008-08-04
OK, I think the question about the icons is not relevant any longer: they **all** disappeared and I can live with that. **BUT** I also lost the option of doing stuff by right-clicking on the desktop (i.e. adding launchers, etc.). So the thing is I would like to **add** icons to the desktop, not delete any. But perhaps losing the right-clicking option is something that should not have happened by changing Nautilus prefs in GConf-editor? (But it did &#8212; and I did not fiddle around with anything else, I think.)

---

### Post by Vivaldi Gloria on 2008-08-04
I suggest you check "show desktop" again and look at

GConf-editor > Apps > Nautilus > desktop

to get rid of the icons on the desktop.

---

### Post by NilsE on 2008-08-04
After you re-checked show desktop did you either restart gnome and nautilus or at least reboot.  I think that setting only takes effect on a restart.

---

### Post by Vivaldi Gloria on 2008-08-04
> The problem is that re-checking the "Show desktop" box doesn't seem to have any effect.

Ahh. Now I get it. Try restarting.

---

### Post by Piraja on 2008-08-04
Well, that's what I already did &#8212; and actually I **don't** want to get rid of icons. I'd rather **have them back**...

Perhaps I'll try to clarify the situation once more: In **GConf-editor > Apps > Nautilus > Preferences**, I do have the "Show desktop" box checked. I also checked the icons I want displayed in the Preferences. Maybe the following screenshots might help: 

[http://www.aijaa.com/v.php?i=2461828.png](http://www.aijaa.com/v.php?i=2461828.png)
[http://www.aijaa.com/v.php?i=2461838.png](http://www.aijaa.com/v.php?i=2461838.png)
[http://www.aijaa.com/v.php?i=2461848.png](http://www.aijaa.com/v.php?i=2461848.png)

The last screenshot shows that there are indeed no icons on my desktop...

**EDIT**: Sorry, this was meant as a reply to # 6. BTW, I also did reboot. Could you explicate the command line for restarting Gnome and Nautilus? Thanks!

---

### Post by Vivaldi Gloria on 2008-08-04
> **Piraja said:**
> I also did reboot. Could you explicate the command line for restarting Gnome and Nautilus? Thanks!

Hmm. It's weird that a reboot didn't fix it. Restarting gnome is pretty much equivalent to restarting your session. You can do it by pressing

CTRL + ALT + Backspace

---

### Post by Piraja on 2008-08-04
To V.G.'s #10: That's what I thought: reboot should probably do what restart (Ctrl+Alt+backspace) should. BTW, now I know ho to restart Gnome (optionally by sudo etc/init.d/gdm restart, I suppose), but I still wonder how to restart Nautilus...? Well, I suppose it doesn't really make any difference if reboot doesn't fix the prob.

---

### Post by Piraja on 2008-08-04
Oh, I might add that it's not just that I've lost the right-clicking-on-desktop function, but (perhaps obviously?) I cannot add launchers from the Applications menu either (e.g. Applications > Graphics > Kooka > right-click > Add this launcher to desktop) &#8212; while adding launchers to the panel still works.

---

### Post by Vivaldi Gloria on 2008-08-04
> **Piraja said:**
> how to restart Nautilus...? 

I think it's as simple as closing all nautilus windows.

```
pstree
ps -ef
``` 

shows all running apps. Use

```
ps -ef | grep <app_name>
```

to narrow it down. For example

```
vivaldi@narval:~$ ps -ef | grep nauti
1000     18203 18112  0 Aug03 ?        00:02:26 nautilus --no-default-window --sm-client-id default2
1000     25456 18538  0 16:15 pts/0    00:00:00 grep nauti
```

The second line is the "ps -ef | grep nauti" itself. The first is a nautilus window that I have open.

To kill an application use kill with the number in the second column. In the above example

```
sudo kill 18203
```

will kill that nautilus window.

If restarting didn't fix things, I don't know how you can fix it.

---

### Post by tacutu on 2008-08-04
I think you hit a bug. I can also reproduce the same on my computer.
It seems that when you uncheck the 'show desktop' option, nautilus dies (no longer in the ps aux list). Upon restart, it doesn't start-up automatically.

To fix: check back the 'show desktop' option and from a command line start nautilus. It will work.

BTW: this should not require restarting or rebooting, since all the changes made w/ config editor happen immediately. But, as I said, it seems you discovered a bug. Maybe you should report it to the Ubuntu developers.

---

### Post by Piraja on 2008-08-04
Thanks a lot tacutu! I will report the bug.

**EDIT**: The bug's already marked invalid, Launchpad #239488: "thank you for your bug report, do you have nautilus dialogs open when you change the value? you need to have nautilus running to react to such changes and if it's not managing the desktop and you don't use it it's not running [...] closing the bug, nautilus can't do changes when it's not running" ([https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/239488](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/239488)).

Interesting! Anyway, it's good to know that the simple solution of _Alt+F2 > nautilus_ reawakens the sleeping Nautilus.

---

