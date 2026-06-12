---
title: "How to fix broken HTML Links in Thunderbird (for Ubuntu 6.06 and 6.10)"
date: 2006-11-05
forum: Outdated Tutorials &amp; Tips
---

### Post by irv on 2006-11-05
After having trouble with HTML Links in Thunderbird not working for a long time I found a fix on Thunderbird's forum. Just in case others are having the same problem finding a fix here is a quick how-to.

First find your Thunderbird profile, something like /home/[your user name]/.mozilla-thunderbird/.
Then edit or create a file  "user.js", and put the follow code in the file and save it to your profile folder.
By the way this is a hidden folder which starts with a ".".

> Code:

user_pref("network.protocol-handler.app.http", "/usr/bin/firefox"); 
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox"); 
user_pref("network.protocol-handler.app.ftp", "/usr/bin/firefox"); 

Now, restart Thunderbird and your HTML links should work.

---

