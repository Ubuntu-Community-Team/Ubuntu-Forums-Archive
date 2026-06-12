---
title: "How to load driver module foe Epson printer"
date: 2020-06-11
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-06-11
Hello!

So I'm having trouble working out how to load the driver module for an Epson printer. I ran "sudo apt install printer-driver-escpr" which did it's thing, but the printer still wouldn't work. I then tried "lsmod|grep -E "printer|driver|escpr"" but nothing showed up so I rebooted and tried again but still no luck.

I then ran "dpkg -L printer-driver-escpr" which showed me various file-paths leading to libraries of the same name as the package, which I then used in conjunction with "modinfo" to basically just see what it would tell me, but to no avail.

Can anyone give me any clues?

Edit: okay so in a thrilling twist I plugged the printer in after I rebooted the laptop and it now offered me two printer devices - one was just named "Epson ET-2550" and the new addition was "Epson ET-2550-series" with the second one showing it's location as the name of my laptop. At this point I tried printing using the latter and it worked.

still I'd like to find out if the printer is using the driver I downloaded or if something else is going on, as GNOME settings just shows the printers driver as "EPSON ET-2550 Series" which isn't the name of the package I installed?

---

