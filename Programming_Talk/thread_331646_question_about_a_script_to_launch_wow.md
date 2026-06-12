---
title: "question about a script to launch wow"
date: 2007-01-04
forum: Programming Talk
---

### Post by Phesto on 2007-01-04
I guess first, i'll start with my setup.
I'm running twinview with an nvidia card and two dell crt monitors. One monitor can handle 1600x1200 but the other one has to be set at 1280x1024.  I run wow windowed in wine at 1024x768. As it goes now i have two resolution choices setup 2880x1200 and 2560x1024. i'll manually switch to the 2560x1024 then start wow in wine. This way i can play it on the better monitor and still have thottbot, IM, etc.. open on the other monitor. When i'm done playing i will switch it back to 2880x1200. What i want to do is put all this manual work into a script. 
Like xrandr -s 2560x1024 then wine wow.exe and then when wine closes xrandr -s 2880x1200. My problem comes in as to how to inexpensviely tell if wine closed, that way i can change the resolution back. Any thoughts or suggestions would be appreciated.

Thanks in Advance.

Update - My bad for such a stupid question since one line does not get executed until the previous one finishes the whole problem was actually non-existent. I didn't need to know when wine was closed and my previous description of the script was all that was needed. Just starting out, sorry again.

---

