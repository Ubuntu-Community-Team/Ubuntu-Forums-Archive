---
title: "Open sessions on login cannot close"
date: 2014-06-13
forum: New to Ubuntu
---

### Post by dee7 on 2014-06-13
Xubuntu 14.04 32 bit old Dell PC On login there appears a window with 2 open sessions 'default' and my log in name Options are to disconnect or new session Option disconnect does nothing . There appears to be program/s running . New session works , I'm here and disconnects. On shutdown indicates program/s running . Program running ?

---

### Post by Toz on 2014-06-13
If you want to clear all sessions, go to Settings Manager -> Session and Startup >> Sessions tab and click on "Clear saved sessions".

And if you don't want to automatically save sessions, then on the General tab, uncheck "Automatically save sessions on logout". Also note that during logout/shutdow, you are also prompted to save the session - make sure you uncheck this as well.

If you would like to _not_ see the session chooser on startup, go to Settings Manager >> Session and Startup >> General tab and uncheck "Display chooser on login".

More info on the Xfce session manager can be found [here]("http://docs.xfce.org/xfce/xfce4-session/start").

---

### Post by dee7 on 2014-06-13
Worked, obviously ! PC crashed a few times yesterday and I'd obviously got into the complicated solution mindset . + As other users don't speak english using a French setup and my French isn't as good as I thought it was hence am miss-reading items on French menus . Merci bien.

---

