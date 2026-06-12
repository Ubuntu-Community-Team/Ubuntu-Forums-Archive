---
title: "DASH search not working"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by renchu on 2013-10-19
I have been using Ubuntu for a while now. Recently when I try to use Dash Search, it cycles for a long time and then finds nothing. Happens more often with Apps but now occurs with Home so even Recent used app, files etc dont show up.. It appears to be working on our other accounts on the same laptop. Any thoughts??

---

### Post by grahammechanical on 2013-10-19
Have you modified the privacy options at all? Not only can we limit the Dash from searching on-line but we can stop the Dash from recording the files and applications that we have used. This is what Security and Privacy says under the Files and Applications tab.

> This operating system keeps track of Files and Applications you have used to provide extra functionality. If other people can see or access your user account, you may wish to limit which items are recorded. 

We have the option to switch all recording off or to switch off the recording of particular items. But we lose functionality.

Regards.

---

### Post by rtimai on 2013-10-19
The Privacy Options you refer to, except "include online search results," records the user's usage history, and doesn't have to do with the DASH Search function. On my system immediately after upgrading to Ubuntu 13.10, Dash Search either displayed the spinning 'working' logo and was unresponsive, or returned the message, "Sorry, there is nothing that matches your search." This continued for about two hours (while I searched the web for a solution,) and then Dash Search suddenly began working normally again, without any fix attempted. It's possible the mlocate database index (or something similar) has to be rebuilt in some cases, and may take some time before Dash search regains functionality.

In my specific case, Dash Search automatically fixed itself. So, it's possible that the mere act of searching for a solution will fix the solution without any fix being applied. (Only kidding!!!)

UPDATE: After re-enabling third-party software sources (which were temporarily disabled during the 13.10 upgrade) and installing the additional updates, I rebooted -- and DASH search is once again acting as previously described. I think it may once again start working after a while, but I hope this doesn't occur on every reboot. Will report here additional information, if any.

UPDATE: After more searching, one user mentioned that the required unity-scope-home was removed due to a bug, and reinstalling it restored his DASH functionality. I started Synaptic (Package Manager) from Ctl-Alt-T Terminal, entered my password, and searched for unity-scope-home. It was not installed. Selecting it also selected a dependency call unity-scopes-master-default. After installing these two unity-scopes DASH appears to be working normally. YMMV, HTH.

---

### Post by echotech2 on 2013-10-21
Same as RTIMAL.  Just the "busy" signal and "No matches......" displayed.  I did some browsing for a while till the coffee kicked in and when I decided to try and find out what was happening, it was working.

---

