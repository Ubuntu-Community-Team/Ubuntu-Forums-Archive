---
title: "Top panel disappeared after upgrading to 8.10!!!"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by ComputerExpertVK on 2008-11-03
My panel disappeared for no apparent reason right after I upgraded to 8.10!!!
HELP!!!

---

### Post by talsemgeest on 2008-11-04
Both of them?

---

### Post by Ryadt on 2008-11-04
```
sudo apt-get install gnome-panel
```

---

### Post by mc4100 on 2008-11-04
Providing it's just the upper one, you can right click the bottom one and select "New Panel", and then add menu's, clock's, Notification area's, etc., through the "Add to Panel" dialog.

---

### Post by eternalnewbee on 2008-11-04
It could also be that, because of the resolution, the panel is just out of the screen. Maybe by adjusting the resolution you'll see it again. Happened to me...

---

### Post by ComputerExpertVK on 2008-11-04
BOTH PANELS DISAPPEARED AND NONE OF THE SOLUTIONS ABOVE WORKED!!!
Sorry I am all worked up...
THIS IS BECAUSE I USE THIS COMPUTER FOR EVERYDAY STUFF AND I REALLY DEPEND ON THIS...
I might have to get Fedora if I cannot fix this!!!

---

### Post by Zopiac on 2008-11-04
> **ComputerExpertVK said:**
> BOTH PANELS DISAPPEARED AND NONE OF THE SOLUTIONS ABOVE WORKED!!!
Sorry I am all worked up...
THIS IS BECAUSE I USE THIS COMPUTER FOR EVERYDAY STUFF AND I REALLY DEPEND ON THIS...
I might have to get Fedora if I cannot fix this!!!

going to terminal and just typing 'gnome-panel' does nothing?

---

### Post by ComputerExpertVK on 2008-11-04
thank you sooo much!
it works now!!!
however,
it says this...
** (gnome-panel:6592): WARNING **: panel-applet-frame.c:1270: failed to load applet OAFIID:GNOME_FastUserSwitchApplet:
(null)

(gnome-panel:6592): Gdk-WARNING **: /build/buildd/gtk+2.0-2.14.4/gdk/x11/gdkdrawable-x11.c:878 drawable is not a pixmap or window

what does it mean?

---

### Post by Zopiac on 2008-11-04
> **ComputerExpertVK said:**
> thank you sooo much!
it works now!!!
however,
it says this...
** (gnome-panel:6592): WARNING **: panel-applet-frame.c:1270: failed to load applet OAFIID:GNOME_FastUserSwitchApplet:
(null)

(gnome-panel:6592): Gdk-WARNING **: /build/buildd/gtk+2.0-2.14.4/gdk/x11/gdkdrawable-x11.c:878 drawable is not a pixmap or window

what does it mean?

it means that one of the applets that is on the bar isnt working....dunno why tho. (or at least thats all i can tell)

also, if you restart the computer and the bar is gone again, go to System>Preferences>Sessions, add a new sartup program, name is Gnome Panel, and set the command to 'gnome-panel'

---

### Post by Malac on 2008-11-06
If you open a terminal and enter: ```
killall gnome-panel
```it will reload the panel and they should appear again.
I am having this same issue, including warning.
Oddly it looks like it may be a compiz issue.
[https://bugs.launchpad.net/ubuntu/+bug/2923](https://bugs.launchpad.net/ubuntu/+bug/2923) mentions the same error > Gdk-WARNING **: /build/buildd/gtk+2.0-2.14.4/gdk/x11/gdkdrawable-x11.c:878 drawable is not a pixmap or window
Hope this helps.

**EDIT**: Okay I tried setting Desktop Effects to None in Appearance and it seems to have cured it for now.

---

### Post by lisati on 2008-11-10
<aside>
Having accidentally lost my panels in Xubuntu 8.10 a couple of times, and figuring people won't want to do a full reinstall (like I did the first time it happened to me), the corresponding command to enter from the terminal to get the Xubuntu 8.10 panels back is [code]xfce4-panel &[code]
(Stuck on getting to the terminal? Right-click on the "home folder" icon on the desktop, and click on "Start terminal here")
</aside>

---

### Post by romaDa on 2009-01-28
Hey guys I'm having the same problem with the panels on my desktop at home.
The problem is that since I lost my panel I don't know how to get to the terminal to enter the commands to get the pannels back.

After doing some research, I found that you can make a keyboard shortcut via the 'create launcher' option but for some reason when I right-click the desktop and chose the following nothing happens.

I was wondering if there was another way to bring up the terminal so I can fix my panels.

Thanks in advance. :)

---

### Post by talsemgeest on 2009-01-28
> **romaDa said:**
> Hey guys I'm having the same problem with the panels on my desktop at home.
The problem is that since I lost my panel I don't know how to get to the terminal to enter the commands to get the pannels back.

After doing some research, I found that you can make a keyboard shortcut via the 'create launcher' option but for some reason when I right-click the desktop and chose the following nothing happens.

I was wondering if there was another way to bring up the terminal so I can fix my panels.

Thanks in advance. :)
You will probably be better off starting a new thread than resurrecting an old one. :)

---

### Post by romaDa on 2009-01-28
Sorry about that I forgot to check the date, it won't happen again.

Good news though I found a solution to my problem.

I found the terminal in /usr/bin through a folder that was on my desktop and ran the commands given earlier and now I got my panels back. It might be simple but I'm a newbie.

Sorry for bringing back the old thread! :)

---

