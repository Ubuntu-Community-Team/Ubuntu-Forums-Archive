---
title: "Monitor shuts down"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by Drawstop on 2012-04-16
Please will someone tell me how to stop my monitor shutting down after a few minutes whilst I am watching a video? I am using 10.04 and think it is excellent.
Thanks for help in the past.
Richard.

---

### Post by Tamlynmac on 2012-04-16
> Drawstop

Some additional information would be nice.

For example, does your monitor power go out or does the monitor screen just go blank and the monitor power stay on? What type of video card are you using and what application(s)? In other words is it a power management problem or is it an app/related software issue?

I noticed, in one of your previous threads you were asked what type of graphics card your using and you never responded. I'd strongly suggest that when you ask for assistance here, you provide as much information as possible. This will help others to help you.

Try and provide as much system & relevant information (including applications) as it relates to your issue(s). Remember we can't see your system and have no way of identify your system components. Neither do we know which applications your running or what you've installed - unless you share that information. My recommendation is to take the time not only to ask for assistance, but to learn about Ubuntu.

Good Luck

---

### Post by Drawstop on 2012-04-16
Firstly my sincere apologies and thank you for your reply. I am suitably chastened.  This comes of being 80 and not growing up with computers. Also  - I am writing on behalf of a disabled friend whom I look after and the problem is on his PC.
Th monitor is an Asus P8Z68-V/GEN3
The graphics card is an XFX AMD graphics card.
The monitor fades out over 4 or 5 seconds but the power stays on. If I click the cursor before the screen fades to black then it immediately recovers for another 6-8 minutes.

---

### Post by audiomick on 2012-04-16
It looks like all that is happening is that the energy management thinks you are not using the computer and turns off the monitor. This is "normal", even if not apparently logical, behaviour. The system just doesn't register the viewing of the film as activity.

The solution is to go into the energy management menu entry and change the setting for the time after which the monitor is turned off on inactivity from a time value to "never".

The menu is at 
system> preferences> energy management.

I'll attach screenshots of the menu and of my mouse pointing to the setting on my laptop set to "nie", the German for "never". It is all in German, but it should show you where to look despite this.

---

### Post by Drawstop on 2012-04-16
Michael
Many thanks indeed for your help. Having carried out your suggestions it seems the problem is cured and Steven can now watch videos to his hearts content.
Thanks again.
Richard.

---

### Post by audiomick on 2012-04-16
Glad to help. :)

---

