---
title: "Missing XFCE Panels on Install"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by beejaycee on 2008-05-03
On my older Compaq laptop, I upgraded from Ubuntu 7.10 to 8.04.  8.04 seemed to be more resource intensive so I thought I'd try using the xfce desktop environment.  If I remember correctly, I did "sudo apt-get update && apt-get install xubuntu-desktop".  It installed fine but when I tried to log out of Ubuntu and into Xubuntu, I got a blue screen with about 4 icons.  I uninstalled everything and tried again but got the same results.  Next I used ALT-F2 to run xfce4-panel and then was able to add 2 panels which I then configured as best I could. But I would prefer to have the default panels with the default layout that SHOULD be present.  Can anyone point me in the right direction?

Thanks.

---

### Post by blithen on 2008-05-03
> **beejaycee said:**
> On my older Compaq laptop, I upgraded from Ubuntu 7.10 to 8.04.  8.04 seemed to be more resource intensive so I thought I'd try using the xfce desktop environment.  If I remember correctly, I did "sudo apt-get update && apt-get install xubuntu-desktop".  It installed fine but when I tried to log out of Ubuntu and into Xubuntu, I got a blue screen with about 4 icons.  I uninstalled everything and tried again but got the same results.  Next I used ALT-F2 to run xfce4-panel and then was able to add 2 panels which I then configured as best I could. But I would prefer to have the default panels with the default layout that SHOULD be present.  Can anyone point me in the right direction?

Thanks.
Try installing xubuntu-default-settings
```
sudo apt-get install xubuntu-default-settings
```

---

### Post by beejaycee on 2008-05-03
Thanks but no luck.  Running "sudo apt-get install xubuntu-default-settings" returns "xubuntu-default-settings is already the newest version."

I read that for Ubuntu, to [revert to the default panels]("http://ubuntuforums.org/showthread.php?p=4785823#post4785823"), I could remove the .conf directory.  Is there an equivalent for Xubuntu?

---

