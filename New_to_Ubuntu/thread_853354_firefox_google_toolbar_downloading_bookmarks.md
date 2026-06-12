---
title: "firefox google toolbar downloading bookmarks"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by aBitLater on 2008-07-08
ubuntu 8.04 hardy
firefox 3.0

Google Toolbar suddenly won't show my bookmarks - it just says "Downloading Bookmarks...", but never fills in the drop-down list

any ideas?

---

### Post by aBitLater on 2008-07-08
I think this problem has something to do with using adobe flash player version 10, beta 2.  I was also having problems with Vuze (azureus) after installing flash version 10... so I went back to version 9 flash player to fix azureus, and all is good with bookmarks in google toolbar too.

---

### Post by ryukent on 2008-07-09
Open terminal. Type:

sudo apt-get install libxul-dev libstdc++5 gcc-4.1 libstdc++6

Then in firefox, go to tools, add-ons, disable google toolbar and let it restart firefox. Then do the same, but enable and restart firefox. Should now work.

---

### Post by lk_517 on 2008-09-01
I did exactly the same step as ryukent said, but it doesn't work. I am using 64bit Ubuntu 8.04. 

Anyone has any other idea?

---

### Post by braveerudite on 2008-09-09
Need help with this as well. Am I alone on this one?

---

### Post by jenkinsr99 on 2009-01-23
I had the same problem, 64 bit 8.10.  Just uninstall the toolbar and reinstall the toolbar beta 5, fixes everything.

---

