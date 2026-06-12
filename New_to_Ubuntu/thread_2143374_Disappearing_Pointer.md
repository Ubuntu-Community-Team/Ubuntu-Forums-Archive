---
title: "Disappearing Pointer"
date: 2013-05-08
forum: New to Ubuntu
---

### Post by thatstheway on 2013-05-08
This is a subtle but annoying problem that's managed to get under my  skin and now I'm obsessed with solving it. Clearly I need a life. ; )  Meanwhile, onward. 

What happens is, under certain conditions, the pointer changes from being "normal" to being "flawed":
[LIST]
[*]"Normal": it remains in view at all times, switching seamlessly between images (hand, arrow, etc.) 
[*]"Flawed": it disappears after clicking, and reappears when moved. It also very reliably disappears over the icons in System Settings. 
[/LIST]

A Google on this tells me that it's pretty common across versions and  distros, but the common solutions I've seen don't work for me:
[LIST]
[*]Switch  from DMZ-White (the cursor theme I'm using) to something else: I tried  this, and it works, but (and I never realized I cared about this so  much) I really like DMZ-White and haven't found another that I feel like  using. 
[*]Remove/Disable Unclutter: Not using it! 
[/LIST]

I think this is a problem with DMZ-White, but I'm not sure. I tried  another theme "Core," and didn't see the flawed behavior after using it  for several days. Still, I don't think I have enough info to log a bug  with DMZ-White. 

Opening Software Center reliably causes the condition, but there may be other things that cause it too. 

To get it back to normal, this works 90% of the time: Restarting and  THEN logging out and back in. A simple restart or log out almost never  works. 

I'm running Ubuntu 12.04 on a Toshiba Portege R100 with a little over a  gig of RAM. My graphics card is a Trident CyberBlade XP4m32, and the  driver is xserver-xorg-video-trident. I'm using Unity 2D. 

Questions: 

Does anyone else experience this? This would help me to put together a bug report if I ever get there. 

Can anyone reccommend good tools for isolating this? Both syslog and  Xorg.0.log don't seem to catch any differences between the cursor's  normal and flawed behaviors. 

Many thanks!

---

### Post by thatstheway on 2013-05-13
Ah. There are a few bug reports on this out there: [https://bugs.launchpad.net/ubuntu/+bug/774434](https://bugs.launchpad.net/ubuntu/+bug/774434)

---

