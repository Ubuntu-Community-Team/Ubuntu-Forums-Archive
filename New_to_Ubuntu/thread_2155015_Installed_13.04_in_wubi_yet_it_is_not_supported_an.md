---
title: "Installed 13.04 in wubi yet it is not supported anymore-how the heck that happen?"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by davidcholo on 2013-06-16
Hey guys, I don't really know what happened. Some sites and ubuntu users say that wubi is not supported in 13.04 anymore. But how the heck did I do it then?
Will it be bad in the future? I hope not.
Please tell me somthing to do to avoid any problems. Thank you guys.

---

### Post by monkeybrain2012 on 2013-06-16
Not supported means there is no entity in charge of ensuring that it works and release fixes if it fails, but it doesn't mean it is guaranteed not to work. :) BTW why would you want to install Ubuntu with WUBI anyway?

---

### Post by Cheesemill on 2013-06-16
Also Wubi is being dropped because it doesn't work with GPT partitioned drives, all new machines that come with Windows 8 preinstalled are like this.

If your machine has Windows 7 or if you upgraded to Windows 8 from 7 then you are using the old msdos partitioning system, this ***does*** still work with Wubi.

---

### Post by davidcholo on 2013-06-16
> **monkeybrain2012 said:**
> Not supported means there is no entity in charge of ensuring that it works and release fixes if it fails, but it doesn't mean it is guaranteed not to work. :) BTW why would you want to install Ubuntu with WUBI anyway?

Now I know. :) NO sir, I actually wanted it to install while in ubuntu itself. But after like ticking the check boxes and tick continue, it restarted and booted in windows. Then it continued to install there. Maybe because I used universal usb installer? mmm, I don't really know things much about this

---

### Post by Sef on 2013-06-16
> [COLOR=#000000] I actually wanted it to install while in ubuntu itself. But after like ticking the check boxes and tick continue, it restarted and booted in windows. Then it continued to install there. Maybe because I used universal usb installer?[/COLOR]

WUBI is meant to install to Windows, not Ubuntu. If you want to install another Linux, then virtualize.

---

