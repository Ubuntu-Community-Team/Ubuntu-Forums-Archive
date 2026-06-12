---
title: "Kubuntu 19.10 crashing 1-3 minutes after start"
date: 2019-12-13
forum: New to Ubuntu
---

### Post by rainbowraven on 2019-12-13
I got Kubuntu 19.10 dual-booting on my Dell Inspiron 7567 with Windows  10, to make sure everything was compatible before I switched. I guess  I'm glad I did. On my initial "try it out" boot, everything was going  fine, but since I installed, every time I reboot, it crashes within the  first few minutes. By crash, I mean everything freezes up. The keyboard does not respond. The mouse still moves but is unable to click anything. Since the keyboard doesn't work I'm unable to use anything like terminal.

I went back into Windows and installed the only BIOS update for Linux that Dell had available (it was in .exe format and ran fine in Windows.) I downloaded the latest driver for my graphics card from NVidia (GeForce GTX 1050) in Kubuntu but nothing apparent happened.

 I've gone through at least a dozen reboots. All the  Kubuntu available updates have installed. I ran a Memtest which returned 0 errors. Below please see the contents of my system logs. (I cut off a small bit of the bottom of the image that showed my real name, which is my username - but it was all black text, no orange.) This was all I was able to get - after several boots, each time I would try to click on Kernel logs, it would crash again.

The only thing I've installed  that wasn't already was Flux (a utility which changes the temperature of your screen color, kind of like a night mode), and I don't know yet how to remove it. If I have to boot into the OS to do so, I need something that will work *fast* before the system crashes.
 [ATTACH=CONFIG]284610[/ATTACH]

---

### Post by rainbowraven on 2019-12-17
Please, can anyone suggest anything I can try?

---

### Post by Impavidus on 2019-12-18
Random crashes are hard to diagnose.

Can you still use ctrl+alt+F1 through ctrl+alt+F7 to switch between the GUI and some TTYs (command line interface)? Can you still use SysRq+REISUB? Those keyboard commands are directly handled by the OS, not passed on to the GUI, so they should still work if it's just the GUI that crashed. You can also access the log files using your live disk. They may hold some clues.

---

### Post by Autodave on 2019-12-18
To me, the fact that the mouse pointer moves but you cannot click with it, that could be a power supply problem.  How many USB things are you using?  Can you disconnect everything except the mouse and keyboard and see if that helps?  A powered USB port might help also.

Do you have this (or a similar) problem with Windows?

---

### Post by SeijiSensei on 2019-12-18
Any clues in /var/log/syslog or other logs in /var/log?

---

### Post by rainbowraven on 2019-12-19
I don&#8217;t have anything via usb plugged in except my wireless mouse adapter. I tried REISUB but like I said, my keyboard doesn&#8217;t respond. (It&#8217;s a laptop btw.) I don&#8217;t have any issue with Windows. I can try to get to more logs than what I posted but it crashes before I get there. I&#8217;ll try again, though.

---

### Post by Impavidus on 2019-12-20
Do you also get this crash when you run the live disk, try Kubuntu before installing? If you can still run the live disk, we can rule out most hardware problems. And you can access the logs of your installed Kubuntu system from the live session.

---

### Post by Autodave on 2019-12-20
Have you tried with a wired mouse?

---

### Post by rainbowraven on 2019-12-20
I didn’t have any problems when I ran the live disk, no. Here are some more logs I got. Sorry it’s a camera photo...by the time I try to take a screenshot and upload it, the system inevitably stops responding. 

Blacked out part is just my real name. I think I’m going to end up uninstalling and just waiting until I have an old PC I can install Kubuntu on and not dual boot, because now I am finding problems with Windows. After I have been in Kubuntu and I log back into Windows, my clock has been set back 6 hours (my time zone is Central which is -6 - correlation?) and I just had a random reboot in Windows.

[ATTACH=CONFIG]284645[/ATTACH]

---

### Post by rainbowraven on 2019-12-20
> **Autodave said:**
> Have you tried with a wired mouse?

The mouse is working fine, it’s the keyboard that stops working.

---

### Post by CatKiller on 2019-12-20
> **rainbowraven said:**
> I didn’t have any problems when I ran the live disk, no.  

From the live disc you'll be able to grab log files and the like from your hard drive, and you should have Internet, too. You're also able to make configuration changes to your install should you need to. 

>  After I have been in Kubuntu and I log back into Windows, my clock has been set back 6 hours 

Windows expects the hardware clock to be set to local time. Every other OS expects the hardware clock to be set to UTC. You can change the behaviour at either end. 

> **rainbowraven said:**
> I downloaded the latest driver for my graphics card from NVidia (GeForce GTX 1050) in Kubuntu but nothing apparent happened.

If you mean that you downloaded a file with a .run extention from Nvidia's website, nothing will have happened from simply downloading it. Don't try to run it. That file is for package maintainers rather than end users; end users should install the driver through the package manager.

Since you can still move the mouse the computer hasn't crashed. If you were to SSH in you'd probably find that almost everything is still working fine. It sounds to me like the window manager has hung. Optimus setups have quite a few rough edges.

---

