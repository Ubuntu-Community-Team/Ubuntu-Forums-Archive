---
title: "System Improperly Shutting Down?"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by abc617 on 2013-06-06
I recently set up my desktop to dual boot Windows and Ubuntu with an an SSD. It works great but one area I'm concerned with is how fast its shutting down.

It shuts down really fast, a little too fast. The reason I think its a problem is because sometimes I will forget to close out of all my active browser windows (I use Google Chrome as my browser). So when I boot my computer back up, it'll say "Browser was improperly closed". Also I use [screenlets]("https://apps.ubuntu.com/cat/applications/screenlets/"). And I have to cutomize this one screenlet (InfoPanel) to display the right weather and statistics I want. Upon a reboot/restart, I find all my settings for that screenlet have not been saved. Thus leading me to believe that my computer is improperly shutting down.

For reference, I followed this guide right here on how I set up a dual boot Ubuntu/Windows with an SSD + HDD combo:
[http://forum.xda-developers.com/showthread.php?t=1627197](http://forum.xda-developers.com/showthread.php?t=1627197)

I followed many of the tweaks and modifications here, but I have a hard time determining which one of the tweaks/modifications may be causing this issue. At first I thought it was maybe something with the swap file, but it does not seem to be the case. I also tried reinstalling the Ubuntu OS with fresh settings and that doesn't seem to fix it.

Any solutions or insight is greatly appreciated!

---

### Post by Cvxcvgg on 2013-06-06
Basically, when you choose to shut down it forces every process to halt, so it's pretty much the same as closing "chrome.exe" in Windows Task Manager. It will say that it was improperly closed, but it's nothing to worry about in most cases.

---

