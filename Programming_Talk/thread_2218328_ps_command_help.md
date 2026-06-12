---
title: "ps command help"
date: 2014-04-20
forum: Programming Talk
---

### Post by manjaba on 2014-04-20
Recently I was making an adjustment in one of the settings windows when it froze. I have ubuntu 2012.04. I wanted to terminate the process and used ps but could not figure out which process for the settings window. Is there a way to use ps that will identtfy a process that is not working. Also how do I find the process ID of this process ?

I checked the ps man pages and googled this but did not see an answer.

Many thanks.

---

### Post by ofnuts on 2014-04-20
AFAIK ps cannot tell the associated window. Your desktop must have some task manager application that will report the window title associated to the process if there is one, and from which you can usually kill the process directly. Otherwise with PS you can often make an educated guess using the displayed names of the executables.

---

### Post by manjaba on 2014-04-20
Thanks for pointing me in the right direction ofnuts! Found that system monitor is the equivalent of win task manager for unbuntu.

---

