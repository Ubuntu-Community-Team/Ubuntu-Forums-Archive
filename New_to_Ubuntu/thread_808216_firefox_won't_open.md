---
title: "firefox won't open"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by hfp on 2008-05-26
Hey, everyone.  I recently had a problem with firefox.  I was using it and closed it because I had logged out of a webpage with user name and password information.  When I tried to re-open firefox it said that firefox was not responding, and that it was already running and that if I wanted to open it again, I would have to restart the computer or close the current firefox program.  In vista I would have pressed ctrl - alt - delete and closed the process from there, but I don't know how to do that in ubuntu.  I ended up just restarting the computer.  Has anyone come across this problem?  Thanks for your help.

---

### Post by N.N. on 2008-05-26
I've encountered that problem many times on Windows XP as well as on Ubuntu. To close a running Firefox process that doesn't show up in your window list either navigate to "System" > "Administration" > "System monitor" and close it from the "processes" tab as you would in Vista, or open a terminal and type the following command (assuming you're running Firefox 3): ```
killall firefox
``` If you're running Firefox 2, you should modify the command as follows: ```
killall firefox-bin
```

---

### Post by hfp on 2008-05-28
Thanks a lot, N.N.  I'll follow your instructions the next time this problem occurs.

---

