---
title: "Ubuntu won't recognize any devices? (USB, SD, iPod etc.,)"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by giordun on 2008-06-13
Why? Sometimes I need to restart my computer a few times to get it to work, but that's really annoying. Anyway to solve this?

---

### Post by Joeb454 on 2008-06-13
Open a terminal, and post the output of ```
lsusb
``` Now plug something in (say your iPod) and post the output of that command now something is plugged in

---

### Post by giordun on 2008-06-14
Ok...

Before...

jdan@jdan-desktop:~$ lsusb
Bus 003 Device 002: ID 046d:0992 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c018 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  

and after...

jdan@jdan-desktop:~$ lsusb
Bus 003 Device 002: ID 046d:0992 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c018 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  

nothing comes up. :S

The iPod won't show the "Do Not Disconnect' thing that it would usually show when it is connected.

---

