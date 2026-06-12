---
title: "Windows ctrl-alt-del replacement"
date: 2020-06-13
forum: New to Ubuntu
---

### Post by nginmu on 2020-06-13
What's the best way to emulate, on lubuntu, Windows' ctrl-alt-del functionality?

I was thinking of trying to setup a key binding to allow ctrl-alt-del to fire up gnome-system-monitor, but would it also be an idea to set something up to restart the gui somehow, e.g. if an errant application (mainly google earth in my case) has hung in such a way as to disable the mouse and keyboard..

---

### Post by GhX6GZMB on 2020-06-13
I don't quite understand what you need. In Win10 the Ctrl-Alt-Del brings up:

```
Lock
Switch User
Sign out
Change a password
Task Manager
```

Which ones do you want?

---

### Post by T6&amp;sfpER35% on 2020-06-14
> [COLOR=#000000]has hung in such a way as to disable the mouse and keyboard..[/COLOR]

so how you going to press a key combination if the keyboard isn't working?

> [COLOR=#000000]Which ones do you want?[/COLOR]

the task manager i'd imagine?

you could set up a keyboard shortcut to open terminal ( i use F1 ) and in terminal type **xkill ,**that should enable you to click in the window that have crashed and kill it.
but of course,you're keyboard should be working...

---

### Post by guiverc on 2020-06-14
You haven't mentioned your release of Lubuntu.
Legacy Lubuntu using LXDE ?
or a modern Lubuntu using LXQt ?

[I]I didn't know what CTRL+ALT+DEL would do, so I pressed it. Turns out it brings up Qps (modern Lubuntu), but I don't read the manual enough like most of us ...
[/I][https://manual.lubuntu.me/stable/F/keyboard_shortcuts.html](https://manual.lubuntu.me/stable/F/keyboard_shortcuts.html)[https://manual.lubuntu.me/stable/3/3.2/3.2.14/shortcut_keys.html](https://manual.lubuntu.me/stable/3/3.2/3.2.14/shortcut_keys.html)

---

### Post by GhX6GZMB on 2020-06-14
The GUI task manager in Lubuntu 19.04 and newer is called htop. You could make shortcut key to that, if you want.

---

### Post by nginmu on 2020-06-14
19.10 64-bit

Yeah essentially it's something like the task manager I'm after. Emergency escape from hung gui system allowing either a return after killing off the problem, or at least a graceful shutdown

In Windows, ctrl-alt-del seems to be able to invoke the task manager even if the system has otherwise frozen to the extent that the mouse and keyboard are unresponsive in any applications or even the Windows GUI itself, allowing one to select and kill whatever is causing the problem (usually one can sort the entries by memory or cpu usage & that will indicate whatever process has gone awry)

I was having some success with ctrl-alt-f2, which drops my machine out of the lubuntu GUI into a virtual terminal. Once in the terminal using 'top' showed image names against process IDs, and then I could kill the process ID. Then get back into the GUI with ctrl-alt-f1 (from what I've read the exact ctrl-alt- sequence differs on different hardware)

This worked for a while but I eventually came across instances where Google Earth hung the system so badly that even ctrl-alt-f2 wouldn't drop me to a terminal.

I've only got 3Gb RAM on this system. I read Lubuntu wants at least 4, I've ordered 2 4Gb sodimm's so maybe that will prevent the GE crashes.. but interested in ways to gracefully escape a badly hung lubuntu gui all the same..

---

### Post by T6&amp;sfpER35% on 2020-06-14
i also has only 3Gb RAM and my google earth runs flawlessly .

---

### Post by GhX6GZMB on 2020-06-14
The sequence to get to a Terminal is normally Ctrl+Alt+t. To get back, closing it or typing 'exit' is usually enough.
3 GB is enough for Lubuntu, even 2 GB will run well. The lower limit of 4 GB is rather for Ubuntu.
And as said, HTOP is the GUI task manager in Lubuntu.

---

### Post by mastablasta on 2020-06-15
perorm REISUB when all is stuck: [https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

> [COLOR=#202122][FONT=sans-serif]A common use of the magic SysRq key is to perform a safe reboot of a Linux computer which has otherwise locked up (abbr. [/FONT][/COLOR]**REISUB**[COLOR=#202122][FONT=sans-serif]). This can prevent a [/FONT][/COLOR][COLOR=#202122][FONT=monospace][fsck]("https://en.wikipedia.org/wiki/Fsck")[/FONT][/COLOR][COLOR=#202122][FONT=sans-serif] being required on reboot and gives some programs a chance to save emergency backups of unsaved work.[/FONT][/COLOR][SUP][[4]]("https://en.wikipedia.org/wiki/Magic_SysRq_key#cite_note-4")[/SUP][COLOR=#202122][FONT=sans-serif] The QWERTY (or AZERTY) [/FONT][/COLOR][mnemonics]("https://en.wikipedia.org/wiki/Mnemonic")[COLOR=#202122][FONT=sans-serif]: "[/FONT][/COLOR]**R**[COLOR=#202122][FONT=sans-serif]aising [/FONT][/COLOR]**E**[COLOR=#202122][FONT=sans-serif]lephants [/FONT][/COLOR]**I**[COLOR=#202122][FONT=sans-serif]s [/FONT][/COLOR]**S**[COLOR=#202122][FONT=sans-serif]o [/FONT][/COLOR]**U**[COLOR=#202122][FONT=sans-serif]tterly [/FONT][/COLOR]**B**[COLOR=#202122][FONT=sans-serif]oring", "[/FONT][/COLOR]**R**[COLOR=#202122][FONT=sans-serif]eboot [/FONT][/COLOR]**E**[COLOR=#202122][FONT=sans-serif]ven [/FONT][/COLOR]**I**[COLOR=#202122][FONT=sans-serif]f [/FONT][/COLOR]**S**[COLOR=#202122][FONT=sans-serif]ystem [/FONT][/COLOR]**U**[COLOR=#202122][FONT=sans-serif]tterly [/FONT][/COLOR]**B**[COLOR=#202122][FONT=sans-serif]roken" or simply the word "BUSIER" read backwards, are often used to remember the following SysRq-keys sequence:[/FONT][/COLOR]
[LIST]
[*]un**R**aw (take control of keyboard back from [X]("https://en.wikipedia.org/wiki/X_Window_System")),
[*]t**E**rminate (send [FONT=monospace][SIGTERM]("https://en.wikipedia.org/wiki/SIGTERM")[/FONT] to all processes, allowing them to terminate gracefully),
[*]k**I**ll (send [FONT=monospace][SIGKILL]("https://en.wikipedia.org/wiki/SIGKILL")[/FONT] to all processes except [init]("https://en.wikipedia.org/wiki/Init"), forcing them to terminate immediately),
[*]**S**ync (flush data to disk),
[*]**U**nmount (remount all filesystems read-only),
[*]re**B**oot.
[/LIST]


---

### Post by nginmu on 2020-06-16
Thanks for your tips folks - appreciated

I've tried experimenting with the magic SysRq key but can't seem to get it to do anything.

On my Microsoft-branded UK qwerty keyboard there is no explicit SysRq key, but there is a PrtScn key which I've read is equivalent?

I read somewhere the content of /proc/sys/kernel/sysrq determines the state of enablement of the SysRq key, looking at my copy of the file it contains "176".

But the path of that file looks a bit scary to me so I haven't tried changing anything.. should I change "176" to "1" to enable SysRq? or am I trying the wrong keys?

---

### Post by TheFu on 2020-06-16
Support for 19.10 ends next month. I&#8217;d move to 20.04 now and see if that helps. There isn't any other choice at this point anyway.

if you use X11 then you can kill the xorg process. For most GUis, that would restart the session forcing a new login.  There used to be a <ctl>-<alt><bksp> method to kill X/Windows. Someone decided that wasn't useful about 5 yrs ago and removed it.
Gui lockups are seldom whole-system lockups though they appear that way to some users.  Just ssh in from another system or change to a different console and kill xorg.

---

### Post by tea for one on 2020-06-16
> **TheFu said:**
> Support for 19.10 ends next month. I&#8217;d move to 20.04 now and see if that helps. There isn't any other choice at this point anyway.

if you use X11 then you can kill the xorg process. For most GUis, that would restart the session forcing a new login.  There used to be a <ctl>-<alt><bksp> method to kill X/Windows. Someone decided that wasn't useful about 5 yrs ago and removed it.
Gui lockups are seldom whole-system lockups though they appear that way to some users.  Just ssh in from another system or change to a different console and kill xorg.

If you are using Gnome 3, Ctrl > Alt > Backspace is still available via gnome-tweaks.

Gnome-tweaks > Keyboard & Mouse > Additional Layout Options > Key sequence to kill the X server

Whoops - I've only just noticed the OP is using Lubuntu, therefore my comment is redundant.

---

### Post by tea for one on 2020-06-16
> **nginmu said:**
> Thanks for your tips folks - appreciated

I've tried experimenting with the magic SysRq key but can't seem to get it to do anything.

On my Microsoft-branded UK qwerty keyboard there is no explicit SysRq key, but there is a PrtScn key which I've read is equivalent?

I read somewhere the content of /proc/sys/kernel/sysrq determines the state of enablement of the SysRq key, looking at my copy of the file it contains "176".

But the path of that file looks a bit scary to me so I haven't tried changing anything.. should I change "176" to "1" to enable SysRq? or am I trying the wrong keys?

Ubuntu does not ship with REISUB fully enabled.

Here is a method to enable the process by editing a file:-

```
sudo nano /etc/sysctl.d/10-magic-sysrq.conf
```

Then change the number in line 26 from 176 to 244 i.e. **kernel.sysrq = 244**

I found the solution at this site [https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/](https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/) and the information was in section 3.

By the way, the last letter in the process B reboots your system, sometimes you may want to power off completely by substituting the **B** for an **O**

---

### Post by TheFu on 2020-06-16
> **nginmu said:**
>  
On my Microsoft-branded UK qwerty keyboard there is no explicit SysRq key, but there is a PrtScn key which I've read is equivalent? 

On my IBM 101M keyboard, the SysReq is on the same key as the Print Screen, just that the label is on the front, not on the top.  I'd take that to mean <alt>Print Screen would activate it. The "pause" key similarly has the "break" on the front of the key-cap.  I think the last time I used either keys was when I still used MS-DOS or DR-DOS.

No other keys have any front-labels on this keyboard.  There is not "Super" key either, though I've remapped the "Caps Lock" to be "Super" for my program launch controls (I don't use/have menus in my customized setup).

---

### Post by GhX6GZMB on 2020-06-16
> **TheFu said:**
> On my IBM 101M keyboard, the SysReq is on the same key as the Print Screen, just that the label is on the front, not on the top.  I'd take that to mean <alt>Print Screen would activate it. The "pause" key similarly has the "break" on the front of the key-cap.  I think the last time I used either keys was when I still used MS-DOS or DR-DOS.


That would normally mean using AltGr+PrtScr to get SysReq (I'm aware that AltGr doesn't exist on US keyboards). But SysReq really is a relict from the IBM 370 mainframe days and is not really defined for PCs. 
PrtScr is normally "take screenshot of full screen", Alt+PrtScr is "take screenshot of active window".
And on top, all this is language specific, US/UK keyboards differ.

For the desired functionality, I´d say the "Pause/Break" key makes more sense (it has no useful function anyway) and is a bit more logical from the name. And, you can assign it directly without Alt, Ctrl or other keys. 

OP, you'll need to find the right command sequence first. Assigning this to a Shortcut key in Lubuntu is child's play.

---

