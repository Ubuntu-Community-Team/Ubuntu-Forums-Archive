---
title: "Ramdonmly suspension/Lid"
date: 2016-08-17
forum: New to Ubuntu
---

### Post by xedoc on 2016-08-17
Hi,

I have a Razer Blade Stealth, i installed ubuntu-gnome.

When i close the lid the laptop suspend as it should, when i open the lid the system restart, also as it should but after a few secs it suspend again. I turn it on and it does the same over and over. Final solution is restarting the laptop.

An user here in the forum gave me a temporary solution:

Suspend Loop
Suspending (Close laptop lid) does not seem to work with a basic  installation. You can suspend but once the system resumes it suffers  from random suspends or the screen going blank for no apparent reason.
A temporary fix is to disable the automatic systemd suspend action by  chaning the HandleLidSwitch value in the /etc/systemd/logind.conf file:
HandleLidSwitch=ignore

My question is: Does anyone knows if there's a permanently solution for this problem ?

Kind regards,

---

