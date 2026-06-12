---
title: "[SOLVED] Startup script locations"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by NormR2 on 2008-05-25
How many different places can you put lines of code/scripts to be executed when the system starts or when a terminal window is opened?

It seems like every day I see a new place referenced in the forum.
So far: ~/.profile, ~/.bashrc, /etc/rc.local, /etc/environment, /etc/profile, /etc/profile, /etc/bash.bashrc   and more


Is there doc that would tie these all together?

That would explain what files are "executed":
 when the system starts 
 when a login session starts 
 when a console session(virtual console or emulated terminal) starts

Thanks,
Norm

---

### Post by bwhite82 on 2008-05-25
[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

---

### Post by NormR2 on 2008-05-25
That site was sort of high level. I'm looking for more details on how the system starts up and where each folder in my list is referenced in the startup process. 
I just saw another folder referenced: /etc/init.d/ where the system get scripts to be run at startup. The list grows.

---

### Post by bwhite82 on 2008-05-25
[http://oldfield.wattle.id.au/luv/boot.html](http://oldfield.wattle.id.au/luv/boot.html)
[http://www.debianadmin.com/the-lniux-boot-process-explained.html](http://www.debianadmin.com/the-lniux-boot-process-explained.html)

---

### Post by NormR2 on 2008-05-26
Thanks for those sites. They answer 1/3 of my questions.
The other two areas I'm interested in are:
Init for a user login
Init for bash shell stattup

Finally did a Google for this stuff and found more than I can read in a week.

---

