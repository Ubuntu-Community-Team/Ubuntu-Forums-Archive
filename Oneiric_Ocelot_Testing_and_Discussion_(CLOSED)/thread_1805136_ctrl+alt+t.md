---
title: "ctrl+alt+t"
date: 2011-07-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-07-15
is it just me or does the above shortcut key to open the terminal not working?

---

### Post by sgage on 2011-07-15
> **rburkartjo said:**
> is it just me or does the above shortcut key to open the terminal not working?

Well, at the moment I'm running in Gnome Shell, and the above key combo does not open a terminal.

---

### Post by mc4man on 2011-07-15
On a fresh install of todays iso among the multitude of things that don't work that is one

It seems to have been disabled in ccsm > gnome-compatibility > commands
For the moment you can re-enable there, may take a log out/in after

---

### Post by rburkartjo on 2011-07-15
tks mc

---

### Post by mc4man on 2011-07-15
Actually it may be better in the long run to set up in system settings > keyboard

---

### Post by jerrylamos on 2011-07-15
Doesn't work here either.  
Partial fix, select BFB enter t then when the terminal launcher icon appears select keep in launcher.

Big rub is, select terminal launcher winds me up in the same window when I wanted another.

Alt-F2 does work to run a command.  I haven't found Alt-F2 all that useful since the window closes and I can't see what the command did.

Jerry

---

### Post by mc4man on 2011-07-15
here I just keep an icon for the terminal and quicklists in unity launcher to open a new instance and one for a slightly larger terminal
Ex.  - gnome-terminal.desktop placed in ~/.local/share/applications (larger is sized appropriate for 13" ws laptop

```
[Desktop Entry]
Name=Terminal
Comment=Use the command line
TryExec=gnome-terminal
Exec=env UBUNTU_MENUPROXY=0 gnome-terminal
Icon=utilities-terminal
Type=Application
X-GNOME-DocPath=gnome-terminal/index.html
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-terminal
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=3.0.1
Categories=GNOME;GTK;Utility;TerminalEmulator;
X-Ubuntu-Gettext-Domain=gnome-terminal
X-Ayatana-Desktop-Shortcuts=NewTerminal;NewLargeTerminal;

[NewTerminal Shortcut Group]
Name=New Terminal
Exec=env UBUNTU_MENUPROXY=0 gnome-terminal
TargetEnvironment=Unity

[NewLargeTerminal Shortcut Group]
Name=New Large Terminal
Exec=env UBUNTU_MENUPROXY=0 gnome-terminal --geometry=140x34
TargetEnvironment=Unity


```

---

### Post by rburkartjo on 2011-07-15
jerry try this it works. first as mc said add the terminal to the unity bar. then install byobu terminal and also add the to the unity bar. when you want to a lot of terminals open separately. make sure the first one you open is the byobu terminal . then for any additional ones you want open in a separate process just click on the reg terminal icon. if you want a third then click on the reg terminal icon and so on. works like a charm i had over 7 separate terminal opened at once

---

### Post by VinDSL on 2011-07-16
> **rburkartjo said:**
> is it just me or does the above shortcut key to open the terminal not working?
Yes n' No...

After a fresh boot, Ctrl-Alt-T works for a while.

Then, after a couple of error messages pop up, here n' there (often unrelated), Ctrl-Alt-T quits working until I reboot.

I can't explain this behavior, but it's been happening in my install for a couple of weeks.

I might also mention, other things quit working too - like Nautilus, various indicators, et cetera.

When I've had enough of it, I reboot, and everything is fine again, for a while.

I figure it goes with the turf...  ;)

---

### Post by tlcstat on 2011-07-16
Greetings,
Works just fine on my Oneiric/Unity. And PS, thanks for the tip I didn't know that little shortcut existed.
tlcstat

Greetings,
Oops! Take that back! I have my Natty partition running. I'll check it out and let you know.
tlcstat

Greetings,
I booted my 11.10/Unity and the shortcut worked just fine. Did an update, and it still works fine. So the answer so far as I'm concerned is "it is still working".
tlcstat

---

