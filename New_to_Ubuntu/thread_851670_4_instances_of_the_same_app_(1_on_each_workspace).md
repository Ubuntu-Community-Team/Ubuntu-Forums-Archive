---
title: "4 instances of the same app (1 on each workspace)"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-07-06
i am using conky

i have used gconf-editor to make nautilus stop drawing the desktop (so compiz can take over and i can have 4 seperate wallpapers)

if i make conky sticky then part of one desktop shows up on another (see attached thumbnails)

how can i do this so that 4 conkys open at login with one on each desktop?

btw: this is a pic from this morning (my conky has black text now, i just need for the wallpaper to not stay behind conky)

---

### Post by tjwoosta on 2008-07-16
i was hoping that maybe someone from the unanswered posts team would have answered by now

guess not so...

bump
bump

---

### Post by tjwoosta on 2008-07-17
aww..

come on now..

nobody knows how to do this?

---

### Post by Inxsible on 2008-07-17
Try running 4 instances of conky. Have them use 4 different config files at startup.

I am not sure if you can use compiz to start apps on different desktops or not..but I think its doable. I haven't been using compiz since I switched to Fluxbox and Openbox

---

### Post by appi2012 on 2008-07-17
Changed my mind:
try this:

Go to advanced Desktop effect settings and go to window rules. under the sticky windows textbox, click the add button. Set the dropdown to window class, click grab, and then click on conky. 

Then add it to your startup programs in System -> Preferences -> Sessions. 

Hope that helps!

---

### Post by mjwhitfield on 2008-07-17
My conky appears on all of my desktops.

see this post:
[http://ubuntuforums.org/showthread.php?t=695813](http://ubuntuforums.org/showthread.php?t=695813)

---

### Post by tjwoosta on 2008-07-17
> Go to advanced Desktop effect settings and go to window rules. under the sticky windows textbox, click the add button. Set the dropdown to window class, click grab, and then click on conky.

Then add it to your startup programs in System -> Preferences -> Sessions.

Hope that helps! 

> My conky appears on all of my desktops.

see this post:
[http://ubuntuforums.org/showthread.php?t=695813](http://ubuntuforums.org/showthread.php?t=695813)

thank you guys for your responses but thats not the problem


i can make conky sticky very easily


the problem is that when i make it sticky parts of one desktop show through to the others  ( i am using four different wallpapers)

see my attached screenshots in the first post to get a better understanding

---

### Post by Joshuwa on 2008-07-17
> **tjwoosta said:**
> thank you guys for your responses but thats not the problem


i can make conky sticky very easily


the problem is that when i make it sticky parts of one desktop show through to the others  ( i am using four different wallpapers)

see my attached screenshots in the first post to get a better understanding

It's because conky doesn't use real transparency, and uses a "snapshot" of the background correctly aligned to give the illusion of it being transparent.

To achieve what you're looking for, you'd need conky to update that snapshot each and every time you switched work-spaces (maybe possible) or rotated your cube (doubt if its possible).

But I don't know how to make that happen, unfortunately.

---

