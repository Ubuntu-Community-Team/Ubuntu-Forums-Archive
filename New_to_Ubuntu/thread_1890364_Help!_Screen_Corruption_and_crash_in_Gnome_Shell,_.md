---
title: "Help! Screen Corruption and crash in Gnome Shell, cannot report bug"
date: 2011-12-03
forum: New to Ubuntu
---

### Post by The Bright Side on 2011-12-03
Hey guys,

I'm on 11.10 Gnome Shell, and about once a day, there's a screen corruption around the "Activities" button right after boot, a random group of black squares flashing on and off. If I continue working, the corruption will get worse, and the top of the screen fills with garbage spreading from left to right. See my screenshots.

Eventually, Ubuntu crashes to the login screen.

Only occurs right after login. If it doesn't happen then, it never happens, so right now, when I see it, I log out and back in and I'm good.

I've been trying to file a bug using ubuntu-bug, but the application always tells me to call tech support, no matter which information I give it.

Does anybody have the same issue?
Did you find a way to solve it?
Do you know how I can get it into launchpad?
Do you know if there is already a bug for it?

My PC is a desktop. Hardware:
CPU: AMD Phenom II X6 1090T Six Core Processor AM3 3.2GHZ
Graphics: Gigabyte GeForce GTX 460 1GB Fermi 760MHZ

Software:
Ubuntu 11.10 64-bit
Gnome Shell
Nvidia 290.10 drivers

Screenies attached. Hope you can help me or point me in the right direction! Thanks. :-)

---

### Post by 2F4U on 2011-12-03
Did you look into the log files? Places to look at
- /var/log/syslog
- /var/log/Xorg.0.log
- .xsession-errors in your home directory

---

### Post by The Bright Side on 2011-12-03
Thanks man! Found the logs, but not sure what I'm looking for inside...

---

### Post by The Bright Side on 2011-12-06
I found out that when this bug appears, what's actually happens is that there is a console "hiding" behind the GUI. When I type anything, then what I am actually taping is an input into the console.

So for instance, when these corruptions appear, and I type the letter "r", it will restart Gnome Shell.

It's a bit hard to describe, but it's basically a mixture between GUI and command prompt. The GUI is there, but the command prompt is there inside the corruption and working.

Is there a way to turn off the Gnome Shell so I can see what's going on there?

---

### Post by Diametric on 2011-12-06
> **The Bright Side said:**
> I found out that when this bug appears, what's actually happens is that there is a console "hiding" behind the GUI. When I type anything, then what I am actually taping is an input into the console.

So for instance, when these corruptions appear, and I type the letter "r", it will restart Gnome Shell.

It's a bit hard to describe, but it's basically a mixture between GUI and command prompt. The GUI is there, but the command prompt is there inside the corruption and working.

Is there a way to turn off the Gnome Shell so I can see what's going on there?

I like this suggestion, or try logging into another desktop - if I recall there are several option on a base 11.10 install.  They can be found on the login screen upon a fresh boot.

---

### Post by The Bright Side on 2011-12-06
Hey Diametric (best avatar ever! :-)),

yeh, thing is, this bug only happens on first login. Once I log out and into another DE, the bug will be gone.

Ideally, there'd have to be a way to "switch off" the GUI and see the underlying console. I'm sure there is, as obviously, the console was there first and we're on Linux. Just don't know how to do it.

---

### Post by lolpenguin on 2011-12-07
> **The Bright Side said:**
> Hey Diametric (best avatar ever! :-)),

yeh, thing is, this bug only happens on first login. Once I log out and into another DE, the bug will be gone.

Ideally, there'd have to be a way to "switch off" the GUI and see the underlying console. I'm sure there is, as obviously, the console was there first and we're on Linux. Just don't know how to do it.

You want the console? There's 6 of them. Ctrl+Alt+F1/F2/F3/F4/F5/F6 will bring you to tty1/2/3/4/5/6. Ctrl+Alt+F7 will bring you back to the graphical session.
The issue really looks like a hardware problem.

---

### Post by Diametric on 2011-12-07
> **lolpenguin said:**
> You want the console? There's 6 of them. Ctrl+Alt+F1/F2/F3/F4/F5/F6 will bring you to tty1/2/3/4/5/6. Ctrl+Alt+F7 will bring you back to the graphical session.
The issue really looks like a hardware problem.

Agreed.  Don't forget that once you switch to a tty session like the previous poster said, if you want to get back to an x session just type:

```
startx
```

Yeah, I dig me some Mr. Torrence...lol.

---

### Post by The Bright Side on 2011-12-07
Yeah I was considering a hardware problem, too. But it started the day I installed 11.10 ... And I haven't changed any of my hardware since March.

Also, the thing is, I already have an "invisible" console running in the background, basically it _is_ the graphical corruption. When I type stuff, the corruption changes with every letter I type. And it seems that as soon as I press Enter (regardless of what I typed, but I'll have to double-check), it logs me out.

When I press ALT-F1-F7, it takes me to other consoles (tty1-6), but the problem's on tty7...

Next time I have the bug, I'll give it a shot though. Who knows what will happen :-) Thanks for your suggestions so far!

---

### Post by The Bright Side on 2011-12-12
I can now say that, when the corruption occurs, as soon as I press Enter, I am thrown back to the login screen (and then the bug is gone). I don't have to type anything first.

I have disabled the automatic login in Ubuntu (btw, changing account settings crashes Gnome Shell: panel and window decorations disappear, and it no longer responds to keystrokes like CTRL-ALT-DELETE), because I figure that if I have to go to the login screen every other time I boot, I may as well start out there.

Now, when the corruption occurs and I press CTRL-ALT-F1 to F7 to cycle through the consoles, about half of the screen is cleared, but the corruption stays.

I clearly remember seeing consoles displayed that way a couple distros ago: the graphics driver wouldn't properly switch to text mode, and show garbled pixel junk instead of the console.

I am now almost convinced that when this bug happens, Ubuntu boots into console mode, but overlays the GUI over the console in some way. I have no way of telling what the console is saying. There has to be some message there that explains what's going on.

If anybody is reading this, do you know how where Ubuntu's boot logs are? Is the log overwritten with each new boot, or can I see the log from when the bug occurs?

Attached screenshots show what's left of my login screen after I press CTRL-ALT-F1 while the bug occurs. When I go back to CTRL-ALT-F7, there's more corruption visible. The bits I highlighted in red are flashing cursors.

I will wipe my hard disk soon and completely reinstall my system. Will keep posting here.

---

### Post by lolpenguin on 2011-12-13
All the logs are in **/var/log/**.
This really shouldn't happen, there should be no overlap between the teletypes and the graphical session. This is really getting, uh, [insert adjective here].
Load a liveCD, install GNOME Shell and see if the problem persists. If it doesn't happen on other installs/live sessions, then it should be corruption of some sort.

---

