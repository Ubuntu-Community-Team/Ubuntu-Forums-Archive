---
title: "CPU Underperforming?"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by Dj Melik on 2008-10-07
Is my CPU underperforming?

I have a AMD Athlon(tm) 64 Processor 3800+ 2400 ghz processor. But according to the following "Sysinfo" it seems like its underperforming and only operating at 1000 mhz.

[img]http://omploader.org/vdDR6/Screenshot.png[/img]

If it underperforming, how can I fix it?

---

### Post by bikeboy on 2008-10-08
Put your CPU under heavy load and check again. Most likely it's just frequency scaling to save power when its full speed is not needed.

---

### Post by Dj Melik on 2008-10-08
> **bikeboy said:**
> Put your CPU under heavy load and check again. Most likely it's just frequency scaling to save power when its full speed is not needed.

Yes you are right. Thanks for clarifying :)! I put it under heavy usage and it jumped right up to 2400 ghz.

Is there any way I can just make it use full speed all the time?

---

### Post by bikeboy on 2008-10-08
I don't think it's really necessary, it's done to save power and heat (Windows does it too).

If you want though, try Ubuntugeek's guide - [http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)

---

### Post by jerome1232 on 2008-10-08
This is actually a hardware feature (sometimes software) most amd chips you would disable cool 'n quite technology in the bios to disable cpu scaling.

But it's a good thing really, saves on wear and tear on your fan because it's not always having to go full blast keep your cpu cool.

---

