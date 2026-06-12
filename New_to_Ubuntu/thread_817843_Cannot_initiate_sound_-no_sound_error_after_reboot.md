---
title: "Cannot initiate sound -no sound error after reboot"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by D.Sync on 2008-06-04
After installed MPD and GMPC yesterday, my laptop cannot output sound anymore after reboot.

When I try to open/play music from Rhythmbox, the app just hang then I need to force quit. Any attempt to play movie file also result in the similar case, where the video can be rendered/output with no sound output.

However, when I try to playback music using GMPC, the sound can be output. Login system sound also working fine.

Any ideas on how to rectify this problem?

---

### Post by D.Sync on 2008-06-04
Ah, finally got it solved! It seems like all those files under /usr/lib/codecs are gone except readme.txt. After moving all those files extracted from essential-20071007 again to the directory, everything is fine.

Couldn't figure out why they're gone after rebooting though.

---

### Post by cariboo on 2008-06-04
Could you please mark this thread solved.

Jim

---

