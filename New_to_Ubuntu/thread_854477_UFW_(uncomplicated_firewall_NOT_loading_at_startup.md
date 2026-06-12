---
title: "UFW (uncomplicated firewall NOT loading at startup).."
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Mark.H on 2008-07-09
I use ufw and have folowed the commands to run the firewall at startup etc.

I also check if ufw is enabled and loaded by typing (in Terminal)

sudo ufw status: and get this output:  Firewall not loaded

I even repeat the command sudo ufw enable

every time i start my system, and repeat the command ufw status and it always says

Firewall NOT loaded..

What do you think is causing this problem and do you think I have NO firewall what so ever??

---

### Post by kansasnoob on 2008-07-09
I personally decided that for a single computer (not networked in any way) it's best just to depend on iptables just as it installs by default.

I do have Firestarter installed but I left the defaults just as they are out-of-the-box. That way I can see just by looking at the log what is being blocked etc. (It doesn't launch at startup, but I don't care)

Just my opinion though.

---

