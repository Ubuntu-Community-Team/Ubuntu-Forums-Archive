---
title: "Bind Port 80 - Vibe Streamer"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by sablefoxx on 2008-10-26
So im running [vibe streamer]("http://www.vibestreamer.com/") (in wine).  Its basically a webserver that streams MP3s for you.  I'm trying to set it up on port 80 so i can listen to it at school (almost all the other ports are blocked).  But when i try to set vibe streamer's port to 80 i get a

"2008-10-26 17:50:53 Webserver could not be started (Could not bind socket to (All unassigned) port (80))"

But 8080 (and all the higher ports) work fine, why is this?  Is there a way to find what is bound to port 80 or just assign vibe streamer to port 80.

---

### Post by sablefoxx on 2008-10-26
***SOLVED***

You need to run wine as root. Only root can have a program open a listening port in the range 1 to 1024. 

--In case someone else reads this thread :)

---

### Post by drubin on 2008-10-26
> **sablefoxx said:**
> ***SOLVED***

You need to run wine as root. Only root can have a program open a listening port in the range 1 to 1024. 

--In case someone else reads this thread :)
How to mark threads as [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

