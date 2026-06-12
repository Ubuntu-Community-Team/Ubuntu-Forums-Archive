---
title: "dbus-send ... UPower.suspend can be used for Ubuntu server also?"
date: 2012-08-09
forum: New to Ubuntu
---

### Post by pneum on 2012-08-09
Can I use the following command for Ubuntu server 12.04 LTS 32bit (with some package installation if needed) ?

dbus-send --system --print-reply --dest="org.freedesktop.UPower" /org/freedesktop/UPower org.freedesktop.UPower.Suspend

For my case, it worked for Ubuntu desktop 12.04 LTS 32bit but I'd like to know if it also works for the server version .

My goal is to build a server and to use WoL to wake it up. I tried WoL by following posts here and there but failed. So I installed desktop version for testing purpose and noticed that WoL works only when the desktop is suspended using the above command (though it still has another issue I posted in another thread). I used only pm-suspend and did not try the above command when I tested the server version.

( Actually I failed to understand what the above command means though I tried to understand the freedesktop website. I could install the server version and test it by myself but if the above command does not work for the server version, then I need to re-install the desktop version, so I'd appreciate your teaching. )

---

### Post by pneum on 2012-08-10
I re-installed the server version and tried the above "dbus-send ... UPower.Suspend" command and the machine was suspended but then WoL did not work. For both desktop and server versions, I did not setup any special things. What would be the difference between the desktop version and the server version in regard to WoL?

---

