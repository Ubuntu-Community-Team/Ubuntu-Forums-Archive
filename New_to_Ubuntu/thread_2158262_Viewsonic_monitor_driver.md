---
title: "Viewsonic monitor driver"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by 2good2btrue on 2013-06-28
Hi - I'm a brand new ubuntu 12.04 user.

Just bought a new viewsonic monitor VA2448-LED. There does not appear to be
a driver available? Can anyone help please?

Thank you.

---

### Post by Dennis N on 2013-06-28
They supply a driver cd with the monitor, but those drivers are for Windows. I have several Viewsonic monitors here in the lab, and they all work with Linux (including Ubuntu) out of the box - no driver needed to be installed by the user.

What happens when you use the monitor as is?

---

### Post by 2good2btrue on 2013-06-28
Thank you so much for your time. Yes i have just contacted Viewsonic and they only support windows and mac.
When I first loaded ubuntu i was using an old monitor, and this works fine. I bought this now viewsonic
monitor and it does not respond. Is is because the system is only looking at the old monitor? do I delete?
I did think about reloading the os system with the new monitor connected - a bit long winded though.

**Hi Dennis N - Don't know what I've done, but it's working now! thank you for your response**.

---

### Post by Dennis N on 2013-06-28
You say it does not respond. What does that mean? There should be a Viewsonic splash screen for a few seconds when the monitor is turned on by itself. If not, I would suspect the monitor. Then check with both VGA and DVI connections. If there is signal from the computer, you should see startup display in some low resolution at least.

That monitor is not a new model, (2010-2011?) so newness is not the reason. I have three VA2250wm LED here which are about that age and probably very similar electronically - they work fine with Linux.

When they say "we do not support..." they are talking about their customer help, not that it doesn't work with Linux.

EDIT
Missed your edit - glad you have it working.

---

### Post by JKyleOKC on 2013-06-28
As Dennis said, the response from Viewsonic simply means that they don't provide tech support for systems other than Windows and Mac; the monitor itself willl work properly with any system that sends it the signals it expects.

Glad to hear that it's working now. Linux systems, unlike Windows, customize their configuration to match the hardware each time they power up rather than at install time. I suspect that you rebooted and that's what made it work. If you want to see all the gruesome details, you can examine the files /var/log/dmesg and /var/log/syslog to see what happens, step by step, but be warned that it really is a huge mass of detail and quite easy to get lost in... There's also a log at /var/log/Xorg.0.log that will detail exactly what happens during initialization of the display.

However there could have been other factors, too. The Viewsonic on my wife's older machine (now retired) had to have both the VGA and DVI cables connected, before it would display during the boot sequence. That machine's BIOS supported only VGA, while its video card made the switch to DVI during its initialization. Before I discovered the need to connect the VGA cable, the monitor appeared to be totally dead! After connecting it, the display started as "Analog" and later switched to "Digital" automatically. I've not connected that monitor to my Xubuntu systems so don't know what it will do there...

---

### Post by 2good2btrue on 2013-06-28
Thanks for the detailed reply. I guess in future I should try and work through the problems
over a couple of days before posting for help. I fear that the change from XP to Ubuntu
is going to be a long and frustrating journey.

---

### Post by QIII on 2013-06-28
Hello!

No, don't worry about waiting to ask a question.  Ask up front if you encounter a problem.  Also ask up front if you are thinking about making some change to your installation -- that will help keep you from borking it.

Don't frustrate yourself by trying too hard to get things done blindly.  We are here to help!  Ask away!

And yes, there is a learning curve.  This is just like learning a foreign language.  Germans speak German without thinking about it.  If you want to learn German, you have to study and work at it.

Best wishes.

---

