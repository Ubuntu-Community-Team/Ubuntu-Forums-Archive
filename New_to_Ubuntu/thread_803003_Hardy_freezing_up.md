---
title: "Hardy freezing up"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by bmann11 on 2008-05-21
I've been running Hardy since a few days after it was born.  Worked well to begin with but now it's beginning to freeze up and causing me to reboot, at least once a day.  Often this seems to happen when I'm running Firefox.

Anyone know if this is a common issue or if there is a way to fix it?  Thanks.

---

### Post by kilroy423 on 2008-05-22
Could you post any logs from /var/log for us?  

Kilroy

---

### Post by Fedz on 2008-05-22
Possible resolutions:

Goto Home (folder) > View (menu) > show hidden files and navigate to:
.mozilla > firefox > xxxxxxxx.defualt and delete urlclassifier3.sqlite file.

Un-install firefox and re-install.

Install the last stable version (not beta).

Could be a plug-in conflict.

Make your start-up homepage a plain'ish page and not any multi-media rich page (to test).

Hope this helps.

---

### Post by nick_h on 2008-05-22
Checking the log files is a good idea.

When it freezes does it freeze completely?  Can you still move the mouse?  Does audio continue to play?

How do you reboot?  Do the Magic SysRq keys work?

---

