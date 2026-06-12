---
title: "Evolution Mail Window"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by Ludwig9 on 2008-05-23
I am using Hardy and have generally been able to correct problems with fitting windows such as that of this forum onto my computer screen, but not that of Evolution Mail. Its window overlaps on the right side of screen, and I cannot see or access all of it. I see only as far as the "F" of "Current Folder." Please help!

---

### Post by Golem XIV on 2008-05-23
I don't understand what the exact problem is, but here are a few suggestions:

Can't you just drag the window (click and drag the title bar or press and hold the Alt key, then click and drag the window) so that the window is fully on screen?

If the window is too big, you can resize it by dragging the borders.

There is also the possibility that your monitor is not correctly adjusted.  Try adjusting the horizontal and vertical position of the picture on your monitor - it should have a menu for this kind of adjustments.

---

### Post by Ludwig9 on 2008-05-23
> **Golem XIV said:**
> I don't understand what the exact problem is, but here are a few suggestions:

Can't you just drag the window (click and drag the title bar or press and hold the Alt key, then click and drag the window) so that the window is fully on screen?

If the window is too big, you can resize it by dragging the borders.

There is also the possibility that your monitor is not correctly adjusted.  Try adjusting the horizontal and vertical position of the picture on your monitor - it should have a menu for this kind of adjustments.

I have a 17” Sony CPD-200ES Trinitron monitor with buttons on the front for adjusting color, geometry, size, and centering. I have tried to use them to correct the problem, but without success. I had a similar problem when I first installed the Ubuntu a couple of weeks ago: the icons for Trash and Shut Off on the desktop were barely visible in the lower and upper right-hand corners of the screen. I corrected this problem by choosing a different theme in System/Preferences/Appearance. But nothing works to correct the problem with Evolution Mail. I have tried dragging the edges of the window, but I cannot reach the right-hand edge of the window with my cursor. I can drag the left side of the message window to the left and thereby reduce the size of the Inbox/On This Computer window, but that does not make the right side of the message window appear. By pressing ALT and dragging, as you suggested, I have succeeded in moving the entire Evolution Mail window to the left, and have thus for the first time seen the up/down sliding bar on the right in the message window, but when I do this, I lose the left part of the screen, including File  Edit  View at the top. Any suggestions. It is very inconvenient not to have the up/down sliding bar visible on the right. 
I have changed and unchanged the settings in View/Layout, View/Preview, View/Current View, etc. but nothing fixes the problem. Thanks.

---

### Post by sayakb on 2008-05-23
Are you certain that it's not a monitor problem. Does you mouse go out of the screen when you move it to the extreme right side?

---

### Post by Ludwig9 on 2008-05-23
> **LinuxIsInnovation said:**
> Are you certain that it's not a monitor problem. Does you mouse go out of the screen when you move it to the extreme right side?
Certainty is beyond my capacity, but I don't think it's the monitor because I used to use a different  monitor, a Dell flat screen monitor which came with the computer, and I had the same problem, in even more extreme form. But by fiddling with the monitor buttons, I am now able to just see about a quarter of the up/down sliding bar. The cursor almost leaves the screen, but a little bit of it is visible. Before it left the screen entirely. 
However, now oddly I can no longer drag any of the window border lines, nor can I drag the windows with  ALT pressed.

---

### Post by cpsalvestrini on 2011-01-20
For evolution 2.30, there's a workaround for this: activate the express interface, which is built-in and has a notebook-friendly layout. I did this by renaming /usr/bin/evolution to /usr/bin/evolution-bin and then create a bash script that runs the following:

# /bin/bash
# Script to replace evolution
evolution-bin --express

One snag: the calendar part ceases to be available. This seems to be a bug in Evolution 2.30.

---

