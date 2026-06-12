---
title: "Upstart script for TeamViewer to automatically restart"
date: 2013-11-25
forum: Programming Talk
---

### Post by RyanJA1982 on 2013-11-25
Wondering if someone can help me out with an upstart script in the etc/init folder to restart Teamviewer if it is accidentally shut down! At a complete loss since I've never used or written an upstart yet! 

Many thanks to any help! :D

---

### Post by ian-weisser on 2013-11-25
Does it currently have an upstart script?
If so, simply add "respawn" to it.  Reference: [http://upstart.ubuntu.com/cookbook/#respawn](http://upstart.ubuntu.com/cookbook/#respawn)

If it doesn't have an upstart script, then it's not a service that can be (easily) respawned by Upstart.
In that case, you might consider an hourly cron job that checks to see if a TeamViewer process is live, and restarts it  if needed.

Do be aware that TeamViewer is not in the Ubuntu Repositories, and is supported teamviewer.com instead of by the Ubuntu community (though we'll try). We can help you with Upstart - that's supported here.

---

