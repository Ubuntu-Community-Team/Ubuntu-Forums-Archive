---
title: "[SOLVED] netgear WG311v3"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by Stef11 on 2008-07-13
Hi all. Have loaded new Ubuntu 8.04, looks good.
Only problem i have is with netgear wireless pci card wg311v3.
Loaded ndiswrapper common, Utilities and finally ndisgtk.
Followed Ubuntu 804 documentation from this site and opened windows wireless driver,then followed these steps:
1/ selected install new driver
2/ chose location of my win.inf file
3/ then clicked on install
After step 3 nothing seemed to happen. The window marked "installed drivers still showed nothing.
Then went to Terminal
Typed "iwconfig"
this showed no wireless connection
typed ndiswrapper -v
This showed version on ndiswrapper as correct
typed ndiswrapper -l
this came up BLANK
no drivers listed

any help would be much appreciated
regards
Stef11

---

### Post by Stef11 on 2008-07-14
Have i forgotten something in the loading of ndiswrapper?
Help please
regards
stef11

---

### Post by Stef11 on 2008-07-14
Downloaded driver from different site, just in case problem.
No good, ndisgtk still indicates no drivers installed.
Whats Next?
Ran ndiswrapper from terminal just in case. No GOOD. STILL NO DRIVER LOADED.
HELP
Regards
Stef11
found the help i needed in the community Documentation titled configuring the netgear WG311v3.To the writer of the Doc, my sincere many thanks, all is now working perfect.
Regards stef

---

