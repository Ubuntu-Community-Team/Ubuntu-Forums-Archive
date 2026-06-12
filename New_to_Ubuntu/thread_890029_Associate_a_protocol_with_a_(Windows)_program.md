---
title: "Associate a protocol with a (Windows) program"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Sam324 on 2008-08-14
Hi.  How do I associate a protocol (like http:// or ftp://) with a certain program?  In this case, the program that I need to associate it with is a plugin (Xfire) for Pidgin.  Also, is protocol association possible for Windows programs running under WINE?

---

### Post by damis648 on 2008-08-14
This is probably what you are looking for: [http://blog.ryaneby.com/archives/firefox-protocol-handlers/](http://blog.ryaneby.com/archives/firefox-protocol-handlers/)

EDIT: And yes, wine is also possible. Typing as the path
```
wine C:\Program Files\[directory]
```
should do it, where "C:\" is /home/[user]/.wine/drive_c/

---

### Post by wdaniels on 2008-08-14
Or if you need to do it directly through Gnome, run gconf-editor and look under the key path /desktop/gnome/url-handlers/ (the existing handlers should serve as sufficient examples of what needs to be added). It's only a command so I don't see any reason why it wouldn't work with wine.

---

