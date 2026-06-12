---
title: "Kubuntu 14.10: Laptop only sleeps when closing lid every other time"
date: 2015-05-26
forum: New to Ubuntu
---

### Post by Matt_Smigielski on 2015-05-26
I am running Kubuntu 14.10 on an older Toshiba Satellite laptop. I  have configured it via System Settings to sleep when I close the laptop  lid.
  
This works but only every other time I close the laptop. For example,  the first time I close the lid, it sleeps. When I open the lid, wait  for it to wake up, and close it again, it won't sleep (but the screen  turns off). 


  It is consistently sleeping only every other time I close the lid. Am I missing something?

---

### Post by DuckHook on 2015-05-28
It's just my guess, but it is possible that you may have two (or more) power handling services active at the same time, each in conflict with the other. This will sometimes lead to odd behaviour such as yours.

Most distros have a number of services capable of modifying power settings. To my knowledge, there is at least ACPI and the power manager that comes with the DE. In your case, the latter would be the system settings that you have already configured. I don't run Kubuntu, so am unfamiliar with it. It is possible that the screensaver is yet a third power manager. A Kubuntu expert could tell us.

Try disabling power management in your system settings and see if that helps. You are not actually disabling power management: you are just allowing ACPI the chance to handle it alone and without interference from the DE. Also, check your BIOS settings to see if power management is also turned on there.

---

