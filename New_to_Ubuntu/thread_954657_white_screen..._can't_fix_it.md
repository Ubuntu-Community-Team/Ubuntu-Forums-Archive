---
title: "white screen... can't fix it"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by Veke99 on 2008-10-21
just installed ubuntu...

When I log in to ubuntu, I get this common problem... the white screen. I'm quite sure that's because of the screen effects that are turned on (I didn't do that :() and which I can't get off. 
Tried rebooting a few times to no avail, instead, now, when I reboot, it goes to grub and I don't know how to go to the login from there. And I haven't tried ctrl-alt-backspace on the white screen yet, because I can't get out of grub.

help appreciated ;)

---

### Post by billgoldberg on 2008-10-21
Lots of hits about this on google, try this:

[http://www.linux.com/forums/topic/548](http://www.linux.com/forums/topic/548)

---

---

### Post by eternalnewbee on 2008-10-21
Never heard of "When I log in to ubuntu, I get this common problem... the white screen" before...

---

### Post by larry Price on 2008-10-29
I have the same problem with HH... login screen and password screens come up and works just fine... after a few seconds the screen goes white. I used to be able to hit Alt F2 then blindly enter metacity --replace. Now that doesn't work. This occurs each time after a fresh install. Incredably frustrating.

---

### Post by loomsen on 2008-10-29
> **larry Price said:**
> This occurs each time after a fresh install. Incredably frustrating.

So you're used to? :)

I acually try and mind "fresh" installs like the devil minds the water. But well...

This is obv a problem caused through your graphics driver, which isn't configured after a "fresh" install (Basically this is all a fresh install does... deconfiguring your system config... Useless imho, even destructive)

However, backup your xorg.conf to a easy accessible place so that you'll be able to replace the unconfigured "fresh" one with your proven working one you backed up. And make sure you install the drivers, which isn't too hard from cmd line neither...

---

### Post by larry Price on 2008-10-29
I should have explained a little better. After each fresh install everything works well until either A; I try to configure the video card. White screen is the result. Or B; if I download the bazillion patches and upgrades that pop up. Same result, white screen. It appears there is no generic intel graphics driver that works properly.

---

### Post by igknighted on 2008-10-29
> **larry Price said:**
> I should have explained a little better. After each fresh install everything works well until either A; I try to configure the video card. White screen is the result. Or B; if I download the bazillion patches and upgrades that pop up. Same result, white screen. It appears there is no generic intel graphics driver that works properly.

The intel graphics driver has seen some major revisions, but they just missed intrepid (the major ones, at least).  Once kernel 2.6.28 is out for intrepid +1, and the new GEM enabled intel driver is in use, you should see drastic improvements.

In the mean time, most of the drivers have fixes available if you add a line or two to a config file.  Which intel graphics chip do you have?  And is it a laptop or a desktop?

---

