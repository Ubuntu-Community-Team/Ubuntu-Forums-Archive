---
title: "Privoxy not starting on every reboots"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by duceduc on 2011-10-23
I have upgraded my privoxy to 3.0.17 and now it doesn't start on boot. I can manually start it, however. The docs is saying to put rc.privoxy in rc.local. I'm not sure how to do this since rc.local is a file and it contains some iptable lines.

---

### Post by vasa1 on 2011-10-23
> **duceduc said:**
> I have upgraded my privoxy to 3.0.17 and now it doesn't start on boot. I can manually start it, however. The docs is saying to put rc.privoxy in rc.local. I'm not sure how to do this since rc.local is a file and it contains some iptable lines.

Hi!
Check out this thread:
[http://ubuntuforums.org/showthread.php?p=11208422#post11208422](http://ubuntuforums.org/showthread.php?p=11208422#post11208422)
and
```
sudo service privoxy restart
```

---

### Post by duceduc on 2011-10-23
Thanks for the reply. I am running a server edition and do not have a gui.

---

### Post by duceduc on 2011-10-25
I got it working by adding this line to /etc/rc.local

> /bin/sleep 20 && /etc/init.d/privoxy start

---

