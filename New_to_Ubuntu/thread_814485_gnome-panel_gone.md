---
title: "gnome-panel gone?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Mentem on 2008-05-31
I went to windows XP(dual boot Ubuntu-Windows XP) and drove chkdsk /f(I decided to try this since my HD was obviously messing around a bit, some videos gave error at ubuntu(they worked at windows side though) and some videos had random mp3 music playing(the same thing happened on windows side too so I deleted them). My windows is formetted NTFS.


Since then, my panels haven't started, I'm not 100% sure that the chkdsk is the one to blame but it's the biggest thing I ran while on the windows side.

I read some info about alt+F2 but no terminal run window popped up. then I(don't ask why, I just felt like trying the combination) I pressed alt+ctrl+F2 and the ubuntu started to terminal. I then wrote gnome-panel. no "response(iirc, the gnome-panel didn't exist). The terminal suggested me to try sudo get-apt gnome-panel(and informed me that it wasn't installed and downloaded it).

 I restarted but the panels were still gone. I then did the ctrl+alt+F2 again and tried metacity --replace(I read about this in the same forum message that had the gnome-panel thingie) but it did nothing either.

So, any ideas about how to fix this? reinstalling ubuntu(well, actually, I was thinking about linux mint) is ok with me, as my computer wasn't too configured yet, but can I just pop the LiveCD in and choose some reinstall option? 

I'm kinda afraid about GRUB going awol and messing the whole system.

any ideas what to do? like I said, reinstallation of ubuntu is ok for me.

---

### Post by aysiu on 2008-06-04
That's weird. Can you do ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
``` just to make sure you have everything you need?

Can you also try creating and logging in as a new test user to see if the problem is system-wide or user-specific?

---

### Post by Hoppiesbox on 2008-10-20
Running the beta of 8.10 but yeah, I had the same problem - though I'm not on a dual-boot. 

I had just run apt-get update && apt-get upgrade. After rebooting, my gnome panel was nowhere to be found. Somehow gnome-panel and several other packages had been deselected... I did an apt-get install ubuntu-desktop and it restored everything. Thanks Aysiu.

---

### Post by billgoldberg on 2008-10-20
If you can get a terminal open, try this:

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

If you can't , then copy/paste that in tty3 or something, but I'm not sure that will work.

(tty3 -> press "ctrl+alt+f3". Then press "ctrl +alt+ f9" to get back)

---

