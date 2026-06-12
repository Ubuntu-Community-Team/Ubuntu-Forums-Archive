---
title: "Problems with &quot;Startup Programs&quot;"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Spiral_Architect on 2008-04-27
Installed Ubuntu 8:04 last week and love it. Just have a small problem with Sessions -> Startup Programs...

I added my music player (Audacious) in the startup programs list, and it worked fine upon login. However, when I now removed it from the list (don't want it anymore) it stills starts up automatically... why does this happen?

Anyway to restore the "default" startup programs?

Thanks! :)

---

### Post by southernman on 2008-04-27
Look in your user directory for
~/.aucacious

Look inside it for a config file you can edit or you could (I think) delete the folder entirely (.audacious I mean). The period in front of the name means it's a hidden folder.

Probably, it's still happening cause that configuration is saved in the above hidden folder for your user name.

---

### Post by hyper_ch on 2008-04-27
do you save the sessions when logginout / shutting down? And if you do and audacious is running, then it will auto-start it next time again :)

---

### Post by Spiral_Architect on 2008-04-27
Thanks guys, just realized that before I saved the session, I forgot to click that tiny apply-button in currently running sessions. :lolflag:

---

