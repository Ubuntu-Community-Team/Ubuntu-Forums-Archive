---
title: "Evolution does not open"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by Alan Kearin on 2008-09-08
I've been playing with Evolution (connecting to Exchange), was trying to get the GAL to work, wasn't sure of the server name exactly, email was fine but couldnt open GAL. Anyway, the last time I changed it, closed and restarted to see if it would work I got the tab on the lower panel saying "Starting Evolution Mail" then nothing.

tried again- same result
and again - same result

checked processes and had multiple processes running. ended them all, tried again -same result.

restarted ubuntu - same result

looked online and found a few instances of this happening but no fix ( a few suggestions like - killing all the processes, same result

sudo mv .evolution .evolution-old-config - same result

try from a terminal - opened up the first time, but not again... strange, tried  moving the config again, but still wont open from terminal

any ideas?

---

### Post by Alan Kearin on 2008-09-11
So, I discovered that Evolution would open, but it was taking minutes to do so. Deleted the entry I had in the GAL and now I can access evolution quickly again. The thing is, I'm sure that the GAL entry I had in was correct, when it was incorrect the symptoms were different... anyone had any problems where the GAL caused a massive slowdown in Evolution?

---

### Post by LowSky on 2008-09-11
maybe this will help???

[http://ph.ubuntuforums.com/showthread.php?t=771622](http://ph.ubuntuforums.com/showthread.php?t=771622)

---

### Post by Alan Kearin on 2008-09-11
thx, saw that thread earlier but not the latest about the port - trying it out now

---

