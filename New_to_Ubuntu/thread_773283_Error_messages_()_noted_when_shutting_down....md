---
title: "Error messages (?) noted when shutting down..."
date: 2008-04-28
forum: New to Ubuntu
---

### Post by norfair on 2008-04-28
I'm not exacly sure how to describe this, but when I shutdown Ubuntu 8.04 and it goes though its usual quick cycle of screens, it displays one dark black screen (as it does when turning it on and it displays Starting Up... in the top left corner) with a bunch of what look like error messages. I see the word "failed" and so forth. The screen is slightly streched when shutting down/starting up so I can't quite read everything. Plus it all happens so quick I can't write it all down. 

My question is, is there a way I can check and fix whatever those errors might be? Does what I am asking make sense? I just want to nip whatever problems may be existing behind the scenes before they fester and blow up. I'll be happy to clarify in any way I can. Thanks.

---

### Post by hermes0710 on 2008-04-29
You could check it through "dmesg".

```
sudo dmesg
```

You could also change the usplash settings in order to have a more readable boot up screen (System>Administration>Startup Manager).

---

### Post by Vadi on 2008-05-01
It's usually Network Manager giving some assertion errors and whatnot. Safe to ignore, and just hope NM developers make it less buggy...

---

