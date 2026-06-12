---
title: "[SOLVED] I accidentaly removed my taskbar"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by BetterSense on 2008-05-12
Not really my whole taskbar I guess, I'm not sure what you call it. My taskbar dock icons (amarok, ktorrent, update notifier, etc) are now homeless since I accidentally removed the dock from the panel (I was intending to just 'remove from panel' the update notifier icon, but I guess it though I meant to remove the whole dock). Now he little widget icons are homeless on my desktop, very annoyingly, when I reboot. Any ideas how to restore them? I looked at the 'add to panel' list and I didn't see anything likely.

---

### Post by pearjam on 2008-05-12
Try this from the command prompt?

(May have to hit ctrl+alt+f6, then log in as user or su. If already at a command prompt, then type below.)

sudo apt-get update

sudo apt-get -f install

sudo apt-get install ubuntu-desktop

(If you used ctrl+alt+f6 above, then use ctrl+alt+f7 to get out.)

Then reboot. It's worked when something like that happened to me.

Hope that helps!

---

### Post by SunnyRabbiera on 2008-05-12
we refer to it as the panel actually.
re adding a panel is easy, if you have one panel running right click it and select "new panel" to get your started.
now did you loose your top panel or bottom one?
I can give you a list of what to add to it.

---

### Post by BetterSense on 2008-05-12
Well, you know, the top panel, usually has a little area with mini-icons for amarok, ktorrent, and the update notifier? Well, the top panel is intact, it has the power button icon and the gnome button and all, but that little area where the mini-icons live is gone, so when I rebooted, all the mini-icons showed up homeless on my desktop and I couldn't do anything with them. I want to put them back in the panel where they were. I tried dragging and dropping them but it didn't work. I'm not sure I want to reinstall ubuntu-desktop, that seems a bit drastic?

---

### Post by SunnyRabbiera on 2008-05-12
alright, well here are suggestions to add to your bottom panel:
show desktop
window list (taskbar)
workspace switcher
trash

this will restore the bottom panel to its original settings, just make sure you lock each one by right clicking each one.
if need be add a drawer too.

---

### Post by BetterSense on 2008-05-12
no, my bottom panel is fine, i want to fix up my top panel to be the way it was. The problem is I deleted whatever entity it is that holds the update notification icon, and I don't know what it is to put it back.

---

### Post by SunnyRabbiera on 2008-05-12
for that what to add to the top panel:
menu bar (the main menu)
clock
quit
system notification

and any shortcuts you wish to add, you can drag and drop to the top panel.

---

### Post by BetterSense on 2008-05-13
I don't see 'system notification' in the 'add to panel' list. I see system monitor? But no system notification.

---

### Post by letubenaiah on 2008-05-13
I think what you are actually looking for is the "Notification Area"



> **BetterSense said:**
> I don't see 'system notification' in the 'add to panel' list. I see system monitor? But no system notification.

---

### Post by BetterSense on 2008-05-13
Well I added the notification area, but I can't get my icons back in it. As you can see, adding the notificiation area causes little divider things to appear, but I can't drag and drop the icons in they won't go up there, I can only move them around on my desktop.


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=69908&d=1210701110[/IMG]

---

### Post by the_lex on 2008-05-13
Very strange... I managed to accidentally remove my notification area once, but all that happened was the icons disappeared rather than going to my desktop. Adding the notification area back from "add to panel" worked for me... Have you tried giving up with that panel and then making a new panel with notification area and all that, then deleting the old one? I'm sure you have, but that's all I can think of... 

Maybe you've discovered a bug! *applause* :lolflag:

---

### Post by dfreer on 2008-05-13
After you have added the gnome notification area, did you reboot?

I've noticed these dangling icons before, it sometimes can happen by having two notification areas active at the same time (such as the default gnome notication area and avant-window-navigators notification area). Try making sure no dock or other notification area is running, and reboot.

---

### Post by shinobitux on 2008-05-13
There's probably a better way to do this, so act with care.

I've had trouble with both kde and gnome on several occasions where (being unfamiliar with the gui) I've changed certain profile settings and been unable to revert them back to normal.

One such time I managed to mess up my gnome taskbars.

Both gnome and kde keep your individual profile settings in a hidden ~/.gnome OR ~/.kde directory in your home folder.

*As a last resort* you might want to delete the .gnome directory and log off and back on. When gnome doesn't find the .gnome directory with your profile settings it should revert to the default settings (All your changes you've made to gnome desktop since install will be lost!) and create a new .gnome directory.

As a safety measure tar or zip the .gnome directory so if you don't like the default settings you can always untar or unzip the backed up profile.

What version of Ubuntu are you running? Gnome has been getting better each revision.

Hope this helps.

---

### Post by BetterSense on 2008-05-13
I'm currently runnng Hardy, but I'm still running the Beta and haven't upgraded, because the new kernal broke my graphics last time I did.

---

### Post by BetterSense on 2008-05-13
Yay! I added ONE and only one instance of he notification area and rebooted. It's back! I've been off windows so long, I forget that rebooting can sometimes fix things.

---

### Post by drs305 on 2008-05-13
Once you get your panel setup the way you like it, you may want to save it by running this:
```
gconftool-2 --dump /apps/panel > ~/Desktop/my_panel_settings
```

You can restore them by running:
```
gconftool-2 --load ~/Desktop/my_panel_settings
```

---

