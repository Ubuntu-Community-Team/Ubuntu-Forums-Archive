---
title: "Make window active...in another X screen"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by seanos on 2008-09-17
Is that title cryptic enough?  Let me explain.

I have nvidia config setup so that my TV is a separate X screen to the right of my monitor.  I have MythTV installed and can run it from the TV screen, although the resolution isn't optimal.  I have a wireless mouse and keyboard setup for use with the TV.

Problem is, if I do anything back at the computer while MythTV is running I lose focus on MythTV.  Since MythTV is full screen and only controlled by keyboard, not mouse, I can't figure out how to get focus back to that window and have to kill the process to do a simple thing like change channel.

Maybe this would be better in the multimedia forum, but I thought I'd post here first in case there was a simple solution.

---

### Post by northern lights on 2008-09-17
Can't you simply 'Alt+Tab' your way there?

---

### Post by seanos on 2008-09-17
> **northern lights said:**
> Can't you simply 'Alt+Tab' your way there?

No.  Alt-TAB only switches between programs on the computer's screen (Screen 0), never the TV (Screen 1).

In (nvidia) X Server Display Configuration I'm using the setting "Separate X screen" rather than "Twinview".  Compiz is running only on Screen 0, so that the TV output is much simpler.

---

### Post by Dill on 2008-09-18
A little while back someone wanted to take a screenshot of a certain window, no matter the workspace in which the window resided. While this isn't exactly your problem, you may find a tool like *wmctrl* helpful (and you should read the man page to check out its wealth of features). You can read the discussion here:
[http://ubuntuforums.org/showthread.php?t=893506](http://ubuntuforums.org/showthread.php?t=893506)

Cheers, 
Dylan

---

### Post by seanos on 2008-09-18
Thanks Dill.  I had found that thread, but thought it worth checking if there was a simpler solution that I'd missed.

I won't have a chance to look at this again until tomorrow, but a quick test of wmctrl had some odd results...

**Screen 1:**
```
sean@nung:~$ wmctrl -m
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  20 (X_GetProperty)
  Resource id in failed request:  0x26000b6
  Serial number of failed request:  12
  Current serial number in output stream:  12
sean@nung:~$ wmctrl -l
0x01200034  0 nung Painéal Ciumhaise Leathnaithe ag Bun
0x0120005f  0 nung Painéal Ciumhaise Leathnaithe ag Barr
0x014000c4  0 nung Deasc
sean@nung:~$ wmctrl -d
0  * DG: 1440x576  VP: 0,0  WA: 0,25 720x526  N/A
```

The only open window was terminal which was also missing its title bar.

**Screen 0:**
```
sean@nung:~$ wmctrl -m
Name: compiz
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
sean@nung:~$ wmctrl -l
0x02c001d0  0 nung Ubuntu notes - Google Notebook - Mozilla Firefox
0x030003df -1 nung N/A
0x0140001f -1 nung Deasc
0x01200004 -1 nung Painéal Ciumhaise Leathnaithe ag Barr
0x0120002f -1 nung Painéal Ciumhaise Leathnaithe ag Barr
0x04400005  0 nung sounds - Brabhsálaí Comhad
0x02c000ca  0 nung [all variants] Make window active...in another X screen - Ubuntu Forums - Mozilla Firefox
0x05200082  0 nung Synaptic Package Manager 
0x05400022  0 nung sean@nung: ~
0x054005e3  0 nung sean@nung: ~
sean@nung:~$ wmctrl -d
0  * DG: 1440x1800  VP: 0,0  WA: 0,51 1440x849  N/A

```

The next step is probably to disable the script that stops compiz working on screen 1.

---

### Post by Xnyper on 2008-10-28
I'm currently struggling with the same thing.  Though I have compiz running on both screens.  Every time I want to use something in the other screen I have to use the mouse (yuck) to make a window active over there.  Once one window is active I can alt-tab between windows in that screen, but I have to use the mouse to traverse screens.

perhaps some kind of script that will simulate a mouse click at a given location?

Did you ever find a solution?

---

### Post by seanos on 2008-10-28
No I haven't found a solution.  I've been away, but was back fiddling with Myth today.  I tried switching off "Hide mouse cursor", but you can't really get focus back with the mouse - only activate menu items that you can't get back from because you don't have focus.

My problem is a bit worse than yours I think, because MythTV (when it's showing TV) is full screen and doesn't respond to mouse-clicks, only the keyboard.  I suppose if I had some small app running that was always the top window (not that I know how to do that) that would be some kind of (bad) solution.

I'm hoping to get a box set up next week to just do TV/downloads, so that will probably be my solution.

It has given me a new appreciation though, for the way nvidia handle TV out under Windows.

---

