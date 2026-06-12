---
title: "[SOLVED] CPU usgae at 99%"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by natman on 2008-07-27
I am running Kubuntu 8.04 on a laptop, and when i leave it idle for a bit ( 10min ish ) the fan goes wild, but when i touch the mouse it clams back down to normal. I ran "top" and seen that Xorg was using 99% of cpu at idle and drop away once i star working again. The only desktop effects i have are transparent windows, no compiz, just the standard KDE transparent stuff - the fan is fine when im working just not when its idle. Any ideas?

---

### Post by gjoellee on 2008-07-27
The same happened to me when I was running Kubuntu...I have no idea why, but running Ubuntu it isn't a problem(however I run Ubuntu and not Kubuntu, i was just trying Kubuntu using kubuntu-destop). The only thing I can help you with is this: > sudo killall
 and see what you can do...or just try restart or use one other kernel, and see if it gets better

---

### Post by braddcadd on 2008-07-27
What are your hardware specs?

---

### Post by stmiller on 2008-07-27
Disable any screensavers. Or set the screensaver to a blank screen.

---

### Post by silkstone on 2008-07-27
+1 for that. If you add the system monitor to your top panel, it displays processor usage in the icon. Some of the screensavers use a lot of processor!

If that isn't it, the Tracker tool may be indexing. That can take quite a while, but once it has finished everything should calm down. You can turn off the tracker - not sure how in Kubuntu, but in Ubuntu it's under System > Preferences > Search and indexing.

---

### Post by durand on 2008-07-27
Ummm, correct me if I'm wrong but tracker uses up I/O wait or whatever it's called and not the processor.

---

### Post by dhughes on 2008-07-27
> **silkstone said:**
> +1 for that. If you add the system monitor to your top panel, it displays processor usage in the icon. Some of the screensavers use a lot of processor!

If that isn't it, the Tracker tool may be indexing. That can take quite a while, but once it has finished everything should calm down. You can turn off the tracker - not sure how in Kubuntu, but in Ubuntu it's under System > Preferences > Search and indexing.

 Careful, there's also a bug that makes your CPU usage go to 100% when you add System Monitor to a panel. I don't know if it's been fixed yet and I'm not sure if it's specific to Gnome or any Ubuntu/Kubuntu version.

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/93847](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/93847)  Confirmed
"*Gnome System monitor sometimes claims to be using all of the spare capacity of my CPU, I cannot pinpoint when it happens, but it does happen. I pressed the report bug button while it was using 86% of my CPU according to itself, but now a few minutes later, it has settled on 11%.*"


 Although I see it's also a combination of the two problems: Fix released
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383)
"*Just opening system monitor (not sure if it's always) causes one of my CPUs to go to 100% usage. The process Xorg is the one that actually has all the CPU usage but I guess it must be system-monitors fault.*"

---

### Post by silkstone on 2008-07-27
I haven't had that problem, but thanks for the headsup. Re Tracker, it does run the processor but stops when another application is called. Once indexing is complete, it no longer uses the CPU except to update the index.

---

### Post by eightmillion on 2008-07-27
Tracker doesn't run when running KDE. KDE uses strigi.

My first thoughts on this issue was screensavers. Definitely disable screensavers.

---

### Post by natman on 2008-07-27
Cool, thanks i was using the double pendulum simulator screen saver ( ive modeled it using maths, guess its not as easy for a cpu :) ). Down to a simple clock screensaver now and fan is all quite - thanks

---

