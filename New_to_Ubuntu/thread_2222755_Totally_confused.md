---
title: "Totally confused"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by bobmac on 2014-05-08
Folks,

I am now totally confused! I have been running version 12.04 LTS since it was released (complete with all the latest updates). However, I notice that there is talk all over the place about version 14.04 LTS.

I have my settings set to:
'Automatically check for updates' (Daily),
'Notify me of a new Ubuntu version:' (For long-term support versions), 

but I haven't received notification of this new version.
What have I done wrong that I haven't received this notification.

I note also, that some people are commenting that before installing the new version that version 12.04.4 needs to be installed. I've never heard of this version.

Can someone explain my confusion.

Regards,

Bob

---

### Post by deadflowr on 2014-05-08
14.04 won't be available for 12.04 users until July.
So don't expect it to show up any time soon.

If you have kept your system up-to-date, you should be on 12.04.4.
```
lsb_release -a
```

If you wanted to upgrade to 14.04 now, you would have to either upgrade through the longer way of going to 12.10 then to 13.10 and then 14.04.
Or you would have to run "update-manager -d" The -d means development, as in the method to direct upgrade from 12.04 to 14.04 is still considered under development and as such isn't quite ready.

More confused, or less confused?

---

### Post by bobmac on 2014-05-08
Deadflowr,

Many thanks for your quick reply and info. I won't bother reading anything else wrt 14.04, I'll just wait for it to appear. And thanks for showing how to view the latest version on my system.
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise

Regards,

Bob
PS I'll close the thread now, thanks again.

---

### Post by mastablasta on 2014-05-08
you will get the notification when 14.04.1 is out - this of it as being notified after SP1 is out to keep it stable :-)

you can trigger upgrade earlier if you desire. i owuld suggets to do a test using live session first to make sure all works.

---

