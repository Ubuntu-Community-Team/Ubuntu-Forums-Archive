---
title: "How do I change the default size of windows that are unmaximized?"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by bobsmith2 on 2008-09-26
When I "unmaximize" windows, they shrink such a tiny amount that I'm forced to manually resize them via dragging the corners, which is a complete pain. How do I change the default size of windows that are unmaximized?

---

### Post by bobsmith2 on 2008-09-28
Could someone confirm? Is this just something I will have to tolerate if I use Ubuntu? Or is there a fix? Thanks.

---

### Post by hijglander on 2008-09-29
Check [http://www.iuselinux.com/2008/09/how-to-change-default-terminal-size-in.html]("http://www.iuselinux.com/2008/09/how-to-change-default-terminal-size-in.html") for a solution...
Works for me. :D

---

### Post by binbash on 2008-09-29
If you are using compiz, there is a setting for this.

---

### Post by bobsmith2 on 2008-09-29
Binbash, where is the setting? I've searched and can't seem to find it.

---

### Post by bobsmith2 on 2008-09-29
OK, I'll try asking another way...

When you need to unmaximize a maximized window (Firefox, for example), and you click on the unmaximize button in the upper right, what does the window do? Does it shrink to a reasonably smaller size, or does it shrink by an amount that is so minuscule that the window is still (almost) maximized? 

My windows shrink by an amount that is so minuscule that the window is still (almost) maximized. So the ONLY way that I can get my windows to unmaximize is to go to the corner and manually drag the window to make it smaller. Is everyone else forced to do this? If not, how did you fix this?

---

### Post by binbash on 2008-09-29
sorry for my late reply.Look at "window rules" at compiz.You can define which will be maximized etc

---

### Post by bobsmith2 on 2008-09-29
Thanks binbash. I tried that, but windows rules forces windows to one size, which I don't want. Maybe I'm missing some setting. All I want to do is this: When I click on the button in the upper right to unmaximize a window, I want it to unmaximize to a reasonable size. By default it only shrinks by a minuscule amount - the window essentially stays maximized. I don't see any way to accomplish what I need using window rules. I can get the windows to perform a ballet for me if I want, or to do a thousand other completely useless things, but I don't see any way to get it to do a simple necessary thing like unmaximize to a sensible size. Does everyone else just tolerate this?

---

### Post by mc4man on 2008-09-29
Normally when you resize a window and then *close* it, the next time you open a window of the *same type* it will open at the same size. 
In other words -  if you were to open a text file, resize it with the mouse to half the screen and then close, when opening a different text file it will be that size. 
Same for firefox, try sizing it to what ever size you'd want,(in a un maximized state) *then close*. The next time you open it it should be the same. If you maximize it, then un maximize it should return to that size.

maybe better put like this
the 'un maximized size' is **set** by resizing a window of a particular type (class) and then closing. It remains at that size till it's reset by same method.

The closing state (maximized, unmaximized ) determines the next opening state (maximized, unmaximized) ( and the size if unmaximized

---

### Post by bobsmith2 on 2008-09-30
Thanks mc4man. You're right. However, in many programs I prefer to work with maximized windows (like Firefox) and I usually close them maximized. When you work with maximized windows, shrinking the window requires manually resizing every session (and with EVERY program I work in that is maximized). Gnome remembers the unmaximized size during each session, but every time I reboot or log off, I have to go through the whole routine again: 

1) Start the program maximized until I need to drag a link to the desktop (or whatever).
2) Hit the unmaximize button - the window shrinks by 2 or 3 pixels, which is completely useless.
3) Manually drag the corners to shrink the window to a reasonable size.
4) Move the window out of the corner (because when you're forced to resize by dragging a corner - the other corner stays put.

Steps three and four shouldn't be necessary. I can't understand why the default "unmaximize" size would be set to a completely useless size so that manual dragging and moving would be required - and with no way to change the problematic default size. If there is a way to change the default unmaximize size, I'd like to hear about it.

---

### Post by WWSmith36 on 2008-09-30
If using Compiz there is a utility that might help.

Try the Place Windows module in the Windows Management sections.  In the general tab make sure that Placement mode is set to Smart.

Hope this helps

---

### Post by bobsmith2 on 2008-09-30
Thanks WWSmith36. I tried that. It doesn't affect the default unmaximize size.

---

### Post by mc4man on 2008-09-30
I just tested it across reboots, the unmaximized size and last state remain persistent for text files and the file browser. How ever if you exit firefox in a maximized state then your last unmaximized size is 'lost' and results just as you described.
I never noticed that because I access and play my music collection from the r. click context menu which isn't available in a Firefox window. So I always leave a little of the desktop showing to r. click on.

Maybe there is a setting in firefox itself?
about:config in the location bar

---

### Post by mc4man on 2008-09-30
firefox seems to only remember it's last state (last active window) across reboots. If there is no way to adjust settings there are several ways to be using it in a *maximized state only or last* and have it remember the unmaximized size across a reboot. 

The simplest would be to open firefox to your home page, resize, and then minimize . Then open another firefox, use as normal, when your done close it out but **leave the minimized firefox that's on your home page there thru the reboot.** When you open firefox again it will open on your start page maximized (last state), but because you left the resized window open  when rebooting  it will retain the sizing for unmaximize.

Then you you'd just unmaximize, minimize ect. 

Probably best when using a fairly static home page. I use ubuntu's.

---

### Post by dhughes on 2008-10-22
I have the same pet peeve, windows won't unmaximize, it seems to be more common in Firefox but that's what I use the most although I'm quite sure it happens with other applications.

---

### Post by Somnus07 on 2008-11-01
Hi - did anyone find a solution to this (apart from having an extra dummy window open)?

I experience this problem with both firefox and thunderbird in intrepid ibex. Where a maximised window is open - then after closing it & starting up the program again, the window is maximised ... but then trying to unmaximise it only shrinks it by a bit.

thanks
Somnus

---

### Post by mc4man on 2008-11-01
> Hi - did anyone find a solution to this (apart from having an extra dummy window open)?

Actually there is no problem. I mistakenly thought I never saw the issue bobsmith2 was talking about because i never use firefox maximized, when actually it was because I'd already 'set' the unmaxized size. Then when duplicating what he saw I started getting the behavior described (unmaximized window almost the size of maximized ect., ect.

Just do this
Open firefox and resize to desired 'unmaximized' size, close firefox and reboot.
This will now become your 'default unmaximized' size irregardless of whether you close firefox maximized or not.
Even if you resize during a session if you close firefox maximized, the 'default unmaximized' size chosen above will be retained.

The way to change your 'default unmaximized' size is to resize, close firefox and reboot.

---

### Post by Somnus07 on 2008-11-02
> **mc4man said:**
> Actually there is no problem. I mistakenly thought I never saw the issue bobsmith2 was talking about because i never use firefox maximized, when actually it was because I'd already 'set' the unmaxized size. Then when duplicating what he saw I started getting the behavior described (unmaximized window almost the size of maximized ect., ect.

Just do this
Open firefox and resize to desired 'unmaximized' size, close firefox and reboot.
This will now become your 'default unmaximized' size irregardless of whether you close firefox maximized or not.
Even if you resize during a session if you close firefox maximized, the 'default unmaximized' size chosen above will be retained.

The way to change your 'default unmaximized' size is to resize, close firefox and reboot.

-> Hi, This did not work for me :(
I resized and rebooted. 
Then opened firefox.
maximised and closed.
opened firefox again (opens maximised) and tried to unmaximise... but it only shrank by a bit.

same story for thunderbird (all in ibex)

---

### Post by Somnus07 on 2008-11-04
Actually I just noticed that the bug doesnt exist when using the unmaximise window button at the top right .. but it does exist when double clicking on the title bar to achieve the same effect. 

ie after restarting firefox/thunderbird in intrepid in maximised then double clicking the title bar to unmaximise it only shrinks by a little bit.

---

