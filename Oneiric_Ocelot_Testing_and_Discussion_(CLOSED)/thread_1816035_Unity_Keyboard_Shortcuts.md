---
title: "Unity Keyboard Shortcuts"
date: 2011-08-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sgage on 2011-08-01
Can someone point me to a list of Unity keyboard shortcuts that is relatively up to date? I've run across a couple, but they seem out of date, with the shortcuts not working as advertised. Is there something current that is kept updated?

TIA

---

### Post by castrojo on 2011-08-01
Here you go: [http://askubuntu.com/q/28086/235](http://askubuntu.com/q/28086/235)

---

### Post by sgage on 2011-08-01
> **castrojo said:**
> Here you go: [http://askubuntu.com/q/28086/235](http://askubuntu.com/q/28086/235)

Thanks, but that's one I've checked out. Most of those key-combos do nothing. Super opens the dash. Super-S and Super-W both work. Alt-F2 works. Nothing else seems to work.

If I hold down the Super key, the little numbers come up on the launcher icons. Pressing a number key does nothing. Super-T, nothing - it just brings up the little numbers on the icons. Same with Super-D.

Am I doing something wrong?

---

### Post by castrojo on 2011-08-01
You might want to check to make sure your compiz settings haven't been changed (I don't remember how to do that offhand, it's in CCSM somewhere).

---

### Post by mc4man on 2011-08-01
All of the ones listed in ccsm > unity plugin  work here

As far as super -  only super+w (scale window picker for all Open windows
None of the other super+ work (super+1>9, s.a.f

ctrl+alt+arrow keys - switch workspaces works
shift+alt+ctrl+arrow keys  - switch workspace with window works

---

### Post by sgage on 2011-08-01
> **castrojo said:**
> You might want to check to make sure your compiz settings haven't been changed (I don't remember how to do that offhand, it's in CCSM somewhere).

I poked around in CCSM, and I don't see anything obvious in the Unity section. I've looked around elsewhere in there, but again, nothing I can see that seems relevant.

What is weird is that when I hold down the super key, those little numbers show up, but then when I press a number key, nothing.

---

### Post by mc4man on 2011-08-01
> **sgage said:**
> I poked around in CCSM, and I don't see anything obvious in the Unity section. I've looked around elsewhere in there, but again, nothing I can see that seems relevant.

What is weird is that when I hold down the super key, those little numbers show up, but then when I press a number key, nothing.

I  think you can consider them broken atm. (along with drag & drop functions on the launcher 

Plus - if you do a super+<whatever> while focus is on the desktop then any keyboard input goes to a search box.. if a window in focus the input may go there, like gedit, ect.

---

### Post by sgage on 2011-08-01
> **mc4man said:**
> I  think you can consider them broken atm. (along with drag & drop functions on the launcher 

Plus - if you do a super+<whatever> while focus is on the desktop then any keyboard input goes to a search box.. if a window in focus the input may go there, like gedit, ect.

Yes, I've noticed :KS

Thanks for the confirmation.

---

### Post by mc4man on 2011-08-01
The other thing 'broken' or possibly changed is the l. click on launcher icon > scale > window picker for window group which used to pull all windows of the same group from ALL workspaces, inc. minimized, then return them to prior state if not the one chosen

The current behavior is just to pull from current workspace if more than one window is open/min, otherwise just focus window on that workspace

Hopefully it's just a break, (from my perspective),  though I've seen some indication to the contrary 
(and it seems quite difficult to get an answer one way or the other

Edit: I'd think unity will get an upgrade shortly, (new nux libs), will be interesting what it brings

---

### Post by sgage on 2011-08-01
> **mc4man said:**
> The other thing 'broken' or possibly changed is the l. click on launcher icon > scale > window picker for window group which used to pull all windows of the same group from ALL workspaces, inc. minimized, then return them to prior state if not the one chosen

The current behavior is just to pull from current workspace if more than one window is open/min, otherwise just focus window on that workspace

Hopefully it's just a break, (from my perspective),  though I've seen some indication to the contrary 
(and it seems quite difficult to get an answer one way or the other

Edit: I'd think unity will get an upgrade shortly, (new nux libs), will be interesting what it brings

Yes, I see it too - interesting indeed.

I have to keep reminding myself that Oneiric is Alpha software. When I do that, everything is OK :KS

---

### Post by mc4man on 2011-08-01
Some nice fixes and several additions  - well worth _reading the unity changelog_ and checking out 

The D&D and super+ are still mia

I think the window group picker from all workspaces just may be gone, though **if so** a very poor decision.

for any interested a current bug on O
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/811744](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/811744)

in the description are linked 2 seemingly opposing natty bugs on this, though I still think there is/was some degree of confusion, noting some comments by the same people in both, supporting both..?
When it was broken in natty dev similar to now in O
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/707214](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/707214)

What I took as the opposing how it works in natty
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/689733](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/689733)

The latter one seems to hold the most sway atm, though I'm unclear on exactly what 'design' feature was fix released. Comment # 4 describes how it does work in natty and how I'd hope it would in O

---

### Post by mc4man on 2011-08-02
One thing I've noticed here with the unity upgrade, when first logging in, -  if trying to run a quicklist entry from launcher the 1st attempt always produces a non-functional quicklist box.
After that quicklists work fine

---

### Post by mc4man on 2011-08-03
The D&D onto the unity launcher now has a fix committed so that should be ok shortly, nothing as yet on the launcher keyboard shortcuts
edit - super + are also now fix committed

---

### Post by sartic on 2011-08-04
[IMG]http://endrigo.com/files/forum/unity_tricks_wallpaper.png[/IMG]

use it as wallpaper :)

---

### Post by Kride81 on 2011-09-23
Those window placement shortcuts don't seem to work anymore. They were great and hopefully restored.
Also missing the icon on top left corner bugs me. I'm running Ubuntu in VirtualBox and on the extended screen on right side my main display. I have to move pointer really carefully to get panel to pop out.

---

