---
title: "Firefox broken after update"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Julian Lewis on 2008-06-10
Firefox broken after update ....

ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],hidden)
5:()
6:()
7:currentEngine()
8:get_currentEngine()
9:updateDisplay()
10:init()
11:([object XULElement],1)

I tried to remove it and re-install, no joy.
It was working perfectly before the last update. I can't uninstall it and re-install. The package manager says its not installed but I still have the bad version after an uininstall.
I suspect its a DownThemAll plug in bug, can I get rid of this plugin by hand. Firefox is only just working and can't give me the usual windows for plugin removal.
How can I force a complete removal and re-install ?

Thanks Julian

---

### Post by alienexplorers on 2008-06-10
go to ~/.mozilla/firefox/profilename/extensions

---

### Post by Julian Lewis on 2008-06-10
I found the problem, it was netbeans that still had a firefox thread running. This screwed things up and the update failed. After I killed the thread and re-installed FF3 it restarted correctly .... phew !!!
I took a look at that location... scary stuff, luckily I didn't need to remove it and re-install all. Thanks for your prompt reply. Opera is OK but I am very dependent on FF3 and would have missed it ...
What was interesting is that I couldn't remove FF3, I installed FF2, but it displayed the title FF3 Beta when I ran it.. wierd.
Cheers Julian

---

