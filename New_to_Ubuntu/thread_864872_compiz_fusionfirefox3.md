---
title: "compiz fusion/firefox3"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by muddNZ on 2008-07-20
Hi, new user here, just got myself a cheap laptop (compaq presario) and set it up with ubuntu, loving not having anything microsoft:)

been using it for a week and one of the features i particularly liked - compiz fusion/desktop cube seems to be conflicting with firefox (as far as i can make out)
i first noticed that the minimise/maximise/close bar at the top dissappears + the top and bottom desktop panels aren't visible. i have to go file>quit to close firefox - can't minimise to bottom panel.
if i go system>preferences>appearance>visual effects and click on "none" firefox goes back to normal but i lose my desktop cubes.
it only seems to effect firefox, other apps work fine.
a friend who knows linux way better than me got me to enter something in terminal to show the graphics info - glxinfo? i think, anyways he said everything was fine from that end - graphics was recognised and stuff, so seems to be something wrong between compiz fusion and firefox3.

any help with this is much appreciated:)

---

### Post by Huss on 2008-09-04
I'm having the same problem. 

Anyone?

---

### Post by ntbutler on 2008-09-04
What graphics card are you using, and which distro have you installed. I am not sure if it is a graphics card associated problem, but i am using a nvidia GeForce 8800GT and i have been having a lot of problems with it. Noone can seem to give me an explanation as to why, but there is a lot of speculation about compiz and Hardy causing a lot of problems together (possibly related to the graphics cards and drivers)

---

### Post by kpkeerthi on 2008-09-04
What [window decorator]("http://wiki.compiz-fusion.org/Plugins/Decoration") are you using with compiz? 

You may want to install emerald and emerald-themes and switch to it.

---

### Post by Huss on 2008-09-04
Thanks for the quick replies,

I'm using hardy with a Nvidia Gforce 6series. the window decorator is selected and has the command "gtk-window-decorator --replace". I don't think it would be the decorator though because it only happens with firefox.

I should also mention that when I sue the window selector (where all the windows zoom out) I still cant see the title bar. 

Will I have to wait for the next firefox update?

---

### Post by quanumphaze on 2008-09-04
Firefox appears to be in a fullscreen mode. It's a feature of Gnome (or the window manager) where it strips the window border and makes it 'fullscreen'. I don't know why it spontaneously triggers itself for some users but the fix is easy enough.

The way to fix this (assuming you use Gnome) is to go to 'Keyboard shortcuts' in system>preferences and scroll near the bottom to an option named 'Toggle fullscreen mode'. Set his to something like Crtl+F11 or a keybinding your own preference. and just press it next time you run into this problem

This is, as I said, a Gnome feature and can be used on any standard window to make it fullscreen (and will also not change the toolbars in apps that have a built in fullscreen mode).

---

### Post by Huss on 2008-09-04
Ah great!

I'll try it as soon as I can.

---

### Post by Huss on 2008-09-17
The funny thing is that the bug spontaneously went away. The sad thing is that it's back again. 

I tried toggling full screen but it didn't do the trick. It must be a cairo dock bug. I just installed an update and after a reboot it's not working.

---

### Post by Huss on 2008-09-17
If you're having the same problem as I did, check this post:

[http://ubuntuforums.org/showthread.php?t=844178&highlight=window+decoration](http://ubuntuforums.org/showthread.php?t=844178&highlight=window+decoration)

---

