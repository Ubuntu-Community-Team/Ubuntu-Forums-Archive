---
title: "Shutdown button FREEZES computer?"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Roasted on 2008-05-07
On Gutsy and now Hardy, both installations have left me with having to do a ctrl alt backspace to do a hard logout in order to find a restart option that works. It just freezes all of the icons. I can't type. I can move the mouse, but clicking on stuff doesn't yield anything.

How can I fix this so when I click on shut down, it doesn't freeze, and I'm prompted with shut down/restart/logout/etc?

Edit:
Also - even though I enable my restricted driver, it says not in use. For the 2nd time today, Gutsy is getting put back on here.

---

### Post by Roasted on 2008-05-08
I can't figure this out. I just put Hardy in my computer, and it freezes it also. All during this, I haven't formatted my home partition. I have my stuff backed up on 2 other drives, so I'll format my home dir and see what happens. Maybe there's a bad setting?

---

### Post by Joeb454 on 2008-05-08
It sounds likely. Keep a backup of your home directory anyway, so you can restore actual documents.

Also you could then try restoring the settings for app's 1 by 1 :)

---

### Post by Roasted on 2008-05-08
I have my home directory backed up on 2 other hard drives. So I just need to pull the data back over. :)

---

### Post by Roasted on 2008-05-08
Well, cancel that. The button works, it just takes an insanely long time to function. I clicked it 15 minutes ago and only now when I came back to the computer it was up. But then again, I just did it six times in a row and each time it came up instantly. Weird.

---

### Post by wootah on 2008-05-08
ATI, Nvidia, Intel ?

I remember I had a similar issue back in 6.10 or 7.04 (not quite sure) where I had some small config. issues surrounding my graphics.

---

### Post by maddog39 on 2008-05-08
I think this is a long standing bug with GNOME because I commonly have issues like this with a stock GNOME setup on Arch. Generally I just do Control + Alt + Backspace and shutdown from GDM if thats the case. Give that a try and see what happens.

---

### Post by ell02 on 2008-05-08
might wanna check your services and bum if you have that installed,under administration.i had same problem.reenabling some things fixed me back up.not sure but i think bootclean did it for me.good carefull luck.

---

### Post by shifty_powers on 2008-05-08
had this problem a few times, and i found out it was a problem in my ./config folder. iirc, it was something with the autostart. I've deleted the whole folder before, and that always solves the problem.

make a backup and experiment, but i can guarantee it will solve it ;)

---

### Post by Roasted on 2008-05-08
> **maddog39 said:**
> I think this is a long standing bug with GNOME because I commonly have issues like this with a stock GNOME setup on Arch. Generally I just do Control + Alt + Backspace and shutdown from GDM if thats the case. Give that a try and see what happens.

Yeah, I been using ctrl alt backspace to reboot and shutdown when I need to if this happens. But it still urks me when it doesn't work the way it should. It seems to be okay now. *shrug*

---

### Post by Joeb454 on 2008-05-08
I just use the terminal to shut down if this ever happens ```
sudo shutdown -P now
``` shutsdown straight away :)

---

