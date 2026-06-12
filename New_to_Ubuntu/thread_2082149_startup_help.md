---
title: "startup help"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-11-08
just not my day. i dont know what happened but now whenever i log into an xubuntu session. my home folder auto opens and then chrome.
any idea. i dont have either of these set to auto open at login. weird.

---

### Post by rburkartjo on 2012-11-08
chrome stopped autostarting. however what is happening is that when i log in x is restarting again by itself causing my home folder to open.

---

### Post by Toz on 2012-11-08
Xfce has saved sessions functionality (see: [http://wiki.xfce.org/faq#session_manager]("http://wiki.xfce.org/faq#session_manager")). It is possible that those applications were saved in this manner.

If they are not listed in the autostart location, then deleting the contents of ~/.cache/sessions _when not logged in_ will clear those saved sessions.

Also, when logging out, pay attention to the "Save session for future logins" checkbox and select accordingly.

**Note:** If you are using Xubuntu 12.10 (Xfce 4.10) I believe there is now an option to clear sessions at Settings Manager -> Session and startup -> Session tab.

---

### Post by rburkartjo on 2012-11-08
toz tks and i was not auto saving sessions. will give the clear sessions a try

---

### Post by rburkartjo on 2012-11-08
toz that did the trick.

---

