---
title: "Keyboard shortcuts not working over rdesktop?"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by d4m1r on 2012-05-16
Hey guys, I am connecting to my Windows XP machine at work over remote desktop using the "rdesktop" or "Remote Desktop Viewer" package. It was the default one that came with 11.04 and worked beautifully so I installed it manually after doing a clean install of 12.04.

Anyway, now it still works wonderfully EXCEPT keyboard shortcuts no longer work....For example, using it under 11.04, I was able to take screenshots on the Windows XP side by hitting ALT + Print Screen, but now that no longer works and instead the default 12.04 screenshot app launches....In fact, **NO** Windows keyboard shortcuts work when connecting over RDP...

And yes, I have View > Keyboard Shortcuts enabled. Anyone else seeing this issue or know how to fix it? :confused:

---

### Post by d4m1r on 2012-05-16
Update: I have tried the KDE RDP client in the software centre and even the default RDP client for 12.04 (Remmina) and none of those function regards to keyboard shortcuts either....Does anyone know of ANY RDP clients for Ubuntu 12.04 that have remote keyboard shortcuts functioning?!

---

### Post by d4m1r on 2012-05-17
101 views and nobody else is experiencing this?

Does anyone have functioning remote desktop keyboard shortcuts under 12.04?! :confused:

---

### Post by d4m1r on 2012-05-20
Seems like the package I was using is actually called vinagre and I found a previously reported bug that describes this exact same issue:

[https://bugs.launchpad.net/ubuntu/+source/vinagre/+bug/922276](https://bugs.launchpad.net/ubuntu/+source/vinagre/+bug/922276)

^Can anyone comment on this issue or suggest a workaround? :confused: If this is affecting you too, please mark the bug as such so they actually fix it!

---

### Post by shizeon on 2012-06-08
Just upgraded to 12.04 and I'm seeing the same thing.  I use the rdesktop command directly.  Where I used to be able to force it to full screen and it would intercept alt-tab, win-* bindings, it appears that dash and unity now intercept these :(  I've tried remapping the DASH command from ALT and other tweaks to the rdesktop command line, but it doesn't seem to make a difference.  I went in and marked that bug as effecting me too.  Please post if you come up with a solution and I'll do the same.

---

### Post by d4m1r on 2012-06-20
> **shizeon said:**
> Just upgraded to 12.04 and I'm seeing the same thing.  I use the rdesktop command directly.  Where I used to be able to force it to full screen and it would intercept alt-tab, win-* bindings, it appears that dash and unity now intercept these :(  I've tried remapping the DASH command from ALT and other tweaks to the rdesktop command line, but it doesn't seem to make a difference.  I went in and marked that bug as effecting me too.  Please post if you come up with a solution and I'll do the same.

Well, I ditched rdesktop a few weeks ago since I couldn't get the keyboard shortcuts to work properly despite it still being the best client otherwise....Anyway, I am now using the default client (Remmina) which disconnects at least once an hour which is annoying but it's the only other client that supports TRUE fullscreen mode and has a semi-working remote keyboard shortcut function. By semi-working, I mean you have to click a button to enable ALL keystrokes to go to the remote PC. This also means you will lose local shortcuts when in this mode, but it's toggable.

Hope that helps.

---

