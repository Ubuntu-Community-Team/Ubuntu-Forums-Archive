---
title: "[SOLVED] I think ubuntu is using the wrong graphics card?"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by Axis on 2008-10-06
So as my topic states I believe ubuntu may be using the wrong graphics card on my system. I think its using the integrated instead of the 8600gt that I installed.

How can I check to see what card ubuntu is using?
And if it is using the wrong one, how can I fix it?

Thanks,
Axis

---

### Post by Ocxic on 2008-10-06
The onboard card is disabled when a graphics card is installed, and your monitor will not work on a card that is not in use.

---

### Post by Zzl1xndd on 2008-10-06
> **Ocxic said:**
> The onboard card is disabled when a graphics card is installed, and your monitor will not work on a card that is not in use.

Ocxic is 100% correct if you install another card it would disable your on board card and I assume you hooked you monitor into the new card so if you have information displaying on the screen you are good. 

You might need to install drivers to get the full effect from your new card though, try going to System > Hardware Drivers, and see if the drivers for your 8600 are installed.

---

### Post by eternalnewbee on 2008-10-06
There's a system tool called sysinfo. If you don't have it you can install it via add/remove applications. That will show you all your hardware. And in system - administration you can find Hardware Drivers.

---

### Post by Axis on 2008-10-06
> **eternalnewbee said:**
> There's a system tool called sysinfo. If you don't have it you can install it via add/remove applications. That will show you all your hardware. And in system - administration you can find Hardware Drivers.

Thank you very much for you useful reply. It tells me I am in fact using the installed card, I wonder why my performance is lacking so much. Must be a problem with wine? O well I will have to research it.

Thanks to everyone else for their replies as well. :popcorn:

---

