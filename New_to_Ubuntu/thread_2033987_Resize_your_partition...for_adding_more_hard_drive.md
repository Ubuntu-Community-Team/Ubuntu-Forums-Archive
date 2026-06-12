---
title: "Resize your partition...for adding more hard drive space"
date: 2012-07-27
forum: New to Ubuntu
---

### Post by neomatrix7 on 2012-07-27
hi ubuntu fans....my question is ...how to resize your partition...for adding more hard drive space for linux system....if you already installed ubuntu in windows 7....and now I get every time..... not enough space error....its really annoying.....thanks

---

### Post by Cheesemill on 2012-07-27
Is this a normal dual-boot installation or did you install using WUBI?

Can you open a terminal and post the results of:
```
df -h
```

---

### Post by neomatrix7 on 2012-07-27
I installed using wubi..... and now I need more space to work with ubuntu.... by the way I really like it....I'm experienced in computers but till now i used live cd with knoppix... and last year i pointed out a good version of ubuntu... and I'm really enjoying it...

---

### Post by Cheesemill on 2012-07-27
[https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk)

---

### Post by oldfred on 2012-07-27
If you really like Ubuntu, it may be time to convert to a full partitioned install as the creator of wubi expects.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

---

