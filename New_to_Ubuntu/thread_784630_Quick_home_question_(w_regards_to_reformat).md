---
title: "Quick /home question (w/ regards to reformat)"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by mdk7 on 2008-05-06
I want to completely reinstall Ubuntu from the latest liveCD.  I currently have my /home on it's own partition, but I was wondering about all those hidden folders (like .audacity or .config) in there.  

I really am doing this reinstall to clear out some package / dependency clutter that's accumulated and messed up my 'uname -r' output with the actual headers installed.

I'd prefer to just start over with it and was wondering if I am OK deleting pretty much everything in /home that's a hidden folder (not "Documents" and the like).

---

### Post by Blutack on 2008-05-06
Watch out if you have any personal data - for example Emails, tomboy notes, firefox bookmarks etc may need saving.  Best thing is to dump all the .folders into a spare folder with your home (DotFolders for example) so programs won't find them and that way, if you find you need anything critical you can get it.  If you don't need any after a couple of weeks just delete the DotFolder folder.

---

### Post by Oldsoldier2003 on 2008-05-06
> **mdk7 said:**
> I want to completely reinstall Ubuntu from the latest liveCD.  I currently have my /home on it's own partition, but I was wondering about all those hidden folders (like .audacity or .config) in there.  

I really am doing this reinstall to clear out some package / dependency clutter that's accumulated and messed up my 'uname -r' output with the actual headers installed.

I'd prefer to just start over with it and was wondering if I am OK deleting pretty much everything in /home that's a hidden folder (not "Documents" and the like).

the hidden folders are configurations, with the exception of some apps like tomboy, wine and virtualbox. For the most part, deleting them won't hurt you, you'll just have to reset any special preferences you had for your applications.

---

### Post by mdk7 on 2008-05-06
Yeah that's kind of what I wanted to do by getting rid of them.  Somehow my kernel version says 2.6.22.14-generic but the linux-image headers installed were 2.6.26.16 or something similar (that was newer).  I tried running the update and upgrade wizard / apt but nothing updated that uname -r kernel.

---

