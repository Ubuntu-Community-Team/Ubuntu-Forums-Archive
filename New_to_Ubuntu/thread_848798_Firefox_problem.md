---
title: "Firefox problem"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by dunbrokin on 2008-07-03
Why do I keep getting these errors with Firefox?

Jul  4 04:26:42 PJ kernel: [25035.617854] ipw2200: Firmware error detected.  Restarting.
Jul  4 08:01:21 PJ kernel: [28946.637603] ipw2200: Firmware error detected.  Restarting.
Jul  4 10:29:42 PJ kernel: [16244.221053] firefox[14415]: segfault at b78ab31a eip b7d992a5 esp bfa9a6e0 error 4
Jul  4 10:29:57 PJ kernel: [16250.045409] firefox[14425]: segfault at b784231a eip b7d2e2a5 esp bfc4f890 error 4
Jul  4 10:30:11 PJ kernel: [16260.707138] firefox[14439]: segfault at b77fc31a eip b7ce22a5 esp bf9d8de0 error 4
Jul  4 10:50:23 PJ kernel: [16646.160496] firefox[15138]: segfault at b77de31a eip b7cbd2a5 esp bfbe8010 error 4
Jul  4 11:58:29 PJ kernel: [17413.523734] firefox[17558]: segfault at b784231a eip b7d522a5 esp bfee9af0 error 4
Jul  4 11:58:29 PJ kernel: [17413.661135] firefox[17560]: segfault at b78ab31a eip b7d802a5 esp bf80f410 error 4

---

### Post by ZabiGG on 2008-07-03
Hi,

I'm sure lots of people could help, but you'll have to be more specific about your problem.

You appear to have a problem with your wireless driver (ipw2200), which may very well be connected to your Firefox problems. 

Did you install anything new or play with your system settings in any way before you started getting these messages?

Z.

---

### Post by dunbrokin on 2008-07-05
> **ZabiGG said:**
> Hi,

I'm sure lots of people could help, but you'll have to be more specific about your problem.

You appear to have a problem with your wireless driver (ipw2200), which may very well be connected to your Firefox problems. 

Did you install anything new or play with your system settings in any way before you started getting these messages?

Z.

Actually, my wireless seems to be working OK, this segfault seemed to start on the new FF update....I think...

I just rebooted my system ....and opened FF....again ..a whole load of segfaults.

---

### Post by ZabiGG on 2008-07-05
You should try removing Firefox completely from your system (in Synaptic, choose Mark for complete removal), reboot, and re-install.

It might solve the problem.

---

