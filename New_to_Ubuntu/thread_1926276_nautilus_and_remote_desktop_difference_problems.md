---
title: "nautilus and remote desktop difference problems"
date: 2012-02-16
forum: New to Ubuntu
---

### Post by djyoung4 on 2012-02-16
So to begin ill say that I have a server and a laptop on the same network.  The server acts as a media server with a bunch of movies and music and what not on it and I stream it to my laptop.  I use nautilus for my file sharing and it has always worked great.  The problem is I downloaded a video on my laptop and copied it to the media server.  If I go through nautilus the video is there and plays but if I go through remote desktop it is not.  Does this mean that the file wasn't transferred over to the media server.  Sorry if the description is a little vague

---

### Post by lechien73 on 2012-02-16
It sounds to me like the share on the media server isn't mounted, and so the video has just been copied to the mount point directory on your laptop (because I've done that before with mine :)).

If you open a terminal window on the media server, and "cd" to where the file should be, can you see it with "ls"?

---

### Post by djyoung4 on 2012-02-16
no its not there.  So what do I do to actually transfer the files over to the server

---

### Post by djyoung4 on 2012-02-17
Any ideas?

---

