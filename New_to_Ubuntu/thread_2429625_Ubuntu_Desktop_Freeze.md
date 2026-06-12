---
title: "Ubuntu Desktop Freeze"
date: 2019-10-21
forum: New to Ubuntu
---

### Post by treatyman on 2019-10-21
Hi, I've installed latest version of Ubuntu on dell xps laptop. Every day the desktop freezes and doesn't accept keyboard or mouse clicks anywhere on the desktop except on the Ubuntu sidebar, time display on top and WiFi, power and sound icon are all click able. Show applications is also clickable and once I click this I can type in the search bar and the icons on the desktop are clickable. As soon as I click on any app the main desktop area again becomes frozen. This is really annoying as restarting the laptop seems the only way I can fix it. 

It's like there is something from the sidebar active which doesn't allow desktop input. As the sidebar icons are clickable always I've tried right clicking and closing all apps, moving them around is case one is highlighted but no joy. 

Any help would be appreciated.

---

### Post by TheFu on 2019-10-21
Please be specific on "latest version" ... a new release happened a few days ago.  If you are a typical end-user and not a developer, you'd be better served by using 18.04, which has 5 yrs of support, unlike any of the 19.xx releases which have 6-9 months of patches only.

There is a big difference between the entire system locking up and just the GUI locking up.  Typically, the lockups are just the GUI and are caused by either extremely low RAM/virtual memory or by a GPU driver issue.

There are a few different ways to troubleshoot those issues.
a) switch to a different tty - normally <alt><cntl>-F7 is the GUI tty, so by switching to <cntl><alt>+F1, F2, F3, ,,, F6 we can get to a text login prompt, then login and use **top** to see how RAM use is going.  Can also check the logs for problems.

b) if you have ssh-server setup on the machine, we can ssh into it from another machine on the network and use **top** and other tools to see issues.

In the end, normally, if you can get into the system using either of those methods, killing the web browser will often release RAM and de-lock a system stuck due to very low RAM.  There might be some reasonable solutions to a low RAM situation that would provide some feedback BEFORE getting to the point of lockup.
**free -hm** is the command to see how RAM is being used on a macro scale. For example, 
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           996M        727M        140M        3.0M        128M        133M
Swap:          2.1G        528M        1.6G
```
That output isn't for a desktop system.

---

### Post by treatyman on 2019-10-21
Hi, sorry for not being more specific. I am using Ubuntu 18.04.3.
When the desktop freezes there are only a few actions I can take, sidebar and top toolbar remain active. Therefore I can switch between apps using the mouse on the sidebar but I can't type or click on these active applications.

Therefore any keyboard input doesn't work either so any combination of keys I press nothing happens.

---

### Post by pakhuridze2017 on 2019-10-21
Guys after shut down ubuntu ,ubuntu stuck at loading ,not starting user panel for authorization.
if i press restart manual or auto ubuntu starting well.
what the problem ? 19.10 19.04 problems is same.

---

### Post by uRock on 2019-10-21
> **pakhuridze2017 said:**
> Guys after shut down ubuntu ,ubuntu stuck at loading ,not starting user panel for authorization.
if i press restart manual or auto ubuntu starting well.
what the problem ? 19.10 19.04 problems is same.

Please start your own thread and include the output of the following command run in a terminal.```
lspci
```

---

### Post by treatyman on 2019-10-21
Back to my issue.. It's happened twice since I've first posted and it seem to happen when I am opening apps from the sidebar. Its like something on the sidebar is active like moving an icon or something
It's hard to explain but it seem to always happen when I've clicked on an icon on the sidebar, sometimes the little hand appears to move the icon and I hit esc and usually the hand disappears and there is no issue. Sometimes the hand disappears but the desktop freezes.

---

### Post by TheFu on 2019-10-21
Can you ssh in from another machine?

---

