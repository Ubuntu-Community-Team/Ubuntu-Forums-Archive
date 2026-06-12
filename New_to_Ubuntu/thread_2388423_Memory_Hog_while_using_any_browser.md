---
title: "Memory Hog while using any browser"
date: 2018-04-02
forum: New to Ubuntu
---

### Post by sonustar on 2018-04-02
[COLOR=#111111][FONT=Ubuntu]I am using 64 bit Ubuntu 17.10 running on Intel Quad Core i5 M560 @ 2.67GHz with 3.7GB Ram and 75 G Hard Drive. I am running GNOME 3.26.2.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have noticed that the Mem usage drastically increases as I use any browser. I have gone from Chrome to firefox to Opera to Chromium to Midori finally to Epiphany, with only slight improvement in results. I have also noticed that If I walk away with the browser open for more than an hour, I invariable come back to nearly non responsive computer with the memory consumption at full 100%. I am forced to kill the computer and restrat it. [/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Also , I find that closing the browser every 30 or so minutes does seem to help with performance, however, it is an extremly inefficient way to operate.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I only use the browser to get at Google Apps (Docs, drive mail, etc.) and no other application for the computer.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Please help me troubleshoot the issue and fix.[/FONT][/COLOR]

---

### Post by kerry_s on 2018-04-02
they say there's a memory leak in gnome. it's not the browsers.

---

### Post by TheFu on 2018-04-02
* Check the system logs. Always check the logs for issues, warnings, errors.
* Capture system performance data.  Best to do this using server-type tools. Pretty GUI tools aren't useful for gathering consistent data every 2-5 minutes in a way that can be compared over time.
* Use zswap.  Look for a how-to.
* monitor the amount of swap used. If the swap partition is smaller than 4G, you probably need more.  IMHO, 4.1G is the correct size for all desktops that don't use hibernation (if you care about security, do not hibernate!)
* memory constrained systems need to be carefully monitored to prevent out-of-memory problems.
There is a known bug in gnome3 that leaks memory.  Don't know if/when the fix will get to Ubuntu.  Perhaps switch to a different DE until it does?  [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1731071](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1731071)  and [https://fossbytes.com/gnome-3-26-memory-leak-issue-no-fix-ubuntu-18-04/](https://fossbytes.com/gnome-3-26-memory-leak-issue-no-fix-ubuntu-18-04/) and [https://www.omgubuntu.co.uk/2018/03/gnome-shell-memory-leak-is-being-fixed](https://www.omgubuntu.co.uk/2018/03/gnome-shell-memory-leak-is-being-fixed) seems to have some good news.

Hope this is helpful and perhaps accurate.

---

### Post by sonustar on 2018-04-02
Thanks Kerry,

Is there a resolution to the situation ? 

Any guidance is appreciated.

---

### Post by kerry_s on 2018-04-02
other than using another de, you'll just have to wait it out. shutdown when not using.
[https://www.omgubuntu.co.uk/2018/03/gnome-shell-memory-leak-is-being-fixed](https://www.omgubuntu.co.uk/2018/03/gnome-shell-memory-leak-is-being-fixed)

i'm using pop!_os 18 & i don't see that issue, my ram is always below 2gb, i can get it up to 3 using lots of apps, but it always drops back down to around 1.8

edit: i remembered, press-> alt+f2 & type r

this will restart gnome shell, it should bring the memory down when to high.

---

