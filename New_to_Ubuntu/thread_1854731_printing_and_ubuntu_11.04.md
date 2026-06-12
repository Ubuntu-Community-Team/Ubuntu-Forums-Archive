---
title: "printing and ubuntu 11.04?"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by soylentcola on 2011-10-04
So I've been having a serious hassle with trying to get my HP Deskjet 90Cse to print.  I had set it up once where my entire family could print from the main computer (that has Ubuntu 11.04 installed on it) with no problems, but it suddenly stopped working.  Deleting and reinstalling the printers on the Windows machines didn't help, as it couldn't find the printer on the Ubuntu machine at all - despite me having set it up to be shared.

So now I'm coming to you all for help.  The printer in itself isn't wireless, but we could print to it via wireless router.  I'm willing to provide any necessary information if I can get this fixed once and for all.

I've installed HPLIP on the Ubuntu 11.04 machine, and even set the IP address as static on the machine itself (which I think I did right, I'm not 100% sure) but none of that seemed to help as I would always get an Error 5012 when opening HPLIP.

So is there anyone out there who'd be willing to help out? If you need anything else, don't hesitate to ask!

---

### Post by mastablasta on 2011-10-05
can you see the printer form windows? can you somehow reach it manually (type in the path to printer)?

---

### Post by soylentcola on 2011-10-06
Initially I could - via Network (on a Windows computer) but then it suddenly disappeared and couldn't be found. The printer still worked with the Ubuntu machine, but I couldn't connect it to others on the network because it wasn't visible.

---

### Post by Robyn-Hoodridge on 2011-10-07
Did it disappear at the time you gave it a static IP? And if so are you using CUPS print server?
Because as i understand it CUPS only listens for directions from the local machine by default. 
Have a look here - [https://help.ubuntu.com/11.04/serverguide/C/cups.html](https://help.ubuntu.com/11.04/serverguide/C/cups.html) - especially under the 'Listen' sub section, for how to set it to listen over the LAN that it's on through the wireless router.

---

