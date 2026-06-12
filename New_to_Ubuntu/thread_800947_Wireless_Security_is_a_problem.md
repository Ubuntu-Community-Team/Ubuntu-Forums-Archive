---
title: "Wireless Security is a problem?"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by PPAAUULL on 2008-05-20
Ok so I am trying to get a computer going on WiFi. I have gotten the card all working (at least I think I have) It can see networks and even connect to open networks the problem arises when I try to connect to my secure network. A window pops up asking for the security stuff, pass, type (WPA) and what type of encryption (TKIP). I enter the password the same as I would in my other computers where it works and it seems to go away for a minute or two (where I think it trys to authenticate the password) then the same window pops up again and again. I thought maybe it was my routers problem so I turn the security off but it worked. so I looked at the log and I can see the same mac address authenticate then it is connected to the network (it says on the log) but for some reason it must disconnect and try again even though everything is good. How would I make this work? Am I missing something?
Thanks for the help.

---

### Post by GCoffee on 2008-05-20
Are you sure that its WPA and not wep? Try changing TKIP to other options.

Hope that helps,
GCoffee.

---

### Post by PPAAUULL on 2008-05-22
I have tried that. The only two encryption choices I have is Automatic and TKIP and from what I have tested it tries to detect the type and it does a pretty good job.
I am also sure that it is WPA and not WEP. Do you think there may be a compatibility issue with the security and encryption and card driver? I did use the ndiswrapper for the drive.

---

