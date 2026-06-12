---
title: "Compiz problem again"
date: 2014-05-15
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2014-05-15
I use scale, expo and wall edge flippling plugins in Compiz to navigate my Unity desktop. A recurring problem since 12.04 is that the hot corners and edge settings are not reliably remembered so that one or more would stop working during a session or on reboot. The workaround before 14.04 consists of disabling auto plugin sorting in ccsm and pile these towards the bottom of the list. But everytime a new Ubuntu releases there are some changes to how one should order the plugins while the problem never get solved. So a fun sport after installing a new Ubuntu has always been to juggle around these plugins and see how they should be ordered.

But with 14.04 I seem to have hit an impass. In 13.10 expo basically can be placed anywhere and the hot corner will persist, but scale have to be close to the end and wall has to be at the very bottom. Now with 14.04 expo MUST be placed at the bottom for the hot corner to be remembered but that means I have to put wall on the next available slot up the list. The result is that edge flipping sometimes would just stop working out of the blue during a session. Now scale would have to be above unity shell in the plugin list, for otherwise triggering scale would kill Unity. The ordering is getting more rigid.

Is there any more work around? 

Why is this bug and its variations (may involve scale as well) never get fixed dispite endless bug reports since 12.04 and perhaps even before it? Ok, so they have no resource to fix Compiz (even though Unity is a compiz plugin) because they have poured the resources into tinkering menus, icons and webapps, it is more important to look pretty than to work reliably, that's ok, we can work around it. But if you don't fix the bug  at least don't move the furniture around in such a way that breaks workarounds that used to work.

---

### Post by Ferux on 2014-05-26
Yes I also have this bug and I'm very annoyed by it...

---

### Post by monkeybrain20122 on 2014-05-26
> **Ferux said:**
> Yes I also have this bug and I'm very annoyed by it...

I have found a combination that works on my machine for 14.04. In ccsm disable auto plugin sorting, then order the puligins so that the bottom of the list looks like this (in descending order) "scale, unuty-shell, scale-addon, wall, expo" This way all of scale, wall edge flipping and expo work and remember the corners and edges on reboot. 

But everytime when I drag and drop something edge flip is killed (the only exception is dragging icon from one place to another along the launcher bar, that doesn't kill wall's edge flipping), that seems to be a separate bug.

---

### Post by Ferux on 2014-05-27
OK, I'll give it a try. Thanks for the tip!

---

### Post by monkeybrain20122 on 2014-06-08
Man this is really not cool. It was working for a while then comes some Unity update and now scale is not working.

If you are not fixing the bugs at least don't screw it up!

---

### Post by monkeybrain20122 on 2014-06-08
OK, This is my work around. I wiped my / partition and restored a clone I made before the update, then locked the packages unity, libunity-core-6.0-9 and unity-services at version 7.2.0 and it appears to work. 

But before this I tried to downgrade these packages from 7.2.1 to 7.2.0 and locked them but didn't work. Maybe upgrading these packages changed something which was not reversed by downgrading.

This is really frustrating! Good thing that I have a cloned my system.

---

