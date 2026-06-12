---
title: "Touchpad stops working randomly"
date: 2011-09-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by BeRoot ReBoot on 2011-09-26
After logging in, the touchpad on my netbook (Asus 1018P) stops working, apparently randomly, no matter what I do, a few minutes into the session. Plugging in a USB mouse allows me to do work, but I can't get the touchpad to work again. It's listed as enabled in the settings, and the Fn switch doesn't affect it at all. The mouse keys below the touchpad don't work, either. The only way to restore function is to log out and log back in.

Anyone else get this?

---

### Post by BeRoot ReBoot on 2011-09-27
bump

---

### Post by dino99 on 2011-09-27
look at video driver activation first (sudo jockey-gtk)

---

### Post by BeRoot ReBoot on 2011-09-27
Nope, nothing there. It only lists the proprietary broadcom wireless driver, which is already activated and in use.

---

### Post by garok89 on 2011-09-27
same here - HP DV6-2106ae for me though.....
only started happening thismorning

---

### Post by t-c on 2011-09-28
I noticed this (along with the battery indication showing the battery wae removed) about 24hrs ago.
 
I thought it may have been an issue with Synaptiks which I have found not to reliably restart on startup. But since it was random in the first place I cannot determine as to whether or not the issue was there or not. But I haven't noticed it in the last few hours since it's removal so maybe something in it?

---

### Post by BeRoot ReBoot on 2011-09-28
up

---

### Post by WarThiefF on 2011-10-08
Same issue here, has someone file a bug report yet?

---

### Post by speedwlk on 2011-10-08
Please have a look at the post (post number 5) by Hopper122 at this page:
[http://ubuntuforums.org/showthread.php?p=9410163](http://ubuntuforums.org/showthread.php?p=9410163)



Edit: It is an old post, but might help.

---

### Post by mc4man on 2011-10-08
Could  be the same as this thread
[http://ubuntuforums.org/showthread.php?t=1852081](http://ubuntuforums.org/showthread.php?t=1852081)

The timing of this seems to be around an xserver update, may be involved, may not be. ( the update didn't appear to change much

---

