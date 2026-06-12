---
title: "[SOLVED] How to configure a printer in xubuntu?"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by anders_r_r on 2008-08-05
Hi

I attempted to follow the [[COLOR="Red"]printer configuration instructions[/COLOR]]("https://help.ubuntu.com/xubuntu/desktopguide/C/printer-configuration.html") given in the xubuntu desktop guide. However in Applications->System->Users and Groups I cannot find the the tab Groups, and I don't see the group shadow anywhere.

\Anders

---

### Post by Vishal Agarwal on 2008-08-05
Is xubuntu is different from ubuntu. Otherwise System->Administration->Printing Should work.

---

### Post by K2712 on 2008-08-05
Those instructions are for Xubuntu 6.04.  The settings you probably need would be under Settings->Printing->Edit->New Printer and it will search for attached printers.

---

### Post by prshah on 2008-08-05
> **anders_r_r said:**
> 
I attempted to follow the printer configuration instructions given in the xubuntu desktop guide. However in Applications->System->Users and Groups I cannot find the the tab Groups, and I don't see the group shadow anywhere.


There's an easier way: Open a browser, and in the address bar, type in ```
http://127.0.0.1:631
``` this will open the CUPS (Common Unix Printing System) administration page. You can make changes here very easily.

---

