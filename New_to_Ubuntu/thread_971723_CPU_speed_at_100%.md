---
title: "CPU speed at 100%"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by absintheminded on 2008-11-05
I am using 8.04. Whenever I try and launch a web browser, Opera (latest release) or Firefox (version 3), CPU speed shortly after goes up to 100% in the system tray and the browser windows crash (greys out). What can I do to sort this problem? My processor also generates a really annoying high pitched whistle.

I'm now having to use XP for my surfing, which kind of beats the point of having ubuntu for me.

Any ideas what this could be?

EDIT: I also have intel quad core 2.4 ghz processor... so my system isn't supposed to be this slow.

---

### Post by Sealbhach on 2008-11-05
When it happens, look in System Monitor and see what's using up the resources.

The usual suspect would be Flash. Try uninstalling and reinstalling it.


.

---

### Post by philinux on 2008-11-05
> **absintheminded said:**
> I am using 8.04. Whenever I try and launch a web browser, Opera (latest release) or Firefox (version 3), CPU speed shortly after goes up to 100% in the system tray and the browser windows crash (greys out). What can I do to sort this problem? My processor also generates a really annoying high pitched whistle.

I'm now having to use XP for my surfing, which kind of beats the point of having ubuntu for me.

Any ideas what this could be?

EDIT: I also have intel quad core 2.4 ghz processor... so my system isn't supposed to be this slow.

From a terminal, Apps>Accessories>Terminal use the command ```
top
```
Launch FF or opera and see what it causing the problem.
Have you checked in System>Admin Hardware Drivers for your graphics driver.

---

### Post by absintheminded on 2008-11-05
I ran 'top'. While at 100% a command called "Xorg" takes up most of my CPU. I'm in Ubuntu now, the 100% CPU usage went away finally with an error message saying "A malicious client may be eavesdropping on your system" or something the like. Anybody got a clue? Is my computer being hijacked? I have uninstalled flash and I have checked that I am using my ATI restricted driver. Hope it works, we'll see.

---

### Post by Sealbhach on 2008-11-05
> **absintheminded said:**
> I ran 'top'. While at 100% a command called "Xorg" takes up most of my CPU. I'm in Ubuntu now, the 100% CPU usage went away finally with an error message saying "A malicious client may be eavesdropping on your system" or something the like. Anybody got a clue? Is my computer being hijacked? I have uninstalled flash and I have checked that I am using my ATI restricted driver. Hope it works, we'll see.

Xorg is your graphical environment. On my laptop it normally uses 1% to 3% of CPU.

The warning about eavesdropping is a bit worrying. If I were you I would report it in the Security forum:

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)



.

---

### Post by absintheminded on 2008-11-05
Strangely I get the 100% CPU when completely disconnected from any internet, and without any browser open, so I dont think my computer is getting hacked into. Problem still presists occasionally. When cpu goes to 100% every window opened greys out and I cant perform any tasks.

---

### Post by Monotoko on 2008-11-05
There still could be something running, regardless whether your connected to the internet, it could still be monitering your system and checking to see if the internet is available, and when it is it will send it all off to the hacker, it sounds to me like a trojan.

I would post on the security forum, if you dont have the firestarter firewall, go get it:
```

sudo apt-get install firestarter

```

and see if that catches anything

---

