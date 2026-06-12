---
title: "Upgraded to 10.10 - Won't boot"
date: 2012-04-08
forum: New to Ubuntu
---

### Post by NewClim on 2012-04-08
Hi all,
 
I upgraded to 10.10 today but it won't boot. I can boot into safe mode. My computer is a Satellite L505D-S5965.
 
I can't load a screenshot so I'm posting a picture.
 
Output amounts to:
 
Failed to load module "ati" (module does not exist, 0)
Failed to load module "vesa" (module does not exist, 0)
Failed to load module "fbdev" (module does not exist, 0)
NO Drivers available.
 
Fatal server error:
no screens found
 
Please consult the The X.Org Foundation support etc etc.
 
Please also check the log file at "/var/log/Xorg.0.log" for additonal information.
 
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.
 
 
 
Xorg.failsafe.log looks something like this:
GConf Error: Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon.... etc. etc
 
 
Thank you all for any help you can provide!

---

