---
title: "Vokoscreen audio issues"
date: 2023-10-07
forum: New to Ubuntu
---

### Post by kiwipenguin on 2023-10-07
Please can I have some guidance for finding out how to fix an issue with VokoscreenNG? It won't let me record audio (only video). Is this the right place to ask?
I have tried re-downloading it from several different places but problem persists. Says audio recording not implemente (sic). Many other menu options and settings are also missing.
It works fine on my desktop but not on my HP laptop.
VokoscreenNG 3.1.0
Ubuntu 22.04 LTS
Many hours searching forums and google have not found the solution.

---

### Post by MAFoElffen on 2023-10-07
VokoscreenNG, when it was rewritten, Pulse Audio was added, just like 22.04 uses. In the App Settings dialog, select the audion tab and ensure "Pulse" is selected. In Ubuntu Settings > Sound > Input... Ensure that the Input Device is set to a device microphone, and the level is turned up.

If it happens after being Idle for a while, then in this file
```

mafoelffen@msi-ubuntu:~$ grep -A 1 'become idle for too long' /etc/pulse/default.pa
### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

```
Open /etc/pulse/default in an editor with elevated permissions, search for that setting and comment it out, just like this:
```

### Automatically suspend sinks/sources that become idle for too long
#load-module module-suspend-on-idle

```
Save and reboot.

---

### Post by kiwipenguin on 2023-10-08
Thanks for your reply.
I just found the problem. It was something to do with using Wayland or X11. I found a note in small print inside the vokoscreen UI saying that only limited functionality in Wayland and to switch to X11 for the full service. 
Not knowing what either were, I researched and then changed over at login. Now it works properly, all menu items and settings are back. I also selected pulse audio afterwards as you suggested.
It is now working properly.
Thanks again.

---

### Post by MAFoElffen on 2023-10-08
Glad it is working for you now.

If solved for you now, then select the "Thread Tools" link, in the upper right of this page, then mark your thread as "Solved". That help other users with similar problems to find your solution.

---

