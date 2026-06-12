---
title: "get Ubuntu on its feet easily (with XGL)"
date: 2006-07-06
forum: Outdated Tutorials &amp; Tips
---

### Post by ericesque on 2006-07-06
This is a killer tutuorial.  Can't take credit for it, but I found it on Digg (dugg it).  It'll get your ATI or Nvidia 3d accelleration going, take you through an Automatix install and show you how to use it, then get XGL and Compiz working to boot! Total time from 0 to hero?  Ballpark it at 40 min with a high speed connection.

This worked for me with ATI X600

Linkage: [http://tazforum.thetazzone.com/viewtopic.php?t=2189]("http://tazforum.thetazzone.com/viewtopic.php?t=2189")

last note: This was my first attempt to get XGL going. After playing with it for 10 minutes, I must say I'm more geeked about Ubuntu than ever before! ;)

---

### Post by The Noble on 2006-07-08
Nice guide. It works very well on my laptop*, although some options aren't working for me (Just the rain and water effects). Otherwise, Nothing is broken, and I like how XGL is a session, not something I have to enable later. Thank you!

*Specs
P4 Celeron Willamette 2GHz
768 RAM (no clue the speed)
6.06 Ubuntu
32 Meg Graphics card - Nvidia 420 Go

Works a little slow, but it works.

---

### Post by Kung Fu Hamster on 2006-07-08
I've just went through this guide, and everything worked like a charm! The effects appeared perfectly, and there was minimal slowdown on my system.

The problem didn't crop up until I tried going back to standard Gnome. When I select standard Gnome from the GDM login manager, everything will load fine. Then the screen wihh go blank and I'll end up at another GDM login. Trying to go back into standard Gnome from here will freeze the system, requiring a reboot.

What can I do to fix this?

---

### Post by Brando569 on 2006-07-11
is it possible to use XGL with KDE??

---

### Post by mbirkis on 2006-07-11
> **Brando569 said:**
> is it possible to use XGL with KDE??

yes it is. search forums for "xgl kde".
or try this link for a start
[http://ubuntuforums.org/showthread.php?t=148351&highlight=xgl+kde]("http://ubuntuforums.org/showthread.php?t=148351&highlight=xgl+kde")

---

### Post by no neck joe on 2006-07-11
> **Kung Fu Hamster said:**
> I've just went through this guide, and everything worked like a charm! The effects appeared perfectly, and there was minimal slowdown on my system.

The problem didn't crop up until I tried going back to standard Gnome. When I select standard Gnome from the GDM login manager, everything will load fine. Then the screen wihh go blank and I'll end up at another GDM login. Trying to go back into standard Gnome from here will freeze the system, requiring a reboot.

What can I do to fix this?


In an XGL session you need to disable "/usr/bin/startcompiz" under Preferences > Sessions > Startup Programs. Logout then log back in with a Gnome session.

---

### Post by bionnaki on 2006-07-11
very good guide. installation went perfectly. xgl works great.

however, it is too much unnecessary eye-candy for me. good to have available when I want to "wow" someone and show-off.

thanks!

---

### Post by ericesque on 2006-07-12
Remember, I didn't write that tutorial.  I just found it.  Glad that it's working for some people.  

I had some trouble with the rain/water effects at first too. I think it started working after I did a system update.  -- although after today's updates, I get no window decoration when I start my XGL session.  If anyone runs into this issue--and resolves it, please let us know! 

--the issue is not directly correlated to the linked tutorial, but rather to the Compiz or XGL update itself.

---

### Post by bocmaxima on 2006-07-12
> **bionnaki said:**
> 

however, it is too much unnecessary eye-candy for me. good to have available when I want to "wow" someone and show-off.

thanks!

sudo apt-get install gset-compiz

Run that and you can tweak the effects so that so its funtional and beautiful. I for one hate the default setting for Wobbly windows, however, just a little as a detail makes mine look kick ***. Theres settings for nearly everything and I dont think I could live without the Expose thing (F12)

Try it out.

---

