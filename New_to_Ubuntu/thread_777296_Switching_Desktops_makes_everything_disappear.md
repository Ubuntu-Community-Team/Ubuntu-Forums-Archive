---
title: "Switching Desktops makes everything disappear"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by eatlotsoffruits on 2008-05-01
Hi all,

I upgraded yesterday from Feisty to Gutsy (I know, a bit behind the times but my laptop's ultra-old and it takes baby steps) and the whole process seemed to go well.  No warnings, no failures, my laptop didn't explode.  And i restarted the system and got onto my desktop and all of my folders and icons were still in place.

But when i tried to switch to another virtual desktop, everything disappeared!  And i mean EVERYTHING short of my mouse pointer and my background picture.  The system didn't freeze, though, because when i hit the power button the "shut down" prompt popped up.

Has anyone come across this before?  Or am i stuck with one desktop?

Thanks!

---

### Post by Paqman on 2008-05-01
Have you had a fiddle with your desktop settings? Most people use horizontal=4 vertical=1. Try resetting it to 1x1, then set it back up maybe?

[/wild guess]

---

### Post by Myglaren on 2008-05-01
Yes.  I do get that when I enable the advanced desktop settings, did with Fiesty and Gutsy too.  I think it is my graphics card not being up to it.  The mimimise, maximise/restore and close icons would all disappear from the various windows too.

---

### Post by AndThenWhat on 2008-05-01
Do you have compiz enabled?  

If so, you might have 4 virutal desktops instead of 1.  Hence, when you switch you get a completely new desktop without icons etc.  If that is the case, here is the fix:

download advanced compiz settings manager:

```
sudo apt-get install compizconfig-settings-manager
```

Go to System>Preferences>Advanced Desktop Settings

Now, click on the **general options** button and then go to the **desktop size** tab.  Change the vertical virtual size to 1 and then you should have 1 virtual desktop.

---

### Post by eatlotsoffruits on 2008-05-01
Thank you for your help!  I checked it just now and it turns out that the system had reset to 1x1 even though it was still displaying 1x4.  I set it to 1x4 and it works great.  THanks so much for your help!

---

