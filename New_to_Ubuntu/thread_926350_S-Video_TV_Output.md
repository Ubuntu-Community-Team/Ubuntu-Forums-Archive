---
title: "S-Video TV Output"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by subaruwrc01 on 2008-09-21
How do I go about outputting to a TV using S-video on Hardy?  I have Intel X3100 integrated graphics.

---

### Post by C.S.Cameron on 2008-09-22
I think normally plug the S-video cable into computer and TV then change the TV input to S-video

---

### Post by willca on 2008-09-23
Hi 

I am assuming you have only configured your vga in xorg.conf and not your s-video.

The idea basically is you want to use both simultaneously. Now the changes to your xorg.conf differs depending if you want a clone or an extended desktop (like xinerama) for instance.

Best place to do is to backup your xorg.conf and then edit it. I would check out [www.ubuntuguide.org](www.ubuntuguide.org) for some specific details on this.

---

### Post by wersdaluv on 2008-09-23
Same graphics and same issue. hehe

---

### Post by subaruwrc01 on 2008-09-27
I'm relatively new at this and not sure how exactly I would edit my xorg.conf.

---

### Post by C.S.Cameron on 2008-09-27
If you have Nvidia graphics I think Nvidia settings should recognize your TV when it is plugged into S-video. It will modify your xorg.conf for you.

---

### Post by subaruwrc01 on 2008-09-27
I have Intel X3100, not Nvidia.

---

### Post by C.S.Cameron on 2008-09-29
Everything I've found on the internet sounds pretty negative for the 965 and S-video.
I'm thinking about a board with GMA 950 and S-video and can't find much info on that one either.
I know nothing so far, so just consider this post a friendly bump.

---

### Post by darco on 2008-09-29
Try this link......not sure if it pertains to your issue....

[http://ubuntuforums.org/showthread.php?t=361124&highlight=s-video](http://ubuntuforums.org/showthread.php?t=361124&highlight=s-video)

darco

---

