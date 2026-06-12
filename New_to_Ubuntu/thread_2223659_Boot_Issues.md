---
title: "Boot Issues"
date: 2014-05-12
forum: New to Ubuntu
---

### Post by shayne2 on 2014-05-12
I'm a Linux Noob and hobbiest.

I have a Ubuntu server primarily set up for running Plex Media Server which it has done pretty well for past year. I recently upgraded to 14.04 LTS and have been having problems with booting that I don't know how to begin to problem solve. My server is headless and is a box in the garage - major pain in the ass to move to my office to connect a screen to see what is going on. I do everything on the machine via a Putty ssh terminal from my Windows 7 desktop.

Basically the issue is that when I reboot using *sudo reboot -h now *my server does not come back online and gets stuck in the boot process somewhere but because I can't connect to it I can't see what is going on. If I then do a hardware reset it boots no problem and I can ssh and the Plex server restarts no problems.

Help!

Ultimately I want to install nomachine on it and connect a GUI remotely but I can't get it to boot properly since the upgrade to 14.04.

---

### Post by TheFu on 2014-05-12
Welcome to the forums.

Well, until you can access the boot log files, we cannot help. What does dmesg show? I would guess that some hardware is failing inside the machine and only a full HW reset clears it.

I couldn't put any running PC in my garage. The environment is just too hot for that here.
Also ... **reboot** doesn't accept **-h** according to my man pages. What do your manpages say that option does?  **shutdown -h now** is a common way to halt a system, however.

We need some facts and data to be helpful. Only you can gather those things.  Or you can press the BRS until that stops working too.  Most of my systems don't really get rebooted all that often - perhaps once every few months, so maybe this isn't an issue for you either?

BTW, running headless is extremely common, but running without a console ... that is a different issue. I have a few servers that don't have any graphics cards at all.

---

### Post by shayne2 on 2014-05-12
Thanks Fu... my "Garage" is not that kind of garage... I have a clean workspace in there and patch panel, comms, Router etc for the house is housed in a dedicated fan cooled cabinet. Most hardware in the is pretty new i.e. < 2 years old so I hope hardware failure is last resort! I had considered just carrying on with status-quo but I'm having major problems getting nomachine (no available sessions on this server) to work and thought I'd start with getting server running smoothly.

Sorry but noob question - what is the difference between headless (I though this meat no monitor) and no console?

Happy to provide whatever info is needed to help problem-solve but I don't know where to begin...

---

### Post by TheFu on 2014-05-12
Well, you need a way to watch the boot process.
* connect a monitor
* use a console (of some sort)

[http://www.cyberciti.biz/hardware/5-linux-unix-commands-for-connecting-to-the-serial-console/](http://www.cyberciti.biz/hardware/5-linux-unix-commands-for-connecting-to-the-serial-console/)

If may be possible to see the warnings/errors from the boots that work, which are breaking a reboot.  Again, what does **dmesg** show?
[http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files) might be helpful too.

---

