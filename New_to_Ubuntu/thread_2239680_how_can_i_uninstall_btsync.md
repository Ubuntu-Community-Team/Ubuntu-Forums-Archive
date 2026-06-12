---
title: "how can i uninstall btsync?"
date: 2014-08-15
forum: New to Ubuntu
---

### Post by gnormal on 2014-08-15
the install that i performed worked great.  i answered a series of prmpts and when i finally accessed the interface at 127.0.0.1:8888 it worked fine.
days later i rebooted but by then forgot the password i had set (was it default?) so im locked out of configuring it.
i deleted the config file but it still prompts for login :(
so i installed desktop version (over server) but it never stepped me thru the prompts so i dont know if that really happened.
now my browser is still asking me for btsync login and i still dont know it.
so id like to start over with the installation.

how does one start fresh in ubuntu?
thanks

---

### Post by TheFu on 2014-08-15
Boot off a liveCD or usb-flash drive and reinstall.
During the install, tell it to reformat every partition. That will completely wipe everything. All data, programs, settings, will be gone, completely.  Be careful if there is anything on the drive you don't want deleted. If so, make a backup of it first.

---

### Post by carrington2 on 2014-08-15
You can uninstall BitTorrent Sync from your computer by using the Add/Remove Program feature in the Window's Control Panel.

---

### Post by sandyd on 2014-08-15
> **gnormal said:**
> the install that i performed worked great.  i answered a series of prmpts and when i finally accessed the interface at 127.0.0.1:8888 it worked fine.
days later i rebooted but by then forgot the password i had set (was it default?) so im locked out of configuring it.
i deleted the config file but it still prompts for login :(
so i installed desktop version (over server) but it never stepped me thru the prompts so i dont know if that really happened.
now my browser is still asking me for btsync login and i still dont know it.
so id like to start over with the installation.

how does one start fresh in ubuntu?
thanks
Do you want to reinstall btsync or ubuntu?

By default, btsync has local files in ~/.btsync

Delete that directory and all should be golden.

---

