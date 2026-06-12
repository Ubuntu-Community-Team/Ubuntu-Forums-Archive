---
title: "Full-screened app killer / task manager coming anytime soon??"
date: 2011-05-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Yfrwlf on 2011-05-11
Are there any plans on implementing a task manager for 11.10, or is that a project that is going to be implemented for Wayland, and thus for Ubuntu 12.10?  I know there's already System Monitor, but implementing a way to call it on top of any existing hung full-screen app is what is needed, i.e. ctrl-alt-del on Windows.

So many users have problems killing a hung full-screen app, and knowledge of the terminal isn't something any Ubuntu user should be forced to know.  Windows did this right, but Linux can do it better!

[http://askubuntu.com/questions/33904/how-to-recover-from-fullscreen-crash](http://askubuntu.com/questions/33904/how-to-recover-from-fullscreen-crash)

---

### Post by seeker5528 on 2011-05-11
> **Yfrwlf said:**
> Are there any plans on implementing a task manager for 11.10, or is that a project that is going to be implemented for Wayland, and thus for Ubuntu 12.10?  I know there's already System Monitor, but implementing a way to call it on top of any existing hung full-screen app is what is needed, i.e. ctrl-alt-del on Windows.

Don't know if there are any plans for such a thing.

You could map 'Ctrl'+'Alt'+'Del' to gnome-system-monitor or ksysgaurd, don't know if there are equivalents in non-KDE/Gnome environments, 'Ctrl'+'Alt'+'Del' used to be mapped to ksysgaurd in KDE, don't know if that's still the case.

I do think it should be an option on whatever menu comes up when you hit 'Ctrl'+'Alt'+'+Del.

If one of the above doesn't work, then you probably have to switch to a VT and try to kill the stuff from there.

Next would be to stop/start GDM or whatever display manager you happen to be using assuming you were able to switch to a VT.

Or if you can't switch to a VT, use 'SysRq'+'K' to reset the current session the xserver is running in.  'Ctrl'+'Alt'+'Print Screen'+'K' simulates 'SysRq' if you don't have a 'SysRq' key or can't figure out what modifier makes 'SysRq' key work, usually (but not always) it would be the 'Alt' key if 'SysRq' is on a 'Print Screen/SysRq' key. 

Last resorts are 'SysRq'+'B' to shutdown or do a hard reset.

Just tried pressing (as opposed to holding in) the power button to see what the current state of that is, it did an immediate shut down, some times this works even when the computer is not responding to mouse or keyboard input. It would be nice if there was a small countdown to give you the option to opt out if it wasn't what you intended or you have small children around that like to push buttons.

Holding the power button in for 5 seconds or so should always trigger the hardware to do a hard shut off, could be some exceptions if there was a kernel panic. 

Later, Seeker

---

### Post by Yfrwlf on 2011-05-11
> **seeker5528 said:**
> You could map 'Ctrl'+'Alt'+'Del' to gnome-system-monitor or ksysgaurd, don't know if there are equivalents in non-KDE/Gnome environments, 'Ctrl'+'Alt'+'Del' used to be mapped to ksysgaurd in KDE, don't know if that's still the case.

Why yes you can, and this doesn't solve the problem at all for many full-screen hung apps as they take over the screen in such a way that alt-tab and other keystrokes are useless, the display is corrupted, and the only way out is to ALT-F* to a terminal.  That's the problem.  Windows has a CTRL-ALT-DEL screen that will cover/minimise any and all apps no matter how hung up they are unless the app managed to crash the driver.

Linux needs a bail-out mechanism like Windows has.



> **seeker5528 said:**
> If one of the above doesn't work, then you probably have to switch to a VT and try to kill the stuff from there.

Hence the problem.  Desktop users should never be forced to use a terminal.  Windows has a pretty and functional bail-out screen and does not require it.  Thus, recovering from frozen apps in Windows is cake.  Linux users such as myself would love a piece of that cake too.  If Ubuntu wants 200 million users, it needs to address shortcomings like this.



> **seeker5528 said:**
> Next would be to stop/start GDM or whatever display manager you happen to be using assuming you were able to switch to a VT.

Or if you can't switch to a VT, use 'SysRq'+'K' to reset the current session the xserver is running in.  'Ctrl'+'Alt'+'Print Screen'+'K' simulates 'SysRq' if you don't have a 'SysRq' key or can't figure out what modifier makes 'SysRq' key work, usually (but not always) it would be the 'Alt' key if 'SysRq' is on a 'Print Screen/SysRq' key. 

Last resorts are 'SysRq'+'B' to shutdown or do a hard reset.

I know, but Joe Sixpack doesn't, except for the hard reset of course, which is really sad to see someone do, especially if they lose any unsaved documents, while back on Windows they can do a simple ctrl-alt-del and be fine.

> **seeker5528 said:**
> Just tried pressing (as opposed to holding in) the power button to see what the current state of that is, it did an immediate shut down, some times this works even when the computer is not responding to mouse or keyboard input. It would be nice if there was a small countdown to give you the option to opt out if it wasn't what you intended or you have small children around that like to push buttons.

There is a Gnome setting where you can tell it to shut down the computer upon pressing the power button, or have it pop up with a prompt box on what to do.  The default setting Ubuntu ships with is the latter.  The latter is useless in the case of a frozen full-screen app, and the former, a reboot, isn't the way any user should have to deal with one frozen app when Windows can easily do so with a ctrl-alt-del.

---

### Post by jerrrys on 2011-05-11
i keep gnome-system-monitor in my panel and find that it can be accessed during a full screen freeze

---

### Post by Yfrwlf on 2011-05-11
> **jerrrys said:**
> i keep gnome-system-monitor in my panel and find that it can be accessed during a full screen freeze

Then it's obviously not a full-screen freeze?  I'm talking about the whole screen, including the Gnome panels.

It depends on how an app is locked up, sometimes you can manage to alt-tab out even, but even with apps that may allow you to see the Gnome panel, that are heavily glitching your desktop but BARELY allow you just enough access to your desktop to close them somehow, it's still **no where near as elegant as the Windows ctrl-alt-del screen**.

So I guess you got lucky?

---

### Post by jerrrys on 2011-05-11
it works most of the time, not all the time. so maybe i do get lucky.   but that would also make me think that this type of freeze is uncommon.   still your right, not the best of setups

maybe a shortcut key set to killall gnome-session ?

---

### Post by Yfrwlf on 2011-05-11
> **jerrrys said:**
> it works most of the time, not all the time. so maybe i do get lucky.   but that would also make me think that this type of freeze is uncommon.   still your right, not the best of setups

maybe a shortcut key set to killall gnome-session ?

Imagine Ubuntu shipping that as the default...no way in hell.  They got rid of ctrl-alt-backspace, they'd definitely not make ctrl-alt-del do the same thing.

As I said before, Xorg or Wayland needs a keypress which overrides any and all graphical applications on the desktop with a user-friendly GUI for terminating apps, as well as perhaps logging out, rebooting, etc, anything else that might be useful to have there.

You can't just say "Linux programs should be more stable!"  Well, yes, of course they should be, but that will never happen, and so Xorg and/or Wayland needs a built-in failsafe just like Windows (and OSX?) has.  It would be a great *feature* for the OS to *have*.

Nuff said.

---

