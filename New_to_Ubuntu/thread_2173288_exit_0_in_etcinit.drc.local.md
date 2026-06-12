---
title: "exit 0 in /etc/init.d/rc.local"
date: 2013-09-08
forum: New to Ubuntu
---

### Post by oapeter on 2013-09-08
Hello!

I have an HP dv6 laptop with hybrid graphics, and I'm trying to set up a script that I've found on this page: [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

Specifically the part that says: 
> "To  have permanent write permissions to the switch file, add the following  line, replacing USERNAME with your username, to /etc/init.d/rc.local: 
```
chown USERNAME /sys/kernel/debug/vgaswitcheroo/switch
```

right before the "exit 0" line. This gives you exclusive permission to switch GPUs."

When I edit /etc/init.d/rc.local, there is no "exit 0" line. 

Is there a new/different solution for doing this, or is there something I'm not understanding correctly?

Even if I can't get the script from that page working, I'd at least like to be able to write my own scrips to change cards without having to be logged in as root every time.

Thanks a lot!

---

### Post by Bucky Ball on 2013-09-08
*Thread moved to **Multimedia & Video**.*

Welcome. You'll probably have better luck here with this two part thread. You are primarily asking about getting your hybrid graphics up, though. Some of the community links are somewhat dated.

---

### Post by Elfy on 2013-09-09
moved back

---

### Post by steeldriver on 2013-09-09
In Ubuntu/Debian you should probably use /etc/rc.local (which is called from /etc/init.d/rc.local) - this is where you will find the 'exit 0'

However I don't really agree with the philosophy of having a particular user take ownership of a system file at boot time - *nix is inherently multi-user (even if you happen not to be using it that way).

---

### Post by oapeter on 2013-09-10
Thanks for the response! You're correct, there was just an "exit 0" line in that file. However, I added the line of code with my username into the file, made it executable, and restarted the computer. I still wasn't able to send commands to /sys/kernel/debug/vgaswitcheroo/switch without logging in as root. 

I suppose that's not really the purpose of this thread, though.
Thanks again!

---

