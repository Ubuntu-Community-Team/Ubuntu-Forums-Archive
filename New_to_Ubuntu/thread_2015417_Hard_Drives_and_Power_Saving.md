---
title: "Hard Drives and Power Saving"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by andperry on 2012-07-03
I have got Ubuntu 12.04 Server running on a desktop machine. As this needs to run 24/7 on a domestic electricity bill, power saving is a major consideration. There is no monitor overhead as the machine is run entirely from another via SSH, which leaves the hard drive as the main item likely to consume a significant amount of power.

I read on another forum that it is quite easy to configure Ubuntu to spin down hard drives after a period of inactivity, but the person had never succeeded in making it spin down the system drive, but only additional drives. Does anyone know whether it is actually the case that the system drive cannot be spun down?

I also have an idea for another solution which has come from reading a magazine article. Whist this was aimed mainly at Windows users, there is probably no reason why it cannot be applied to Linux systems as well. The idea is to use a solid state drive, but to use it as system partition only with the data partition still on a conventional drive. The reason for configuring it this way is that constant data access will put more wear and tear on a solid state drive than a conventional drive.

The solid state drive seems a nice idea and would solve any problem of not being able to spin down the system drive, but how long would it take to pay for itself in terms of the resulting energy saving? Bearing in mind the small footprint of Linux compared to Windows, what about permanently booting and running the system from a USB flash drive with the data on a conventional hard drive? Is this viable and would it be efficient in terms of system performance?

Any ideas about any of the issues mentioned here?

---

### Post by Paqman on 2012-07-03
> **andperry said:**
> Does anyone know whether it is actually the case that the system drive cannot be spun down?

It's highly unlikely that the drive would ever be able to spin down, as there would be constant little writes going on. You could try shifting stuff like the logs to RAM or a network share, but I suspect there would be just too much background activity from the OS for it ever to be idle.

> The idea is to use a solid state drive, but to use it as system partition only with the data partition still on a conventional drive.

Yep, that would work well. You can get SSDs as small as 40GB that be suitable.

> 
how long would it take to pay for itself in terms of the resulting energy saving?

Never, the drive would likely fail first. If you were saving, say 5W on average then at UK electricity prices it would save under £6 per year. Getting an SSD purely for power saving doesn't make economic sense on a desktop, and the embodied energy of the drive would negate any emissions savings.

---

